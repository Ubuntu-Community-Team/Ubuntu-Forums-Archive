---
title: "Face Of Mankind"
date: 2010-04-26
forum: Wine
---

### Post by peterj on 2010-04-26
So I post in anticipation of this being a mission. From preliminary searches it seems that wine will run Face of Mankind -a mmorrpg. However it will not install patches, and the game refuses to run without most updated version. 

I am not aware of anybody who has managed to get this game running on Ubuntu thus far. I am wondering whether anybody here has experience manually installing patches and if they could advice me on how to do so? 

As I commence this quest I will use this thread to annoy you all with buggy questions ;)

---

### Post by AllRadioisDead on 2010-04-26
Post the terminal output.

---

### Post by peterj on 2010-04-26
Terminal won't help so far. Heres the problem:

Patch downloads fails. Right now their server is down, when it comes back up I'll try again and show you the patch log. 

I manually downloaded all the patches and put them in the appropriate folder. However the remote launcher still thinks I'm running an early version of the game. Basically I either need to download the patches through the launcher, or find a way to tell the launcher I am up to date and don't require patches. 

The patch fail log is optimal - I'll post as soon as I can.

---

### Post by peterj on 2010-04-26
14:56:18.588	04/26/2010	Connection to server closed
14:56:18.601	04/26/2010	Initializing ...
14:56:18.604	04/26/2010	Initialization done (3ms)
14:56:38.958	04/26/2010	Connection to server closed
14:56:38.958	04/26/2010	Connection to server closed
14:56:41.644	04/26/2010	Update start.................................
14:56:41.645	04/26/2010	Trying to connect to server <fompatcheu.nexeontech.com> ...
14:56:41.993	04/26/2010	Connection to server established
14:56:41.993	04/26/2010	Update step 1
14:56:41.993	04/26/2010	Connection Time: 348ms
14:56:41.994	04/26/2010	Get remote file version from File: launcherversion.txt
14:56:42.115	04/26/2010	Remote file version: 1.0.2.6
14:56:42.116	04/26/2010	Update step 2
14:56:42.116	04/26/2010	Get remote file version from File: version.txt
14:56:42.244	04/26/2010	Remote file version: 1.5.4.3
14:56:42.244	04/26/2010	Update step 3
14:56:44.315	04/26/2010	Get patch location from File: version.txt
14:56:44.443	04/26/2010	patch location found.
14:56:44.443	04/26/2010	Get patch file information
14:56:44.579	04/26/2010	patch location found.
14:56:44.579	04/26/2010	Patch file information: Filename=1521.lzr Checksum=B520D1E8
14:56:44.580	04/26/2010	Get patch file information
14:56:44.719	04/26/2010	patch location found.
14:56:44.719	04/26/2010	Patch file information: Filename=1522.lzr Checksum=A54683B0
14:56:44.721	04/26/2010	Get patch file information
14:56:44.863	04/26/2010	patch location found.
14:56:44.863	04/26/2010	Patch file information: Filename=1523.lzr Checksum=371DE81D
14:56:44.865	04/26/2010	Get patch file information
14:56:44.999	04/26/2010	patch location found.
14:56:44.999	04/26/2010	Patch file information: Filename=1524.lzr Checksum=38C4C4BF
14:56:45.001	04/26/2010	Get patch file information
14:56:45.189	04/26/2010	patch location found.
14:56:45.189	04/26/2010	Patch file information: Filename=1525.lzr Checksum=A4F75C9D
14:56:45.190	04/26/2010	Get patch file information
14:56:45.928	04/26/2010	patch location found.
14:56:45.928	04/26/2010	Patch file information: Filename=1526.lzr Checksum=1AE8CABE
14:56:45.929	04/26/2010	Get patch file information
14:56:46.104	04/26/2010	patch location found.
14:56:46.104	04/26/2010	Patch file information: Filename=1527.lzr Checksum=B682561F
14:56:46.105	04/26/2010	Get patch file information
14:56:46.268	04/26/2010	patch location found.
14:56:46.268	04/26/2010	Patch file information: Filename=1528.lzr Checksum=8C019049
14:56:46.269	04/26/2010	Get patch file information
14:56:46.408	04/26/2010	patch location found.
14:56:46.408	04/26/2010	Patch file information: Filename=1529.lzr Checksum=9B9B661C
14:56:46.409	04/26/2010	Get patch file information
14:56:46.560	04/26/2010	patch location found.
14:56:46.560	04/26/2010	Patch file information: Filename=1530.lzr Checksum=223C5BBB
14:56:46.561	04/26/2010	Get patch file information
14:56:46.712	04/26/2010	patch location found.
14:56:46.712	04/26/2010	Patch file information: Filename=1531.lzr Checksum=109FF5FC
14:56:46.713	04/26/2010	Get patch file information
14:56:46.847	04/26/2010	patch location found.
14:56:46.847	04/26/2010	Patch file information: Filename=1532.lzr Checksum=5E5E52DB
14:56:46.849	04/26/2010	Get patch file information
14:56:46.996	04/26/2010	patch location found.
14:56:46.996	04/26/2010	Patch file information: Filename=1533.lzr Checksum=ED90F423
14:56:46.997	04/26/2010	Get patch file information
14:56:47.135	04/26/2010	patch location found.
14:56:47.136	04/26/2010	Patch file information: Filename=1534.lzr Checksum=96A37209
14:56:47.137	04/26/2010	Get patch file information
14:56:47.273	04/26/2010	patch location found.
14:56:47.274	04/26/2010	Patch file information: Filename=1535.lzr Checksum=E4457B9A
14:56:47.275	04/26/2010	Get patch file information
14:56:47.432	04/26/2010	patch location found.
14:56:47.432	04/26/2010	Patch file information: Filename=1536.lzr Checksum=AC459FC6
14:56:47.433	04/26/2010	Get patch file information
14:56:47.567	04/26/2010	patch location found.
14:56:47.567	04/26/2010	Patch file information: Filename=1537.lzr Checksum=6EAFC0A6
14:56:47.569	04/26/2010	Get patch file information
14:56:47.715	04/26/2010	patch location found.
14:56:47.715	04/26/2010	Patch file information: Filename=1538.lzr Checksum=8A0CBA74
14:56:47.717	04/26/2010	Get patch file information
14:56:47.855	04/26/2010	patch location found.
14:56:47.855	04/26/2010	Patch file information: Filename=1539.lzr Checksum=A540461E
14:56:47.857	04/26/2010	Get patch file information
14:56:47.995	04/26/2010	patch location found.
14:56:47.996	04/26/2010	Patch file information: Filename=1540.lzr Checksum=1135DC03
14:56:47.997	04/26/2010	Get patch file information
14:56:48.131	04/26/2010	patch location found.
14:56:48.131	04/26/2010	Patch file information: Filename=1541.lzr Checksum=D26CF4E8
14:56:48.133	04/26/2010	Get patch file information
14:56:48.267	04/26/2010	patch location found.
14:56:48.267	04/26/2010	Patch file information: Filename=1542.lzr Checksum=26D55A14
14:56:48.268	04/26/2010	Get patch file information
14:56:48.399	04/26/2010	patch location found.
14:56:48.399	04/26/2010	Patch file information: Filename=1543.lzr Checksum=D9381D02
14:56:48.401	04/26/2010	Update step 4
14:56:48.433	04/26/2010	Download file  'versions/1521/1521.lzr' to 'C:\Program Files\Face of Mankind\PatchTmp\Download\1521.lzr'
14:56:50.054	04/26/2010	Downloading file failed
14:56:52.736	04/26/2010	Update start.................................
14:56:52.736	04/26/2010	Update step 1
14:56:52.736	04/26/2010	Connection Time: 0ms
14:56:52.737	04/26/2010	Get remote file version from File: launcherversion.txt
14:56:52.868	04/26/2010	Remote file version: 1.0.2.6
14:56:52.868	04/26/2010	Update step 2
14:56:52.868	04/26/2010	Get remote file version from File: version.txt
14:56:52.991	04/26/2010	Remote file version: 1.5.4.3
14:56:52.992	04/26/2010	Update step 3

