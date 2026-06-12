---
title: "[SOLVED] BabasChess - I can't get it working"
date: 2008-12-12
forum: Wine
---

### Post by LeeLgrqst on 2008-12-12
I just installed Wine 1.1.10 on 8.10 64.

I have a dual boot with Vista.

I'm trying to get my BabasChess to run in Ubuntu.
BabasChess is in the Wine AppDB, and is Platinum.

I've downloaded the recommended zip version, and right clicked on the .exe and selected start with Wine.  The slash screen starts up and then an error report pops up.  

I've been searching for a way to fix this on the Internet, but have not found anything that helps me, which tells me that the solution must be something easy.

One thing I have done is try to start the program in the terminal, and this is what it says:

 lee@lee-laptop:~$ wine \home\lee\Desktop\BabasChess\BabasChess.exe
wine: could not load L"C:\\windows\\system32\\homeleeDesktopBabasChessBabasChess.exe": Module not found
lee@lee-laptop:~$ 

I just recently switched from Windows to Linux, so I still don't know very much about this yet.  Any help anybody can provide will help me out a lot.

---

### Post by jacksaff on 2008-12-12
Which version of Babas have you tried to install? I have it working on 64bit intrepid and it has been pretty much perfect for months of wine updates. You might need to tweak the version of windows that wine is pretending to be. You also might want to try the versions of babas for earlier windows.

The command you are typing into the terminal will not get you to run babas - the command is not telling the shell the correct place to find the .exe. You need to find out where the babas.exe has been installed to (if yo've got it installed at all). 

If the install worked you should now have the following file in your home

/home/USER_NAME/.wine/drive_c/Program Files/BabasChess

You can browse to this normally using a file browser but remember that .wine is a hidden folder and so you will have to enable viewing hidden folders before you can see it and click it.

By default the following should work in the terminal after adding in your linux user name

wine "/home/YOUR_USER_NAME/.wine/drive_c/Program Files/BabasChess/BabasChess.exe"

Please post any error messages you get if it isn't working.

---

### Post by LeeLgrqst on 2008-12-13
Accidentally posted twice.

---

### Post by LeeLgrqst on 2008-12-13
I downloaded the XP/Vista version.
Opened the install file with "Wine Windows Program Loader".
The program said it was going to install in c:\program files\babaschess\
I found the program in /home/lee/.wine/dosdevices/c:/Program Files/BabasChess/

So in the terminal I typed:
 wine "/home/lee/.wine/dosdevices/c:/Program Files/BabasChess/BabasChess.exe"

and this is what popped up:
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:gdiplus:GdipCreateAdjustableArrowCap not implemented
wine: Call from 0x7b845810 to unimplemented function gdiplus.dll.GdipCreateHatchBrush, aborting

---

### Post by soluphobe on 2008-12-14
If you have this installed in Vista, you might want to copy the gdiplus.dll file over into your /.wine/drive_c/WINDOWS/system32/ file.  The same thing happens to me sometimes when I install stuff.

Also, when you type in wine commands, leave out the quotes.  You need to pass the file to wine as a param, not a path to the file (though it seemed to work in this case).

---

### Post by jacksaff on 2008-12-15
Everything in the quotes is passed as one parameter, in this case the name of the file wine should run including it's full path. As the path has a space in it (in Program Files) something has to be done to escape the space and quotes is one such option. That's how I understand it anyway.

Back on topic, if the native dll suggested above doesn't work, have you tried the win98 version of babas? It looks like your version is calling a function that wine doesn't have. Might not be there in the win98 version. I can't remember which version I have working as I'm not at home at present, but I'll check... If the dll does work, please post that too!

---

### Post by LeeLgrqst on 2008-12-15
I copied the gdiplus.dll file to /.wine/drive_c/windows/system32 and BabasChess works now.

Thanks so much for the help!

---

### Post by matteojg on 2009-01-01
I had the same problem with BabasChess crashing during set up.
Getting the gdiplus.dll into system32 folder got it up and running.
However i get a never ending list of fixmes while its running (most dealing with richedit:RichEditWndProc_common or win:SetLayeredWindowAttributes) and a couple errors concerning sound files and unknown timers.

Any help would be much appreciated...

---

### Post by freefal67 on 2009-07-11
This worked great.  Thanks for the post.  It's too bad there isn't something native that is as advanced as Babas.

---

