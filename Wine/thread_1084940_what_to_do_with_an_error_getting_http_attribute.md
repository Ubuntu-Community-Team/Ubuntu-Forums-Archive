---
title: "what to do with an error getting http attribute?"
date: 2009-03-02
forum: Wine
---

### Post by nachos99 on 2009-03-02
i've installed a program called ClickForms and am trying to run it in wine.  

im getting an error mesasge "Error occured - Error getting http attribute (122)".  (details below)

is there a way to get past this?  or does it just mean that it doesnt run in wine and i should use a VM instead?

thanks for any suggestions.  




EurekaLog 6.0.10

Application:
-------------------------------------------------------
  1.1 Start Date      : Mon, 2 Mar 2009 12:27:49 -0800
  1.2 Name/Description: ClickForms.exe - (ClickFORMS)
  1.3 Version Number  : 6.6.0.0
  1.4 Parameters      : 
  1.5 Compilation Date: Thu, 15 Jan 2009 12:04:01 -0800
  1.6 Up Time         : 4 seconds

Exception:
---------------------------------------------------------
  2.1 Date          : Mon, 2 Mar 2009 12:27:54 -0800
  2.2 Address       : 0086D528
  2.3 Module Name   : ClickForms.exe - (ClickFORMS)
  2.4 Module Version: 6.6.0.0
  2.5 Type          : Exception
  2.6 Message       : Error getting http attribute (122).
  2.7 ID            : 2047
  2.8 Count         : 1
  2.9 Status        : New
  2.10 Note         : 

User:
---------------------------------------------------------
  3.1 ID   : 
  3.2 Name : Change preferred owner in ~/.wine/system.reg
  3.3 Email: 

Computer:
---------------------------------------------------------------------
  5.1 Name          : -desktop
  5.2 Total Memory  : 2048 Mb
  5.3 Free Memory   : 1074 Mb
  5.4 Total Disk    : 283.85 Gb
  5.5 Free Disk     : 261.42 Gb
  5.6 System Up Time: 20 seconds
  5.7 Processor     : GenuineIntel - x86 Family 15 Model 2 Stepping 9
  5.8 Display Mode  : 1152 x 864, 32 bit
  5.9 Display DPI   : 96
  5.10 Video Card   : X11 Windowing System (driver  - RAM 0 MB)
  5.11 Printer      : PDF (driver )

Operating System:
------------------------------------
  6.1 Type    : Microsoft Windows XP
  6.2 Build # : 2600
  6.3 Update  : Service Pack 2
  6.4 Language: English
  6.5 Charset : 0

---

### Post by cogadh on 2009-03-02
Instead of that EurekaLog output, it would be better to get Wine's raw terminal output. Run the app from a terminal and post what it produces, it should tell us what Wine is doing.

---

### Post by nachos99 on 2009-03-02
im sorry im a total linux noob, and thanks by the way for the reply.

is this what you are asking for? not sure if that's the correct command to run the program in wine...


desktop:~$  wine "C:\Program Files\Bradford\ClickForms\ClickForms.exe"
fixme:mixer:ALSA_MixerInit No master control found on AK5370          , disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f7a8,0x00000000), stub!

---

### Post by cogadh on 2009-03-02
Assuming that is the correct install path and executable name, that is the correct command, but is that the entire output from the application? There really should be more output.

---

### Post by nachos99 on 2009-03-02
im pretty sure it's the entire output.

and i really dont know what the output means, but i see audio related stuff in there along with something about my mic.

clickforms has nothing to do with sound/video/media etc, so im not sure what that is all about.

---

### Post by nachos99 on 2009-03-02
ive decided to just uninstall it and run it in VM.

thanks for your help.

---

