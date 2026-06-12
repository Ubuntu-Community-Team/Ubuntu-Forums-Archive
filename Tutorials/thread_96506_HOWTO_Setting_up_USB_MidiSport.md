---
title: "HOWTO: Setting up USB MidiSport"
date: 2005-11-29
forum: Tutorials
---

### Post by yaaarrrgg on 2005-11-29
[SIZE="3"]Setting up Midisport Uno, Midisport 1x1, or Midisport 2x2, USB-2-Midi [/SIZE]

The Midisport Uno is a usb-based cable that connects a midi controller (like a synthesizer) to a usb port on your computer.  Then you can use a midi sequencer like Rosegarden to record and edit music scores.  A while back, I didn't have a sound card that had midi ports, so I just purchased a Midisport Uno instead.  The advantage to the using a Midisport is that you don't need a special sound card for midi devices, and can connect them to any computer that has a free usb input. 

If your device does not auto-magically work out of the box, setting this device up for Linux is not that tricky.  The Midisport Uno requires firmware to be loaded to the device before it will do anything.  In other words, you need (a) a firmware file, and (b) a program for loading the firmware.

Install the **midisport-firmware** package (firmware is included in package).  

If you prefer the graphical interface, go to:

**Applications -> Ubuntu Software Center**

And search for midisport.  You should see the package named "**midisport-firmware**."  Click install.

Or, you can install the firmware by running this command in a terminal:

```

sudo apt-get install midisport-firmware

```

Now plug in the USB cable and you should be good to go (you should see pulsing lights).  

That's it.  ENJOY!  

**------------------------------------------------------------------------------------------------------------**

If you have an older/alternate version of Linux, there are more how-to's below which may work:

**This is a HOWTO for Ubuntu 9.04 (Jaunty Jackalope)**

I'll give two ways to set this up.  The first method (in Section I) should be easiest.  The second method (in Section II) will almost always work if the first does not.

**Section I.**

First install the midisport-firmware package (firmware is included in package).  You can run:

```

sudo apt-get install midisport-firmware

```

Now you will need to create a configuration file (that defines the rules for recognizing the device and loading the firmware).  

You can create/edit this file by running:

```

gksudo gedit /etc/udev/rules.d/99-midisport-firmware.rules

```

Then paste the following code:

```

# midisport-firmware.rules - udev rules for loading firmware into MidiSport devices

# MidiSport 1x1
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1010", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport1x1.ihx -D %N"

# MidiSport 2x2
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1001", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport2x2.ihx -D %N"

# KeyStation
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1014", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSportKS.ihx -D %N"

# MidiSport 4x4
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1020", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport4x4.ihx -D %N"

# MidiSport 8x8
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1031", ATTRS{bcdDevice}=="0110", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport8x8-2.10.ihx -D %N"
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1031", ATTRS{bcdDevice}=="0121", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport8x8-2.21.ihx -D %N"

# vim: ft=conf


```

Then save the file, it should force the rules to reload.  

Then plug in device and you should see flashing lights.  This means that the firmware has loaded and you are in business. 

Tip borrowed from post [#59](http://ubuntuforums.org/showpost.php?p=6206159&postcount=59).

**Special Notes on Ubuntu 8.10 Intrepid Ibex, 8.04 Hardy Heron**

A config file exists, but is broken.  The same steps above will work, or you can edit the existing file with:

```

gksudo gedit /etc/udev/rules.d/*-midisport-firmware.rules

```

**Special Notes on Ubuntu 7.10 Gutsy Gibbon**

Looks like the only difference between the gutsy and the ibex file is the SUBSYSTEM string is matching on "usb_device" instead of "usb".  So I used a wildcard in the conf to match both patterns.  The same patch should work for both systems.

For more info see post [#39]("http://ubuntuforums.org/showpost.php?p=4342648&postcount=39"), [#41]("http://ubuntuforums.org/showpost.php?p=4375773&postcount=41")

[B]------------------------------------------------------------------------------------------------------------
[/B]

**Section II. -- Alternate Instructions**

If the above instructions do not work, try these below... this is not the easiest method, but it will almost always work.

See post #60:
[http://ubuntuforums.org/showpost.php?p=6224184&postcount=60](http://ubuntuforums.org/showpost.php?p=6224184&postcount=60)

[B]------------------------------------------------------------------------------------------------------------
[/B]

**Section III.**

**Configuring Rosegarden and Your Keyboard**

In Rosegarden, goto:

```

	Studio -> Manage Midi Devices

```

I selected my midisport as the playback and record option. (I use my synthesizer for generating sound rather than my cheap sound card.)

Note, if you hear phase shifting when recording, or choppy playback, you probably need to turn off the local control on the keyboard.

---

### Post by gosh on 2006-03-01
I try to set up my 1x1, but get this message when i try to load:

```
jos@ubuntu:~/usbmidi$ sudo fxload -I /etc/firmware/ezusbmidi1x1 -D /proc/bus/usb/001/003
/etc/firmware/ezusbmidi1x1: unable to open for input.

``` 
Any ideas?

---

### Post by gosh on 2006-03-05
I've found it:

The command should read:
```
~/usbmidi$ sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/001/003
```

---

### Post by arnoudscheer on 2006-04-27
... seems to be no problem after all

---

### Post by yaaarrrgg on 2006-04-29
thank you for the feedback... corrected the typo.

---

### Post by sbennettgso on 2006-10-26
I got to the step above where I'm supposed to load the firmware on my Uno, and I got an error about some pipe being broken (I don't have it in front of me right now).  So I abandoned this and used [http://usb-midi-fw.sourceforge.net/]("http://usb-midi-fw.sourceforge.net/")

This seems to work fine; it even seems to do plug and play, but I have to plug it in after I power up or it takes priority over my sound card and then the sound card won't work.

I'm a new Ubuntu (and Linux) user running Dapper Drake, so that might be a reason the above step didn't work for me.  Is it different than for Breezy?

---

### Post by gosh on 2007-01-09
> **sbennettgso said:**
> I got to the step above where I'm supposed to load the firmware on my Uno, and I got an error about some pipe being broken (I don't have it in front of me right now).  So I abandoned this and used [http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/)

This seems to work fine; it even seems to do plug and play, but I have to plug it in after I power up or it takes priority over my sound card and then the sound card won't work.

I'm a new Ubuntu (and Linux) user running Dapper Drake, so that might be a reason the above step didn't work for me.  Is it different than for Breezy?

I just tried this too, but didn't work on my 1x1. So no plug and play for me, not even after reboot with or without usb plugged in.

---

### Post by gosh on 2007-01-09
Q: Why does the device number and name of the device change after fxload?
This is what I mean.

before fxload: Bus 005 Device 009, name Midiman Midisport 1x1
```
jos@jos-desktop:/tmp/midisport-firmware-1.2$ lsusb
Bus 005 Device 009: ID 0763:1010 Midiman Midisport 1x1
Bus 005 Device 007: ID 05ac:1300 Apple Computer, Inc. iPod Shuffle
Bus 005 Device 006: ID 6993:b001 Freshtel FT-102 VoIP USB Phone
Bus 005 Device 002: ID 07ff:00ff  
Bus 005 Device 004: ID 0930:653e Toshiba Corp. 
Bus 005 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:00d1 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08c5 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

```

After fxload: Bus 005 Device 010, name Midiman
```
jos@jos-desktop:/tmp/midisport-firmware-1.2$ sudo midisportsetup
fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/005/009
jos@jos-desktop:/tmp/midisport-firmware-1.2$ lsusb
Bus 005 Device 010: ID 0763:1110 Midiman 
Bus 005 Device 007: ID 05ac:1300 Apple Computer, Inc. iPod Shuffle
Bus 005 Device 006: ID 6993:b001 Freshtel FT-102 VoIP USB Phone
Bus 005 Device 002: ID 07ff:00ff  
Bus 005 Device 004: ID 0930:653e Toshiba Corp. 
Bus 005 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 045e:00d1 Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:08c5 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  

```

---

### Post by yaaarrrgg on 2007-01-15
hmmm good question!  I hadn't noticed that.  

I wonder if fxload is re-registering the usb device?  Maybe the first is the default usb connection (which is broken?) ... not sure. :-k

---

### Post by ronoc on 2007-01-24
Hi,
Great instructions!
I have a midiman usb 2x2. Carried out the instruction for 1x1 by mistake first. The firmware did load though. With 2x2 firmware loaded the box seems to be all good. Input from both A and B seems fine going on the light from the indicators. 
But how do I get this to work in Pure Data?
I have a layla 24 but couldn't get the midi to work (didn't try to hard).  There is no option in pd to use the midiman device for midi only 
- default midi (which gave no options)
- alsa midi which started fine but PD did not register any input. Granted I did not look any further into this.

Should the midi man appear as the default device? As I said the box itself looks good with it's interaction with the keyboard.

regards,
Conor

---

### Post by ronoc on 2007-01-24
oh yeah 
I'm running ubuntu dapper 6.06 with the most recent stable alsa firmware.

---

### Post by yaaarrrgg on 2007-02-01
> **ronoc said:**
> Hi,
But how do I get this to work in Pure Data?
I have a layla 24 but couldn't get the midi to work (didn't try to hard).  There is no option in pd to use the midiman device for midi only 
- default midi (which gave no options)
- alsa midi which started fine but PD did not register any input. Granted I did not look any further into this.

