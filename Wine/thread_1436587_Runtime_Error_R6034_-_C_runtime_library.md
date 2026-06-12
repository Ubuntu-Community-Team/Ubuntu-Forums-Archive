---
title: "Runtime Error R6034 - C runtime library"
date: 2010-03-22
forum: Wine
---

### Post by issachan on 2010-03-22
Hi all,

I installed Office 2007 and while everything seemed to install correctly I keep getting a runtime error when I try to run Access. The other programs work, but Access won't start because it says it has a runtime error R6034. 

I used winetricks to get vb4run, vb5run, vb6run, and even vs6sp. It still won't work. 

Anyone know how to fix this?

---

### Post by asdfoo on 2010-03-22
which version of Wine?

terminal output?

---

### Post by issachan on 2010-03-22
My terminal says I have the latest version of Wine. I looked under the About tab (in the Configure Wine window) and it says I have 1.0.1

Here's what it says in the terminal window after attempting to run wine MSACCESS.EXE

fixme:actctx:p****_depend_manifests Could not find dependent assembly L"AceDAO"
err:module:attach_process_dlls "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Microsoft Office\\Office12\\MSACCESS.EXE" failed, status 80000003
[EMAIL="issa@issa-desktop:%7E/.wine"]issa@issa-desktop:~/.wine[/EMAIL]/drive_c/Program Files/Microsoft Office/Office12$

I have Office installed on my Windows hard drive, if I need to copy files over, I need to know what. I can't figure out what it wants. I've tried copying over some files that I thought were it but it didn't do anything.

I took a snapshot of the error message...

[IMG]http://mythandmagicstudios.com/screenshot-1.png[/IMG]

---

### Post by ajackson on 2010-03-23
> **issachan said:**
> I used winetricks to get vb4run, vb5run, vb6run, and even vs6sp. It still won't work. 
So the error message clearly shows that the problem is with Visual C++ run-times and you try installing the Visual Basic run-times to solve it?

Try installing the Visual C++ 2005 run-time using winetricks.

---

### Post by issachan on 2010-03-23
Thanks for the help!

I tried to install it but it gave me an error...

fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
The .NET Runtime Optimization Service is running.
C:\windows\temp>del /F "Del8dea.tmp"
C:\windows\temp>if exist "Del8dea.tmp" goto Repeat
C:\windows\temp>del /F "Del8dea.bat"
Sharing violation

fixme:powrprof:DllMain (0x608f0000, 0, 0x1) not fully implemented
waiting for setup to finish
Install of vc2005trial done
winetricks done.

I tried the other variation and it said the same thing.

What should I do now? 

Thanks again :KS

---

### Post by ajackson on 2010-03-23
> **issachan said:**
> Thanks for the help!

I tried to install it but it gave me an error...

fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 16
The .NET Runtime Optimization Service is running.
C:\windows\temp>del /F "Del8dea.tmp"
C:\windows\temp>if exist "Del8dea.tmp" goto Repeat
C:\windows\temp>del /F "Del8dea.bat"
Sharing violation

fixme:powrprof:DllMain (0x608f0000, 0, 0x1) not fully implemented
waiting for setup to finish
Install of vc2005trial done
winetricks done.

I tried the other variation and it said the same thing.

What should I do now? 

Thanks again :KS
The only error I see there is it failing to tidy the temporary directory it used for the install.

---

### Post by godspeedmav on 2010-05-08
Hello, 

I'm a Ubuntu noobie. Just started using 1 week ago. I'm also having the same problem. I can't get MS Access to open even though I did what they showed in this link 

[http://ubuntuforums.org/showthread.php?t=1173365](http://ubuntuforums.org/showthread.php?t=1173365)

I did what they told me to do in step (F) Installing Winetricks till steop (G) Configure Wine

Now that I have done step (F) I see one more override in the libraries of wine configuration. msvcr80, I think it is set to native then Builtin therefore it shows msvcr80(native,builtin)

Please help me! I still can't run MS Access :cry:

---

### Post by ajackson on 2010-05-09
You'd probably get more help posting in that thread since it is that how-to you are following.

---

