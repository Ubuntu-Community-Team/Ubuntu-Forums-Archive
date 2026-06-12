---
title: "Web Page Printing"
date: 2008-11-11
forum: Windows
---

### Post by rabbitCode on 2008-11-11
I need to print a web page through another page, the following is the VB script function I'm using:

Sub Print()
On Error Resume Next  
Const OLECMDID_PRINT = 6 
Const OLECMDEXECOPT_DONTPROMPTUSER = 2 
Const PRINT_WAITFORCOMPLETION = 2 
Dim oIExplorer : Set oIExplorer = CreateObject("InternetExplorer.Application") 
oIExplorer.Navigate "http://www.microsoft.com/southafrica" 
oIExplorer.Visible = 1 

Do while oIExplorer.ReadyState <> 4 
 wscript.sleep 1000 
Loop 
oIExplorer.ExecWB OLECMDID_PRINT, OLECMDEXECOPT_DONTPROMPTUSER 
              
End Sub

The function execute with no errors without the loop and doesn't print, but I get the following messae with the loop executing:
"A script on this page is causing Internet Explorer to run slowly. It it continues to run, your computer may become unresponsive." :(

---

