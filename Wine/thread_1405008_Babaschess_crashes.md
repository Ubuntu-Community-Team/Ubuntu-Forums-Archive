---
title: "Babaschess crashes"
date: 2010-02-12
forum: Wine
---

### Post by LeeLgrqst on 2010-02-12
I just installed Babaschess using Wine.  Babaschess crashes all the time, and I have not found any solution to the problem online.

I have:
Ubuntu 9.10 64
Wine 1.0.1
Babaschess 4.0 for XP/Vista

I already installed the gdiplus.dll in the right place.

Here is what I copied from the terminal, there was a lot of stuff so I filtered out some of what was in there.

_a very long list of this:_
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub

_some of these mixed in:_
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:RichEditWndProc_common ECO_AUTOWORDSELECTION not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub

_and this stuff:_
fixme:richedit:RichEditWndProc_common ECO_AUTOVSCROLL not implemented yet!
fixme:richedit:RichEditWndProc_common ECO_NOHIDESEL not implemented yet!
fixme:wave:wodPlayer_Reset shouldn't have headers left
fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub

fixme:dciman:DCICreatePrimary 0x38c 0xd9128c

fixme:richedit:RichEditWndProc_common WM_STYLECHANGING: stub
fixme:richedit:RichEditWndProc_common WM_STYLECHANGED: stub
fixme:richedit:IRichEditOle_fnGetClientSite stub 0xebf110
fixme:ole:OleCreateStaticFromData (not shown), stub!
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
wine: Unhandled exception 0x40000015 at address 0x3f290023:0x0051bd33 (thread 0009), starting debugger...
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
lee@lee-desktop:~$ process  tid      prio (all id:s are in hex)
0000000c 
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
00000019 
	0000001d    0
	0000001a    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'


Then I get some message about a Runtime error.

I can provide more information if you need it.

Please help, Thanks.

---

### Post by gsmanners on 2010-02-12
Have you read the install notes? [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9602](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9602)

---

### Post by MrNatewood on 2010-02-12
BabasChess w/wine has issues with pulseaudio ALSA driver. you might want to try changing the audio driver in wine config to EsounD or OSS&padsp.

At least that's what caused the crashes to me.
You might also want to try using the latest version of wine(via PPA)

---

### Post by MrNatewood on 2010-02-12
oops double post

---

### Post by LeeLgrqst on 2010-02-13
I've tried both of the sound settings you suggested in the Wine config, and Babaschess still crashes.  I will try using the Wine from the PPA and will let you know the results.

---

