---
title: "C#, MonoDev, System Time &amp; Date Problem"
date: 2012-09-05
forum: Ubuntu Application Development
---

### Post by Rigsmith on 2012-09-05
Hi

I am trying to change the system time/date on Ubuntu operating system from c# code. I am using MonoDevelop Complier.

My end user should never see the operating system (FluxBox) nor will they be provided the passwords for the system so I must build my own control to adjust the time/date.

I am very stuck and have been on google and trying various things for weeks and I worry now that I am not going to find a solution without help

I have seen two methods and I cannot implement them

I have tried the following.

System.Diagnostics.Process.Start(“Sudo date 031212001986”);

This fails because it cannot find a TTY or password. 

I have also tried to use DLL import on Kernel32.dll, Enter point = “SetLocalTime”. This just totally fails as it cannot find the Entry point (All though it loads the DLL). I guess this method has been intended for C# on windows.

I have tried quite a few variations and I am just totally stuck/confused. I really need to ability to change the system clock without the user knowing passwords and having excess to the operating system.

Any method will do, I couldn’t care if its 1000 lines of code or 2 lines. I just really need to adjust this clock and date urgently.

---

### Post by tienlbhoc on 2012-09-05
you can save in a file script (execute checked) and open this file.
If you want change command, open and rewrite this file, run.

---

