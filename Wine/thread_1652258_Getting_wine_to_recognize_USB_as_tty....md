---
title: "Getting wine to recognize USB as tty..."
date: 2010-12-24
forum: Wine
---

### Post by trinitydan on 2010-12-24
...running iTunes.

^That was deliberately left out of the title in hopes of keeping this thread technical.  Please do not post here with questions(except related to technical specifics) or moral support.  Technical support on the other hand is greatly appreciated.

The last time I was working on running iTunes in wine was using iTunes 8.02 or something.  It ran ok, but the USB was not recognized.  Using other Windows programs in Wine, I have been able to get them to successfully recognize the USB by creating a sym link so that COM=/dev/ttyS2. Then using the command ```
sudo ln -sb /dev/ttyUSB0 /dev/ttyS2
```For my DeLorme GPS to work in a map program this worked.  It did not work in iTunes.  That was about the time when I gave up on running iTunes in Wine.  I think this may be a potential method that could be used to get the USB to work with a little tweaking.  I am downloading the current iTunes right now to play around with it.

Let's try to figure this out and give the iPod fans a really Merry Christmas!

---

### Post by marin123 on 2010-12-25
could you explain how can i get my wine program to see mass storage? if i get this working, i can get rid of windows :)

---

### Post by trinitydan on 2010-12-25
The current iTunes did install for me in Ubuntu 10.10.  The sym link idea does not seem to work for devices with kernel level drivers.  It detected the device but not as an iPod.  It was interesting because I started with an empty library except one track for testing, and when I plugged in the iPod, iTunes went directly to "Adding files" and added all the music on the iPod to the music library.  I was really excited for the moment as I thought it was about to pop up the iPod in iTunes but no joy.  It did determine the gapless playback information of all the tracks on my ipod as well as find album artwork for everything, which is pretty cool in itself.  I have to admit, there are some things that just work well in iTunes. 

Next thing I tried was following this howto to enable USB support in Wine.

