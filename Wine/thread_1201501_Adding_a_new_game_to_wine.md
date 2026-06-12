---
title: "Adding a new game to wine"
date: 2009-07-01
forum: Wine
---

### Post by ToppKatt on 2009-07-01
[SIZE=3][FONT=Arial]Ok really new to this.  Have read everything in here I thought might help.  If I understand this right I should put the installer program in the Wine Dir and open it from there and tell it to install.  It keeps coming up install to c:/ I hope that I change that to /usr/libs/wine. As the default dir.  I know the installer will make a dir under wine and will ask me for a player name and password which would go into the Windows Registry...Here I don't know how it will save it.  Thanks for any help. [/FONT][/SIZE]

---

### Post by cogadh on 2009-07-01
Wine creates its own "fake Windows" directory in your home directory (labeled ".wine") where all Windows application should be installed. Applications will see that "fake Windows" directory as the "C:" drive, as if they were actually being run on Windows. You should not try to install it in /usr/libs/wine at all, and honestly, you won't be able to anyway, due to permission problems and the fact that Wine is only really aware of it's own "fake Windows" directory (by default). It does not matter where you run the installer from, so you don't need to try and copy it anywhere and you shouldn't try to put that in /usr/libs/wine at all. Within Wine's "fake Windows" directory is Wine's version of the Windows registry, which your Windows app will write to as necessary... assuming the game you are trying to install is one that already works in Wine. Before you try to install anything, you should check Wine's [Application Database]("http://appdb.winehq.org/") to be certain the application will actually work with Wine.

---

### Post by ToppKatt on 2009-07-02
[SIZE=4]Ok well I goofed and tried to install it the wrong way.  Broke windows and had to use a restore point to bring it back.  Went to AppDb they didn't have the game in there.  So I just run the installer and let it install to C:/Program Files/name of program and let it do its thing?[/SIZE]

---

### Post by kzersatz on 2009-07-02
Pretty much...

It is unwise to try and change the install path when installing something through WINE

Good luck =)

---

### Post by cogadh on 2009-07-02
There's no need for the giant font and I think most people would prefer if you didn't use it; personally, it gives me a headache.

How did you break Windows trying to install something in Wine? Wine should not be aware that you have Windows and more importantly, it should never touch Windows, unless you have made some significantly bad configuration changes to Wine. To simply use Wine you do not really need to make any configuration changes at all, except picking a sound driver. Virtually every other setting in Wine can be left alone, unless or until a particular application requires a change. Considering you already seem to have made some potentially damaging changes, I would recommend you delete the .wine directory (rm -rf ~/.wine) which will "re-set" Wine to its defaults. Then you can start with a fresh configuration before you attempt to install anything else. Once you have done that, as kzersatz confirmed, you just need to run the install and let it accept the defaults, pretty much just like you can do on Windows.

---

### Post by ToppKatt on 2009-07-03
[SIZE=2]Ok sorry about the font size kind of hard to read these small fonts for an ole geezer.

The game installs fine.  However it will not connect to the internet to download the rest of the files needed to install the game.

Not sure but I might need to learn how to uninstall wine and reinstall it to see if that might be the problem.  

Wine won't let me use Internet Explorer either.  Not that I care. 

Not sure what the blankey blank I did to Windows it just wouldn't boot so I did a restore and then it worked fine.

This game just might not work and I will have to forget it.  MagicJack is another program that looks like the developers of Ubuntu will have to look at to see if they can make it work in Linux.  Shows up on my desktop from time to time but of course won't work.
[/SIZE]

---

### Post by carml on 2009-07-03
to reinstall something in a easy way go to System->Administration->Synaptic Package manager,insert your password ,look for Wine,then right click the little square near the name and select Mark for the reinstallation. :)

---

### Post by cogadh on 2009-07-03
> **ToppKatt said:**
> [SIZE=2]Ok sorry about the font size kind of hard to read these small fonts for an ole geezer.

The game installs fine.  However it will not connect to the internet to download the rest of the files needed to install the game.

