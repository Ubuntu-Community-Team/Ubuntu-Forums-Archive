---
title: "Invalid Path Chosen !?"
date: 2010-10-15
forum: Wine
---

### Post by Alethaeia on 2010-10-15
Hello and thank you for taking the time to read this.  I'm rather perplexed. 
So, i've gotten winamp to work in Wine, but now it's on to my current  game of choice, Diablo II.  As you may be aware, Blizzard has chosen to  allow registered players to download the game files from their site,  given they have the cd key to activate it.  This process i have been  through several times on windows and OSX machines; it's a bit trickier  here in Ubuntu.  It took me some doing, but i eventually got the  download client to run, and the hangup happens just after i choose which  directory to download into.  It says " Invavlid path chosen! "  which i  had thought at first to be a result of insufficient premissions. I then  set about adding the application to Wine's list, and even tried running  the file as an admin, and still, "Invalid path chosen!" . . . . do  applications running in Wine simply not have authority to write to the  disk ? 
~
Any help will be greatly appreciated.  I'm a linux newb, so be gentle.  Thanks again.


UPDATE: Here is the output from our dear friend terminal:
fixme:ntoskrnl:KeInitializeSpinLock 0x457d74
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:PersistStorage_InitNew (0x136258)->(0x5130c8)
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e7fb9b8, overlapped 0x7e7fb99c): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x138ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1362f4)->((null) 1 0x323d00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 25 2 0x323d14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 26 2 0x323d14 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1362f4)->(0x323d58)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x323e14 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x136500)->(L"" L"" 0 0x323e4c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 29 2 0x32f02c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1362f4)
fixme:shdocvw:ClientSite_GetContainer (0x1362f4)->(0x32ecc0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1362f4)->(0x60021b71)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 25 2 0x32ebcc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 26 2 0x32ebcc (nil))
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x3299dc, uiNumDevices=2, cbSize=12) stub!
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 28 2 0x32ee3c (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented

---

### Post by Alethaeia on 2010-10-15
Sorry for the double post, but vBulletin wouldn't let me put this in the previous post.

Interestingly, when i ran the very same command again (literally, i pressed up then enter) i got a different output:
fixme:ntoskrnl:KeInitializeSpinLock 0x457d74
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:PersistStorage_InitNew (0x136258)->(0x5130c8)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7e0219b8, overlapped 0x7e02199c): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x138ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1362f4)->((null) 1 0x323d00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 25 2 0x323d14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 26 2 0x323d14 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1362f4)->(0x323d58)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x323e14 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x136500)->(L"" L"" 0 0x323e4c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 29 2 0x32f02c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1362f4)
fixme:shdocvw:ClientSite_GetContainer (0x1362f4)->(0x32ecc0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1362f4)->(0x6003eb71)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 25 2 0x32ebcc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 26 2 0x32ebcc (nil))
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x3299dc, uiNumDevices=2, cbSize=12) stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1362f4)->((null) 28 2 0x32ee3c (nil))
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented

What does it all mean, Basil ?


Update:
When i choose the path, and click ok, the terminal gives this:
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented

---

### Post by Alethaeia on 2010-10-17
So i've poked around the intarwebs a little bit and done some fiddilng with my machine.
i learned a bit about folder ownership / filepermissions:
:~$ ls -la ~/.wine
total 880
drwxrwxrwx  4 enki enki   4096 2010-10-17 18:18 .
drwxr-xr-x 39 enki enki   4096 2010-10-17 18:18 ..
drwxrwxr-x  2 enki enki   4096 2010-10-16 23:37 dosdevices
drwxrwxr-x  4 enki enki   4096 2010-10-14 20:21 drive_c
-rw-r--r--  1 enki enki 822836 2010-10-17 18:18 system.reg
-rw-r--r--  1 enki enki     11 2010-10-16 23:12 .update-timestamp
-rw-r--r--  1 enki enki   2346 2010-10-17 18:18 userdef.reg
-rw-r--r--  1 enki enki  46352 2010-10-17 18:18 user.reg

Going further in:

:~$ ls -la ~/.wine/drive_c/"Program Files"/Diablo
total 12
drwxrwxrwx 3 enki enki 4096 2010-10-15 20:18 .
drwxrwxr-x 7 enki enki 4096 2010-10-16 23:13 ..
drwxrwxr-x 2 enki enki 4096 2010-10-15 20:18 Downloader_Diablo2_enUS

And, right down to the exe file:

:~$ ls -la ~/.wine/drive_c/"Program Files"/Diablo/Downloader_Diablo2_enUS
total 2716
drwxrwxr-x 2 enki enki    4096 2010-10-15 20:18 .
drwxrwxrwx 3 enki enki    4096 2010-10-15 20:18 ..
-rwxrwxrwx 1 enki enki 2764856 2010-10-14 22:54 Downloader_Diablo2_enUS.exe

Are the permissions set right ?

Also, i am currently updating to the latest -unstable- version of Wine, so another update will soon follow.

---

### Post by Alethaeia on 2010-10-17
Success !
I believe that updating Wine did the trick.  I had previously updated from 1.0.1 to 1.2, and the problem persisted, but here goes that download ! Thank you Wine 1.3 : )

---

