---
title: "Can't get Street Hacker to run in Wine!"
date: 2010-07-11
forum: Wine
---

### Post by ben2000677 on 2010-07-11
Hi there,
So the past 2 days I've been on holiday DYING to get street hacker working on this ubuntu netbook. 

[LIST]
[*]SO i have the cd image and wine installed.
[/LIST]

[LIST]
[*]I can get Street Hacker to install with no problems but when I try to get it to run, it comes up with 'opening street hacker' but then nothing happens
[/LIST]

[LIST]
[*]I tried doing this in terminal, I was getting the install mono error.
[/LIST]

[LIST]
[*]So then I spent a whole day trying to get mono installed, this meant I had to get g++ and glib 2.4+.
[/LIST]

[LIST]
[*]I then found out, it wanted me to install the windows version of mono as an exe ...in wine... which is way easier...](*,)
[/LIST]

[LIST]
[*]So after installing mono into wine I thought 'hey, this should totally work now ...but still I have the same result when running the shortcut.
[/LIST]

[LIST]
[*]I tried again in terminal typing 'wine street\ hacker.exe' in the correct directory and now I get this:
[/LIST]
```
System.TypeInitializationException: An exception was thrown by the type initializer for Street_Hacker.Form_Operator ---> System.NotImplementedException: COM/ActiveX support is not implemented
  at System.Windows.Forms.AxHost.get_CreateParams () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control.InternalSizeFromClientSize (Size clientSize) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control.ClientSizeFromSize (Size size) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Control..ctor () [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.AxHost..ctor (System.String clsid) [0x00000] in <filename unknown>:0 
  at AxShockwaveFlashObjects.AxShockwaveFlash..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) AxShockwaveFlashObjects.AxShockwaveFlash:.ctor ()
  at Street_Hacker.Splash.InitializeComponent () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Street_Hacker.Splash:InitializeComponent ()
  at Street_Hacker.Splash..ctor () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Street_Hacker.Splash:.ctor ()
  at Street_Hacker.Form_Operator..cctor () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Street_Hacker.loader.loader_Load (System.Object sender, System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Form.OnLoad (System.EventArgs e) [0x00000] in <filename unknown>:0 
  at System.Windows.Forms.Form.OnLoadInternal (System.EventArgs e) [0x00000] in <filename unknown>:0 


```THINGS I'VE TRIED:

[LIST]
[*]uninstalling and reinstalling street hacker
[*]searching google to find other people trying to get street hacker working on wine
[/LIST]
THANKS FOR HELPAGE
Ben

---

### Post by cogadh on 2010-07-11
Street Hacker requires a few things in order to work, and even then it isn't guaranteed to work in Wine at all. First and foremost, it requires .NET 2.0. Mono can do most of the things that .NET can do, but in many cases, it just isn't enough. Second, it needs Flash player 7 or higher. Lastly, it requires the DivX codec. You can use [winetricks]("http://wiki.winehq.org/winetricks") to install all three of those for you.

---

### Post by ben2000677 on 2010-07-11
ok so I got winetricks and having errors when getting every component
dotnet20
divx
flash

i managed to get the dotnet20 working but i get this error when installing flash 
```
Executing wget -O install_flash_player_ax.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_ax.exe
--2010-07-12 01:27:24--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_ax.exe
Resolving fpdownload.macromedia.com... failed: Name or service not known.
wget: unable to resolve host address `fpdownload.macromedia.com'
------------------------------------------------------
Note: command 'wget -O install_flash_player_ax.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_ax.exe' returned status 1.  Aborting.
------------------------------------------------------

```

and this error when getting divx
```
------------------------------------------------------
sha1sum mismatch!  Rename /home/h4Sh/.winetrickscache/divx-7/DivXInstaller.exe and try again.
------------------------------------------------------
h4Sh@Osiris:~$ sh winetricks divx
Executing wget -O DivXInstaller.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://download.divx.com/divx/DivXInstaller.exe
--2010-07-12 01:29:52--  http://download.divx.com/divx/DivXInstaller.exe
Resolving download.divx.com... failed: Name or service not known.
wget: unable to resolve host address `download.divx.com'
------------------------------------------------------
Note: command 'wget -O DivXInstaller.exe -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://download.divx.com/divx/DivXInstaller.exe' returned status 1.  Aborting.
------------------------------------------------------

```

Thanks

---

### Post by hikaricore on 2010-07-11
Did you even read the error?..
The domains have changed or are invalid.
You may just need to install them manually or update winetricks.

---

### Post by ben2000677 on 2010-07-12
ok well I tried to get flash manually and that worked, divx codec had an issue, the installer wouldn't run.
I then uninstalled .net 2.0 and street hacker, then installed .net 2.0 then street hacker now when I try to run in terminal with 'wine street\ hacker.exe' I get this response
```
fixme:msvcrt:_controlfp_s ((nil) 65536 196608) semi-stub
fixme:msvcrt:_controlfp_s ((nil) 0 768) semi-stub
fixme:sync:CreateMemoryResourceNotification (0) stub
fixme:msvcrt:_controlfp_s ((nil) 0 768) semi-stub
wine: Call from 0x7b836872 to unimplemented function msvcr80.dll.wcsncat_s, aborting
err:ole:CoGetContextToken apartment not initialised
fixme:msvcr90:__clean_type_info_names_internal (0x60345090) stub
wine: Call from 0x7b836872 to unimplemented function msvcr80.dll.wcsncat_s, aborting
fixme:advapi:RegisterEventSourceW ((null),L".NET Runtime"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003ff,(nil),0x0001,0x00000000,0x32dfd4,(nil)): stub
err:eventlog:ReportEventW L".NET Runtime version 2.0.50727.42 - Fatal Execution Engine Error (7A05FC29) (80131506)"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:msvcr90:__clean_type_info_names_internal (0x7a38d5c8) stub

```

sorry about not recognizing the errors, im quite new to unix. 
THanks

---

### Post by cogadh on 2010-07-12
Looks like you also need to install MS Visual C++ runtime library, specifically the 2005 SP1 version (Winetricks can also do that).

---

### Post by ben2000677 on 2010-07-12
ok well i use the 'sh winetricks vc2005sp1' command, which tells me to download the vc2005trial. 
WHen I do this it just freezes up terminal... I also tried downloading the .exe of the SP1 and I get this error when loading it with wine.

Runtime Error!
Program: C:/Windows/system32/msiexec.exe
abnormal program termination

in a dialogue box

Thanks

---

### Post by cogadh on 2010-07-12
You're getting some really strange issues with winetricks. Did you download the latest version of the script at the link I provided?

---

### Post by ben2000677 on 2010-07-12
yep i used the link you gave me.
I ran the winetricks -V command and I have version 20100618

---

