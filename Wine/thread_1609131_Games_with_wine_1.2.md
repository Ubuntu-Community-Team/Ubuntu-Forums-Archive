---
title: "Games with wine 1.2"
date: 2010-10-30
forum: Wine
---

### Post by Kexolino on 2010-10-30
I have wine 1.2.
I installed some games without any problems (counter strike 1.6, pop warrior within) but none of them works. It just says starting game on the panel, and then nothing happens. Notepad works. I installed Icy Tower, and that started once, but when I switched it to fullscreen, the whole computer froze...
Can this be fixed? I have other problems too, like ipod doesn't work with gtkpod anymore, and I get weird bugs that no one really knows how to fix.. so I was thinking about reainstalling Ubuntu, but I really don't want to do that, if it's not necessary...

---

### Post by gradinaruvasile on 2010-10-30
Start the applications in a terminal and see the error messages.
For games you probably will have to install directx9 - i did it and 3d games work.

---

### Post by bobwyajnr on 2010-10-30
**@Kexolino**

What kind of hardware are you running Lucid on? Is your system/rig actually stable? (Good/known working powersupply, motherboard, etc.)

What kind of graphics card are you using? Are you using an open source or proprietary driver for this?

Can you actually play any native OpenGL 3D GNU/Linux games (i.e. not via WINE) at all?
e.g. [Linux Game Database]("http://www.lgdb.org/list_games")

Have you visited the WINE AppDB for your applications:
e.g. [WINE AppDB : Counter Strike 1.6]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18484")

When asking questions on the forums you should stick to the area the sub-forum covers... Issues with your iPod+native applications need to go elsewhere I'm afraid!

Bob

---

### Post by dino99 on 2010-10-31
latest wine is 1.3.6 ( [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa) )

you can run winetricks to add/replace some libs/fonts/drivers ...

[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by Kexolino on 2010-11-11
> **bobwyajnr said:**
> **@Kexolino**

What kind of hardware are you running Lucid on? Is your system/rig actually stable? (Good/known working powersupply, motherboard, etc.)

What kind of graphics card are you using? Are you using an open source or proprietary driver for this?

Can you actually play any native OpenGL 3D GNU/Linux games (i.e. not via WINE) at all?
e.g. [Linux Game Database]("http://www.lgdb.org/list_games")

Have you visited the WINE AppDB for your applications:
e.g. [WINE AppDB : Counter Strike 1.6]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18484")

When asking questions on the forums you should stick to the area the sub-forum covers... Issues with your iPod+native applications need to go elsewhere I'm afraid!

Bob

My graphics card is nvidia geforce 9600GT. I don't really know the other stuff because they were changed without me knowing (I haven't really had the time to look at the thing, and I'm not really familiar with these thing, to be honest)

I'm using a proprietary driver (NVIDIA accelerated graphics driver), and yes I can play games like that. Yes, I have visited the AppDB.

You're right, I asked that elsewhere though, but it wasn't solved, and I didn't want to open so many threads :)

---

### Post by bobwyajnr on 2010-11-11
> **Kexolino said:**
> My graphics card is nvidia geforce 9600GT. I don't really know the other stuff because they were changed without me knowing (I haven't really had the time to look at the thing, and I'm not really familiar with these thing, to be honest)

I'm using a proprietary driver (NVIDIA accelerated graphics driver), and yes I can play games like that. Yes, I have visited the AppDB.


OK so it's a card with decent support under Linux - that's all good! I'd recommend getting the latest Nvidia driver. If you are not confident about downloading and installing it directly from Nvidia you can get a PPA [here]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") (it's the VDPAU version).

Next I would advise that you install Wine 1.3.6 [here]("http://www.winehq.org/download/deb"). I use this version myself and appears to be quite stable for running Windows <DX9.0c games.

Then the final step is to run the problematic games in Wine - but launch them in a BASH shell/ console window. This way you get output spewed into the console which will (hopefully) include any errors stopping the application from working.

Sorry about bring the command line interface into the picture but it is necessary!!

