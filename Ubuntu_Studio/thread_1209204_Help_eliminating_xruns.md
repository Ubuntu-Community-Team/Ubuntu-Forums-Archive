---
title: "Help eliminating xruns"
date: 2009-07-10
forum: Ubuntu Studio
---

### Post by notesetter on 2009-07-10
Hello,

I'm requesting help getting my machine ready to do recording under Ubuntu Studio so that I can learn how to use JACK, Ardour and some of the other applications. I've been using Ubuntu Studio for about 18 mo. now and am finally ready to get around to some recording. But when I start the JACK server, I invariably get my first xrun within 3 minutes, sometimes less.

I've gone through the steps of enabling RT kernel mode by creating the group "audio" and making myself part of the group, and editing the memlock and other settings. Here are some of my other system settings and specifications:

Compaq Presario 2170US (Laptop)
Intel Celeron 1.99 Ghz
1 GB RAM (maxed out)
Ubuntu Studio 8.04 w/ GNOME

I've fooled around with the settings in JACK (increased buffer size, frames, etc.) and I still get xruns after a few minutes. I'm willing to switch to xfce if necessary, but I'd like to stick with GNOME if possible. From what I've read so far, I should be able to reduce the probability of xruns to negligible, but I don't know what else to change at this point.

Any tips, tricks or pointers to good information are appreciated.

Thanks in advance,

David

---

### Post by thorgal on 2009-07-10
what's your soundcard ? that's a very critical point :)


I have an old Dell Laptop, 1.6 GHz pentium M, 1GB RAM. It works well under jack at low lat because of 2 things:

- kernel 2.6.29.X-rtY
- IRQ sharing: the sound chip, even though an old intel onboard cheapo stuff, does not share its interrupt with other chips.

The setting I have to use is 
jackd -R -P 70 -d alsa -dhw:0 **-n 3** -p 128 (or 64 or 32)

YMMV :)

But of course, as soon as I get jack clients that require a lot of CPU to perform, things are not that dandy. But ardour and basic recording: no sweat :)

---

### Post by notesetter on 2009-07-10
So far, I'm just running playback through OSS using the onboard sound card-- an ALi M5451 which I won't be using for recording.

I have a Tascam US-122 that I haven't set up yet. I'll try that in a few days.

Under 8.04, I'm using 2.6.24-24-rt which is the most recent kernel available to me under 8.04. I tried a fresh install of 9.04 when it was released and things were buggy on this machine, so I went back to 8.04.

How can I tell if my soundcard is sharing IRQ with other hardware on the machine?

I see my work on this probably being limited to simple recording using JACK, Ardour and maybe Hydrogen- 8-10 tracks max (one at a time). I hope I can do this with my current equipment, because I think a new box is at least a year off for me.

Thanks for the reply. I'll fiddle with the Tascam and see if I can get it set up sometime in the next few days.

David

---

### Post by thorgal on 2009-07-10
the following commands are useful (from a terminal). As an example, I will post their output when run on my laptop:

- lists of devices connected to PCI buses
```

lspci

```

mine (greping on "audio"):
```

~$ lspci | grep audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

```

==================

- lists of interrups (IRQs)
```

cat /proc/interrupts

```

mine:
```

~$ cat /proc/interrupts
           CPU0
  0:  261346561    XT-PIC-XT        timer
  1:      91250    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:          6    XT-PIC-XT
  4:          6    XT-PIC-XT
  5:    2980912    XT-PIC-XT        Intel 82801DB-ICH4
  6:          3    XT-PIC-XT
  7:         35    XT-PIC-XT        parport0
  9:        135    XT-PIC-XT        acpi
 10:          3    XT-PIC-XT
 11:   26190457    XT-PIC-XT        ehci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, uhci_hcd:usb4, yenta, yenta, nvidia, firewire_ohci, eth0
 12:    1657232    XT-PIC-XT        i8042
 14:     178726    XT-PIC-XT        ide0
 15:        847    XT-PIC-XT        ide1
NMI:          0   Non-maskable interrupts
LOC:          0   Local timer interrupts
SPU:          0   Spurious interrupts
CNT:          0   Performance counter interrupts
TRM:          0   Thermal event interrupts
ERR:          0
MIS:          0

```


You can see IRQ5 is the one used by the audio chip. It has nothing else sharing it.

==================

- list of realtime processes (task scheduling bit SCHED_FF or SCHED_RR):
```

ps -Leo class,comm,rtprio

```