Not sure but I might need to learn how to uninstall wine and reinstall it to see if that might be the problem.  

Wine won't let me use Internet Explorer either.  Not that I care. 

Not sure what the blankey blank I did to Windows it just wouldn't boot so I did a restore and then it worked fine.

This game just might not work and I will have to forget it.  MagicJack is another program that looks like the developers of Ubuntu will have to look at to see if they can make it work in Linux.  Shows up on my desktop from time to time but of course won't work.
[/SIZE]

Just a suggestion on the font thing; rather than post in a large font, you could increase the font display settings in your browser or just hold down the CTRL key and scroll up on your mouse wheel, which will scroll through available font sizes. That way what you see on your end will be readable while not affecting the rest of us.

Internet Explorer doesn't really work in Wine at all, but you might be able to get it working by using [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").

If you delete the .wine folder, you shouldn't need to uninstall/reinstall Wine, but it can't really hurt to try. Just follow carml's suggestion to accomplish that.

After you have Wine back to a default config, then try running the install and the game using the terminal, which will provide you with Wine's error output that you can copy/paste here and may provide us with the necessary information to help you:

```
cd /path/to/install/executable
wine install.exe

after it is installed

cd ~/.wine/drive_c/Program\ Files/path/to/install/directory
wine game.exe
```
Obviously change those paths and executable names to what you have on your system.

---

### Post by ToppKatt on 2009-07-05
Ok don't know what I am doing wrong.  Started with this in the terminal and worked my way down to the last two Desktop/iplaysetup.exe...says file or Dir not found for all.  cd /computer:///Filesystem/home/toppkatt001/desktop/iplaysetup.exe wine install.exe  

After going over this I guess u mean the path that the program wants to install to.  C:/program files/iplaynet

---

### Post by cogadh on 2009-07-05
Okay, a couple of mistakes there. I'm not sure what the "/computer:///Filesystem" stuff is, bu it is not needed at all. Additionally, it looks like you tried to change directories to an executable, which is not a directory. What you need to do is this:
```
cd /home/toppkatt001/desktop
wine iplaysetup.exe
```
Assuming it installs successfully, then you will need to do a similar process when you run the game:
```
cd ~/.wine/drive_c/Program\ Files/iplaynet
wine <whatever the name of the executable is>.exe
```
Both of those should provide us with complete error output on each process.

---

### Post by ToppKatt on 2009-07-06
Here is the output.

toppkatt001@OWNER-PC:~$ cd /home/toppkatt001/desktop wine iplaysetup.exe
bash: cd: /home/toppkatt001/desktop: No such file or directory
toppkatt001@OWNER-PC:~$

Only thing I can think of at this time is I am missing a forward slash after desktop/ but since it wasn't stated that way I didn't use it.

---

### Post by carml on 2009-07-06
You have to change desktop to Desktop,if you don't do so you can't access it via terminal. ;)

---

### Post by ToppKatt on 2009-07-06
Here is the output from the installer.  Will wait to try the next step after this is viewed and seen to be acceptable to continue. Seems like to many errors involved for this program to run in Wine.