So you fire up a BASH shell (Terminal or Konsole, etc). I am assuming you haven't used a Wineprefix (basically where Wine uses a different profile directory in your home folder).
```

cd ~/.wine/drive_c/Program\ Files\

```
**Change Directory** - changes you to the "Program Files" directory of the default Wineprefix directory.
```

ls

```
**List**s the contents of the current working directory.
```

pwd

```
**Present working directory** - lists where you are currently in the directory hierarchy.

You need to find (say) the Counter Strike install directory (using **ls** - to list folders and files in the current directory - and then **cd** to move into a subdirectory). The BASH shell will "tab complete" what you type in if you start type the first letter or two of a directory and press the **TAB** key.

If Wine has setup a shortcut for Counter Strike on your desktop you can right-click on this with your mouse - to get the properties of the shortcut. This will show you the main executable name and path for the game. Then you need to get to this path in your terminal window. Type
```
cd 
```
into your terminal window (with a space after it) and then cut & paste the working path (from the shortcut properties window) directory into your terminal window. NB pasting into a terminal window is either done using the RH mouse button or _CTRL_+_SHFT_+V (not the normal keyboard shortcut of _CTRL_+V). Then press the _RETURN_ key to go to the games main directory in your terminal window.

Once you have found the main (start) executable for the game *and* your **pwd** is the directory where that executable is stored. You would run it using:
```

wine CS.exe &> ~/debug.txt

```
typed at the command line. This will launch the game and all the console output from Wine will be stored in a file called **debug.txt** in your home folder.

If you managed to do all that (!!) then could you post a follow-up message with the debug file attached? Otherwise just let me know where you got stuck. It's a bit of steep learning curve to start using a BASH shell if you haven't done so before! ):P

Bob

---

### Post by Kexolino on 2010-11-12
I got everything up to the point where I have to write the path in the terminal; this is what I found, but which part do I have to write in the terminal after the cd command? env WINEPREFIX="/home/noel/.wine" wine "C:\Program Files\Counter-Strike 1.6\cstrike.exe"

---

### Post by bobwyajnr on 2010-11-13
> **Kexolino said:**
> I got everything up to the point where I have to write the path in the terminal; this is what I found, but which part do I have to write in the terminal after the cd command? env WINEPREFIX="/home/noel/.wine" wine "C:\Program Files\Counter-Strike 1.6\cstrike.exe"

OK that's good!

The fullpath for you software is actually:
```

cd '/home/noel/.wine/drive_c/Program Files/Counter-Strike 1.6/'

```
Then run Counter Strike via Wine:
```

wine cstrike.exe &> ~/debug.txt

```

Bob