mine, greping on FF
```

~$ ps -Leo class,comm,rtprio | grep FF
FF  sirq-high/0         50
FF  sirq-timer/0        99
FF  sirq-net-tx/0       50
FF  sirq-net-rx/0       50
FF  sirq-block/0        50
FF  sirq-tasklet/0      50
FF  sirq-sched/0        50
FF  sirq-hrtimer/0      99
FF  sirq-rcu/0          50
FF  posixcputmr/0       99
FF  events/0             1
FF  IRQ-12              90
FF  IRQ-1               91
FF  loadavg             50
FF  IRQ-5               93
FF  IRQ-3               50
FF  IRQ-4               50

```

The higher the number, the higher the RT priority. A 2.6.24 kernel should provide processes called 'softirq-timer', not 'sirq-timer'. I tuned some of these numbers thanks to a script called rtirq. Debian based 64studio has a package that you can install. It will be installed in /etc/init.d as a startup service (when you boot your machine). The tuning can be done in /etc/default/rtirq

You can invoke it to get a status of the RT processes whose scheduling priority that it has modified :
```

/etc/init.d/rtirq status

```

mine:
```

~$ /etc/init.d/rtirq status

  PID CLS RTPRIO  NI PRI %CPU STAT COMMAND
 1500 FF      93   - 133  0.0 S<   IRQ-5
  304 FF      91   - 131  0.0 S<   IRQ-1
  303 FF      90   - 130  0.0 S<   IRQ-12
 2748 FF      50   -  90  0.0 S<   IRQ-3
 2752 FF      50   -  90  0.0 S<   IRQ-4
   67 TS       -  -5  24  0.0 S<   IRQ-9
  552 TS       -  -5  24  0.0 S<   IRQ-11
  776 TS       -  -5  24  0.0 S<   IRQ-14
  777 TS       -  -5  24  0.0 S<   IRQ-15
 1069 TS       -  -5  24  0.0 S<   IRQ-7

```

When RTPRIO is equal to -, it means that it is not an RT process. The rtirq script can be told to remove the scheduling bit SCHED_FF for interrupts that you don't want to have an RT priority.