toppkatt001@OWNER-PC:~$ cd /home/toppkatt001/Desktop wine iplaysetup.exe
toppkatt001@OWNER-PC:~/Desktop$ wine iplaysetup.exe
toppkatt001@OWNER-PC:~/Desktop$ fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:reg:GetNativeSystemInfo (0x33f378) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x12e040 0x33f37c) stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:reg:GetNativeSystemInfo (0x33fb68) using GetSystemInfo()
fixme:mscoree:GetRequestedRuntimeInfo ((null), L"v2.0.50727", (null), 0x00000006, 0x00000018, 0x33fc44, 0x00000104, 0x33fbac, 0x33fe4c, 0x00000014, 0x33fba4) stub
fixme:mscoree:GetCORVersion (0x33fe4c, 20, 0x33fba4): semi-stub!
fixme:mscoree:CorExitProcess (1) stub
fixme:exec:SHELL_execute flags ignored: 0x00000400
fixme:advapi:LookupAccountNameW (null) L"toppkatt001" (nil) 0x33f87c (nil) 0x33f880 0x33f874 - stub
fixme:advapi:LookupAccountNameW (null) L"toppkatt001" 0x12ccc0 0x33f87c 0x12cf38 0x33f880 0x33f874 - stub
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub SelfUnregModules -> 19 ignored L"SelfReg" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
err:module:import_dll Library MFC42.DLL (which is needed by L"C:\\windows\\system32\\ipview.ocx") not found
Failed to load DLL C:\windows\system32\ipview.ocx
Successfully registered DLL C:\windows\system32\udppor60.ocx
err:module:import_dll Library MSVBVM50.DLL (which is needed by L"C:\\windows\\system32\\hlink.ocx") not found
Failed to load DLL C:\windows\system32\hlink.ocx
Successfully registered DLL C:\windows\system32\ipinfo60.ocx
Successfully registered DLL C:\windows\system32\UDPPOR35.OCX
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\windows\\system32\\comct332.ocx") not found
Failed to load DLL C:\windows\system32\comct332.ocx
Successfully registered DLL C:\windows\system32\ipdaem60.ocx
Successfully registered DLL C:\windows\system32\http60.ocx
Successfully registered DLL C:\windows\system32\HTTP35.OCX
Successfully registered DLL C:\windows\system32\IPPORT35.OCX
Successfully registered DLL C:\windows\system32\ipport60.ocx
err:module:import_dll Library MFC40.DLL (which is needed by L"C:\\windows\\system32\\asock32.ocx") not found
Failed to load DLL C:\windows\system32\asock32.ocx
Successfully registered DLL C:\windows\system32\ftp60.ocx
Successfully registered DLL C:\windows\system32\FTP35.OCX
Successfully registered DLL C:\windows\system32\ipinfo35.ocx
Successfully registered DLL C:\windows\system32\COMCTL32.OCX
Successfully registered DLL C:\windows\system32\COMCT232.OCX
Successfully registered DLL C:\windows\system32\IPDAEM35.OCX
Successfully registered DLL C:\windows\system32\comdlg32.ocx

---

### Post by carml on 2009-07-06
Did you try to simply double click the .exe file?

---

### Post by starcraftmaster on 2009-07-06
so is that why am getting errors when i try to run max payne 1 off drive D:
can i just copy the max payne folder(u can copy max payne any where u want it , it wont complain  about not being installed right) to  .wine folder
if i can where is .wine folder ? is it a folder ?

if thats not the problem why max payne is not starting,
on the wine data base it says it should run fine

the error am getting is:
Error: no zbuffer formats found

does wine need direct x to be installed ?

also starwars battle front wont start either
that justs closes on its on self

---

### Post by cogadh on 2009-07-06
> **ToppKatt said:**
> 
err:module:import_dll Library MFC42.DLL
err:module:import_dll Library MSVBVM50.DLL
err:module:import_dll Library MSVBVM60.DLL
err:module:import_dll Library MFC40.DLL

Okay, we have the start of an explanation. You need to install some of the Microsoft runtimes. You need to get [winetricks]("http://wiki.winehq.org/winetricks") and use it to install Visual C++ Runtime 6 (vcrun6), Visual Basic Runtime 5 and 6 (vb5run and vb6run) and MS Foundation classes from C++ 4 (mfc40). The instructions for winetricks are pretty straightforward and provided on the page I linked to. After they are installed, you should run the install of the game again, so that it can (hopefully) register its components correctly.

> **starcraftmaster said:**
> so is that why am getting errors when i try to run max payne 1 off drive D:
can i just copy max payne folder(u can copy max payne any where u want it , it wont complain  about not being installed right) to this .wine folder
if i can where is .wine folder ? is it a folder ?
It is bad form to hijack someone else's thread with an unrelated problem. If you have not already, you should start your own thread with this problem where we can appropriately help you.

---

### Post by starcraftmaster on 2009-07-07
> **cogadh said:**
> 


