---
title: "HOWTO: Install Wrath of the Lich King on Ubuntu 9.10"
date: 2009-10-04
forum: Wine
---

### Post by Drakebyte on 2009-10-04
**This may or may not work on earlier releases of Ubuntu. But this is the system I tested it on and had successful results.**

For some reason Blizzard decided to throw some encrypting and protection over their WotLK DVD, which is rather silly as you need a paid account to play the game anyway and you can even download the files from their server. Never the less this DOES cause a lot of issues. Luckily for us, there's a rather simple work around which works for me in 9.10 at least, and might work for you.

First of you will need Wine-1.2 and Wine-gecko-1.2 from **synaptic package manager**. The Software Center has an outdated version which prevents you from accepting the license terms. After doing that, slip your WotLK DVD in your DVD drive.

Pre 9.10 users may try getting the latest version of wine from here:
[Wine Installation Instructions for Ubuntu and Deratives]("http://www.winehq.org/download/deb")

Having done that, wait till your DVD is mounted, if it doesn't seem to mount, rebooting your system may cause it to appear (it did for me).

With your DVD mounted, open up a terminal window and write the following commands:
> sudo mount -o remount,unhide /dev/**cdrom***
gksudo nautilus /media/**cdrom0******NOTE:** This may vary for your system based on your hardware, but for most people this should be right.

There you go, you should see all the files now and with the proper permissions, run the Installer.exe file with Wine and off you go! If you don't have the patches backed up, I recommend you download the patches while installing, to save you further waiting:
[Patch Mirrors]("http://www.wowwiki.com/Patch_mirrors")

If your stuck, please do not hesitate to ask any questions. If this worked for you in any Ubuntu version below 9.10, please let me know so I can add it to a list with confirmations.

--D

---

### Post by CDNeh on 2009-11-16
This helped me huge.  I got stuck at accepting the license terms and found this.  Installing it down.  Although i downloaded WotLK from their site as i cant find my discs..

Do you still have to edit the games file and make a registry to get it to work?  or should it run fine?

Thanks again!  HUGE help!

---

### Post by bwisdom on 2009-11-16
Ive gotten WoW to install just fine I am having problems running it. Im not sure if you meant for your post to be about post-installation, but I thought I would try anyway.

Here is my post.

[http://ubuntuforums.org/showthread.php?t=1327627](http://ubuntuforums.org/showthread.php?t=1327627)

It has all the problems Ive been having and Ive been trying to figure out what it could be. I thought it was my graphics card perhaps so Ive been trying to find drivers. Ive found a few instructions on my cards drivers but those dont see to work. Thats not to say that my cards drivers are out of date, I just dont know

---

### Post by CDNeh on 2009-11-16
Just doing the above setup got the game to load, but it was changing the resolution on my  screen then the game would crash with no error code.  Graphics stopped but the games audio(intro movie) was still going in the background.

I did the following steps after the above guide and the game works perfectly:

With Wine 1.2 and Ubuntu 9.10 64-bit


[LIST=1]
[*]Setup your display drivers
[*]Install and Setup Wine 1.2
[*]Install WoW(i downloaded WotLK from the site)
[*]Edit config.wtf and added to the bottom: ```
SET gxApi "opengl"
```
[*]Edit Registry.  Open Terminal and type "regedit". Wine will open Windows Registry edit in the following:
```
a.      Find this key HKEY_CURRENT_USER\Software\Wine\
b.      Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
c.      Right-click on the wine folder and select [NEW] then [KEY]
d.      Replace the text New Key #1 with OpenGL
e.      Right-click in the right hand pane and select [NEW] then [String Value]
f.      Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
g.      Then double click anywhere on the line, a dialog box will open.
h.      In the value field type GL_ARB_vertex_buffer_object
```
    
Should look like this:
    [IMG]http://www.fsckin.com/wp-content/uploads/2007/12/regedit.png[/IMG]
[/LIST]
With all that completed the game updated and im playing.  Hope this helps.

---

### Post by id10twork on 2009-11-22
> **Drakebyte said:**
> **This may or may not work on earlier releases of Ubuntu. But this is the system I tested it on and had successful results.**

For some reason Blizzard decided to throw some encrypting and protection over their WotLK DVD, which is rather silly as you need a paid account to play the game anyway and you can even download the files from their server. Never the less this DOES cause a lot of issues. Luckily for us, there's a rather simple work around which works for me in 9.10 at least, and might work for you.

First of you will need Wine-1.2 and Wine-gecko-1.2 from **synaptic package manager**. The Software Center has an outdated version which prevents you from accepting the license terms. After doing that, slip your WotLK DVD in your DVD drive.

Pre 9.10 users may try getting the latest version of wine from here:
[Wine Installation Instructions for Ubuntu and Deratives]("http://www.winehq.org/download/deb")

Having done that, wait till your DVD is mounted, if it doesn't seem to mount, rebooting your system may cause it to appear (it did for me).

With your DVD mounted, open up a terminal window and write the following commands:
***NOTE:** This may vary for your system based on your hardware, but for most people this should be right.

There you go, you should see all the files now and with the proper permissions, run the Installer.exe file with Wine and off you go! If you don't have the patches backed up, I recommend you download the patches while installing, to save you further waiting:
[Patch Mirrors]("http://www.wowwiki.com/Patch_mirrors")

If your stuck, please do not hesitate to ask any questions. If this worked for you in any Ubuntu version below 9.10, please let me know so I can add it to a list with confirmations.

--D

This fixed all the random problems I was having with the download!  (9.1)

---

### Post by petrocles on 2009-11-24
i tried what you did and i am still unable to install wrath of the lich king

faz@faz-laptop:~/Desktop/wowlk$ sudo mount -o remount,unhide /dev/cdrom
faz@faz-laptop:~/Desktop/wowlk$ gksudo nautilus /media/cdrom0
(nautilus:3601): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3601): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3601): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3601): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

err:wineboot:pendingRename couldn't get file attributes (2)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:font:CreateScalableFontResourceW (1,L"C:\\windows\\temp\\Blizzard\\Installer_37E48455\\FrizQuadrata.fot",L"C:\\windows\\temp\\Blizzard\\Installer_37E48455\\FrizQuadrata.ttf",(null)): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x15f2a8,0x15f6c8): stub
fixme:reg:RegSetKeySecurity :(0x6c,4,0x150520): stub
fixme:shdocvw:PersistStreamInit_Load (0x165268)->(0x33da18)
fixme:shdocvw:OleControl_FreezeEvents (0x165268)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x165268)->(0)

---

### Post by Xog on 2009-11-24
> **petrocles said:**
> i tried what you did and i am still unable to install wrath of the lich king

faz@faz-laptop:~/Desktop/wowlk$ sudo mount -o remount,unhide /dev/cdrom
faz@faz-laptop:~/Desktop/wowlk$ gksudo nautilus /media/cdrom0
(nautilus:3601): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3601): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3601): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3601): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

err:wineboot:pendingRename couldn't get file attributes (2)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24000 (device=2 access=1 func=0 method=0)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:font:CreateScalableFontResourceW (1,L"C:\\windows\\temp\\Blizzard\\Installer_37E48455\\FrizQuadrata.fot",L"C:\\windows\\temp\\Blizzard\\Installer_37E48455\\FrizQuadrata.ttf",(null)): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x15f2a8,0x15f6c8): stub
fixme:reg:RegSetKeySecurity :(0x6c,4,0x150520): stub
fixme:shdocvw:PersistStreamInit_Load (0x165268)->(0x33da18)
fixme:shdocvw:OleControl_FreezeEvents (0x165268)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x165268)->(0)

try installing from the downloaded install. Login to your account on [www.worldofwarcraft.com](www.worldofwarcraft.com) in the "Account Management" area, and  download the installer from there. It's much easier and simpler.

---

### Post by justmikeit on 2009-12-14
well a problem i had was with wine, and the user agreement page. after i read the part about going to the package manager and getting wine 1.2 i was able to click agree for the installer. right now it is installing. I downloaded the pc client from account manager at the wow website

---

### Post by justmikeit on 2009-12-15
got it all downloaded and im able to play, even got some addons going also from wow matrix. My fps is pretty low though. In dalaran its jumps between 4 and 15 fps. when i had it installed on vista my fps was around 35 in the city

---

### Post by 8Kuula on 2009-12-15
[quote=Drakebyte]
gksudo nautilus /media/cdrom0*[/quote]
Just a noob question but why open nautilus window as root?
Just that when you doubleclick installer to run in that window it runs as root too. Or so I think...

---

### Post by lemyroks on 2009-12-27
I did all the steps
my wow is installed,
i entered the game, appears the video but after that my game crashes everytime the video finishes
any solutions?
p.d: once it didn't crash but the log in window was black and i only could hear the log in sounds >.<

---

### Post by Sceiron on 2009-12-31
Hello,
this worked perfectly until it was about to install the updates.
Can someone try to help me with this?
Posting a Screen for the Error message.

Edit:
Realized that the img was very small. Saying:
Program Error. The program Launcher.exe has encountered a serious problem and need to close. We are sorry....

Immidiate output from terminal when fault occurs:

```
fixme:wininet:InternetLockRequestFile STUB
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->((null) 26 2 0x33cb44 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->((null) 29 2 0x33cb54 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x16c958)->(L"Done")
fixme:font:ExtTextOutW flags ETO_NUMERICSLOCAL | ETO_NUMERICSLATIN | ETO_PDY unimplemented
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x14cad0, 0x33f36c
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:RegisterRawInputDevices (pRawInputDevices=0xd4de40, uiNumDevices=2, cbSize=12) stub!
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x2971930)->()
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->({000214d1-0000-0000-c000-000000000046} 67 0 0x33d714 0x33d704)
fixme:hlink:IHlink_fnGetStringReference (0x28db018) -> (1 (nil) 0x33d5cc)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x1f97e0)->((nil))
fixme:imm:ImmReleaseContext ((nil), 0x14cb38): stub
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:shdocvw:BindStatusCallback_OnProgress status code 1
fixme:shdocvw:BindStatusCallback_OnProgress status code 2
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x16c958)->((null) 1 0x33d600 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->((null) 25 2 0x33d614 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->((null) 26 2 0x33d614 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x16c958)->(0x33d658)
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d6ec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x16c958)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33d714)
fixme:wininet:InternetLockRequestFile STUB
wine: Unhandled page fault on read access to 0x00000000 at address 0xec7e66 (thread 0022), starting debugger...

```

---

### Post by Sceiron on 2009-12-31
Trying to use the Installer from Blizzards site, but during startup of installation I think that I get the following error:
Maybe its trying to launch a browser for me to verify my account??

```

fixme:shdocvw:WebBrowser_Stop (0x1514d0)

```

I desperately need help with this! Second day of trying to install wow....

---

### Post by Sceiron on 2009-12-31
Solved the initial problems with Installer from Blizzard, so downloading 6 GB at the moment.


Solution:
After doing this the installer started the dl.
```

> wget http://www.kegel.com/wine/winetricks 

> sh winetricks vcrun2005sp1 vcrun2005

```

---

### Post by Dava02 on 2010-01-22
ok i've got WoW installed but then needed to install the Lich King addon. I used the download from the site which took some time. Now all i need to do is install the latest patches. 3.2 and 3.3. However at 70% i get a white screen popup in the middle of the launcher/downloader. Anyone seen this before or know how to fix this

---

### Post by user1397 on 2010-01-23
people...stop playing WoW...or any mmorpg's for that matter.

sorry to shake your little bubble, but they are the most time-consuming, wasteful, lame, and expensive ways of using your time.

/rant

---

### Post by Dava02 on 2010-01-23
> **lemyroks said:**
> I did all the steps
my wow is installed,
i entered the game, appears the video but after that my game crashes everytime the video finishes
any solutions?
p.d: once it didn't crash but the log in window was black and i only could hear the log in sounds >.<

Had this problem early on. To fix this simply turned off pixel shading in the wine config, graphics tab.

> **ubuntuman001 said:**
> people...stop playing WoW...or any mmorpg's for that matter.

sorry to shake your little bubble, but they are the most time-consuming, wasteful, lame, and expensive ways of using your time.

/rant

So pleased you were around to help me, i guess trolling forums is a great way to spend your time instead is it?

---

### Post by user1397 on 2010-01-23
> **Dava02 said:**
> Had this problem early on. To fix this simply turned off pixel shading in the wine config, graphics tab.



So pleased you were around to help me, i guess trolling forums is a great way to spend your time instead is it?good point, although I'm not wasting nearly as much time as you are playing WoW. :popcorn:

---

### Post by Liz on 2010-03-12
> **ubuntuman001 said:**
> good point, although I'm not wasting nearly as much time as you are playing WoW. :popcorn:

are you sure about that??
im sure you spend as much time on forum as i do in wow. 
well when its working neway.

---

### Post by Liz on 2010-03-12
> **Sceiron said:**
> Solved the initial problems with Installer from Blizzard, so downloading 6 GB at the moment.


Solution:
After doing this the installer started the dl.
```

> wget http://www.kegel.com/wine/winetricks 

> sh winetricks vcrun2005sp1 vcrun2005

```


i tried that. 
didnt make a difference for me unfortunately. and i was getting similar errors to you.

---

### Post by fragsteel on 2010-05-10
Any solutions found guys?  I'm trying to update now, and it freezes at 10% with this:

```

failed to open C:\Program Files\World of Warcraft\WTF
failed to open C:\Program Files\World of Warcraft\WTF
fixme:reg:RegSetKeySecurity :(0x88,4,0x15de08): stub
fixme:ras:RasEnumEntriesW ((nil),(null),0x170948,0xd8e610,0x170634),stub!
fixme:msimtf:DllGetClassObject ({50d5107a-d278-4871-8989-f4ceaaf59cfc} {00000001-0000-0000-c000-000000000046} 0x32b0b4)
err:ole:apartment_getclassobject DllGetClassObject returned error 0x80040111
err:ole:CoGetClassObject no class object {50d5107a-d278-4871-8989-f4ceaaf59cfc} could be created for context 0x401
err:ole:CoGetClassObject class {6c736db1-bd94-11d0-8a23-00aa00b58e10} not registered
err:ole:CoGetClassObject no class object {6c736db1-bd94-11d0-8a23-00aa00b58e10} could be created for context 0x1
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:seh:_abnormal_termination (void)stub
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:shell:UnixFolder_IShellFolder2_QueryInterface Unimplemented interface {062e1261-a60e-11d0-82c2-00c04fd5ae38} (unknown)
fixme:ras:RasEnumConnectionsW (0x129820,0xb4e948,0x70279524),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:win:RegisterRawInputDevices (pRawInputDevices=0x3398cc, uiNumDevices=2, cbSize=12) stub!
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x146be8, 0x944e130
fixme:hnetcfg:fw_profile_get_FirewallEnabled 0x146c00, 0x944e130

```

---

### Post by jinijava on 2010-05-15
> **Drakebyte said:**
> **This may or may not work on earlier releases of Ubuntu. But this is the system I tested it on and had successful results.**

For some reason Blizzard decided to throw some encrypting and protection over their WotLK DVD, which is rather silly as you need a paid account to play the game anyway and you can even download the files from their server. Never the less this DOES cause a lot of issues. Luckily for us, there's a rather simple work around which works for me in 9.10 at least, and might work for you.

First of you will need Wine-1.2 and Wine-gecko-1.2 from **synaptic package manager**. The Software Center has an outdated version which prevents you from accepting the license terms. After doing that, slip your WotLK DVD in your DVD drive.

Pre 9.10 users may try getting the latest version of wine from here:
[Wine Installation Instructions for Ubuntu and Deratives]("http://www.winehq.org/download/deb")

Having done that, wait till your DVD is mounted, if it doesn't seem to mount, rebooting your system may cause it to appear (it did for me).

With your DVD mounted, open up a terminal window and write the following commands:
***NOTE:** This may vary for your system based on your hardware, but for most people this should be right.

There you go, you should see all the files now and with the proper permissions, run the Installer.exe file with Wine and off you go! If you don't have the patches backed up, I recommend you download the patches while installing, to save you further waiting:
[Patch Mirrors]("http://www.wowwiki.com/Patch_mirrors")

If your stuck, please do not hesitate to ask any questions. If this worked for you in any Ubuntu version below 9.10, please let me know so I can add it to a list with confirmations.

--D

i wrote the commands as u say and seems to work, since bash doesn't say anything, but when attempting to open install.exe from the wotlk dvd it says 

"Sorry the installer was unable to start up.
No installer data could be found. If this problem persists, please contact Blizzard Technical Support." 
ive emailed the support but i dont think they are able to help me.

ive been using ubuntu for 3days now, so i have only scratched the surface, but am loving it and preaching it allready.
please help me
[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by sparticus4life08 on 2010-07-18
Im installing WOTLK on linux, I've just updated to 10.04 and Im having problems with WOTLK. I tried doing it the same way with BC and the original but I'm getting no where. I have looked all over and tried all the ways and its still not working. These are the messages that come up.

1. wine: cannot find L"H:\\Desktop\\wowlk\\Installer.exe"

2. scott@Controlroom:~$ gksudo nautilus /media/cdrom0
Initializing nautilus-gdu extension
wine: '/root' is not owned by you, refusing to create a configuration directory there

Please help me, Thanks

---