Here, you can get a debian package of rtirq that should install on Ubuntu 8.04 cleanly (maybe not, you can try):
[http://apt.64studio.com/64studio/testing/pool/main/r/rtirq/rtirq_20070101-1_all.deb](http://apt.64studio.com/64studio/testing/pool/main/r/rtirq/rtirq_20070101-1_all.deb)

You can try this:
```

wget http://apt.64studio.com/64studio/testing/pool/main/r/rtirq/rtirq_20070101-1_all.deb
sudo dpkg -i rtirq_20070101-1_all.deb
/etc/init.d/rtirq start

```

of course, you can tune rtirq in /etc/default/rtirq before starting the service.


===========

if you start jackd with the RT mode ticked, you can check like that:
```

ps -Leo comm,class,rtprio | grep jackd

```

you get:
```

ps -Leo comm,class,rtprio | grep jackd
jackd           TS       -
jackd           TS       -
jackd           TS       -
jackd           TS       -
jackd           RR      70

```

jackd has one RT thread (audio process) running at priority 70 (my own setting, from qjackctl, you can set this number). The default is 10 I believe. It does not have to be higher than the sirq-timer processes spawned by the RT kernel (a generic kernel will not spawn such processes by the way).

---

### Post by notesetter on 2009-07-10
Thanks for all of this helpful information. I'm going to take a few days and figure out what it means for my system and (hopefully) get the Tascam set up.

I'll post back here if I have questions or run into problems.

Thanks a lot,

David

---

### Post by notesetter on 2009-07-16
I tried the version of rtirq you linked to but there are problems with it under Ubuntu Hardy. It seems to have broken synaptic. When I try to open synaptic to remove the package, I get the message: > E: The package rtirq needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report. Closing the error message causes synaptic to close without allowing me to select/de-select packages.

In a terminal, I've tried:

> sudo apt-get remove rtirq and > sudo apt-get purge rtirq with the result: > E: The package rtirq needs to be reinstalled, but I can't find an archive for it. 

I've removed all of the rtirq files using > sudo rm -rf but I still get the error message. Any clue how to completely remove rtirq and get synaptic to behave normally?

---

### Post by thorgal on 2009-07-17
in the terminal, try

```

sudo apt-get install -f

```

this should "fix" packages flagged as broken.

when you "sudo dpkg -i some-package.deb", this should not confuse synaptic or apt-get. If the package is confusing, it shoudl abort before installing it. How did you go about installing the package ? as I described ?

if you want to reinstall, try this:
```

sudo dpkg -i --force-overwrite rtirq_blabla.deb

```

---

### Post by notesetter on 2009-07-17
I used > sudo dpkg -i to install the rtirq package. > sudo apt-get install -f didn't work. I ended up doing > sudo dpkg --remove --force-remove-reinstreq rtirq && sudo apt-get autoremove && sudo apt-get autoclean && sudo apt-get update && sudo apt-get upgrade to completely remove rtirq, fix synaptic and partially upgrade my system. Everything works now.

On another note, I've got the Tascam set up now to work plug & play style. I can get sound out of it, and I seldom have xruns while it's plugged in and hooked up via JACK. But using it causes JACK and sometimes Ardour to crash. As a test, I tried using the card to playback sound and music from other applications (Transcribe!, Rhythmbox) and they crash too, sometimes even causing me to have to reboot the system. This was occurring prior to > && sudo apt-get upgrade and is still the case afterward.

Are there settings somewhere that I may need to tweak? I'm anxious to hook up some mics and start foolin' around.

---

### Post by thorgal on 2009-07-17
glad you fixed your apt environment! I cannot understand why it would go wild like this since rtirq is just a script and a couple of text files ... weird.

for your tascam, don't know, it's USB isn't it ? I have close to no idea on how to tweak at this level. Maybe some firmware update ? don't blame if it is makes your device unusable after that ... :D

---

### Post by notesetter on 2009-07-17
Thanks for the friendly advice.

For the Tascam, I'm using the latest ALSA firmware loaders. I did this in order to set up the device using the recommended method on the ALSA Wiki in combination with some Ubuntu fixes (on the forums here) to set up Hardy to recognize it when it's plugged in (rather than having to manually load the firmware each time from a terminal). It is a USB card.

I'll tool around the forums and 'net to see what solutions others have had success with. Thanks again.

David

---

### Post by notesetter on 2009-07-17
BTW, looks like there are now packages for rtirq in Jaunty and Karmic, so maybe an upstream version for Hardy is on the table. It sounds like a good tool, but I'll wait it out for an official Hardy package before I try it again.

---

### Post by pneaveill on 2009-07-30
> **notesetter said:**
> Thanks for the friendly advice.

For the Tascam, I'm using the latest ALSA firmware loaders. I did this in order to set up the device using the recommended method on the ALSA Wiki in combination with some Ubuntu fixes (on the forums here) to set up Hardy to recognize it when it's plugged in (rather than having to manually load the firmware each time from a terminal). It is a USB card.

I'll tool around the forums and 'net to see what solutions others have had success with. Thanks again.

David
As you look around the forum here, you can see my name appear more than twice on the Tascam issue.  Have had one for maybe 2 years or so and have yet to get it working much at all.  Have gotten the lights to work, but never any sound or real MIDI to work. Thus, if you do happen to figure it out, would appreciate the full walk through on it.

---

### Post by notesetter on 2009-07-31
pneaveill,

I've gotten the lights to work and have gotten sound out of it by selecting it in System>Preferences>Sound. It's actually hot-plugging for me, so I don't have to reboot with it plugged in to get it to work...I just plug it in when I want to fool around with it and the lights come on and I can access it for playback. I haven't been able to record with it, but I have a strong feeling that that's due to my ineptness with JACK and Ardour (almost 2 years in and I'm still a big-time Linux Noob).

I have yet to try MIDI.

If I discover any magic, I'll post it here.

Cheers,

David

---

### Post by pneaveill on 2009-08-01
> **notesetter said:**
> pneaveill,

I've gotten the lights to work and have gotten sound out of it by selecting it in System>Preferences>Sound. It's actually hot-plugging for me, so I don't have to reboot with it plugged in to get it to work...I just plug it in when I want to fool around with it and the lights come on and I can access it for playback. I haven't been able to record with it, but I have a strong feeling that that's due to my ineptness with JACK and Ardour (almost 2 years in and I'm still a big-time Linux Noob).

I have yet to try MIDI.

If I discover any magic, I'll post it here.

Cheers,

David

Most appreciated there David.  Don't feel bad about feeling like a newb.  Been at this since breezy and been told that jack has kicked more butts and sent them packing back to big brother billy there in redmond than most people want to admit.  Just getting Ardour to work now.

---

### Post by pneaveill on 2009-08-04
> **thorgal said:**
> in the terminal, try

```

sudo apt-get install -f

```this should "fix" packages flagged as broken.

<snip>

if you want to reinstall, try this:
```

sudo dpkg -i --force-overwrite rtirq_blabla.deb

```

Is there such a thing for a 686 based system? Been doing some googling on it, but could not find anything on it.  Had somehow missed that it was Amd64 until earlier or did I miss something worse with it?

Also, my Tascam is the dreaded 122L, so think I wasted the money in buying that piece of crap unless someone knows how to squeeze some miracle out of it or something.