It is bad form to hijack someone else's thread with an unrelated problem. If you have not already, you should start your own thread with this problem where we can appropriately help you.


oh i just posted it here because it was related
sorry;)

---

### Post by ToppKatt on 2009-07-07
Ok I think I got the winetricks downloaded.  Not sure how to extract what I need from it.  Can't find any Cabextract in installed applications.  If I need that.

---

### Post by cogadh on 2009-07-07
Winetricks is a script, you don't need to extract anything from it, you just need to run it and it will get everything you need for you. It does require that you have cabextract installed first, so you need to add it, either through the Add/Remove Programs applet or by simply running "sudo apt-get install cabextract" in the terminal. Once you have that, you just need to run winetricks (change directories to wherever you downloaded it, then run "sh winetricks") and it will bring up a GUI that will allow you to pick what you need to install. ONLY INSTALL WHAT YOU ACTUALLY NEED. Don't throw anything extra on there as it could introduce new problems that we didn't anticipate.

---

### Post by ToppKatt on 2009-07-08
Ok this is the output of the install at the terminal.  Looks good now to on to the second part.



oppkatt001@OWNER-PC:~/Desktop$ wine iplaysetup.exe
fixme:ole:DllRegisterServer stub
toppkatt001@OWNER-PC:~/Desktop$ fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:reg:GetNativeSystemInfo (0x33f378) using GetSystemInfo()
fixme:advapi:CheckTokenMembership ((nil) 0x12e040 0x33f37c) stub!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:reg:GetNativeSystemInfo (0x33fb68) using GetSystemInfo()
fixme:mscoree:GetRequestedRuntimeInfo ((null), L"v2.0.50727", (null), 0x00000006, 0x00000018, 0x33fc44, 0x00000104, 0x33fbac, 0x33fe4c, 0x00000014, 0x33fba4) stub
fixme:mscoree:GetCORVersion (0x33fe4c, 20, 0x33fba4): semi-stub!
fixme:mscoree:CorExitProcess (1) stub
fixme:exec:SHELL_execute flags ignored: 0x00000400
fixme:advapi:LookupAccountNameW (null) L"toppkatt001" (nil) 0x33f87c (nil) 0x33f880 0x33f874 - stub
fixme:advapi:LookupAccountNameW (null) L"toppkatt001" 0x12ccc0 0x33f87c 0x12cf38 0x33f880 0x33f874 - stub
fixme:msi:ControlEvent_HandleControlEvent unhandled control event L"Reinstall" arg(L"ALL")
fixme:msi:msi_unimplemented_action_stub SelfUnregModules -> 19 ignored L"SelfReg" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
Successfully registered DLL C:\windows\system32\ipview.ocx
Successfully registered DLL C:\windows\system32\udppor60.ocx
Successfully registered DLL C:\windows\system32\hlink.ocx
Successfully registered DLL C:\windows\system32\ipinfo60.ocx
Successfully registered DLL C:\windows\system32\UDPPOR35.OCX
Successfully registered DLL C:\windows\system32\comct332.ocx
Successfully registered DLL C:\windows\system32\ipdaem60.ocx
Successfully registered DLL C:\windows\system32\http60.ocx
Successfully registered DLL C:\windows\system32\HTTP35.OCX
Successfully registered DLL C:\windows\system32\IPPORT35.OCX
Successfully registered DLL C:\windows\system32\ipport60.ocx
Successfully registered DLL C:\windows\system32\asock32.ocx
Successfully registered DLL C:\windows\system32\ftp60.ocx
Successfully registered DLL C:\windows\system32\FTP35.OCX
Successfully registered DLL C:\windows\system32\ipinfo35.ocx
Successfully registered DLL C:\windows\system32\COMCTL32.OCX
Successfully registered DLL C:\windows\system32\COMCT232.OCX
Successfully registered DLL C:\windows\system32\IPDAEM35.OCX
Successfully registered DLL C:\windows\system32\comdlg32.ocx
toppkatt001@OWNER-PC:~/Desktop$

---