[http://ubuntuforums.org/showthread.php?t=697238&page=3](http://ubuntuforums.org/showthread.php?t=697238&page=3)

I paid close attention to the details posted by other users but I must have done something wrong as I currently don't seem to have any version of Wine installed.  I am going to go back to work on it a little later on and try to figure out where it went wrong.

I suspect that with this completed the iTunes/iPod sync will be at least very close to working.  The applemobiledevice service is running as well as iPodService.exe (I think this one had to be started manually).  When I did a diagnostic check on the iPod it showed that the services were working but that there was no USB and no iPod attached.  Sounds pretty promising!

Anybody have USB 2.0 support for Wine and want to try it out?

It would probably work better on a dual boot with Windows so there would be better access to drivers.  My computers are all running Linux.

Here is a thread where I am looking for help to be able to continue with my testing:
[http://ubuntuforums.org/showthread.php?t=1652768](http://ubuntuforums.org/showthread.php?t=1652768)

---

### Post by marin123 on 2010-12-28
i tried this but i couldnt get it to work, my program doesnt recognize my usb drive. since i need just program to "think" that there's usb drive (or sd card) connected, can i mount a folder as mass storage and then copy the files on usb drive? any ideas? :)
thanks!

---

### Post by Sly Cooper on 2011-01-09
Hi, I'm trying to run an Adaptec GameBridge in WINE. How do I go about getting WINE to notice the Adaptec GameBridge plugged into a USB 2.0 port

---

### Post by trinitydan on 2011-01-15
Just in case anyone is thinking of trying this, I did get the USB 2.0 patch for Wine working, but it did not work to get iTunes to recognize the iPod.  :(

---

### Post by Sly Cooper on 2011-01-15
> **trinitydan said:**
> Just in case anyone is thinking of trying this, I did get the USB 2.0 patch for Wine working, but it did not work to get iTunes to recognize the iPod.  :(


Ok, well, can you explain how you got the USB 2.0 patch for WINE to work?

Also, doesn't Banshee media player recognize the ipod?

---

### Post by ericrichards420 on 2011-01-15
I bought my niece and nephew both ipod shuffles for christmas. I tried to add them some songs and I didn't have any luck either. It seems as though Apple has made it a lot harder to add files to a mass storage device these days just so you will have to    purchase new music through them.

---

### Post by marin123 on 2011-01-15
> **trinitydan said:**
> Just in case anyone is thinking of trying this, I did get the USB 2.0 patch for Wine working, but it did not work to get iTunes to recognize the iPod.  :(

what application did you test it on? i have an app that requires direct access to an usb pen drive. could that work? can you tell us how did you apply the patch?

---

### Post by trinitydan on 2011-01-15
> **Sly Cooper said:**
> Ok, well, can you explain how you got the USB 2.0 patch for WINE to work?

Also, doesn't Banshee media player recognize the ipod?

[http://ubuntuforums.org/showthread.php?t=697238&page=3](http://ubuntuforums.org/showthread.php?t=697238&page=3)

I used the directions in post number 21, including the important bits added by sysghost to patch Wine.  

Yes, Banshee supports all three of my iPods, since they aren't that new.  I usually just use RhythymBox.  The reason I was excited to get iTunes working with the USB is that I know a lot of users iPods will not work with Banshee or RhythymBox.

> **marin123 said:**
> what application did you test it on? i have an app that requires direct access to an usb pen drive. could that work? can you tell us how did you apply the patch?

I have not done any more testing except with iTunes, so I can't say how well the patches work, but I was successful in applying the patches and installing the patched Wine.  I had a minor hiccup with installation that was covered [here]("http://ubuntuforums.org/showthread.php?t=1652768").

---

### Post by marin123 on 2011-01-21
trinitydan, can you tell me when you run wine application through terminal, do you get error report that L"Usbhub" failed to load? i get that message and thats why i dont have usb support. i tried copying usbhub.sys from my windows, but theyre 64 bit, and now i need to get same files, only from 32 bit windows... i'll let you know how it went :)

---

### Post by trinitydan on 2011-01-21
> **trinitydan said:**
>   Using other Windows programs in Wine, I have been able to get them to successfully recognize the USB by creating a sym link so that COM=/dev/ttyS2. Then using the command ```
sudo ln -sb /dev/ttyUSB0 /dev/ttyS2
```For my DeLorme GPS to work in a map program this worked.  It did not work in iTunes.
Just out of curiosity, did you try just making a sym link?  It did work for my GPS.  It doesn't work with devices that need Kernel level drivers.
> **marin123 said:**
> trinitydan, can you tell me when you run wine application through terminal, do you get error report that L"Usbhub" failed to load? i get that message and thats why i dont have usb support. i tried copying usbhub.sys from my windows, but theyre 64 bit, and now i need to get same files, only from 32 bit windows... i'll let you know how it went :)
Sounds like there might be potential there.  I am not around the computer with the patched wine on it right now, but hopefully at some point today I can check out the error messages and I'll let you know.

---

### Post by trinitydan on 2011-01-21
I don't seem to have that particular error unless I missed it in this mess of errors.
```
ubuntu@ubuntu:~$ wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x4240000 0 0x32f690 4
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x175b60,0x175a60): stub
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:win:EnumDisplayDevicesW ((null),0,0x32e8a0,0x00000000), stub!
fixme:win:DisableProcessWindowsGhosting : stub
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x6002e 0x00000000
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0xa3ea680,0xa3eaff8): stub
fixme:advapi:GetCurrentHwProfileA (0x32e430) semi-stub
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {063d34a4-bf84-4b8d-b699-e8ca06504dde} could be created for context 0x17
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {063d34a4-bf84-4b8d-b699-e8ca06504dde} could be created for context 0x17
fixme:win:RegisterDeviceNotificationW (hwnd=0x6002e, filter=0x32e620,flags=0x00000000) returns a fake device notification handle!
fixme:win:RegisterDeviceNotificationW (hwnd=0x6002e, filter=0x32e618,flags=0x00000000) returns a fake device notification handle!
Set args[3] to --parentPipe
fixme:service:EnumServicesStatusA 0xa431338 type=30 state=3 (nil) 0 0x32f0a8 0x32f0ac 0x32f0b4
fixme:service:EnumServicesStatusA 0xa431338 type=30 state=3 (nil) 0 0x32ef30 0x32ef34 0x32ef3c
fixme:service:EnumServicesStatusA 0xa431368 type=30 state=3 (nil) 0 0x32ef34 0x32ef38 0x32ef40
fixme:service:EnumServicesStatusA 0xa431368 type=30 state=3 (nil) 0 0x32e0d4 0x32e0d8 0x32e0e0
fixme:service:EnumServicesStatusA 0xa431368 type=30 state=3 (nil) 0 0x32e048 0x32e04c 0x32e054
fixme:service:EnumServicesStatusA 0xa431480 type=30 state=3 (nil) 0 0x32e048 0x32e04c 0x32e054
fixme:service:EnumServicesStatusA 0xa431480 type=30 state=3 (nil) 0 0x32e63c 0x32e640 0x32e648
fixme:service:EnumServicesStatusA 0xa431480 type=30 state=3 (nil) 0 0x32f048 0x32f04c 0x32f054
fixme:service:EnumServicesStatusA 0xa431480 type=30 state=3 (nil) 0 0x32f044 0x32f048 0x32f050
fixme:gdiplus:GdipDrawImagePointsRect Image wrap mode not implemented
fixme:advapi:GetCurrentHwProfileA (0x33fbe0) semi-stub
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x17
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x17
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x17
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err:ole:create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x17
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:ole:CoResumeClassObjects stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_CONNECTED_STATE: semi-stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:INET_QueryOption INTERNET_OPTION_PER_CONNECTION_OPTION stub
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
wine: Unhandled page fault on read access to 0x00000004 at address 0x100600d1 (thread 0040), starting debugger...
Can't attach process 003f: error 5
wine: Unhandled page fault on read access to 0x00000004 at address 0x100600d1 (thread 003b), starting debugger...
Can't attach process 005b: error 5
Failed connecting to named pipe, wait result is 258
Wait for connection failed
Parent: Can't create child...
Set args[3] to --parentPipe
fixme:advapi:GetCurrentHwProfileA (0x33fbe0) semi-stub
Failed connecting to named pipe, wait result is 258
Wait for connection failed
Parent: Can't create child...
Set args[3] to --parentPipe
fixme:advapi:GetCurrentHwProfileA (0x33fbe0) semi-stub
```I'll have to try to find a different Windows program to test it on that uses the USB but isn't as uncooperative as iTunes and see what errors I get.

---

### Post by marin123 on 2011-01-22
this is the error message i get when i run regedit from wine-git.

```
marin@marincelo:~/wine-git/wine/programs/regedit$ regedit
err:winedevice:ServiceMain driver L"Usbhub" failed to load
```

i also get this message when i run rekordbox (program that needs usb support) on first line of output. i still didnt try windows' usbhub.sys...

when i get the file, i will see what happens...

---

### Post by marin123 on 2011-01-22
i fixed this usbhub.sys error, it was my fault, i renamed folders windows to Windows and system32 to System32, so the files couldnt be found.

i tried adding symbolic links but it didnt work. i copied the code you gave me and nothing. how did you link COM to ttyS2?

this is my output when i run my program:

```
marin@marincelo:~/wine-git/wine/loader$ wine /home/marin/.wine/drive_c/Program\ Files/Pioneer/rekordbox\ 1.4.0/Rekordbox.exe 
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x138b50, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x20ffd08)
Could not connect. Error code = 0x80041001
fixme:font:SetMapperFlags (0x5a4, 0x00000000): stub - harmless
ippcorel.lib5.3 Update 4 build 85.385385484
fixme:mixer:ALSA_MixerInit No master control found on HD-Audio Generic, disabling mixer
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x12f410,0x16d2e8): stub
fixme:font:SetMapperFlags (0x778, 0x00000000): stub - harmless
fixme:font:SetMapperFlags (0x78c, 0x00000000): stub - harmless
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:font:SetMapperFlags (0x618, 0x00000000): stub - harmless
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
err:winediag:X11DRV_WineGL_InitOpenglInfo Direct rendering is disabled, most likely your OpenGL drivers haven't been installed correctly
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x163428, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x20ff3cc)
Could not connect. Error code = 0x80041001
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:font:SetMapperFlags (0x880, 0x00000000): stub - harmless
fixme:font:SetMapperFlags (0x8f8, 0x00000000): stub - harmless
fixme:font:SetMapperFlags (0x90c, 0x00000000): stub - harmless
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!

```

i think fixme:mountmgr is the reason i cant get read/write on usb drive working...

---

### Post by trinitydan on 2011-01-22
The sym link method:
```
COM3=/dev/ttyS2
sudo ln -sb /dev/ttyUSB0 /dev/ttyS2

```
I was just curious if you tried that way.  If you currently have Wine patched then you shouldn't need to add the sym link as I believe it is already done.  For a non-patched Wine I used the sym link method and it worked for basic USB support.  If I still had that GPS program I would test the patched Wine with that and see if the patch works the same as the sym link method.  I'll look for a Windows program I can download to test it or if anyone has any suggestions for a free Windows program that runs well in Wine and uses the USB please let me know.

---

### Post by marin123 on 2011-01-22
if you are willing to try this program:
[http://www.prodjnet.com/rekordbox/support/download.php?ap_lang=en&scr=F02&no=0&type=WIN](http://www.prodjnet.com/rekordbox/support/download.php?ap_lang=en&scr=F02&no=0&type=WIN)

i'm trying top get this to work. everything works except usb. you need to import music and then it analyzes it and you can export it to usb drive. i think there's a problem with usb because it requires direct access.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=12290](http://appdb.winehq.org/objectManager.php?sClass=application&iId=12290)

this is link to wine appdb to this program.

---

### Post by trinitydan on 2011-01-22
I'll give it a try on a non-patched Wine with the sym link and I'll try it on my patched Wine, but I doubt I will be more successful than you were.  I also want to test it with a simpler program that uses the USB.  I am downloading the Rekordbox installer.  Once again I am not near the patched Wine install, but I will hopefully get to try it later today.

---

### Post by trinitydan on 2011-01-22
I am not sure if I am clear on what you are after.  I installed the beta Wine version 1.3 and Rekordbox on this computer.  I did the sym link thing like this:
```
COM3=/dev/ttyS2
sudo ln -sb /dev/ttyUSB0 /dev/ttyS2
```Rekordbox runs and I can load files off of a external USB hard drive.  I am probably just missing what you are trying to do though.  I can't find any export function.

EDIT: Nevermind, I found the export function but it is greyed out... :(

---

### Post by trinitydan on 2011-01-23
I got a patched version of WINE (1.3.3) working on this computer last night and  tested it with Rekordbox but still no joy with the USB and export  functions.  Here's the errors I get when I run Rekordbox.  It doesn't seem to have quite as many errors as you got, but I don't know which of those is refferring to a USB error.

```
ubuntu@ubuntu:~$ wine /home/kyler/.wine/drive_c/Program Files/Pioneer/rekordbox 1.4.0/Rekordbox.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x131160, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x20ffd08)
Could not connect. Error code = 0x80041001
fixme:font:SetMapperFlags (0x5a4, 0x00000000): stub - harmless
ippcorel.lib5.3 Update 4 build 85.385385484
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13fe28,0x13fd28): stub
fixme:font:SetMapperFlags (0x7c4, 0x00000000): stub - harmless
fixme:font:SetMapperFlags (0x7d8, 0x00000000): stub - harmless
fixme:font:SetMapperFlags (0x618, 0x00000000): stub - harmless
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (30000): STUB
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:wbem_locator_ConnectServer 0x14dd28, L"ROOT\\CIMV2", (null), (null), (null), 0x00000000, (null), (nil), 0x20ff3cc)
Could not connect. Error code = 0x80041001
fixme:mountmgr:harddisk_ioctl unsupported ioctl 2d1400
fixme:font:SetMapperFlags (0x8b0, 0x00000000): stub - harmless
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:font:SetMapperFlags (0x928, 0x00000000): stub - harmless
fixme:font:SetMapperFlags (0x93c, 0x00000000): stub - harmless


```                                [http://ubuntuforums.org/showthread.php?t=697238&page=3](http://ubuntuforums.org/showthread.php?t=697238&page=3)

Once again I used the directions in post number 21, including the important bits added by sysghost.  I wonder what it will take to get the USB patches working. :(

---

### Post by marin123 on 2011-01-23
i think mountmgr's error is the one that wont allow usb to work. i still have to investigate what wbemprox.dll is doing.

i have another idea, i will connect my dj players to virtual dj with usb. they act as midi controllers. i will get back here after i test it. like you, i dont have much spare time to do this...

---