This part, am not sure if this is in the right place and moderators can feel free to move it where needed if they so choose:

Does anyone know where to adjust the IRQ settings for things like this:

> 99 FF migration
99 FF posixcputmr
98 FF IRQ 8 (real time clock)
97 FF Audio IRQ
80 RR Jack

Thanks in advance

---

### Post by RaumTrug on 2009-08-06
hi, I'd like to tune in here, as I'm also eager to tune latency as low as possible in order to be able to use my pc as a realtime guitar/mic fx host.

the system is hardware-configurationwise yet unmodified...

atm I'm a bit unsure of what to do next - it seems like my agp (nvidia) video card shares interrupt 11 with my soundcard (m-audio 2496), which is a very bad setup after all, I guess...latency can be quite low already, but as soon as graphics operations take place (very small things are often enough, like moving a small window) jack coughs up with xruns!

before I mess around badly, what do you suggest to move the soundcard to a seperate interrupt of its own, or the graphics card to another free one? as I like blender and 3d audio visualization things I'd like the opengl performance to be nice after all, but good audio comes first.

my mainboard/bios has options to assign the pci slots to fixed interrupts instead of the "automatic" distribution which is on by default, could that help maybe - or is such rather done in software? I'm still quite new to ubuntu and configuring hardware, so I have little clues on how to fix that problem :(

---

### Post by pneaveill on 2009-08-06
HI and welcome to the forums.  Despite being with this since breezy, am still a bit of newb in some areas, so I can get you started maybe and allow someone else to take over on it.

I have been told to start with the basics (and since unsure what you have done already, will go with that): 

```


[LIST=1]
[*]lspci -- to discover what you have in there
[*]cat /proc/interrupts -- discover where stuff is at
[*]RT kernel with the following:
[/LIST]

[LIST]
[*]preempt_rcu (pretty common for RT)
[*]no_hz (clueless on how to setup, so could use an assist)
[*]hz_1000 (pretty common for RT)
[/LIST]
      4. various forums also suggest the following (which am not sure how to do either)

[LIST]
[*]99 FF migration
[*]99 FF posix_cputmr
[*]98 FF IRQ-8 (realtime clock) -- not assumed within any given kernel
[*]97 FF audio IRQ
[*]80 RR jack
[/LIST]
----- edit ------
    5. favorite editor: /etc/security/limits.conf
@audio   -  rtprio     99
@audio   -  memlock    unlimited
@audio   -  nice       -19

  6. create audio group and add your name to it (wish that ubsustu devs would have somehow done this for us, but alas)
  7. verify alsa headers and that sort of stuff as appropriate
-----/edit------

```Not knowing your exact system, would advise setting the IRQ to a non-used setting obtained from the lspci. As to the sound or video, some are hardwired, so not sure. May have to physically move the sound card from one slot to another in worst case -- DISCLAIMER: Never used that sound card, so am completely clueless.

Someone with a little more experience can help on this one please: As far as I am aware, the X-runs might be at least in part, a sort of conflict with some video driver and the sound card.

Hope that helps some.  Let us know how things turn out.

---

### Post by sgx on 2009-08-07
> **notesetter said:**
> pneaveill,

I've gotten the lights to work and have gotten sound out of it by selecting it in System>Preferences>Sound. It's actually hot-plugging for me, so I don't have to reboot with it plugged in to get it to work...I just plug it in when I want to fool around with it and the lights come on and I can access it for playback. I haven't been able to record with it, but I have a strong feeling that that's due to my ineptness with JACK and Ardour (almost 2 years in and I'm still a big-time Linux Noob).

I have yet to try MIDI.

If I discover any magic, I'll post it here.

Cheers,

DavidThis link is to a detailed web-page ardour tutorial, done on a Mac, but applies a lot to all versions. I also read somewhere a guy has his Tascam 122 fully working, he had the magic hardware, I kick myself now for not bookmarking it, but it is on the google somewhere!

[http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)

---

### Post by pneaveill on 2009-08-07
> **sgx said:**
> This link is to a detailed web-page ardour tutorial, done on a Mac, but applies a lot to all versions. I also read somewhere a guy has his Tascam 122 fully working, he had the magic hardware, I kick myself now for not bookmarking it, but it is on the google somewhere!

[http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)

Sadly, there is a mountain of technical differences between the 122 and the 122L.  Many people have gotten the 122 to work and have yet to find anyone getting the 122L to work properly.  That said, have gotten the jack/ardour system to work fine with minimal xruns  and fairly low latency until I grocked it doing the latest upgrade. Rebuilding now.

---

