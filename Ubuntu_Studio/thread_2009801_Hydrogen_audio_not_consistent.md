---
title: "Hydrogen audio not consistent"
date: 2012-06-24
forum: Ubuntu Studio
---

### Post by themuseman on 2012-06-24
I recently installed Ubuntu Studio 12.04, 64 bit on my desktop PC. I have two sound cards: MAudio 2496 and a sound card built into the  mother board. I'm trying to get audio out of Hydrogen to go to the MAudio 2496 card. Sometimes it works, some times it doesn't. 

Here are some things I have found out:

Using aplay in the terminal, I see that sometimes the MAudio is card 0, and other times its card 1. Whenever its card 0, everything works fine. 

Each time I re-boot, the MAudio card # changes. (its either one or two).

How do I get the MAudio card to stay as card 0?

themuseman

---

### Post by sgx on 2012-06-25
bash-4.1$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

run that aplay -l  command, and replace the hw: entry, with what is in the brackets, and restart qjackctl. ICE1712 multi, in my case,
but you may need the other one, M Audio Audiophile 24/96

Use the names from your command, not mine :wink:

I have the same card, but have also disabled the onboard sound
in the bios, and placed it in a text file called blacklist,
in the folder   /etc/modprobe.d

my file is just one line,

blacklist snd_intel8x0

run the lsmod command, to see what your motherboard sound kernel module is, and create such a file. lsmod lists the kernel modules,
and groups of them that rely on each other, so many sundry audio related modules are clumped together in some lines of the output.

Cheers

---

### Post by themuseman on 2012-06-25
To SGX -- thanks for the response. I am still trying to get a handle on Ubuntu, so please bear with me.

1. QJackCtl settings 

Here is the card 1 part of my "aplay -l" :

card 1: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

It's the same as your card 0. I tried putting the different names listed above as substitutes fore the card # into QJackCtl settings section. I tried the "Interface" section and also the "Output Device" section. But it didn't send the audio out to the MAudio card when I re-started QJackCtl and Hydrogen.

2. Blacklist

I did a "lsmod" from the terminal. I think my motherboard audio card is snd_hda_intel. I checked my /etc/modprob.d folder. I don't have a "blacklist" file but there is a "blacklist.conf" file (and some other blacklist files as well). Do I just make a new file called "blacklist" and put it in /etc/modprobe.d folder ? What makes sure it gets read on bootup? Or do I use the "blacklist.conf" file? 

thanks -- themuseman

---

### Post by sgx on 2012-06-25
Hi, the file blacklist.conf may be the one to use.
If its contents are just a few single lines, or empty, thats a
good sign. That may not be needed if the sound chip is disabled
in the bios.

I switch between guitar interface and keys a lot, so I turned off
qjackctl autostart in the misc tab of the setup panel,
and choose the gear first.

I typed default in the qjackctl input/output fields, and restarted,
log out/in, and it worked ok, and you can also put a copy of your
.jackdrc in your .bash_history textfile, and recall it with tapping
the up-arrow, which cycles through your command history, when a terminal is open, to start jackd as a command.

qjackctl saves the .jackdrc text file in /home/you
each time you make changes and restart. Mine is

/usr/bin/jackd -P89 -t200 -dalsa -d hw:0,0 -r44100 -p512 -n2


In Hydrogen Tools-->Preferences-->audio system panel, choose jack, rather than auto, or try restarting the hydro engine with the
'restart output' option that is right there.

(typing the names in qjackctl input.output fields failed for me,
I recently switched to jackd v2, not sure whats up.

You can use various versions of .jackdrc as commands for different setups. When you start qjackctl after jackd is running, it says 'active' in its display.

Cheers

---

### Post by sgx on 2012-06-26
Hi, there was a typo  in the .jackdrc I posted, the capital D is needed in the duplex portion.
These 3 commands worked to start jackd,
and then I started qjackctl.
Each maudio reference is found within brackets in some command output.

cat /proc/asound/cards
aplay -l
aconnect -i

/usr/bin/jackd -P89 -t200 -dalsa -D hw:M Audio Audiophile 24/96 -r44100 -p512 -n2

/usr/bin/jackd -P89 -t200 -dalsa -D hw:M2496 -r44100 -p512 -n2

/usr/bin/jackd -P89 -t200 -dalsa -D hw:ICE1712 multi -r44100 -p512 -n2

---

### Post by themuseman on 2012-06-27
I was able to disable the on-board sound card in bios. Now I consistently have audio out of the M2496 card. So that's good.

If I start Hydrogen first and then I open QJackCtl, it is already in Play mode, and I have audio out of Hydrogen ... In fact all I have to do is start Hydrogen and I can get audio out of it without starting QJackCtl. And the autostart function in Misc section for QJackCtl is disabled. Because QJackCtl is running, I assume that Jackd is running ??

I will work with it more to make sure I can set up the M2496 card parameters. I'm trying to digest your latest posts ... I will cogitate on them ... and experiment more ... 

Thanks so far ... [IMG]http://ubuntuforums.org/images/icons/icon6.gif[/IMG]

themuseman

---

### Post by sgx on 2012-06-27
qjackctl will light up whenever jackd is running. Here's a link
to a nice drumkit, if you don't have it yet, and how to get it
working in hydrogen

[http://linux-recording.blogspot.com/2011/09/using-analogue-drums-big-mono-with.html](http://linux-recording.blogspot.com/2011/09/using-analogue-drums-big-mono-with.html)

Ardour daw is another app that may start jackd when it is launched.

cheers

---

### Post by themuseman on 2012-06-28
Thanks again.

How do I mark as SOLVED?

themuseman

---