---

### Post by peterj on 2010-04-26
The launcher can find the files, It downloads the names of each patch to temporary internet files in wine/localsettings. 

I'm thinking that it tries to use IE to download them?

---

### Post by peterj on 2010-04-26
I really would appreciate any suggestions on this one folks.

---

### Post by cogadh on 2010-04-26
ihermit was right to start with, we need the terminal output to see what Wine says about this. The game's messages or error log is mostly useless at this point, but if you run the app from the terminal, Wine will give us a world of information on what is happening "on the inside" so to speak.

---

### Post by peterj on 2010-04-26
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoStoreResponse (0x2558000)->(0x32db7c)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x2558000)->(0x32db7c)
fixme:mshtml:nsChannel_GetResponseHeader (0x2558000)->(0x32db44 0x32dad4)
fixme:mshtml:nsChannel_GetResponseHeader (0x2558000)->(0x32dc64 0x32dc84)
fixme:mshtml:nsChannel_IsNoStoreResponse (0x2565908)->(0x32e420)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x2565908)->(0x32e41c)
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {000214d1-0000-0000-c000-000000000046}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented group {de4ba900-59ca-11cf-9592-444553540000}
fixme:shdocvw:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:shdocvw:InPlaceFrame_SetStatusText (0x146fc0)->(L"Done")
fixme:mshtml:nsChannel_IsNoStoreResponse (0x25268b8)->(0x32e3a0)
fixme:mshtml:nsChannel_IsNoCacheResponse (0x25268b8)->(0x32e39c)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
err:richedit:ReadStyleSheet skipping optional destination
fixme:richedit:ME_HandleMessage EM_SETMARGINS: stub
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x146f20)->(0x12d840)
^Cpeter@BOX:~/.wine/dosdevices/c:/Program Files/Face of Mankind$ ^C

---

### Post by peterj on 2010-04-26
Haha, love the code smiley faces!

---

### Post by cogadh on 2010-04-26
That's a whole lotta "wine don't do that" messages. Unfortunately, that usually means that you'll have to wait for Wine to mature more before it will work. A quick check of Wine's Application Database shows that the game hasn't even been tested in Wine before, so its not really surprising that it doesn't work well. One question though, what version of Wine are you using?

---

### Post by peterj on 2010-04-26
I wasn't being overly optimistic, but a couple of people have tried and the patch update was the biggest problem they had. I guess it'll be virtual box instead.

---