Should the midi man appear as the default device? As I said the box itself looks good with it's interaction with the keyboard.


I haven't used Pure Data....  I tried to install it, but ran into some problems. :)

BTW, does your midi man device show up under /dev/midiXX ?  I did notice this bit:

> 
...PD can use raw MIDI devices to read MIDI events that are specified with the option '-midiindev <devnumber>' but it has an irritating way of specifying which device to use. The formula is as follows: To use /dev/midi0, start PD with 'midiindev 1', to use /dev/midi1 start it with '-midiindev 2' and so on. Got it? You must specify the real device number plus 1 here. Another example: For /dev/midi21 start PD with '-midiindev 22'


from [http://tldp.org/HOWTO/MIDI-HOWTO-10.html](http://tldp.org/HOWTO/MIDI-HOWTO-10.html)

---

### Post by UNoob on 2007-02-05
Howdy,

I'm brand new to the whole Linux/Debian/Ubuntu enviro.  Currently using Ubuntu 6.10 (Edgy) on old Gateway 1Ghz pc.  This may not be the right forum for this, but I'll give it a shot.

I followed the instructions listed in the first post to the tee (different .ihx file, of course), and I was able to get my install of Linux to recognize my Midisport 2x2.  I was able to set up Rosegarden to handle the Midisport as an input device.  However, I can't get any midi data to record on the software, or even make a noise, when I press on my attached keyboard.  Frustrating!

Anything I might have missed in the install process?

I should also mention that I'm using an external USB audio card, run through JACK so as to access the sound capabilities in Rosegarden.  Would the fact that I (appear to be) bypassing ALSA have anything to do with it?

Please help.  Thanks!

Helen

---

### Post by gosh on 2007-02-06
Did you made the right connections in Jack?
And what do you mean by bypassing Alsa?

---

### Post by corevette on 2007-02-16
i followed the steps...and the USB light to my Midisport 1x1 constantly dims on and off.  i tried going to KMid or Rosegarden....but they don't recognize the midi.  the firmware is use is the midisport-firmware-1.2

i'm running edgy...any ideas?

---

### Post by Raptor Ramjet on 2007-03-02
Hello,

I've just purchaed a Midisport 2x2 and I'm keen to set it up so my Linux box can join in with my other MIDI gear.

However... If I'm correct then this thread seems to indicate that following the instructions would lead to me updating the firmware in my Midisport with a custom version.

I was therefore just wondering if this is indeed the case ?  as, if so, I'll need to get another device for my Linux box as the Midisport has been bought primarily as a portable solution for when I want to take my main music PC into the studio (my main PC runs Logic 5.5.1 hence it's Windows based)

However if I could first unload the existing firmware before installing Linux firmware for home use but still be able to relod the original firmware for when I want to use the Midisport with Windows that would be "just grand".

Any suggestions as to how I can do this would be most welcome.

---

### Post by yaaarrrgg on 2007-03-13
> **Raptor Ramjet said:**
> Hello,
However... If I'm correct then this thread seems to indicate that following the instructions would lead to me updating the firmware in my Midisport with a custom version.


It's been a while since I read the specifics about the midisport...

although my general understanding is that Windows also loads firmware onto the Midisport, when you plug it in.  In other words, when you unplugged the Midisport, I believe the firmware is lost (not persistent).

