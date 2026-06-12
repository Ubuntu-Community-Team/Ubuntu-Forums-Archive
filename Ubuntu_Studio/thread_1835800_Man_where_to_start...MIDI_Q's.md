---
title: "Man where to start...MIDI Q's"
date: 2011-08-30
forum: Ubuntu Studio
---

### Post by LouManChu on 2011-08-30
The Story,
I am a very recent, and green, Ubuntu convert after a very damaging viral attack left my computer unbootable (and me tired of repeated ms windows failures).  I use the machine for the usual things and have gotten most of that going but I also use it for audio recording.  I am looking for a either a way to get an old windows program called midisoft studio to work or a very close compatible.  I would rather get it going again if I could simply because I have used it for years and it is/was very reliable and also allowed me to manually set event, note pitch, duration, and velocity information.  So far there doesn't seem to be anything like it.  I tried getting it going by using wine but I think there is a problem because the program is 16 bit.  Any suggestions?

btw, if there is an alternative software it must be able to connect to external midi devices like my old DR-5.  Thanks
LMC

---

### Post by jejeman on 2011-08-30
> **LouManChu said:**
> The Story,
I am a very recent, and green, Ubuntu convert after a very damaging viral attack left my computer unbootable (and me tired of repeated ms windows failures).So, wellcome to Ubuntu failures. ;)

As far as I understood, you need midi sequencer?
There are couple of them, depends what you need.
Personaly I've used Seq24, Muse. Also there are Rosegarden, qtractor.

---

### Post by LouManChu on 2011-08-31
Thanks, I think.  I tried Rosegarden but I found there was no actual midi playback on my system.  I then installed Timidity but the output is lousy and I couldn't figure out how to interface with external devices for the sound.  I then uninstalled all of that because all other sound files stopped playing (mp3, wav).  This is probably going to be very difficult, if not impossible.  Has anybody figured out how to install a program created in the 16 bit day that will install onto the 11.04 Natty platform like Midisoft Studio?

---

### Post by jejeman on 2011-08-31
What external devices are you using? With what connections?
Please elaborate on every thing you want to do.
Forget about windows programs, use native linux programs.
If Rosegarden didn't worked for you, maybe other programs would.

---

### Post by LouManChu on 2011-08-31
I want to connect to my DR-5 drum machine and Casio WK-200 via standard midi in/out cabling that connects to the gameport (15 pin D shape) of my Live 5.1+ card.  I'm short on funds so I use either one by itself for now. It's standard and they worked fine without problems under Windows XP Pro.  For the little time I used Rosegarden and Seq24, I could not see how to interface with either.  For all I know Linux does not see my devices.  That's the heart of the matter in itself.  With Midisoft I could use either of those devices to actually record the songs, then use the built in editor to clean it up.  Afterwords I could playback and use the external devices to provide the sound.  I can't do that as of yet.  I would like nothing better than to dump anything Windows based but I haven't yet seen anything that rivaled the simplicity of Midisoft yet allowed detailed editing or connected so well with external midi devices without problems.  I will still try out other programs but this is probably not going to work out for me.  Thanks.

btw, for everything else Ubuntu has been great, faster than Windows by far and easier in most ways to set up.  The typical home user should be running this, not Windows.

---

### Post by jejeman on 2011-09-01
Okay, now it's much clearer what you want to do. Do you connect both this devices at the same time, and than use different midi channels?
Try this, connect one of them and than issue commmand
```
amidi -l
```and give us the output.
First we need to solve the hardware connections, than you can easyly choose the sequencer to work with.

---

### Post by LouManChu on 2011-09-01
Here's the result:

Dir Device    Name
IO  hw:0,0    EMU10K1 MPU-401 (UART)
IO  hw:0,1    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:0,2    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:1,0    MPU-401 UART MIDI

For simplicity sake let's just try to get the DR-5 working as I use it more often than the Casio synth.  DR5Edit can connect to the DR-5 when I select EMU10K1 MPU-401 (UART) as my I/O connection.  So this will probably be the default when it comes to using midi editors of any kind.  I'm guessing there is a config file associated with this setting?

On a related note, I have installed Muse and I like the layout and I think it will be a useful tool but I get this error at program start that says:

*MusE will continue without audio support (-a switch)!*

If this was not intended check that Jack was started.  If Jack *was* started check that it was started as the same user as MusE.

It's not that important to me that MusE (or any midi software for that matter) be able to play back sound directly from the sound card as long as midi data can be sent to and received from the DR-5 so do I need to care about this?  Thanks, also, for your continued interest in helping me get my system back to the studio tool it was before.
LMC

---

### Post by sgx on 2011-09-02
Hi, go here,

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

and start with the bottom link, then go up. This will
show you how to connect hardware devices and software, using jackd, with its qjackctl gui. Muse will use jackd. There is some repetition among the links to skip, but lots of good reading and screenshots. You need this information, and it's not hard, and very flexible in daily use. Midisoft may run under wine, the windows api replacement. Install wine, and wineasio, using synaptic, and run the command

regsvr32 wineasio.dll

run the command  winecfg, and choose alsa for sound. A folder called
.wine will now exist in your /home/username folder, it is your
fake, but very useful, windows environment. 

run the command wine name-of-installer.exe
run the command wine name-of-midisoft.exe

Cheers

---

