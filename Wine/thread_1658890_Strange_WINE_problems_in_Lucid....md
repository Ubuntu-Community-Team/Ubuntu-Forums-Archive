---
title: "Strange WINE problems in Lucid..."
date: 2011-01-03
forum: Wine
---

### Post by lotster on 2011-01-03
Hi all

I just installed WINE 1.2 in Ubuntu Lucid (using Synaptic).  It seems to be fine, but when I try to run a Windows program (right-click the .exe and choose to run using WINE) after a few seconds the screen flickers slightly, the mouse pointer changes to the "busy" pointer (the moving circle thing), and after a few more seconds it changes back, doing nothing.

I know that some programs don't work in WINE, but I've tried about 7 different programs, including E-Sword, Freelancer, and DVD Shrink, all of them doing exactly the same thing, and all of them used to work in WINE under my previous Karmic installation.

Oh yeah, I also tried running it from the terminal, but with no error messages.  It just popped back to the command line after the above-mentioned screen flickers and stuff.

Anyone have any ideas?  I'd really appreciate it...

---

### Post by cogadh on 2011-01-03
Wine cannot possibly produce no error message in the terminal, sounds like something is wrong with the Wine installation itself. I'd purge it and re-install first, making sure to delete or re-name your .wine directory so you are sure to start fresh.

---

### Post by lotster on 2011-01-03
Thanks for the reply; I did that, and it's still doing the same thing, but this time at least I get error messages in the Terminal.  Here's what it says with e-Sword:

err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z:\\home\\lotta\\e-Sword\\e-Sword.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\lotta\\e-Sword\\e-Sword.exe" failed, status c0000135

And with Freelancer:

err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\home\\lotta\\Freelancer\\EXE\\DALib.dll") not found
err:module:import_dll Library DALib.dll (which is needed by L"Z:\\home\\lotta\\Freelancer\\EXE\\Common.dll") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\home\\lotta\\Freelancer\\EXE\\Common.dll") not found
err:module:import_dll Library Common.dll (which is needed by L"Z:\\home\\lotta\\Freelancer\\EXE\\Freelancer.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\home\\lotta\\Freelancer\\EXE\\DALib.dll") not found
err:module:import_dll Library DALib.dll (which is needed by L"Z:\\home\\lotta\\Freelancer\\EXE\\Freelancer.exe") not found
err:module:import_dll Library MSVCP60.dll (which is needed by L"Z:\\home\\lotta\\Freelancer\\EXE\\Freelancer.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\lotta\\Freelancer\\EXE\\Freelancer.exe" failed, status c0000135

Can you maybe make sense of any of it?

Thanks again!

---

### Post by cogadh on 2011-01-03
Some sense. You need to install the MS Visual C++ and Visual Basic runtimes to make the MSVBVM60.DLL and MSVCP60.dll errors go away. You can do that easily with [winetricks]("http://wiki.winehq.org/winetricks") (install the vb6run and vcrun6 packages). You might still get the DALib.dll message on Freelancer after that, I'm not sure. That one is kind of odd, since that file is part of the Freelancer installation. Its possible that error is caused by one of the previous errors, so if we fix those, the DALib one will go away.

---

### Post by lotster on 2011-01-06
That did it!  Thanks again for all the help!

---