NB for your reference the forward-slashes **\** in the Counter-Strike shortcut are Windows delimiters between folder names. The Linux shell uses back-slash **/** characters to delimit folder names in a path. (Wine is able to interpret the Windows form as an argument if the whole path is quoted **" "**.)

---

### Post by Kexolino on 2010-11-13
So this is in the debug file:
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\Counter-Strike 1.6\\cstrike.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Counter-Strike 1.6\\cstrike.exe" failed, status c0000135
By some miracle Icy Tower is working perfectly (even before installing 1.3), and Warrior Within starts, without any sound (Warrior Within is installed from an original cd, CS probably wasn't original)

---

### Post by bobwyajnr on 2010-11-13
> **Kexolino said:**
> So this is in the debug file:
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\Counter-Strike 1.6\\cstrike.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Counter-Strike 1.6\\cstrike.exe" failed, status c0000135


Type the following in a console window to load the Visual Basic 6.0 runtime libraries (which includes that missing .DLL):
```

winetricks vb6run

```

Run Counter-Strike again (from the console) and report back how you get on!

RE: **Prince of Persia: Warrior Within**
have you tried running this under Wine 1.3.6?
[There appears to be a sound bug posted with this under Wine 1.2]("http://bugs.winehq.org/show_bug.cgi?id=23536").

Bob

---

### Post by Kexolino on 2010-11-14
Now it started, but it only showed the main menu's background
fixme:ole:OleLoadPictureEx (0x92e114,7790,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fa70), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0x12d2a0)->(0x12fb48, 0, (nil)), hacked stub.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f500,0x00000000), stub!
fixme:ddraw:ddraw7_FlipToGDISurface iface 0x140d38 stub!
fixme:shdocvw:ViewObject_SetAdvise (0x1be2d8)->(1 00000002 0x125d438)
fixme:shdocvw:PersistStreamInit_InitNew (0x1be2d8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1be2d8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1be2d8)->(ffffffff)
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8a2, disabling mixer
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x1c6820,0x1c6c60): stub
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1789 requests (1789 known processed) with 0 events remaining.

Yes I tried to run PoP, it's the same, and it can't switch fullscreen completely

---

### Post by bobwyajnr on 2010-11-14
Hi **Kexolino**

[LIST=1]
[*]The screen problems are caused by running Compiz-Fusion visual effects. Even the basic "some visual effects" setting in the Ubuntu control panels will enable this. As these effects are run using GPU resources they can cause conflicts with OpenGL 3D-based applications like Wine. You will find most Wine (/Windows) 3D games are best launched under [Metacity]("http://en.wikipedia.org/wiki/Metacity") (the current default Gnome Window Manager).
The easiest way to control this (without resorting to the commandline/ BASH scripts) is to install the [CompizFusionIcon]("http://wiki.compiz.org/CompizFusionIcon") - which you can do in **Synaptic**. This will run an icon in your notification area that allows you to switch between Compiz and Metacity easily. I think you need to set this to autostart with Ubuntu (if you want to) - also an option in the right-click menu.


[*]The problem with your audio sounds (bur-dum) like the wrong output device is set for your PulseAudio service. The best bet would be to try installing [PAVUControl]("http://manpages.ubuntu.com/manpages/jaunty/man1/pavucontrol.1.html") (which should also show up in **Synaptic**). This will allow you to set the default output audio device - the device that your ALSA sound layer will try to connect to.
It is also important to run **winecfg** (either from the Start Menu under **Wine**-**Configure Wine** or on the command line). Select the audio tab and make sure that ALSA is selected as an output device and that it is outputting to "sensible" device name (i.e. the one you chose previously in the Pulse Audio Volume controller app)!
[/LIST]

Please post here back your problems :-({|=  or good news! :popcorn:

Bob

---

### Post by Kexolino on 2010-11-14
Hi,
I already had Compiz Fusion Icon installed, so I could try that today, but sadly nothing changes :-k

I'll try the audio part tomorrow. And thanks for all the help!

---

### Post by Kexolino on 2010-12-04
OK, I tried the audio too. Now ALSA is ticked in the audio menu, but nothing changes. Was I even supposed to do that?
Sorry for the "delay". School, teachers, you know.

---

### Post by gradinaruvasile on 2010-12-04
Wines ALSA doesnt always work nice with PulseAudio. I switched to OSS via padsp.
But i use Debian and i still have OSS, but as i heard Ubuntu does not have it anymore...

Also in the later Wine versions (1.3.6 and up, 1.3.8 now) there is gstreamer support that some games can use - i play LotRO and i have direct access to PulseAudio via gstreamer (perfect sound).

But other games like CounterStrike cannot use this and wines ALSA playback is skipping - OSS + padsp is better, but not perfect.
Or there is an option to use Esound emulation (via PulseAudio) - it is not perfect, but its working better than ALSA atm for me (and worse that OSS).


BTW - try LotRO (install pylotro as launcher, the default one is crap and does not work), it is free now and works perfectly with wine (untick in winecfgs window the "allow the window manager to decorate the windows" to be able to switch fullscreen/windowed mode).

---

### Post by bobwyajnr on 2010-12-04
> **gradinaruvasile said:**
> Wines ALSA doesnt always work nice with PulseAudio. I switched to OSS via padsp.
But i use Debian and i still have OSS, but as i heard Ubuntu does not have it anymore...


I agree but the big push is for PulseAudio. (Well really for the whole translation layer to be ripped out and started from scratch - but that's another story!!)

Basically I was recommending that **Kexolino** fully checks out the PulseAudio option before going on to something less mainstream. 

Personally I have found PulseAudio to work OK as long as you have the **PAVUControl** application installed.

As a _last resort_ there is a [Ubuntu PPA for Gnome OSS Support]("https://launchpad.net/~holindho/+archive/gnome-opensound").

Bob

---

