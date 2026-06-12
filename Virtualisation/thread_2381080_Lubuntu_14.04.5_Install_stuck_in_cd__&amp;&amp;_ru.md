---
title: "Lubuntu 14.04.5 Install stuck in cd / &amp;&amp; run-parts --report /etc/cron.hourly."
date: 2017-12-26
forum: Virtualisation
---

### Post by osuts on 2017-12-26
I'm new to Linux, and I've been trying to install Lubuntu 14.04.5 since yesterday evening. 

I'm trying to install Lubuntu 14.04.5 from a live CD, the first time it gave me the known bug running the Live Disc - Something about missing files or couldn't find certain files - followed the instructions, and did not fix it.


- While booting Ubuntu 14.04.5 it from the desktop Install Icon gave me this error: the disk drive for /dev/mapper/cryptswap1 is not ready yet or not present is showing - [https://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or](https://askubuntu.com/questions/341979/what-to-do-about-the-disk-drive-for-dev-mapper-cryptswap1-is-not-ready-yet-or)

I followed the instructions, to no avail. It did not work.


Then I gave in and tried installing Ubuntu 14.04.5 without encryption, from the Install Icon in the Live CD bootable version, and is as follows: 

Then I tried installing from the Installer inside the Lubuntu Live Disc Boot, from the version which is available to use with the dvd, and it gave me the error - Unsafe swap space detected - [https://askubuntu.com/questions/393418/unsafe-swap-space-detected](https://askubuntu.com/questions/393418/unsafe-swap-space-detected) - tried fixing that with many walkthroughs, and nothing fixed it. - Not specifically those on that page, but easier ones, more basic.

Now for the second time, the installer is stuck at - lubuntu CRON[29534]: (root) CMD (  cd/ && run-parts --report /etc/cron.hourly for over an hour.

I checked the DVD with the Lubuntu boot checker, I checked my system as well (RAM effectiveness, and other pertinent stuff)

I need to have my computer running due to work matters, is there a way for me to install Lubuntu 14.04.5? (I can't boot from usb, only burned Cd's and DvD's, as my motherboard doesn't permit that function.

I did ran into other conflicts while installing, which were fixed. Other errors could not fix.

Do I need to burn another DvD (I don't have much left) and Install another version of Lubuntu?

My specs are 64amd 120 GB HDD 4 RAM.

---

### Post by deadflowr on 2017-12-26
Is this an actual virtual machine?

---

### Post by osuts on 2017-12-26
I'm not really sure what a virtual machine is, but I'm running a PC that had Windows XP some years ago. With a mobo that accepts winxp and win2000.

Update:

[SIZE=3][FONT=arial]
[/FONT][/SIZE]I reinstalled (booted) Lubuntu 14.04.5 from the Live Cd, with the first option (the light version, only erase previous Lubuntu Versions, no disk partitions or erase disk, neither encrypting, I'll do that later - at the moment I'm downloading the updates - That's the part where in previous installs it went haywire and gave me error messages. - The system is running slow tho, I'll have to make some adjustments after the download and install is complete. Any advice is welcome. –[SIZE=3][FONT=arial]
[/FONT][/SIZE]

Used all the techniques described above, and after a lot of try outs, Lubuntu 14.04.5 is running.

I have studied the Ubuntu sotware for over a week and doing all kinds of research on how it works, without taking breaks.


I thought that Lubuntu 14.04.5 best fitted my specs - a mobo that supports winxp and win2000 - Athlon 64 AMD, 4 RAM, 120 HDD.


I finally could work for about 10 minutes in Lubuntu 14.04, and it was behaving laggy and heavy, I open up Resources, and the CPU was at 100% and the memory, only showed 998mb, and it was maxed out as well.


Then it stated that there was a problem and I could only boot from the disk. Don't remember the error message. 


I tested all my computer (RAM, AMD CPU, as well as the HDD).


Why is Lubuntu 14.04 behaving this way with my specs? Can somebody help me or point me in the right direction?

---

### Post by QIII on 2017-12-26
Hello!

Can you replicate the error and let us know what it is?

---

### Post by oldos2er on 2017-12-26
See [https://docs.lubuntu.net/lubuntu_installation_on_old_computers.html](https://docs.lubuntu.net/lubuntu_installation_on_old_computers.html)

If you do indeed have an Athlon 64 CPU (from 2003?), that's likely the bottleneck. Did you installed 32- or 64-bit Lubuntu?

---

### Post by osuts on 2017-12-26
Hi QIII!! - when I turn on my computer, it says: "Disk Boot Failure, Insert System disk and press enter" - Then it takes about 8 minutes to load, and the desktop and features are laggy, it freezes, it becomes unresponsive, it has 15 to 20 second delays, the same as the previous installed 14.04.5 Desktop amd64 Version when the CPU Spiked. Sometimes the CPU doesn't spike for 20 or more minutes, using all the features I can, then it starts again even not having one window or application open or functioning in the background. Seems that the CPU Spikes on itself, because in Task Manager I could see that none of the programs where using resources, and the CPU meter was at 100%. What I dont understand, I mean, what I don't know, is why it shows 998mb of RAM instead of 4 RAM that the mobo has.

Oldos2er - Yes, I installed the 64 Version. 

from the doc : [COLOR=#666666][FONT=&amp]It is possible to run Lubuntu Core and standard Lubuntu with Pentium II, Pentium III or Celeron processors and contemporary AMD processors, but the computer will be slow, and some tasks may not work. -
[/FONT][/COLOR]
I looked in every version, and I thought that 14.04 handled old AMD processors, obviously I'm mistaken. That can be what's causing the whole problem. I have spent 3 days checking out specs, so that might have slipped by. Thanks for that info!

Which Version can I use, with an old AMD Processor and Lubuntu? Should I look into Fedora, Parrot Linux or Debian?

I was hoping to use libreoffice and surf the net, and with a little luck use Gimp and Inkscape with very lightweight projects (I know the Limitations of this AMD PC), then pass them thru usb to my Windows 10 Machines, which usually are rendering or cooling down. I was looking how to make a Windows-Linux File System Sharing using my Router, and it wasn't that complicated. I wanted to leave everything set up so I could get on with my work. 

Thanks for the responses!

---

### Post by oldos2er on 2017-12-26
I was looking at the "A rule of thumb is that the computer should not be more than 10 years old" bit.

---

### Post by osuts on 2017-12-26
I know, but being an Advanced Professional Engineer, and at the same time a Paid Artist, (both merge into one), I have to make work what I have, or work with what I have.

Can you recommend a System that can work with my Specs? (or semi-work, nothing too fancy, libreoffice and browse the internet and post will do), before I get the parts of a semi-new one in the mail? Any other recommendations? That way I can keep learning Linux and that way I can look the recommendation over, while I do my own research. Thanks for the help!

---

### Post by QIII on 2017-12-26
How old is your hard drive?  Model and manufacturer?  Have you checked and double-checked the connections?

The error you told us about in post #8 is a hardware issue not an OS issue.  If you have a failing drive or power supply there is little that can be done short of replacement.

---

### Post by osuts on 2017-12-26
Thanks QIII, I would never have come to that assessment. I had my goal set for today to get Lubuntu working (deadline), then I have other projects (fix hardware), then I have to get back to my main Job (Art Stuff). Around the 4th or 5th of January 2018 I think I will be able to spend more time (hours on end) with the old PC doing some more accurate tests, or finally installing a Linux Distro. In the mean time I will be playing around with Linux none the less. And looking for a Version that can run in this PC before the parts of the new one arrive. Which I still have to find a CPU for it and other parts. Old parts in this part of the world can be found very cheap, I wouldn't mind doing a minor upgrade to this computer, then giving it to a elder relative when I get my new one, and in the mean time play around with Linux.

I haven't had the time to check the connections, as I am new to this. First I wanted to place a working OS, then I would open it up. Going to do that first thing when I get free time and check the connections.

Opening the case I can see: 350W and the model: Model LPj2-20. No brand visible. I guess it's the only Power Supply.

The HDD must be very old, same as the PC. Around 2004 or so.

Pulled out this info from: sudo gparted .command line.



              **Model**: ATA Maxtor 6B160P0 7200 RPM
                **Size**: 152.67 GiB
                **Path**: /dev/sda
**Partition Table**: unrecognized
              **Heads**: 255
    **Sector Tracks**: 63
       **Cylinders**: 19929
   **Total Sectors**: 320173056
      **Sector Size**: 512

---

### Post by osuts on 2017-12-27
I been looking around in my spare time for a Linux Based Systems that supports old AMDs, but having close to none experience in Linux is limiting my choices and decisions.

When a Distro states "MINIMUM RECOMMENDED SPECIFICATIONS:&#8203;CPU: 700MHz processor"

It means any processor that can run at that speed or higher? or it states a specific processor?

I was looking around and found a few Distros that may seem compatible with my old AMD (I will check the HDD connections later, when I'm rested, and have the time to focus on it, so I don't break anything)

I was looking to install Tiny Core or Bodhi Linux, but I can't find which CPUs from what year they support. Can someone give me a hint of where or how to look for that specific info? They just state something like "500mhz processor".

(I would be trying all these by myself, but my mobo only has boot from disk, no option to boot from USB, and I have like 3 DvDs left)

***Edit: Watched some tutorials on YouTube, read some stuff on the web, and I checked the connections of the HDD and of the Power Supply, they seem to connect properly. The HDD is fact a Maxtor HDD.***

---

### Post by uRock on 2017-12-28
Minimum recommended specifications is just that. The bare minimum. 

Give [Puppy Linux]("http://www.puppylinuxfaq.org/first-steps-in-puppy-linux/9-installing-puppy-linux-installing-puppy-linux/21-minimum-hardware.html") a looking into. System requirements;```
Minimum Hardware Requirements for Puppy Linux 4.2.1
500MHZ processor
128MB RAM
512MB free hard drive space to create an optional save file
No hard drive required to boot a Live Disc.
CD-ROM any speed
Minimum Hardware Requirements for Puppy Linux 4.1.2
233MHZ processor
128MB RAM
512MB free hard drive space to create an optional save file.
No hard drive required to boot a Live Disc.
CD-ROM any speed
```
Or [Peppermint OS]("https://peppermintos.com/guide/downloading/")

---

### Post by osuts on 2017-12-28
Thanks uRock! Tomorrow I'll be looking into those and installing the one that seems best fitting! Can they be downloaded and installed from a command line from Terminal or installed from unetbootin?

---

### Post by uRock on 2017-12-28
Yes. The dd command always works for copying to USB.

---

### Post by osuts on 2017-12-28
Oh, that's a shame! My Bios doesn't have the boot from USB option! I'm looking for downloading the .iso and running it from the computer, or downloading it and installing using Terminal! But if a clean install from a DvD is more stable, (as i have read instead of running it from inside the computer with unetbootin) that's how I'll install it! At least the final install!

---

### Post by uRock on 2017-12-29
Unetbootin works with a variety of distros. I'd be shocked if it didn't work with Puppy or Peppermint.

---