### Post by ToppKatt on 2009-07-08
Ok not sure what's wrong with this I think I have an Idea but will let you look at it and then go from there.

toppkatt001@OWNER-PC:~/Desktop$ cd ~/.wine/drive_c/Program\ Files/iplaynet wine iplaynet.exe
bash: cd: /home/toppkatt001/.wine/drive_c/Program Files/iplaynet: No such file or directory

---

### Post by carml on 2009-07-08
> **ToppKatt said:**
> Ok not sure what's wrong with this I think I have an Idea but will let you look at it and then go from there.

toppkatt001@OWNER-PC:~/Desktop$ cd ~/.wine/drive_c/Program\ Files/iplaynet wine iplaynet.exe
bash: cd: /home/toppkatt001/.wine/drive_c/Program Files/iplaynet: No such file or directory

Maybe the space between Program and Files,try to type "Program\ Files" (without quotes) and it will work,remember that the space is used to separate commands in the terminal,so everytime you have to do with something like Program Files you can force the space with a \ or type "The name of the file I choosed in Windows" if it's a file and not a path ;)

---

### Post by ackanao on 2009-07-08
Or, just type: wine "C:\Program Files\iplaynet\iplaynet.exe"

(Type the full path to your iplaynet.exe)

---

### Post by ToppKatt on 2009-07-08
If you will notice that the input to the terminal was exactly that. Program \Files.  The output to the screen removes the \.

Don't know if the answer ackanao gave above will give the desired output that your looking for. 

The full path to that file is toppkatt001/.wine/Program Files/IPlayNet/IPlayNet.exe.  Don't know if the CAPITAL LETTERS in IPlayNet and IPlayNet.exe will make any difference.  I do know that Linux is case sensitive in many instances.

---

### Post by ackanao on 2009-07-08
OK. Then type:

```
wine "C:\Program Files\IPlayNet\IPlayNet.exe"
```

---

### Post by cogadh on 2009-07-08
We need him to change directories to the games installation directory first, not run it from outside the directory.

ToppKatt, capitilazation does matter in Linux, so when you run the CD command and the wine command, you need to enter the paths and names exactly as they appear, capitilization and all.

---

### Post by ackanao on 2009-07-08
Sorry, but why is so important to go to install directory first ?!

---

### Post by cogadh on 2009-07-08
That will ensure that the application paths are set correctly and eliminate that as a possible cause of any future issues. Windows applications often need to be run from their installation directory, hence why shortcuts on Windows have that "Start in" option. Technically, that is the proper way to use Wine as well.

---

### Post by ackanao on 2009-07-08
I don't want to go offtopic, but:

Sorry but I'm just not convinced - that may be the case with older versions of Wine. The big problem here is that he don't know how to start program in Wine - making it even more diffucult to understand and more "geekish" does not help at all.

---

### Post by cogadh on 2009-07-08
If you don't want to go off-topic, then why bring it up?

It's not a particular quirk of Wine, but rather a particular quirk of Windows applications. What version of Wine you are using does not change that. Obviously you've never run into an app that was unable to find files in its own install directory before, but many of us have and the whole reason it happens is because the app was not run from its install directory.

The big problem here was that he couldn't get an app installed in Wine, but that's beside the point. Changing directories to the install directory is just a troublshooting step to avoid any future problems that are not really problems, but just "red herrings" that would interrupt the whole troubleshooting process; a "better safe than sorry" step, if you will. There should be nothing difficult to understand or geekish about changing directories, that is a very basic part of using any OS, not just Linux and certainly not just with Wine.

---

### Post by ToppKatt on 2009-07-09
Ok this is all that comes up in the terminal after that command.

toppkatt001@OWNER-PC:~$ cd ~/.wine/drive_c/Program\ Files/IPlayNet/ wine IPlayNet.exe
[email]toppkatt001@OWNER-PC:~/.wine[/email]/drive_c/Program Files/IPlayNet$ 

Doesn't run the IPlayNet.exe and I know that it's in there.

---

### Post by ackanao on 2009-07-09
I told you already, type this command:

