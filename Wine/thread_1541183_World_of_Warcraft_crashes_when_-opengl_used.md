---
title: "World of Warcraft crashes when -opengl used"
date: 2010-07-28
forum: Wine
---

### Post by JonnyPickel on 2010-07-28
Hey all,

So I've recently scrapped my install of Windows in favor of Ubuntu and the last lingering detail is my WoW install.  I've followed the instructions [found here]("https://help.ubuntu.com/community/WorldofWarcraft") and as it stands I can technically log in and play.

However!

The gameplay is unbelievably laggy.  Granted, I'm on a laptop with an Intel integrated graphics chipset so I don't expect stellar performance, but I'd like to get more than one frame every two seconds when I have all of the graphics settings turned down to their lowest level.

What's most interesting about my install is that if I run...
[INDENT]wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl[/INDENT]
...WoW will crash before ever giving me the login screen with the normal "report this error to Blizzard" screen saying that I've just experienced Error #132.  Obviously I think I'd get much better performance if I could use the -opengl flag.

Another point of interest, I've tried to renice WoW.exe to priority -20 and I don't notice any change at all.

I'm currently running Ubuntu 10.04 and Wine 1.2 so everyone knows.  Thanks in advance for any help!

---

### Post by asdfoo on 2010-07-29
Wine relies heavily on your video driver, specifically the level of OpenGL support provided by it.  Intel is not the best in this area, you may not have them correctly setup if it crashes immediately (hard to say if you don't post a log of the terminal output) [http://wiki.winehq.org/FAQ#get_log](http://wiki.winehq.org/FAQ#get_log)

Some people use ubuntu-edgers (an alternate configuration for ubuntu which uses the most recent packages involving video related things for Intel) which can improve things.

---

### Post by JonnyPickel on 2010-07-29
This might be useful.  I found on [another forum]("http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/where-can-i-find-video-drivers-for-intel-integrated-505743/") that if I run...
[INDENT]lspci | grep -i vga[/INDENT]
...I'll get an exact response for what my laptop is built with.  When I ran that command I was given this output:
[INDENT]jon@jon-laptop:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)[/INDENT]
So now I know what my chipset is.  My next goal is to find out if there's a suitable and compatible driver.

Just thought I'd post an update.  If anyone has any experience with my chipset in particular (or more specifically if you know of a driver I should use *fingers crossed*) I'd appreciate any pointers.

***Edit***
Here's the terminal output:
> jon@jon-laptop:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x195ee20,0x00000000), stub!
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
fixme:win:EnumDisplayDevicesW ((null),0,0x195eaec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f350,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f464,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f5fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f5f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f564,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f07c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195f1b4,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x139a90,0x139990): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x195f89c): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x195f89c): stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Pro Audio",0x195f89c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x195df60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x195df88,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000

And here's the error that Wine brings up:

> Wow

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:     C:\Program Files\World of Warcraft\WoW.exe
Exception:   0xC0000005 (ACCESS_VIOLATION) at 0073:375116DC

The instruction at "0x375116DC" referenced memory at "0x375116DC".
The memory could not be "read".

Press OK to terminate the application.

---

### Post by JonnyPickel on 2010-07-31
I'm having a lot of trouble finding an appropriate driver for my graphics chipset.  Does the fact that it was recognized so specifically mean I don't need to bother and I should focus instead on tweaking the settings for my graphics hardware?

---

### Post by asdfoo on 2010-08-01
> **JonnyPickel said:**
> I'm having a lot of trouble finding an appropriate driver for my graphics chipset.  Does the fact that it was recognized so specifically mean I don't need to bother and I should focus instead on tweaking the settings for my graphics hardware?

I don't know enough about the specifics because I have not owned an Intel card, every time I've researched them previously they've always been a bad choice.

I mentioned ubuntu edgers, which is a way of getting more up to date components such as the default driver for intel video cards.

This is sort of off-topic for this section of the forum though.

Any tweaks for WoW can probably be found on the wine appdb.

---

### Post by Elonion on 2010-12-06
I'm currently experiencing the same problem as the OP which is why I'm here.

A thing worth noting is that WoW was playing fine in wine on this laptop I'm using about half a year ago. I usually got around 10-20 fps with very low settings so not great but playable.

