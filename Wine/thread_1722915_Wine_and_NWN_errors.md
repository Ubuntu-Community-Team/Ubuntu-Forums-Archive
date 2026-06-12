---
title: "Wine and NWN errors"
date: 2011-04-06
forum: Wine
---

### Post by Naater on 2011-04-06
Hello world. I'm here looking for help about wine errors, what they mean and how to fix whatever the problem is. This has come up over a few programs but not most and I'm going to use my Neverwinter Nights as an example. Heres the story so far:


  When first trying to open my game it crashes and an error window comes up. "The program nwmain.exe has encountered a serious problem and needs to close. We are sorry Blah blah". So the first thing I do is try to identify the problem.  
 
  On my other computer it works fine with wine and so I delete NWN and copied the "working" one over to this one. However the same problem came up. It would be natural to assume that wine is the problem but both computers have the same wine version 1.2.2.

  So I decided to run nwmain.exe in the terminal and I'm going to show you what came up:


naater@Opti-3DO:~$ cd NWN
naater@Opti-3DO:~/NWN$ wine nwmain.exe
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x151b70,0x151ae0): stub
err: ole:COMPOBJ_DllList_Add couldn't load in-process dll L"a3dapi.dll"
err: ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441} could be created for context 0x1
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x152f20,0x151ae0): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x152f20,0x151ae0): stub
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
wine: Unhandled page fault on read access to 0x00000030 at address 0x5cec74 (thread 0009), starting debugger...


  Sadly I can't read this to be honest however I see an error with a .dll file and a bit about the sound system and volume.

 sidenote: I had to put a space between ":"s and "o"s to stop the attacks of smileys

---

### Post by cogadh on 2011-04-08
First of all, NWN has a Linux native client and you shouldn't bother trying to run it through Wine at all: [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)

As for the errors, the only real errors there are the DLL ones ("fixme" errors are just developer notes that are mostly meaningless to end users) and whatever came after that unhandled page fault (there should have been much more to that part of the error). Chances are, the very first error caused the second one which in turn produce the unhandled page fault, but without the rest of the page fault error, can't really say for certain.

EDIT - Almost forgot: to get around that forum smilies problem, just use the forum CODE tags, they work just like the QUOTE tags, only they keep the plain text type formatting of the original terminal output.

---

### Post by IHeequ5i on 2011-04-09
Additional FYI:  The Linux NWN client *WILL* accept the license key from a Windows version of the game.

---

### Post by Naater on 2011-04-11
Yes, your both right. I already know that NWN has a ubuntu client I was really just using it as an example because I think it is weird that the exact same program works on one computer but not the other(The same problem comes up with other programs). And glad for the info about the dll errors. Also about the page fault... thats it! It just hangs there and does nothing it seems. Perhaps I should wait it out even longer?

  For now maybe I should drop the issue however I am  going to start a new thread in "Security Discussions" to ask about default permissions that I'm having trouble with.


-Cheers

---