I've used the midisport with both Linux and Windows (dual booting).  The only thing I'd recommend is doing a cold boot, or unplugging the midisport when swithing between the two (if it's the same machine).  Otherwise, the firmware may not get relloaded.

HTH

---

### Post by t1m on 2007-04-06
Hmmm.
I tried this tutorial, and I got an error about a broken pipe. :( 
> **sbennettgso said:**
> I got to the step above where I'm supposed to load the firmware on my Uno, and I got an error about some pipe being broken (I don't have it in front of me right now).  So I abandoned this and used [http://usb-midi-fw.sourceforge.net/]("http://usb-midi-fw.sourceforge.net/")

This seems to work fine; it even seems to do plug and play, but I have to plug it in after I power up or it takes priority over my sound card and then the sound card won't work.

I'm a new Ubuntu (and Linux) user running Dapper Drake, so that might be a reason the above step didn't work for me.  Is it different than for Breezy?

 I tried installling usb-midi-fw, but how do I test to see if it works? (I know that's a strange question, but I tried Rosegarden and couldn't figure how to record from my kyboard.) Maybe I'm asking for a tutorial.

[SIZE="1"]*scratches head*[/SIZE]

Tnx

[B]Update:
I found out I was using an old version of rosegarden (there are actually three in the repos!)
I upgraded... all fixed! I can play from my keyboard now! :KS  [/B]

---

### Post by jeremie2 on 2007-04-24
Hi yaaarrrgg, 

Just to say tanks for your how-to which has solved a few problems I had with my M-Audio USB MIDISPORT Uno. 
I have also created a wiki-page ([http://wiki.ubuntu-it.org/Hardware/Audio/MidisportUsb](http://wiki.ubuntu-it.org/Hardware/Audio/MidisportUsb)) on the Italian Ubuntu-wiki that shows two methods: one is based on what you have written and the other is based on the readme file which is inclouded in the tar.gz downloadable at [http://usb-midi-fw.sourceforge.net](http://usb-midi-fw.sourceforge.net).

I describe my experience: 
The [http://usb-midi-fw.sourceforge.net](http://usb-midi-fw.sourceforge.net)'s firmware was working well on Dapper. I had some problem using it on Edgy and Feisty. To make it work on Edgy and Feisty I needed to start a session on Dapper and then restart with Edgy or Feisty. 
Now with your how-to I can load the firmware whenever I want... well done! :) 

Thanks again

---

### Post by xi0n0ix on 2007-06-13
Hello,

Most of this seemed to work pretty well.... I can  now type "midisportsetup" and my midisport will work fine (firmware loads).

This is all great but I need the firmware to be loaded to the midisport on boot.  It seems after some extensive searching that there is some kind of bug in 'udev' that does not automatically load the firmware. Am I correct in this assumption?   If I do a udev restart using this method the midisport is also loaded with firmware fine.

I took a look here for a possible fix:
[http://hans.fugal.net/yodl/blosxom.cgi/2005/11/index.html](http://hans.fugal.net/yodl/blosxom.cgi/2005/11/index.html)

This did  not help me too much. I would love udev to be able to load firmware on boot and be able to load upon 'hotplug'. Has anyone come up with a possible solution to the udev problem?

I was thinking i could just put the suggested script in /etc/init.d/ and do something like this:

$ sudo update-rc.d -f midisportsetup start 99 2 3 4 5 

that might work but I haven't tried it yet because I'm really itching to get the udev stuff to work instead...

Thanks for any help/suggestions!

BTW I am on 7.04 and Midisport 2x2.....

mark

---

### Post by xi0n0ix on 2007-06-13
hmmmm....

if i just do a:

$ udevtrigger

after a base install on the firmware:

./configure
make
make install

... the midisport fires up and works fine.  BUT why does udev not load the firmware on boot? udev must be  given a command after boot to work....

m

---

### Post by deadgobby on 2007-08-26
Midisport-firmware can be found in synaptic for Feisty.
I was about to go through the guide and saw it there. Wooo Hooo

Gobby

---

### Post by theorganloft on 2007-10-20
I GET THIS ERROR.  

root@theorganloft:~# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0763:1010 Midiman Midisport 1x1
Bus 005 Device 002: ID 0763:1014 Midiman 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@theorganloft:~# fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/005/003
/proc/bus/usb/005/003: No such file or directory
root@theorganloft:~# fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/005/003
/proc/bus/usb/005/003: No such file or directory
root@theorganloft:~# 


Thanks for any help.

---

### Post by yaaarrrgg on 2007-10-22
> **theorganloft said:**
> I GET THIS ERROR.  

root@theorganloft:~# lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 0763:1010 Midiman Midisport 1x1
Bus 005 Device 002: ID 0763:1014 Midiman 
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@theorganloft:~# fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/005/003
/proc/bus/usb/005/003: No such file or directory
root@theorganloft:~# fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/005/003
/proc/bus/usb/005/003: No such file or directory
root@theorganloft:~# 


Thanks for any help.

two things to try ... 

(1) it's complaining that the file doesn't exist ... so verify that there really is a file at /etc/firmware/ezusbmidi1x1.ihx and /proc/bus/usb/005/003  ...  check the files are named exactly that. 

(2) if that doesn't fix it, trying call sudo, in case there's a permissions issue.

```

sudo fxload -I /etc/firmware/ezusbmidi1x1 -D /proc/bus/usb/005/003

```

... where the bus and device may change.

Otherwise, I'm not exactly sure why it would not be finding the file.  Are you running gutsy gibbon, or fiesty?  It looks like you have two midi devices showing up ...

---

### Post by theorganloft on 2007-10-22
> **yaaarrrgg said:**
> two things to try ... 

(1) it's complaining that the file doesn't exist ... so verify that there really is a file at /etc/firmware/ezusbmidi1x1.ihx and /proc/bus/usb/005/003  ...  check the files are named exactly that. 

(2) if that doesn't fix it, trying call sudo, in case there's a permissions issue.

```

sudo fxload -I /etc/firmware/ezusbmidi1x1 -D /proc/bus/usb/005/003

```

... where the bus and device may change.

Otherwise, I'm not exactly sure why it would not be finding the file.  Are you running gutsy gibbon, or fiesty?  It looks like you have two midi devices showing up ...

Thanks for the reply.  
I did try the Sudo to no avail.  I also check the existance of /etc/firmware/ezusbmidi 1x1 and it is there. 
The error seems to have a problem seeing /proc/bus/usb/005/003. There is nothing in that folder.  

THe other device you see is an old midiman 49a.  I thought I would try to see if it loaded that firmware. It did not work either. 

Another interesting problem I am having is with a USB connected external Hard Drive.  I cannot read the drive anymore. Something went haywire with the USB in the system.  It sees it but will not display any folders. Is there something that I can clear?

I am now trying to use a SB Live card and it's game port midi.  The system picked right up on the SB Live. The Delta is the primary and the SB is the secondary.  I disabled the MOBO sound card in the BIOS. I  ordered a Midi cable for it. It will be here Wednesday. 

I am using Gutsy.  

Thanks again.:guitar:

---

### Post by yaaarrrgg on 2007-10-22
Hmm... I haven't installed Gutsy yet.  

My first guess is that the usb proc filesystem has changed between releases.  On a quick search, this seems to address the issue:

   [http://forums.virtualbox.org/viewtopic.php?t=2302](http://forums.virtualbox.org/viewtopic.php?t=2302)
   [http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

But I'll need to install gutsy before I can test this ...

---

### Post by theorganloft on 2007-10-23
> **yaaarrrgg said:**
> Hmm... I haven't installed Gutsy yet.  

My first guess is that the usb proc filesystem has changed between releases.  On a quick search, this seems to address the issue:

   [http://forums.virtualbox.org/viewtopic.php?t=2302](http://forums.virtualbox.org/viewtopic.php?t=2302)
   [http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

But I'll need to install gutsy before I can test this ...

Thanks very much for this.  I will get a chance to try it this evening.  I am traveling today.  

I will post my results. 

I really like Ubuntu.  I crashed my windoze machine and have not looked back to fix it for more than a month now.  I see no need to reinstall the machine! Truly amazing!

Thanks again.:)

---

### Post by theorganloft on 2007-10-23
> **yaaarrrgg said:**
> Hmm... I haven't installed Gutsy yet.  

My first guess is that the usb proc filesystem has changed between releases.  On a quick search, this seems to address the issue:

   [http://forums.virtualbox.org/viewtopic.php?t=2302](http://forums.virtualbox.org/viewtopic.php?t=2302)
   [http://www.virtualbox.org/ticket/747](http://www.virtualbox.org/ticket/747)

But I'll need to install gutsy before I can test this ...

THIS WORKED!!!! FOR ALL YOU GUTSY USERS!! THIS WORKED!!

I am so happy!!! U R THE BEST FOR HELPING OUT!!!!

The only problem is that I have to run the fxload every time I boot.  

I can now move on to the next phase and that is getting the apps to talk to my sound modules via MIDI. I wonder if Cubase will run under wine?! Hmmmm.....

WINDOZE I AM BEGINNING TO LOSE SITE OF YOU!

---

### Post by esoxx on 2007-11-11
Hello,

I tried your tuto, but with no success...

the problem is a this line :

fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/003/004

(of course I changed the 1x1 by 2x2 (my midi device) and changed the port and device (port 4 device 3 on my pc)

I get this answer : 

/proc/bus/usb/004/003: No such file or directory

Effectively the /proc/bus/ is empty...

Do you have an idea to help me ?

Thanks

Esoxx

---

### Post by yaaarrrgg on 2007-11-28
If you are using gutsy, you probably have the same problem as in the previous post...  Ubuntu removes usbfs in Gutsy.

Try this:

You need to edit an init script:

```

gksudo gedit /etc/init.d/mountdevsubfs.sh

```

Then look for the following:

```

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```

Remove the #'s from the last four lines so it looks like this :

```

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

```


then Reboot, or run:

```

    sudo /etc/init.d/mountdevsubfs.sh start

```

that should fx it....i think.  More info is at: [http://forums.virtualbox.org/viewtopic.php?t=2302](http://forums.virtualbox.org/viewtopic.php?t=2302)

---

### Post by Sirven on 2007-12-13
Hi,
I tried your instructions. I succeeded to load the MIDI device and to got
lights blinking from the FXload. The thing now is the device not booting on startup after a shutdown of the computer. I also tried your script, but did not worked. I even tried to change the path to the midi file ;
/lib/firmware/maudio/MidiSport1x1.ihx, inside the script,
but no things. Thanks in advance.

---

### Post by Sirven on 2007-12-14
I did not succeed to make the script work on startup. Any other way to make the interface recongnized after booting ?
Thanks

---

### Post by Sirven on 2007-12-14
[I did not succeed to make the script work on startup. Any other way to make the interface recongnized after booting ?
Thanks

---

### Post by yaaarrrgg on 2007-12-14
There's a couple ways to get it to load the firmware on startup.  Here's one way.... this will generally work with any script that you want to execute on boot.

1. The script for loading the firmware in the OP won't automatically run at boot.  Copy this to a file (for example "/your/path/to/the/midiman/script"), give the file "execute" permission, and make sure it actually works on the command line, with a command like:

```

sudo /your/path/to/the/midiman/script

```

2. Now to get the script to automatically fire on boot, add this line to your /etc/rc.local file, which will execute when your computer boots up.  To edit the file, you can use:

```

gksudo gedit /etc/rc.local 

```

3. Now, after the block of comments add the same line that you're executing on the command line.   For example

```

# ...
# By default this script does nothing.

sudo /your/path/to/the/midiman/script


```

4. Now, rebooting should automatically load the firmware into the usb device.

---

### Post by angelsguitar on 2007-12-24
Hi guys. I'm trying to make my Midisport Uno work, been following the instructions on this post.  I downloaded the firmware using synaptics (midisport-firmware package), edited the /etc/init.d/mountdevsubfs.sh file and everything, but can't get it to load.

When I  do 

```
sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D proc/bus/usb/001/003 
```
gives me an error:

```
/proc/bus/usb/001/003: No such file or directory
```

So i discovered that in my system it should be /proc/bus/usb/003/001 (I don't know why)

Anyway, my real problem now is that when i do

```

sudo fxload -I /etc/firmware/ezusbmidi1x1 -D /proc/bus/usb/003/001
```
I get

```

/etc/firmware/ezusbmidi1x1: unable to open for input.
```
Some help, please?:(

---

### Post by angelsguitar on 2007-12-24
> **angelsguitar said:**
> Hi guys. I'm trying to make my Midisport Uno work, been following the instructions on this post.  I downloaded the firmware using synaptics (midisport-firmware package), edited the /etc/init.d/mountdevsubfs.sh file and everything, but can't get it to load.

When I  do 

```
sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D proc/bus/usb/001/003 
```
gives me an error:

```
/proc/bus/usb/001/003: No such file or directory
```

So i discovered that in my system it should be /proc/bus/usb/003/001 (I don't know why)

Anyway, my real problem now is that when i do

```

sudo fxload -I /etc/firmware/ezusbmidi1x1 -D /proc/bus/usb/003/001
```
I get

```

/etc/firmware/ezusbmidi1x1: unable to open for input.
```
Some help, please?:(

Ok, I realized I had a typo in

```

sudo fxload -I /etc/firmware/ezusbmidi1x1 -D /proc/bus/usb/003/001
```

it should read

```

sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/003/001
```

My bad.

But now, when I issue the command above, i get

```
can't modify CPUCS: Broken pipe
```

Now I'm really out of ideas. Help, please?:confused:

---

### Post by angelsguitar on 2007-12-24
Ok, forget about the "Broken Pipe" error. I solved it, and found a way to hot plug my Midisport.  Let me share it with you guys.  I'm using Ubuntu Gutsy; I don't know if it would work on feisty too.
The fact that the firmware does  not load is due to an apparent bug. In summary:
1. Install package midisport-firmware (available in synaptics)
2. Edit /etc/init.d/mountdevsubfs.sh as stated in this post.
3. Open /etc/udev/rules.d/85-midisport-firmware.rules and add the instruction -D $env{DEVNAME} at the end of the rule that applies to your interface.  For example, the rule for the Midisport 1x1 should read something like this:

# MidiSport 1x1
ACTION=="add", SUBSYSTEM=="usb_device", ATTRS{idVendor}=="0763", 
ATTRS{idProduct}=="1001", RUN+="/sbin/fxload -s 
/lib/firmware/maudio/MidiSportLoader.ihx -I 
/lib/firmware/maudio/MidiSport1x1.ihx -D $env{DEVNAME}"

For more details about the bug, take a look at this link:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg424960.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg424960.html")

Now I just plug my interface and everything works! :guitar:

---

### Post by DoctorMO on 2008-02-16
You guys could really do with a udev script to sort this mess out; let me help. I'll be back shortly with something nice.

---

### Post by DoctorMO on 2008-02-16
OK after some digging it looks like someone got there first

```

sudo apt-get install midisport-firmware

```

the problem with it is that it's udev rules are lacking in an important flag: " -D %N" now you can edit the file /etc/udev/rules.d/85-midisport-firmware.rules and add this to the fxload run command line for each one of the rules while I try and submit the patch in launchpad.

Now reboot and enjoy, this worked on gutsy for me; so can the original poster please change their instructions for gutsy?

---

### Post by angelsguitar on 2008-02-16
> **DoctorMO said:**
> OK after some digging it looks like someone got there first

```

sudo apt-get install midisport-firmware

```

the problem with it is that it's udev rules are lacking in an important flag: " -D %N" now you can edit the file /etc/udev/rules.d/85-midisport-firmware.rules and add this to the fxload run command line for each one of the rules while I try and submit the patch in launchpad.

Now reboot and enjoy, this worked on gutsy for me; so can the original poster please change their instructions for gutsy?

Could you post a copy of your corrected 85-midisport-firmware.rules file so I can see your fix? Thanks for the help!!

---

### Post by DoctorMO on 2008-02-21
one rules coming up

---

### Post by msjulie on 2008-03-25
Hello yaaarrrgg,

I wish the initial post had a way to thank you like the newer posts do.

I'm using Gutsy and my Midisport 2x2 is up and running.  Thank you.

Julie

---

### Post by carricre on 2008-04-15
Eep!  I followed these directions, also a gutsy user (heh, funny to type that) the 64bit version, the rules thing didn't need an edit because after I installed the midisport-firmware was already there.  Did the reboot, logged in, started up jackd (as root, cause for some reason it refuses to run as my normal user, and yes I'm in the audio group, infact it's my primary group) and plugged in the midisport....

...nothing, no load.

What I did wrong?

---

### Post by yaaarrrgg on 2008-04-27
> **carricre said:**
> Eep!  I followed these directions, also a gutsy user (heh, funny to type that) the 64bit version, the rules thing didn't need an edit because after I installed the midisport-firmware was already there.  Did the reboot, logged in, started up jackd (as root, cause for some reason it refuses to run as my normal user, and yes I'm in the audio group, infact it's my primary group) and plugged in the midisport....

...nothing, no load.

What I did wrong?

It sounds like you did everything correctly .. for the most part.  Although what do you mean the file was "already there"?  The rules file does exists, but needs to be edited to look like the file in post 41.

I also list some "alternate instructions" which might work better for Gutsy, 64 bit .. sometimes it seems the other approach will work better depending on the system.

---

### Post by capsid on 2008-05-17
I just installed Hardy and I'm having trouble.  

Installed the midisport firmware package from Synaptic, rebooted, no load (as expected).  I saw DoctorMO's post about adding "-D %N" to the end of each fxload command.  I went to /etc/udev/rules.d to make that modification, and found that my midisport config file was numbered differently.
I have **42-midisport-firmware.rules** whereas DoctorMO has **85-midisport-firmware.rules**.  How does that number affect the operation of udev?

So far I've tried:
--relying on the default rules file installed by the package
--adding "-D %N" to each fxload line in 42-midisport-firmware.rules
--adding DoctorMO's rules file to the rules.d directory (in addition to the prexisting one)

...all to no avail.  I guess I will try taking out the default file (saving a backup, of course)  and leaving only DoctorMO's file in there.  I seem to be the only Hardy user posting on this thread, so if there are any others that figured it out, please sound off. 

Thanks for any help you can provide!

---

### Post by yaaarrrgg on 2008-05-17
> **capsid said:**
> I just installed Hardy and I'm having trouble.  

Installed the midisport firmware package from Synaptic, rebooted, no load (as expected).  I saw DoctorMO's post about adding "-D %N" to the end of each fxload command.  I went to /etc/udev/rules.d to make that modification, and found that my midisport config file was numbered differently.
I have **42-midisport-firmware.rules** whereas DoctorMO has **85-midisport-firmware.rules**.  How does that number affect the operation of udev?

So far I've tried:
--relying on the default rules file installed by the package
--adding "-D %N" to each fxload line in 42-midisport-firmware.rules
--adding DoctorMO's rules file to the rules.d directory (in addition to the prexisting one)

...all to no avail.  I guess I will try taking out the default file (saving a backup, of course)  and leaving only DoctorMO's file in there.  I seem to be the only Hardy user posting on this thread, so if there are any others that figured it out, please sound off. 

Thanks for any help you can provide!

I don't think the numbers 85 or 42 in the config filename should affect anything ... that just contols the order in which the config files execute... smaller numbers execute first.  You should be able to delete the old file, and replace it with the new one.  

However, I've tried the udev patch on hardy, and hadn't gotten it to work yet either.  udev in hardy seems to have changed in some respects, although I'm not sure how.

I list some alternate instructions (Section II) that worked for me.  It seems like one or the other approach works better depending on the system.

---

### Post by capsid on 2008-05-17
Thanks a lot for your quick reply.  I really appreciate the shell script.  I was manually calling lsusb and fxload for many months.  Your bash-fu has shown me the way.  

Maybe these devices will gain hotplug support during the next release cycle.  The previous package maintainer cited the problems as stemming from >  "udev/usbfs changes that seem to occur once every 3-6 months, and without obvious notification for a package maintainer like myself."
[https://bugs.launchpad.net/ubuntu/+source/midisport-firmware/+bug/213498]("https://bugs.launchpad.net/ubuntu/+source/midisport-firmware/+bug/213498")

Time to read up on the udev stuff...

Thanks again!

---

### Post by cubdukat on 2008-05-23
I just picked up one of these from Guitar Center yesterday to use with my laptop and Rosegarden. I'm currently running Hardy Heron. Do the same procedure listed for Gutsy users apply to Heron as well?

I would think that if it's class-compliant in Mac OSX (which is technically FreeBSD), it would be class-compliant in Ubuntu.

---

### Post by yaaarrrgg on 2008-05-23
> **cubdukat said:**
> I just picked up one of these from Guitar Center yesterday to use with my laptop and Rosegarden. I'm currently running Hardy Heron. Do the same procedure listed for Gutsy users apply to Heron as well?

I would think that if it's class-compliant in Mac OSX (which is technically FreeBSD), it would be class-compliant in Ubuntu.

I've gotten it to work with the directions in Section II, in Hardy  ...

---

### Post by jukingeo on 2008-10-25
Hello all,

I have a Midisport 4x4 that I am trying to get to work in Ubuntu (Hardy).  I followed the first page instructions for Hardy (section II), and I do have slowly flashing lights on my Midisport.  In lights 3 & 4, Out lights 1,2 & 4, and the USB light all slowly flash in unison.

Since I have Ubuntu Studio, I have Jack.  In jack my Midisport is recognized only as a single input and single output midi interface.  So something went wrong with the setup and I would like so assistance in getting my 4x4 to work properly...4 ins and 4 outs.

I have not tested it with midi as of yet.  I have a funny feeling it isn't going to work.

I do have to say that the unit will operate properly (4 in 4 out) if I boot into Windows XP first, then close out of that and reboot into Ubuntu.

Also another thing is that if I shut the computer down and then turn it back on again (into Ubuntu w/o going into Windows first), the Midisport 4x4 doesn't turn on again.  I have to go into the terminal and invoke the last command in the procedure posted above to get it to work again:

sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/004/002 (these last two numbers are where my device is located via finding it using lsusb).

This is obviously unacceptable to me and I would like the unit to be recognized upon plug in.

EDIT:

I have some more information to add after running some more tests: 

When I do a lsusb prior to invoking the above command I can clearly see the identified usb port (usually 004/002) and it says this in the terminal:

geo@home:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0763:1020 Midiman Midisport 4x4
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

Now this is what happens AFTER I invoke the command:

geo@home:~$ sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/004/002
[sudo] password for geo: 
geo@home:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0763:1110 Midiman 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
geo@home:~$ 

Notice the device changes to 003 from 002 and the ID also changes.  The designation on the end just says "Midiman"

It seems like this procedure was geared more for a 1x1 interface.  For some reason it is turning my Midisport 4x4 on, but it isn't acknowledging the proper type of unit.  I am hoping there is a fix for this.

2nd Edit:

Hello again...OK, I am making progress now. As it turned out I was referencing the wrong file location.  That should have been something that should have been pointed out in the tutoirial for anyone not having a 1x1 interfaces.

Ok, as it turned out the correct line I should have used was this:

fxload -I /usr/share/usb/maudio/MidiSport4x4.ihx -D /proc/bus/usb/004/003

This is my terminal output:

geo@home:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 0763:1020 Midiman Midisport 4x4
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
geo@home:~$ fxload -I /usr/share/usb/maudio/MidiSport4x4.ihx -D /proc/bus/usb/004/003
/proc/bus/usb/004/003: Permission denied
geo@home:~$ sudo fxload -I /usr/share/usb/maudio/MidiSport4x4.ihx -D /proc/bus/usb/004/003
[sudo] password for geo: 
geo@home:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 0763:1021 Midiman 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
geo@home:~$ 

(it for some reason relabels everything just as before).

There is a USB folder in the /usr/share folder and all the midisport.ihx files where there.  This obviously must be the master location for all the midisport firmware files.

Anyway, I invoked the above command and presto! Now I only have the USB light flashing and when I go into Jack it sees the full 4in/4out.

So now that I did get it to work, the final thing I need to know is how to set it up so that it is automatically detected upon start up.

Any assistance would be much appreciated.

Thank You,

Geo

---

### Post by yaaarrrgg on 2008-10-25
Hi geo, there's a couple options depending on how much time you want to invest setting it up.

To run scripts when you plug in a device, you basically need to set up a udev rule.  An excellent tutorial is at:

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

Note the device you are setting up is the one *before* you run the script to load the firmware.  I don't have a midi4x4 so would not be able to tell you exactly all the steps or test this on my end.

Also, I read a while back that the next release of Ubuntu is supposed to include native support for these midi devices.  If that is the case, it might be easiest to just create a desktop launcher in the time being that runs the command line tool.

thanks,
Kevin

---

### Post by jukingeo on 2008-10-27
> **yaaarrrgg said:**
> Hi geo, there's a couple options depending on how much time you want to invest setting it up.

To run scripts when you plug in a device, you basically need to set up a udev rule.  An excellent tutorial is at:

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

I took a quick peek at it.  But, there is quite alot there and I couldn't follow through on some of it.  I am quite new to Linux as I only been on it for about 5 months now.  I have to read through it in more detail when I get home from work.

> Note the device you are setting up is the one *before* you run the script to load the firmware.  I don't have a midi4x4 so would not be able to tell you exactly all the steps or test this on my end.

Also, I read a while back that the next release of Ubuntu is supposed to include native support for these midi devices.  If that is the case, it might be easiest to just create a desktop launcher in the time being that runs the command line tool.

That is what I did for now.  With the firmware loaded on my system there is just one command line needed to start up the device.  However, the command line points to an EXACT address and it doesn't work every time.  I have to open up the terminal and type in "lsusb" to locate on what port and buss the device is on. Then I have to edit the launcher to reflect this port...save the changes and then click on the launcher and enter in my sudo password. Then I am in business. However, I find this all to be a pain in the butt.

What I would like is for the unit to be recognized each and every time I plug it in or boot into Ubuntu.  However, I will say that this device isn't something I will be using every day, unlike my keyboard (which is automatically recognized).  

If that is too much to do (or ask) then I, at least, would like a desktop icon that works EVERY time I click on it AND without having to type in my sudo password.  If I can have at least that then I should be good.

Is there a simple script for that?  In that post I mentioned above it looks like the script is supposed to do that, but it doesn't seem to work.

Thanx,
Geo

---

### Post by yaaarrrgg on 2008-10-27
Based on your location of your firmware, I made a quick change to the script in the first post (changed the 'fw' variable).  This should work for you, although I don't have your device to test.  Basically it's just finding the buss and proc numbers with shell tools:

```

#!/bin/bash

#your firmware ... taken from usbmidi
fw=/usr/share/usb/maudio/MidiSport4x4.ihx

#get proc address
bd=$( lsusb | grep Midisport | cut -d ' ' -f 2,4 | sed -e 's/ /\//' -e 's/://' )

dev=/proc/bus/usb/$bd

#load firmware
echo fxload -I $fw -D $dev
fxload -I $fw -D $dev

```

Also, for the sudo password... there are a couple ways around this, although it might be a little tricky if you are new to linux.  In theory it's simple though ... you just add an exception to sudo's config files so that it won't prompt for a password.  

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

thanks,
Kevin

---

### Post by jukingeo on 2008-10-28
> **yaaarrrgg said:**
> Based on your location of your firmware, I made a quick change to the script in the first post (changed the 'fw' variable).  This should work for you, although I don't have your device to test.  Basically it's just finding the buss and proc numbers with shell tools:

```

#!/bin/bash

#your firmware ... taken from usbmidi
fw=/usr/share/usb/maudio/MidiSport4x4.ihx

#get proc address
bd=$( lsusb | grep Midisport | cut -d ' ' -f 2,4 | sed -e 's/ /\//' -e 's/://' )

dev=/proc/bus/usb/$bd

#load firmware
echo fxload -I $fw -D $dev
fxload -I $fw -D $dev

```

Also, for the sudo password... there are a couple ways around this, although it might be a little tricky if you are new to linux.  In theory it's simple though ... you just add an exception to sudo's config files so that it won't prompt for a password.  

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

thanks,
Kevin

Hello Kevin, 

Ok, this is working much better. I created the above file as "midisport4x4start" within gedit and I placed it within the /usr/local/bin directory.

Then I did a sudo nautilus in the terminal and edited the permissions for the midisport4x4start file to allow access within "geo" and not just the root.  I set it as executable.

I then changed the line in my launcher button to

sudo /usr/local/bin/midisport4x4start

Thus now when I hit the launcher icon it activates the Midisport 4x4 EVERY time.  Good! Good!  That is getting one step closer to where I want to be.  However, I STILL have to enter the password for sudo.

I tried to follow through on that web page you sent me on soduer's, but I can't make sense of it.

All I really want to do is set up the launcher button so it doesn't need the sudo password.

Is there a simpler approach?

Thanx for your help thusfar.

EDIT:

Hello Kevin,

Ok, I have some good news.  Two problems I had before were:

1) The problem with the script and the directories that you found.
2) The problem with the file permissions that I found.

So with both problems out of the way, I went back to the beginning of this post and completed the procedure for startup/boot and guess what?  IT WORKED!!  It booted right up upon start up and the best part is...NO SUDO NEEDED!

Granted, if I unplug the unit and then plug it back in, it isn't automatically recognized, I still have to hit the launcher button I made.  However, that will be a rare occurrence.  It would be nice that it would work as soon as I plug the unit in, but with bootup on start and no Sudo needed, I am not complaining and I am good for now.  So I am going to stop here and move on to other things.

Thanx again for your help.

Geo

---

### Post by turfrijer on 2008-11-13
hello everybody,

does the configuration changed for Ubuntu 8.10 ?
I can't get it to work....

Please help ! :confused:
David

---

### Post by yaaarrrgg on 2008-11-13
> **turfrijer said:**
> hello everybody,

does the configuration changed for Ubuntu 8.10 ?
I can't get it to work....

Please help ! :confused:
David

It's very possible it has changed.  I'll need to upgrade to 8.10 to test...

---

### Post by jukingeo on 2008-11-13
> **yaaarrrgg said:**
> It's very possibly it has changed.  I'll need to upgrade to 8.10 to test...

Hmmm, I am not upgrading yet.  I am going to wait for a while to make sure that Intrepid is not going to be like how Hardy was when it first came out...especially since now I pretty much got rid of most of the problems I had with Hardy!

EDIT:

One fellow is reporting problems with his M-Audio 1010lt under 8.10 in another thread I post to.  So far I am taking this as NOT a good sign!

Geo

---

### Post by yaaarrrgg on 2008-11-18
> **turfrijer said:**
> hello everybody,

does the configuration changed for Ubuntu 8.10 ?
I can't get it to work....

Please help ! :confused:
David

Sorry for the delay ... I had to upgrade my system.  The good news is that it's a fairly simple fix.

Ubuntu does not have usbfs turned on by default in Intrepid Ibex.  To fix this, you need to add a line at the end of your /etc/fstab file.

To edit the fstab file run this:

```

gksudo gedit /etc/fstab

```

Then add this new line at the bottom of the file, on it's own line.  NOTE: Be careful not to change anything else in this file:

```

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

Then reboot.

Then the rest of the instructions in Section II should work. This has been updated.

thanks,
Kevin

---

### Post by Ubuntolonius on 2008-11-18
To get the method in Section I to work under Ubuntu 8.10, I changed the udev rule for my MidiSport 1x1 adaptor in the file 42-midisport-firmware.rules.
I commented the line 

ACTION=="add", SUBSYSTEM=="usb", DEVPATH=="/*.0", ENV{PRODUCT}=="763/1010/*", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport1x1.ihx"

and replaced it with

ACTION=="add", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1010", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport1x1.ihx -D %N"

Then I reapplied the udev rules by typing
sudo udevadm control --reload_rules

Afterwards the automatic firmware download to the hotplugged midisport adaptor worked perfectly well.

I would hope, that this could be the generic way, to get the package midisport-firmware to work on Ubuntu Ibex

---

### Post by yaaarrrgg on 2008-11-21
Thanks to everyone for the comments and suggestions. 

I'm putting the alternate instructions in a separate post to clean up the tutorial.


**Setting up Ubuntu 8.10 Intrepid Ibex (special instructions)**

Ubuntu does not have usbfs turned on by default in Intrepid Ibex.  To fix this, you need to add a line at the end of your /etc/fstab file.

To edit the fstab file run this:

```

gksudo gedit /etc/fstab

```

Then add this new line at the bottom of the file, on it's own line.  NOTE: Be careful not to change anything else in this file:

```

none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

Save, then reboot.

-----

**Setting up Ubuntu 8.04 Hardy Heron OR Ubuntu 7.10 Gutsy Gibbon (special instructions)**

Ubuntu does not have usbfs turned on by default in Gutsy.  To fix this, you need to edit an init script:

```

gksudo gedit /etc/init.d/mountdevsubfs.sh

```

Then look for the following:

```

    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb

```

Remove the #'s from the last four lines so it looks like this :

```

    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

```

then Reboot, or run:

```

    sudo /etc/init.d/mountdevsubfs.sh start

```

that should fx it.  
More info is at: [http://forums.virtualbox.org/viewtopic.php?t=2302](http://forums.virtualbox.org/viewtopic.php?t=2302)

-----

**Getting the Midisport Firmware.  **

I used an opensource version of the firmware. for convenience, you can work in the tmp directory

```

cd /tmp

# then get firmware from the 'usbmidi' package
wget http://homepage3.nifty.com/StudioBreeze/software/bin/usbmidi-20040829.tar.gz

# unpack
tar xvzf usbmidi-20040829.tar.gz

# to simplify the instructions copy the firmware to /etc/firmware
sudo mkdir /etc/firmware
sudo cp usbmidi-20040829/testing/MidiSport/ezusbmidi1x1.ihx /etc/firmware/

```

----

**Getting the Software to Load the Firmware: **

1. you can use a package called 'fxload'

I just use apt-get (as root)

```

	sudo apt-get install fxload

```

----

**Loading the Firmware**

To get a list of all the usb devices, you can type:

```

	lsusb

```

One line should mention "Midisport", for example:

```

	Bus 003 Device 004: ID 0763:1010 Midiman Midisport 1x1

```

This lists the bus and device number that the device is assigned to.
Also, this device will be mapped to a place like:

```

	/proc/bus/usb/003/004 

```

where 003 is the bus number, and 004 is the device number (these numbers can change if you unplug the usb cable and plug it back in).  To load the firmware, use a command like (you shouldn't need sudo):

```

	fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/003/004

```

the swtch '-I' is the firmware file, and '-D' is the device.  If you see a pulsating light on the Midisport, or fast flickering lights, then you are in business!!!

-----

**Hotplug and Init Scripts**

If you are ambitious, you can set up the script to execute automatically when you plug in the usb cable (see udev, or post [#37]("http://ubuntuforums.org/showpost.php?p=4007105&postcount=37")).  I never really reboot the computer or unplug the cable, so I haven't had much need for anything this fancy.  For a simpler solution, you can simply have the script fire when the computer boots.
  
I wrote a short script that loads the firmware.  You can copy and paste this into gedit, vi, or your favorite editor.  For organization, you can save this script as /usr/local/bin/midisportsetup ... although location does not matter:


--start script--

```

#!/bin/bash

#your firmware ... taken from usbmidi
fw=/etc/firmware/ezusbmidi1x1.ihx

#get proc address
bd=$( lsusb | grep Midisport | cut -d ' ' -f 2,4 | sed -e 's/ /\//' -e 's/://' )

dev=/proc/bus/usb/$bd

#load firmware
echo fxload -I $fw -D $dev
fxload -I $fw -D $dev

```

--end script--


of course, make sure the script has execute permissions. also change user/group if needed.

```

sudo chmod 775 /usr/local/bin/midisportsetup

```

this script will need to be executed as root. to run the script, use (you shouldn't need sudo):

```

/usr/local/bin/midisportsetup

```

----
**Setting up the script to run on startup/boot **

There's a couple ways to get it to load the firmware on startup.  Here's one way.... this will generally work with any script that you want to execute on boot.

1. The script for loading the firmware in the OP won't automatically run at boot.  Copy this to a file (for example "/usr/local/bin/midisportsetup"), give the file "execute" permission, and make sure it actually works on the command line, with a command like:

```

sudo /usr/local/bin/midisportsetup

```

2. Now to get the script to automatically fire on boot, add this line to your /etc/rc.local file, which will execute when your computer boots up.  To edit the file, you can use:

```

gksudo gedit /etc/rc.local 

```

3. Now, after the block of comments add the same line that you're executing on the command line.   For example

```

# ...
# By default this script does nothing.

sudo /usr/local/bin/midisportsetup


```

4. Now, rebooting should automatically load the firmware into the usb device.

5. to undo do this, simply edit the file and remove the line you added.
----

**Other Hardware**

Midisport 1x1 should work with these directions as well, but I have not tested it.  Midisport 2x2 and USB-2-Midi should be similar, but require a different firmware file: ezusbmidi2x2.ihx.  

more info at:

[http://ccrma.stanford.edu/planetccrma/software/usbmidi.html](http://ccrma.stanford.edu/planetccrma/software/usbmidi.html)
[http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html](http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html)

---

### Post by raboofje on 2008-11-22
> **corevette said:**
> the USB light to my Midisport 1x1 constantly dims on and off.

This is normal - it's supposed to do that.

I recently got a 'm-audio midisport 2x2 anniversary edition', and it worked right out of the box without installing this firmware.

Does the firmware in this package provide any benefits over the factory defaults?

---

### Post by jukingeo on 2008-11-22
> **raboofje said:**
> This is normal - it's supposed to do that.

I recently got a 'm-audio midisport 2x2 anniversary edition', and it worked right out of the box without installing this firmware.

Does the firmware in this package provide any benefits over the factory defaults?

Yeah, the light does that in Windows as well.

I own two older versions of the M-Audio Midisport.  They are the yellow and blue enclosures and still have the old Midiman logo on them.  One is a 2x2 and the other is a 4x4.   Both were from about the same mfg.  But here is the kicker.  The 2x2 is automagically recognized in all my Linux distributions.  The 4x4 isn't.  In fact I can't get the 4x4 to work in two of my three Linux Distributions.  It is currently only working in Ubuntu.

---

### Post by David_D on 2008-12-16
Hi everybody!
Though I am no Ubuntu user, I would like to ask you if you could help me loading the firmware for the "M-Audio Midisport UNO" device. 
My distribution, Arch Linux, is running on the realtime kernel (2.6rt) and uses the udev device manager. When I try to compile such firmware packages like from [http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/) it crashes, because the old configuration files are not compatible with my udev version (130-1). Hence, I plan to **fxload the firmware manually** (and put the commands into a startup script later). I obtained the firmware files (*.ihx files) from several sources:

1. The Open Source firmware from this method:
> **yaaarrrgg said:**
> 


**Getting the Midisport Firmware.  **

I used an opensource version of the firmware. for convenience, you can work in the tmp directory

```

cd /tmp

# then get firmware from the 'usbmidi' package
wget http://homepage3.nifty.com/StudioBreeze/software/bin/usbmidi-20040829.tar.gz

# unpack
tar xvzf usbmidi-20040829.tar.gz

# to simplify the instructions copy the firmware to /etc/firmware
sudo mkdir /etc/firmware
sudo cp usbmidi-20040829/testing/MidiSport/ezusbmidi1x1.ihx /etc/firmware/

```



2. By extracting the original windows driver with the firmware loader version 0.5 (from sourceforge). 
This website describes how to do it: [http://demudi.agnula.info/wiki/DocumentsTipsMAudio](http://demudi.agnula.info/wiki/DocumentsTipsMAudio)

Unfortunately, neither the first nor the second file can be transfered by using fxload:

"lsusb" says:
```

Bus 004 Device 001: ID 1d6b:0002  
Bus 003 Device 003: ID 0763:0150 Midiman (<-- this is the M-Audio Midisport UNO)
Bus 003 Device 001: ID 1d6b:0001  
Bus 002 Device 004: ID 0db0:6982 Micro Star International Medion Flash XL V2.7A Card Reader
Bus 002 Device 005: ID 0763:2013 Midiman (<-- this is another M-Audio Device "JamLab")
Bus 002 Device 001: ID 1d6b:0001  
Bus 001 Device 001: ID 1d6b:0001 

```


Thus the fxload command should be:

"fxload -I /etc/firmware/MidiSport1x1.ihx -D /dev/bus/usb/003/003"
or
"fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /dev/bus/usb/003/003"

And here is the actual problem. After running this command, the terminal says:

**"can't modify CPUCS: Broken pipe"**

What should I do now? I don't believe it is the wrong firmware file, since many people in the internet say they used the same as for the Midisport 1x1 (which is basically almost the same as the Midisport UNO). Please help me :(

P.S.: 
The USB light of the device flashes all the time. Could it be that it does not need any firmware install? I already tried to do some actions, but only a few things work: 
- "amidi -l" lists the midi interface correctly
- "aconnect -i" and "aconnect -o" list the midi interface (as an input/output client)
- my computer can **receive sysex** dumps with "amidi -p hw:4,0,0 -r myfile.syx"

But when I try to **send sysex** files from the computer to my midi device, or when I want to **receive MIDI notes or program changes**, nothing works!

---

### Post by yaaarrrgg on 2008-12-17
> **David_D said:**
> P.S.: 
The USB light of the device flashes all the time. Could it be that it does not need any firmware install? I already tried to do some actions, but only a few things work: 
- "amidi -l" lists the midi interface correctly
- "aconnect -i" and "aconnect -o" list the midi interface (as an input/output client)
- my computer can **receive sysex** dumps with "amidi -p hw:4,0,0 -r myfile.syx"

But when I try to **send sysex** files from the computer to my midi device, or when I want to **receive MIDI notes or program changes**, nothing works!

If the light is flashing, it probably already has all the firmware it needs.  I would try to read/write to it in rosegarden (or some sequencer), and see if it works out-of-the-box.

thanks,
Kevin

---

### Post by David_D on 2008-12-22
Thanks for your advice Kevin!
I installed Rosegarden and set the USB UNO as the midi recording device, but I could not record anything :(.

Then I tried to receive midi with the alsa command "aseqdump". Though it does not behave properly, *"something"* happens:

$ aconnect -i
```

client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 16: 'Ensoniq AudioPCI' [type=kernel]
    0 'ES1371          '
client 20: 'MPU-401 UART' [type=kernel]
    0 'MPU-401 UART MIDI'
client 32: 'USB Uno MIDI Interface' [type=kernel]
    0 'USB Uno MIDI Interface MIDI 1'

```
$ aseqdump -p 32
```

Waiting for data. Press Ctrl+C to end.
Source  Event                  Ch  Data

```

When I press on any key of my midi device, this happens:
```

 32:0   Note off                0, note 16, velocity 16

```

After pressing a key, **the process freezes**. I cannot cancel it, neither with Ctrl+C nor with kill -9 *UID*! 
The only way to stop the process and gain access to the device again is to reboot!

I assume it is the firmware that is gone haywire!? Or what do you think?

Thanks, 
David!

Edit:
Could it be that udev or some other program loads the wrong firmware automatically when I start my system? I cannot imagine another reason why I cannot load the firmware manually.

---

### Post by yaaarrrgg on 2009-01-02
If it's locking up the entire machine, it sounds like a kernel driver issue.  Firmware itself shouldn't cause that much havoc.

I suppose hardware issues are ruled out if it worked under windows.

I wonder does this fail under both Ubuntu and Arch?  That would at least determine if the problem is specific to the firmware or some kernel driver.

---

### Post by David_D on 2009-01-19
Sorry, you misunderstood me. It is not the whole system that freezes. It is the process that tried to communicate with the USB device. I cannot force it to stop, thus the connection between the PC and the device is kind of "blocked" until I reboot the system.

I'll try if it works under Windows...

edit: 
OK I found out that it **DOES NOT** work under windows! Damn I spent so much time hunting the reason in my operation system, but in the end it was the device! x_x

And guess what I found out after browsing on the M-AUDIO forum..
[http://forums.m-audio.com/announcement.php?f=10](http://forums.m-audio.com/announcement.php?f=10)
It is a **manufacturing defect**! And guess what, the Serial Number of my device is EXACTLY in the range of the defect products! I should exchange that stupid interface

---

### Post by StudioDave on 2009-02-06
Some extra notes for installing a MidiSport2x2 on Ubuntu 8.10:

I retrieved the midisport-firmware and fxload packages with Synaptic.

I modified y's midisportsetup file to correct "Midisport" to "MidiSport", because lsusb lists it that way.

The path to the firmware is /usr/share/usb/maudio/MidiSport2x2.ihx.

The entry in /etc/rc.local apparently must include the sudo and the full path. Simply indicating the binary didn't work. I haven't fully tested this, but I only got activation at start-up after correcting the entry.

Now the MidiSport starts at boot up and I'm a happier guy. :)

---

### Post by osterchrisi on 2009-02-23
Hey there.
I have a problem with my MidiSport 4x4, the LED just won't go on...
I installed the M-Audio firmware (it put itself into /usr/local/share/usb/maudio) and edited my udev-rules to fit to the installation.
Here's my udev rule file:
```

# midisport-firmware.rules - udev rules for loading firmware into MidiSport devices

# MidiSport 1x1
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1010", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport1x1.ihx -D %N"

# MidiSport 2x2
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1001", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport2x2.ihx -D %N"

# KeyStation
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1014", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSportKS.ihx -D %N"

# MidiSport 4x4
ACTION=="add", KERNEL=="4-2", SUBSYSTEM=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1020", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport4x4.ihx -D %N"

# MidiSport 8x8
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1031", ATTRS{bcdDevice}=="0110", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport8x8-2.10.ihx -D %N"
ACTION=="add", SUBSYSTEM=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1031", ATTRS{bcdDevice}=="0121", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport8x8-2.21.ihx -D %N"

# vim: ft=conf

```

When I re-plug in the device the syslog says the following:
```
Feb 23 20:28:43 station kernel: [ 6567.994545] usb 4-2: USB disconnect, address 2
Feb 23 20:28:50 station kernel: [ 6575.400024] usb 4-2: new full speed USB device using ohci_hcd and address 3
Feb 23 20:28:51 station kernel: [ 6575.619539] usb 4-2: configuration #1 chosen from 1 choice

```

Looks not to bad does it? But still I can't operate with the interface. What is going wrong?

---

### Post by Phil Urich on 2009-02-24
I've jumped back into this recently once I found out how hard it'd be to track down a DIN-to-Mini-din adapter for the Creative Audigy that I salvaged recently, which reminded me I had this fancy Midisport 2x2 Anniversary Edition that I had never gotten working.

Unlike raboofje above, mine does NOT seem to work off the bat, though I fear a bit that perhaps my earlier tinkering may have brought this about (the fears slightly allayed by my other, secondary computers having a similarly hard time).  Basically, other than finding it in lsusb, there seems to be no notice of it being plugged in, even if I try using fxload to push firmware at it (which, again, shouldn't need to be done).

Tailing /var/log/messages, apparently this is going on in the background:

```
Feb 24 02:56:16 foundation kernel: [1979967.732018] usb 1-6: new full speed USB device using ohci_hcd and address 40
Feb 24 02:56:18 foundation kernel: [1979969.450392] usb 1-6: new full speed USB device using ohci_hcd and address 41
Feb 24 02:56:19 foundation kernel: [1979970.838522] usb 1-6: configuration #1 chosen from 1 choice
Feb 24 02:56:19 foundation kernel: [1979970.845061] snd-usb-audio: probe of 1-6:1.0 failed with error -5
Feb 24 02:56:19 foundation kernel: [1979970.846836] snd-usb-audio: probe of 1-6:1.1 failed with error -5

```

I'm hoping one of you forum geniuses can spot a fixable problem!

I have a Windows install buried on a small hard-drive on a spare backup computer, heh, but instead of digging that out I checked using a friend's laptop (WinXP SP3) and Absynth played with my crappy test midi keyboard.  I had to install the optional drivers for XP to get it working, but hey, it's Windows so who knows what that means (and it could have been just me not knowing how things work there anymore).  It definitely worked then, though, so the hardware isn't defective.

---

### Post by jukingeo on 2009-02-24
Hello Phil,

I responded to your PM just a few mins ago.  At any rate, here is the thread that I created when I had a problem with getting the Midisport 4x4 to work.  (I sent this link to you as well, but I am reposting here for others to see).

[http://ubuntuforums.org/showthread.php?t=955097](http://ubuntuforums.org/showthread.php?t=955097)

Now keep in mind, this solution was derived using Ubuntu version 8.04...not 8.10.  That DOES make a big deal because I have been hearing across the board that many people that had their USB devices working under 8.04, now no longer have them working.  I have quite a few USB devices, so I chose to stick with version 8.04 for now.

Hope that info helps.

Geo

---

### Post by yaaarrrgg on 2009-02-24
@osterchrisi 

One thing to rule out is a hardware issue.  Test the device under windows.  If it's fine, it almost sounds like a udev problem to me.  I would think the conf file is not catching the event, and actually executing any command.

I noticed your rule for the 4x4 was:

```

# MidiSport 4x4
ACTION=="add", KERNEL=="4-2", SUBSYSTEM=="usb", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1020", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport4x4.ihx -D %N"

```

This might need to be:

```

# MidiSport 4x4
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1020", RUN+="/sbin/fxload -s /usr/local/share/usb/maudio/MidiSportLoader.ihx -I /usr/local/share/usb/maudio/MidiSport4x4.ihx -D %N"

```

also verify that both files exist and permissions are ok:

/usr/local/share/usb/maudio/MidiSportLoader.ihx
/usr/local/share/usb/maudio/MidiSport4x4.ihx

Also, this is slightly different than conf file I used:

```

# MidiSport 4x4
ACTION=="add", SUBSYSTEM=="usb*", ATTRS{idVendor}=="0763", ATTRS{idProduct}=="1020", RUN+="/sbin/fxload -s /usr/share/usb/maudio/MidiSportLoader.ihx -I /usr/share/usb/maudio/MidiSport4x4.ihx -D %N"

```

You might try the setup in section II.  This would by-pass the udev (hotplug) rules altogether; you could manually try loading the firmware on the command line.

---

### Post by osterchrisi on 2009-02-28
Ok, thanks. The other day it just worked out, seems like my linux needed some time to take the changes :D
Yet another question: Is it really necessary to write a udev-rules-file for all usb-inputs? For example, with my "42-midisport-..." file the firmware only loads when I plug the MidiSport device into that port. As soon as I try another one, it doesn't - as long as I don't write another udev-rule-file (like "33-midisport-...") for that usb-input as well...

Is there a shortcut to this?

---

### Post by theluddite on 2009-06-21
> **yaaarrrgg said:**
> 

also verify that both files exist and permissions are ok:

/usr/local/share/usb/maudio/MidiSportLoader.ihx
/usr/local/share/usb/maudio/MidiSport4x4.ihx


I've had no success with my midisport2x2.  I've got the lights flashing but I can't get a signal from the midi controller no matter what I use:  aseqdump, kmidimon, qsynth, zynaddsubfx or seq24.  I did discover that there's nothing in the path to MidiSportLoader.ihx.  In fact, it's not even on my system.  Is this my problem?  How do I fix it?

---

### Post by yaaarrrgg on 2009-06-22
If the lights are flashing, that means that the firmware is loaded.  The device should be good to go then.  

It sounds like the system just isn't referencing that device.

The only midi software I've used is Rosegarden.  To use the correct device, I have to select the Midisport devices under (IIRC):

Studio -> Manage Midi Devices

If that doesn't work, I'd be inclined to think there could either be a hardware issue with the device, or sound on the computer.  

I'd also double check the setup (if possible) on Windows.  It's possible there's an additional setting on the keyboard (?) that needs to be set, or wiring could need to change.  That could at least rule out the issue having anything to due with your system.

---

### Post by theluddite on 2009-06-22
> **yaaarrrgg said:**
> If the lights are flashing, that means that the firmware is loaded.  The device should be good to go then.  

It sounds like the system just isn't referencing that device.

The only midi software I've used is Rosegarden.  To use the correct device, I have to select the Midisport devices under (IIRC):

Studio -> Manage Midi Devices

If that doesn't work, I'd be inclined to think there could either be a hardware issue with the device, or sound on the computer.  

I'd also double check the setup (if possible) on Windows.  It's possible there's an additional setting on the keyboard (?) that needs to be set, or wiring could need to change.  That could at least rule out the issue having anything to due with your system.

Thanks for the reply!  I'm not familiar with Rosegarden, maybe I'll give it a try but I'd like to use my controller to trigger softsynths such as Alsa Modular Synth, Fluid Synth and Zynaddsubfx, then record them using Ardour (which I'm more familiar with).  

I know it's not a sound problem since I trigger the softsynths with virtual keyboard and I know it's not a device issue since I can trigger windows softsynths with it using my midisport.  Even more frustrating is that I read somewhere else on the forums that someone else has had success using the very same device (a microKorg) as a midi trigger -- although they didn't specify which midi interface they used.  

I guess the only other issue could be jack, although I've tried every combination of connections with it.  Suspiciously, jack would hang if I connected and disconnected the midi connections under the alsa tab.  Are there any key settings I need to tweak in jack to use my midisport?

---

### Post by yaaarrrgg on 2009-06-23
I hadn't used these synths before, but they look nice.  I tested out Qsynth and got it to work with the midisport, after some trial and error.

This thread was helpful:
[http://ubuntuforums.org/showthread.php?t=1068913](http://ubuntuforums.org/showthread.php?t=1068913)

Basically the steps I did were:

1. SET UP JACK

open up the jack control panel.
goto 'setup'
At the bottom (left) is a 'Midi' option.  I selected 'seq'
click 'ok'  
start up jack

2. SYNTH SOUNDS

then download some sound fonts:
[http://www.hammersound.net/hs_soundfonts.html#Melodic_instruments](http://www.hammersound.net/hs_soundfonts.html#Melodic_instruments)
unzip to some folder

3. SET UP QSYNTH 

start up qsynth
goto 'setup'
For the Midi Driver, select 'alsa_seq' 
Click the 'Soundfonts' tab
Click 'open' and select the unzipped soundfont
click 'ok'
Click 'yes' you want to restart jack

4. ROUTING MIDI CONTROLLER TO SYNTH

Now, back in jack control panel, click the 'Connect' button.
Click the 'Alsa' tab
Click the 'Midisport' option from the list of readable devices
Click the 'FluidSynth' option from the list of writeable devices
Click 'Connect'

That should do it.  I would assume you were just missing the last step, that actually connects the midi controller to the synth. 

Thank you for sharing the info about the synths... I will have to play around with these more.  I was kind of getting tired of my (physical) keyboard's sounds. :)

I have ZynAddSubFX and ALSA Modular Synth working as well.  ZynAddSubFX was similar to QSynth ... works by just connecting the Midisport output to the ZynAddSubFX input port.  ALSA Modular Synth confused me for a bit, but then I loaded a demo, and connected both  the midi inputs and (under the Audio tab) connected the output of ams_130_0 to the system input.

My next experiment will be routing qsynth outputs to Ardour.

thanks,
Kevin

---

### Post by theluddite on 2009-06-23
Thanks for the detailed reply.  Maybe I didn't configure Qsynth properly.  Although I'm fairly certain I set Jack to use the seq driver, I don't know that I did the same with Fluidsynth.  I definitely used Jack to create the connections -- so I know that wasn't the problem.  I'll try it tonight and let you know you if it works.

---

### Post by theluddite on 2009-06-23
I determined my problem.  It wasn't the midisport at all.  It's the kernel.  I normally boot into my real time kernel (2.6.27-3-rt), but I thought I'd boot into my default (2.6.27-14-generic) just for sh*ts and giggles.  Voila!  My midisport, microKorg and Qsynth worked perfectly together.  I did some checking online and it seems the Intrepid realtime kernel has a number of issues which is why it wasn't included by default in Ubuntu Studio.  But booting into my generic kernel isn't really a solution for me since I had over 70 xruns in about 5 minutes uptime.  I can't update to Jaunty either since I had some **massive** kernel problems with it that caused my system to hang indefinitely after about 20 minutes uptime.

*Sighs*  I'll be really anticipating the Karmic Ubuntu Studio release -- which had better have a functional real time kernel -- so I can finally get midi running.

---

### Post by jhb1608 on 2009-10-24
That's strange. I have the same ID number, BUT it is a usb phone.

ID 6993:b001 Freshtel FT-102 VoIP USB Phone

it's USRobotics USB Internet phone Model USR9601.

I want it to use as a microphone. Any idea how?

---

### Post by yaaarrrgg on 2009-10-25
I don't have that device so it's hard to say.  If it shows up as a generic audio device, I would think you should be able to route the output connections (in the QT Jack Control) to your program's input channels.

Also, if you are running into a driver issue, you might want to start a new thread... not as many people will see your question in this one.

---

### Post by ionnoizer on 2013-05-05
Thanks a lot, from KUBUNTU 12 LTS. 

Midi Sport 2X2 in working perfectly I did by packet management, search and install.

;-)

---