So some update have broken the OpenGL support for Intel:s mobile graphics cards during this time that I haven't played on this laptop.

lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by cwwilson721 on 2010-12-06
> **Elonion said:**
> I'm currently experiencing the same problem as the OP which is why I'm here.

A thing worth noting is that [COLOR="Magenta"]WoW was playing fine in wine on this laptop I'm using about half a year ago[/COLOR]. I usually got around 10-20 fps with very low settings so not great but playable.

So some update have broken the OpenGL support for Intel:s mobile graphics cards during this time that I haven't played on this laptop.

lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)WoW has upped the graphics. That was about the time the big 3.5 patch came out, to start ramping up for Cata.

Sorry to say, wine/WoW and Intel = FAIL. It's a combination of opengl/Intel. Intel chips and drivers don't fully implement opengl.

Until there's a MAJOR revamp of drivers (the newest xorg attempt doesn't even help), you're stuck with Windows, or get another laptop.

---

### Post by Roger_Rodonyà on 2011-12-17
> **cwwilson721 said:**
> WoW has upped the graphics. That was about the time the big 3.5 patch came out, to start ramping up for Cata.

Sorry to say, wine/WoW and Intel = FAIL. It's a combination of opengl/Intel. Intel chips and drivers don't fully implement opengl.

Until there's a MAJOR revamp of drivers (the newest xorg attempt doesn't even help), you're stuck with Windows, or get another laptop.

Sorry about write in to an old theme, and sorry for my bad english.

The solution for run wow using an intel is download "driconf", from "centre de programari ubuntu" (Sorry i don't know how is in english), but is on where the programs were downloads in ubuntu. Well, after download driconf, you should open it and turn on "S3TC"support. This is in to graphic quality's tab.

Running on wow 4.3, ubuntu 11.10, and wine 1.3

Greetings from Catalunya.

---

### Post by Dlambert on 2011-12-17
> **Roger_Rodonyà said:**
> Sorry about write in to an old theme, and sorry for my bad english.

The solution for run wow using an intel is download "driconf", from "centre de programari ubuntu" (Sorry i don't know how is in english), but is on where the programs were downloads in ubuntu. Well, after download driconf, you should open it and turn on "S3TC"support. This is in to graphic quality's tab.

Running on wow 4.3, ubuntu 11.10, and wine 1.3

Greetings from Catalunya.

Basically: ```
sudo apt-get install driconf
```

Then :

```
driconf
```

Image quality tab turn on S3TC on.

Also, the following wine registry editing works

> Graphics
If you are having trouble with your graphics, add the following to config.wtf:

SET ffxDeath "0"
SET ffxGlow "0"
Note: Disabling ffxGlow may also enable antialiasing for some users.

If you experience a problem with missing character and object models, and/or the login windows background is black, add:

SET M2UseShaders "0"
regedit tweaks
This is a simple registry edit for Wine that either will either fix crash issues and increase frame rate in game, or it will decrease the performance and even make the game crash. You should give it a try to see what is does for you, as you may always easily remove it again, if it acts negatively for you.

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

Find this key HKEY_CURRENT_USER\Software\Wine\
Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
Right-click on the wine folder and select [NEW] then [KEY]
Replace the text New Key #1 with OpenGL
Right-click in the right hand pane and select [NEW] then [String Value]
Replace New Value #1 with DisabledExtensions (Notice it's case sensitive!)
Then double click anywhere on the line, a dialog box will open.
In the value field type GL_ARB_vertex_buffer_object



And instead of using the -opengl :  

> The Windows version of World of Warcraft supports 3D rendering using either Direct3D or OpenGL. However, in Wine the Direct3D mode is supported only through an emulation layer that runs on top of OpenGL. Therefor it's highly recommended that you enable the OpenGL mode directly, instead of using it indirectly through Direct3D.

Find the file wtf/Config.wtf in your main WoW directory. By default it is found in /home/<username>/.wine/drive_c/Program\ Files/World\ of\ Warcraft/, where <username> is you computer login name.

Open config.wtf using a text editor and add or change the following line:

SET gxApi "opengl"
Note: If config.wtf does not exist, run the game and log into a character, then exit WoW. The game should then have created the file.

---

### Post by lisati on 2011-12-17
Time for this old thread to go back to sleep.

---

