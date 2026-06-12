---
title: "Cannot regain Alsa after reinstalling 10.10"
date: 2011-02-11
forum: Ubuntu Studio
---

### Post by LinuxPoolMan on 2011-02-11
Hi there. I am new to posting in the forums but I have never had to before. I have solved dozens of problems thanks to the hard work you guys put into helping us out. I am stuck though...I borked my system today trying to set up a Bamboo drawing tablet and had to do a re-install to root from LiveCD. I am up and running again but without -rt kernel and no sound from my M-Audio mobile-pre usb. 

Before I would run alsamixer in terminal and fix the sound but now that command does not work. Found file in /usr/bin/alsamixer but doesn't work from command line anymore. Device shows up from lsusb.

64-bit
2.6.35-25-generic

Many thanks and please excuse any posting stupidity.

---

### Post by Pablo_F on 2011-02-11
Hi, 

The alsa-info script:

wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Please, upload and give the URL if you wish.

Cheers! Pablo

---

### Post by LinuxPoolMan on 2011-02-11
[http://www.alsa-project.org/db/?f=d0b0dd5b7c955e3e9fc9375628f476d21aac446c](http://www.alsa-project.org/db/?f=d0b0dd5b7c955e3e9fc9375628f476d21aac446c)

I have tried numerous options...hope this helps. Thank you Pablo_F

---

### Post by Pablo_F on 2011-02-11
Hi, 

The alsa drivers are not installed. Check this:

sudo updatedb
locate snd-usb-audio

If I were you I would reinstall the whole system because I am not expert at installing linux modules by hand and this kind of things scares me #-o

Cheers, Pablo

---

### Post by LinuxPoolMan on 2011-02-11
kevtiff@kevtiff-Vostro-200:~$ alsamixer
cannot open mixer: No such file or directory
kevtiff@kevtiff-Vostro-200:~$ gnome-alsamixer

(gnome-alsamixer:2158): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault

Tried this too..
[http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html](http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html)

Still no luck

---

### Post by LinuxPoolMan on 2011-02-12
I am going to revert back to 10.04 when everything worked. Still no -rt kernel but with 8ms latency I'll be OK. Will the 2.6.35-25-generic kernel be used or will 10.04 use an earlier kernel? In other words will doing this solve my problem? Guess I will see shortly...

---

### Post by Pablo_F on 2011-02-12
I think this is a good idea. Lucid will use an earlier kernel by default but I don't see the problem with that. alsa drivers version is earlier too, but afaik, with that card you are fine. 

Note that these kind of basic software changes will be implemented by distros. The next ubuntu release will have more recent versions of kernel, alsa drivers and what not. Patiente is a virtue.  

You can always try with the rt kernel in [Alessio's PPA]("https://launchpad.net/~abogani/+archive/ppa?field.series_filter=lucid") but you already have a usable system, I think.

Cheers, Pablo

---

### Post by LinuxPoolMan on 2011-02-12
Reverted to 10.04. I guess GRUB couldn't find 2.6.35-25-generic so the install failed. Back to 10.10 and same message as above but this time system loaded. Mouse did not work first time but did after reboot. Time to back up all files and do a clean/reformat/reinstall. 

Why am I getting the message FATAL ERROR could not find 2.6.35-25-generic at boot? Never did that before. So confused....

---

### Post by LinuxPoolMan on 2011-02-12
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0763:200f Midiman M-Audio MobilePre
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
   

Do you see a problem with output from lsusb?
Should I see a /usr/share/usb/maudio file? There is currently no /usr/share/usb   or  /usr/local/share/usb

---

### Post by Pablo_F on 2011-02-12
Hi, 

You have the m-audio in the output of lsusb. I see no problem. 

And no, you shouldn't see anything like /usr/share/usb You just need the snd-usb-audio module loaded. Check with:

cat /proc/asound/modules

or 

lsmod | grep snd

---

### Post by LinuxPoolMan on 2011-02-12
Reinstalled 5 times today. Lose mouse every time. Manged to boot from GRUB menu to older kernel in failsafe graphics mode. Backing up files right now. I will do a full format/install tonight of Ubuntu Studio 10.10 64-bit and see what happens. Thanks for the help so far Pablo, hopefully I can begin again tomorrow. Wish me luck!

---

### Post by LinuxPoolMan on 2011-02-12
> **Pablo_F said:**
> Hi, 

You have the m-audio in the output of lsusb. I see no problem. 

And no, you shouldn't see anything like /usr/share/usb You just need the snd-usb-audio module loaded. Check with:

cat /proc/asound/modules

or 

lsmod | grep snd


Tried snd-usb-audio from above and got nothing. Too late now though....borked entire system and backing up now. I will let you know after clean install. Many thanks.

---

### Post by LinuxPoolMan on 2011-02-12
Turns out that 4 days of messing with system files while trying to install a Wacom Bamboo P & T can really screw things up. With 5 beans of luck and a cup of patience I finally have my computer back! Backed up ALL needed files, ran a clean reformat install (not the install to / manual partition from Live CD), and heard those glorious notes from my speakers. 

Ubuntu 10.04LTS 64-bit  ---- Upgraded to Ubuntu Studio
ALSA is all well and good for now
No xruns from JACK
8.21ms latency
and crummy M-Audio Mobile-Pre USB doing its job finally.

Thanks to Pablo for doing your best to work me through this one but sometimes a clean machine runs better than the ones we try to fix. Audios....

---

