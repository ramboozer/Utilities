Utilities
lululu im a noob below is a poorly written usage example.
this is one of many possiblities

```
Missing minior things suchas
System.Windows.Forms
System.Threading
Initialization & Form data
```

=====================
Utilities Library
Usage example
=====================


```c#
Using Flux.Utilities;
namespace Flux.Test
{
    public partial class Test : Form
    {
          public Test
          {
                Logging.OnDebug += Logging_OnWrite;
                Logging.OnWrite += Logging_OnWrite;
          }
          
          private void Logging_OnWrite(string message, Color col)
          {
            if(InvokeRequired){
              Invoke(new Logging.WriteDelegate(Logging_OnWrite), message, col);
            }
            else{
                  // You can use whatever you want here
                  // I normally just use a rtb on a seprate tab or window
                  rtbLog.SelectionColor = col;
                  rtbLog.AppendText(message + Environment.NewLine);
                  rtbLog.ScrollToCaret();
                }
          }
          
          private void Test_Load(object sender, EventArgs e)
          {
            Logging.Write(Color.blue, "The form has loaded!");
          }
    }
}
```