```
wine "C:\Program Files\IPlayNet\IPlayNet.exe"
```

but, because it's "sooo necessary" to run this game from installation directory, type this first:

```
cd ".wine/drive_c/Program Files/IPlayNet"
```

and hit Enter

Then type:

```
wine IPlayNet.exe
```

Or if you have **nautilus-open-terminal** installed, right click on IPlayNet folder and choose "Open In Terminal" option. Then type:

```
wine IPlayNet.exe
```

---

### Post by cogadh on 2009-07-09
> **ToppKatt said:**
> Ok this is all that comes up in the terminal after that command.

toppkatt001@OWNER-PC:~$ cd ~/.wine/drive_c/Program\ Files/IPlayNet/ wine IPlayNet.exe
[email]toppkatt001@OWNER-PC:~/.wine[/email]/drive_c/Program Files/IPlayNet$ 

Doesn't run the IPlayNet.exe and I know that it's in there.
The problem is the directory change and the wine command are supposed to be two separate commands, not one long command:
```
cd ~/.wine/drive_c/Program\ Files/IPlayNet/

hit enter, then:

wine IPlayNet.exe
```
They could be run as one command, but that would involve adding some extra info to the command, which for the purposes of this would just add an extra layer of confusion, so let's skip it.

---

### Post by ToppKatt on 2009-07-10
Ok a few errors not sure they will affect anything.  Have to reboot prior to running the game for the first time may receive more errors then but won't know without trying.  Output to the terminal follow.

toppkatt001@OWNER-PC:~$ cd ~/.wine/drive_c/Program\ Files/IPlayNet/
[EMAIL="toppkatt001@OWNER-PC:%7E/.wine"]toppkatt001@OWNER-PC:~/.wine[/EMAIL]/drive_c/Program Files/IPlayNet$ wine IPlayNet.exe
fixme:ole:OleLoadPictureEx (0xa4fbfc,1086,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32faf0), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x12a4a8)->(0x148008, 0, (nil)), hacked stub.
err:progress:ProgressWindowProc unknown msg 2210 wp=0001 lp=00010054
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
err:animate:ANIMATE_WindowProc unknown msg 2210 wp=00000001 lp=00010058
fixme:ole:OleLoadPictureEx (0xa54134,3134,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32e870), partially implemented.
fixme:ole:OleLoadPictureEx (0xa54134,3134,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32e870), partially implemented.
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on CA0106, disabling mixer
fixme:ole:OLEPictureImpl_FindConnectionPoint no connection point for {33ad4ed2-6699-11cf-b70c-00aa0060d393}
[EMAIL="toppkatt001@OWNER-PC:%7E/.wine"]toppkatt001@OWNER-PC:~/.wine[/EMAIL]/drive_c/Program Files/IPlayNet$

---

### Post by ToppKatt on 2009-07-10
hmmm no easy way to attach a screen shot.  Received this when I attempted to run the game.

COULD NOT LAUNCH "IPLAYNET"

Text ended before matching quote was found for ". (The Text was `env WINEPREFIX ="/home/toppkatt001/.wine" wine "C:\windows\command\start.exe" "C:\Program Files\IPlayNet\'")

---

### Post by cogadh on 2009-07-10
Most, if not all of those error message in your first post can be ignored. Did you actually run that command listed in the text on your second post? Also, I should have asked this earlier, but which version of iPlay are you trying? I just noticed on their website that they have both and XP/2000/Vista version and a 95/98/ME version.

---

### Post by ToppKatt on 2009-07-10
Clicking on the game Icon to open the server caused the error message to display. I am using  the Vista XP version of the game since that is the operating system I am using for Windows.  The shortcut is not valid because I clicked on the Icon in the program files and connected right away to the server.

---

### Post by ToppKatt on 2009-07-10
The last thing I need to find out is how to find out my Ipconfig.  I can change my router in windows to accept the Ipaddress to match what I am using in here once I find out what the address is.

---

### Post by ToppKatt on 2009-07-15
Thanks for all of your help.  Tread Closed

---

