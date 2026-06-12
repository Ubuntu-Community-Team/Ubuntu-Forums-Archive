---
title: "dssi-vst + Addicitve Drums"
date: 2011-08-18
forum: Ubuntu Studio
---

### Post by 0p70u7 on 2011-08-18
so this may be a noob question because i'm not incredibly familiar with the os yet, but i'm trying to load addictive drums through the console with the vsthost command. i start QJackCtl and then type as follows and the result.

[FONT=Courier New]a3n05m41@a3n05m41:~$ vsthost AddictiveDrums
Returning file identifiers: 3cxFRS0CsWeYuhTdC3DqKvZ8
DSSI_PATH not set, defaulting to /home/a3n05m41/.dssi:/usr/local/lib/dssi:/usr/lib/dssi
RemoteVSTClient: executing /usr/local/lib/dssi/dssi-vst/dssi-vst-server -g AddictiveDrums,3cxFRS0CsWeYuhTdC3DqKvZ8
DSSI VST plugin server v0.986
Copyright (c) 2004-2010 Chris Cannam
Loading "AddictiveDrums"... 
VST_PATH not set, defaulting to /home/a3n05m41/vst:/usr/local/lib/vst:/usr/lib/vst
dssi-vst-server[1]: found in /home/a3n05m41/vst/AddictiveDrums
done
Testing VST compatibility... 
dssi-vst-server[1]: VST entrypoint "VSTPluginMain" found
Plugin server timed out on startup: No such device or address
vsthost: bailing out
[/FONT]
[FONT=Verdana]not sure what else to try, i've installed a whole ton of recommended libraries, just seems to crash without cause[/FONT]

---

### Post by sgx on 2011-08-18
Hi, Reaper is by far the best host for vsts in linux, followed by
the windows version of Energy XT2, and several others. Reaper will
require a solid wine/wineasio installation, and enough google time
to sort the basics. By learning the Preferences panels, and clicking all the mousebuttons on widgets in the upper-right corner area, 20% or so of screen size, popups will show you the most needed options.
Reaper installer is 5.8 meg, and puts everything in one folder, so
it's a safe install. Drumcore and EZDrummer also should work. AD has
a great sound!
Cheers

---

### Post by eric71 on 2011-08-19
sgx's advice is especially true regarding today's drum plugins that come with drag and drop midi drum loops. Sure, it's possible to open these in native linux apps with dssi-vst, but dragging and dropping loops into Rosegarden, Qtractor or future versions of Ardour won't work. With Reaper and wineasio it does.

---

### Post by 0p70u7 on 2011-08-19
hello, thank you for the tips.  i upgraded from windows 7 about a week ago. my old setup consisted mostly of acid pro and ezdrummer. i was glad to see a quality open source drum machine available (hydrogen) but i really don't like to fiddle with stuff too much to get the sounds i'm looking for (among other things). i read about reaper in the sticky, couldn't i just run acid pro? i don't have this wine thing quite figured out yet.

also, can reaper be used as a midi sequencer? for drums and keys namely?

edit: i've got reaper working with addictive drums! thanks again! now to figure out the midi..

---

### Post by sgx on 2011-08-19
> **0p70u7 said:**
> hello, thank you for the tips.  i upgraded from windows 7 about a week ago. my old setup consisted mostly of acid pro and ezdrummer. i was glad to see a quality open source drum machine available (hydrogen) but i really don't like to fiddle with stuff too much to get the sounds i'm looking for (among other things). i read about reaper in the sticky, couldn't i just run acid pro? i don't have this wine thing quite figured out yet.

also, can reaper be used as a midi sequencer? for drums and keys namely?
wine
is
not
emulator

It's just a basic windows framework that works quite well. Once wine is installed, it is used as a command. Create this path of folders,
after running  winecfg

/home/user/.wine/drive_c/Program Files/Steinberg/VstPlugins

(when running a wine command, spaces in windows filenames should be filled with an * as in
Program*Files  or

wine /home/username/.wine/drive_c/Program*Files/IK*Multimedia/AmpliTube*Jimi Hendrix/AmpliTube*Jimi*Hendrix.exe

wine reaper401-install.exe

wine reaper/reaper.exe

After installing wineasio, use the command

regsvr32 wineasio.dll

Then choose wineasio in the reaper device preferences. I have not
read about reaper features not working in wine, but for basic recording, it's very useful and flexible. It's output can be routed
using qjackctl, patchage etc, to any jackd input, for recording, or further processing. 
Cheers

---

