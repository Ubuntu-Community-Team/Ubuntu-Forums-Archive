---
title: "UbuntuStudio 12.04 LTS and USB audio interface"
date: 2012-05-19
forum: Ubuntu Studio
---

### Post by paintthedevil on 2012-05-19
Hey folks,
 
I'm no native speaker and a Ubuntu beginner - so please excuse my english ;)
I installed UbuntuStudio 12.04 LTS on my HP Pavilion dv6595eg, it's working fine, but I was not able to get my Tascam US-122L interface started.
I'm also using Win XP on my computer (the only reason I still use it is the VST compatibility) and it's working on it, so it's definitely no hardware problem.
I found different solutions for this problem on older Ubuntu versions, I tried out all of them - maybe I'm too stupid for that.
Of course I tried to change some settings in Jack, Terminal and so on - but when I start Ardour for example, it's only detecting my onboard soundcard.
I hope you can help me out, I want to make Ubuntu my default operating system for my music production :guitar:
 
Thanks for your help,
cheers from Austria

---

### Post by CrocoDuck on 2012-05-19
Maybe I had a stupid thought or this is a thing you just tried... Jack knows that you have a Tascam US-122L? Open qjackctl, then go to setup and have a look in the Input Device and Output Device options. If the harware configuration is ok you should view something related to USB audio interface. Did you have set something in the interface option?

Posting the output of this can help:

```
cat /proc/asound/modules
```

---

### Post by paintthedevil on 2012-06-06
Hey, sorry for the late response....yes, it knows about my Tascam interface, in my case it is set as hw:1.

Here the output:

```
mario@mario-HP-Pavilion-dv6500-Notebook-PC:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l

```

thanks for your help!

---

### Post by BcRich on 2012-06-06
> **paintthedevil said:**
> Hey, sorry for the late response....yes, it knows about my Tascam interface, in my case it is set as hw:1.

Here the output:

```
mario@mario-HP-Pavilion-dv6500-Notebook-PC:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_us122l

```thanks for your help!
If you don't need the onboard sound you could try disabling it in BOIS (if you haven't already tried of that?).

---

### Post by OFobbs on 2012-06-07
I'm no expert in this but I got mine working using this thread:
[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073)

Basically, I set up a file called .asoundrc in my Home directory containing this:
# The usb_stream plugin configuration

pcm.!usb_stream {
@args [ CARD ]
@args.CARD {
type string
default "1"
}

type usb_stream

card $CARD
}

ctl.!usb_stream {
@args [ CARD ]
@args.CARD {
type string
default "1"
}

type hw

card $CARD
}


After you set that up, reboot, start jack, go into your settings, change Interface to 
'usb_stream:1'.  for me 1 is the number my us122l is under.  Hit the '>' to see what your us122L number is.  You should be able to run this time. 

Hope this is helpful. 


Omar

---

### Post by CrocoDuck on 2012-06-08
> **OFobbs said:**
> I'm no expert in this but I got mine working using this thread:
[http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073](http://www.linuxmusicians.com/viewtopic.php?f=6&t=1073)

Basically, I set up a file called .asoundrc in my Home directory containing this:
# The usb_stream plugin configuration

pcm.!usb_stream {
@args [ CARD ]
@args.CARD {
type string
default "1"
}

type usb_stream

card $CARD
}

ctl.!usb_stream {
@args [ CARD ]
@args.CARD {
type string
default "1"
}

type hw

card $CARD
}


After you set that up, reboot, start jack, go into your settings, change Interface to 
'usb_stream:1'.  for me 1 is the number my us122l is under.  Hit the '>' to see what your us122L number is.  You should be able to run this time. 

Hope this is helpful. 


Omar

If this don't work (should work) look if you have installed alsa-tools, alsa-firmware-loaders, libasound2-plugins . **Of course be carefull on installing these if there is some dependencies conflict**, expecially for alsa-firmware-loaders. After some experiments they looks works with no issues on my Ubuntu Studio 12.04 installation.

---

