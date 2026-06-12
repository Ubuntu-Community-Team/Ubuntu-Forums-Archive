---
title: "DOS 1.25 on SIMH 8086 emulator"
date: 2009-03-29
forum: Virtualisation
---

### Post by 10nitro on 2009-03-29
I'm trying to get MS-DOS 1.25 (from [here]("http://www.schorn.ch/cpm/intro.php"))to run in an emulator, right now the one provided on the same page (the Linux binary link).  The build I received is V3.8-1 build 1254 (scp created Feb  9 2009 at 18:10:22 with gcc 4.2.4)

I put the emulator in the same directory as the extracted MS-DOS files, set it to executable, then try to run it with
```
./altairz80l msdos125
```

It looks very much like I am successfully running MS-DOS 1.25, but the output looks like I've been running "cat /dev/urandom" for an hour. (and so does the text when I type)

Any ideas on what's wrong?

[edit:] I attached the output I get at first.  At this point it appears to be at a prompt, as pressing any key triggers a response.

---

### Post by mlentink on 2009-03-29
Did DOS even run on the Z80? I thought you needed a 8088 or 8086 for that

---

### Post by Dedoimedo on 2009-03-29
Maybe you can manage with freedos or dosbox, perhaps?
Did you think of those solutions?
Dedoimedo

---

### Post by 10nitro on 2009-03-29
> **mlentink said:**
> Did DOS even run on the Z80? I thought you needed a 8088 or 8086 for that

It's called the Altair Z80 simulator, but it emulates several processors (according the page I got it from, 8080 CPU, Z80 CPU and 8086 CPU).  I'm using the hardware configuration file provided with the DOS download.If I were to just type "./altairz80l", then it would drop into a "sim>" prompt to enter hardware configuration commands.  Or I can run it with a configuration file that has all the necessary commands in it.
I recieved 4 files with the MS-DOS download, 2 disk images (msblank.imd/msdoscr.imd), a pre-boot program ("SCP 8086 Monitor 1.5", mon.com), and a hardware config file (msdos125).
The  The first command in msdos125 is "set cpu 8086".  And the 8086 emulator defiantly works, because I have gotten 86-DOS 1.00 (which MS bought and renamed MS-DOS) to run fine.

As a note, this and all of the [SIMH]("http://simh.trailing-edge.com/") emulators are available in the Ubuntu package "simh", but are outdated (the z80 in the package is V3.7-0, the one I just downloaded is V3.8-1), and does not appear to handle the config file:
```
Altair 8800 (Z80) simulator V3.7-0
msdos125> set cpu 8086
Non-existent parameter
```


> **Dedoimedo said:**
> Maybe you can manage with freedos or dosbox, perhaps?
Did you think of those solutions?
Dedoimedo

I am aware of these, but I'm not doing this for practical reasons, I just want to emulate every version of MS-DOS I can.

---

### Post by mlentink on 2009-03-31
I need to dive into these, look s like a fun exercise. Might take a while though. But it loooks like a story of my life...

---