### Post by jejeman on 2011-09-02
You can use midi without audio in Muse.(I also get same message for it although I have perfectly running jack. I will investigate on this.)
It's good that you have find out which midi port is your hardware connector.
Here on this computer i have similar card
```
$ amidi -l
Dir Device    Name
IO  hw:0,0    Audigy MPU-401 (UART)
IO  hw:0,1    Audigy MPU-401 #2
IO  hw:0,2    Emu10k1 Synth MIDI (16 subdevices)
IO  hw:0,3    Emu10k1 Synth MIDI (16 subdevices)
```Unfortunately I don't have midi gear to connect to it.
But you can try this.
In Muse go to: Settings>midi ports/soft synth. For the port 1 choose under device name: EMU10K1 MPU-401 (UART). At this moment you sholud get two green lights for I & O. Than choose for midi track the same port for midi comunication.
Connections in qjackctl should follow and be correct. In my example I've created two ports in Muse. One for phasex soft synth, second one for hardware midi port. You can also notice that Muse has just one midi port shown in qjackctl. But it will send midi messages only to selected port on track in sequencer.

I just saw, Muse 1.1 does not work with jack2, thats why that messages appear.

---

### Post by LouManChu on 2011-09-03
Thank you guys, I was following along there and figuring some things out using qjackctl.  Setting patchbays up, I even got some data moving between devices.  Then I had to go and do something extremely dumb.  I realized that Ubuntu Studio was an installation unto its own so I decided to make the 1.5GB dvd and install it.  Bad decision.  After weeks of small hurdles in getting my machine back up and running, I screwed it up.  At the end of the install I get to this part about grub and boot sector and I choose the partition I was using all the time here and it seems to be ok...then a red screen appears and there's a message:
[B]
Unable to install grub in /dev/sda
Executing 'grub-install/dev/sda' failed.
This is a fatal error

[/B]But I am able to finally get to my desktop, after a reboot.  I find outside of the different logon screen all my stuff is there, everything seems to be working but it has loaded the nVidia 173 driver which I don't want because it doesn't work right and I can't detect my monitor or change any of the settings in there correctly, plus a few other video related issues.  So I uninstall the driver and now after the BIOS screen, all I get is a blinking cursor and any keystrokes do nothing.  I even tried reinstalling the original 11.04 disk I created but it too has a problem with the grub issue above, I get the same error message.  Looks like I have to format the partition and start it all again, from scratch.  Maybe I will be more careful now and take better notes on all of the things I'm gonna need to do to just to get back to where I was the night before.  Sorry, I'm just bitching at this point.  This was great stuff when I was younger but this old dog is getting too old to learn new tricks.  Might be a few days before I post again but I am truly appreciative of good folks like yourself helping this Linux Newb along.

**UPDATE**

Big problems now with just getting anything other than a black screen.  I have formatted and reinstalled 4 times my original Ubuntu 11.04 CD (it worked the first time I used it).  Despite all the work the only thing I see after the BIOS is Ubuntu logo with the dots for about 2-3 seconds and then nothing.  Total black screen.  I have tried all the things I can in the recovery mode like repair broken packages, reconfigure display, nomodeset, nothing is working.  Everything appears to be ok except that there was an error in one of the logs[B]:
(EE) Failed to load module "nv" (module does not exist, 0)[/B]
I also could not log in from the "use lower graphics one time" or something to that affect.  A message saying it couldn't find '/home/user' after I entered in the user and password.  I think this thread be done for now as I have bigger fish to fry.  If it aint broke, don't fix it can be painful sometimes.  Again thanks if you read this far, lol.

---

### Post by sgx on 2011-09-04
If you are still reading, if you had a separate /home partition,
you should format that during a reinstall, to thwart corrupt .config files. This /home partition would normally be preserved for convenience, but this is an abnormal occurence. Does the live dvd
boot, and run OK?

If you do reinstall, maybe try a different partition format than the default. Also, a boot option can be tested with the live media, like noacpi or acpi=off noapic, noioapic etc which can sometimes wiggle around flaky hardware detection. There should be a boot message revealing the keypress for the list of boot options.
Cheers

---

### Post by LouManChu on 2011-09-04
Thanks for reply, that has been fixed now but was taking a more methodical approach to setting things up.  I have a new problem now but will post that in a more appropriate place as this thread was intended to help me understand how to connect midi devices.  The more I go here the more it reminds me of the days of DOS and all the commands I had to learn back then.  This time, though, it seems to be going a little better, it's just a new language to learn is all.  Again, thanks.
LMC

---

### Post by LouManChu on 2011-09-08
Ok, a few reinstalls later I have finally figured out a problem is caused if I try to install drivers for my sound card.  Essentially the driver is already there and it works properly.  So after my IO errors were solved I did an update, then installed qjackctl.  As was suggested I did a lot of reading and began to understand about the patchbay and connecting ins with outs and all of that.  I now have a rudimentary patchbay with the basics.  I also took another look at Rosegarden and discovered the portion of it that I was missing from Midisoft, the events page.  I work best when I can see events, notes, pitch, velocity, as a number, each in their corresponding place in time.  I couldn't find this in any other midi editing software.  I wrote a test track last night and was able to get playback through my DR-5 sound output on all 4 tracks (DR-5 has a drum track and 3 rhythm tracks all configured to midi channels 10, 1, 2, and, 3).  Thanks for the links provided above, and for the patience from good people in here to help me along.  I'm jamming now!
LMC

---

