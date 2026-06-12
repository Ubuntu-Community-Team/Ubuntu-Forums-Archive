---
title: "Ramdisk (tmpfs) issue on server 12.04 LTS"
date: 2012-09-07
forum: Server Platforms
---

### Post by InsertPineapple on 2012-09-07
Hi everyone-

I normally find everything I need from these wonderful forums via search but finally ran dry on a problem I've been having while configuring a bukkit server. Any help would be loved and used to educate! :]

Quick system summary-
AMD Phenom X4 9550 (2.2ghz AM2+)
8GB (4x2gb) DDR2 PC2-8500
WD caviar blue 7200rpm 16mb
Ubuntu Server 12.04 LTS x64


This is going to be a somewhat multipurpose server eventually (lamp installed), but at the current moment the plan is to strictly host a large map bukkit Minecraft server until I wrap my head around apache and most of unix in general. I'm new :D

We have provisioned everything for this server and tested, but obviously the hard disk is a pretty bad bottleneck, so the plan is to ramdisk 3GB using tmpfs to /bukkit/world. Then we can get simple scripts to take care of making persistent copies to disk at 20 minute intervals, as well as startup/shutdown copy.

Steps/Problem- (pardon my noob)

I started with chmod 777 on /etc/fstab, to open it in nano.
sudo nano /etc/fstab

I add the following line to the bottom of fstab...

tmpfs    /bukkit/world     tmpfs    rw,size=3072M    0    0

I save and exit nano.
I reboot with init 6

When the PC reboots, I get no loading screen or terminal. It sits idle at a black screen. The monitor does not go to sleep, so it indicates some type of signal is detected. Key board is lit but nothing respond.
I'm not able to see any errors during this, as the blank screen occurs right after POST.

I've read some posts that advise how to remove this via a live disc/usb, but this doesn't exactly help. The PC is pretty quick and I ended up reinstalling the OS in a short time.
Tried the process again on the fresh OS and got the same result.

I also tried installing the same server x64 image onto VMware on my laptop, going through the same simple setup.
I was able to successfully do all of the following steps to a virtual machine, reboot the VM, and see my test mounted disk in /bukkit/world.

Is there something wrong with my PC??... I started a memtest before work but I won't be home for another few hours to check on it. Haven't had any problems up to now.


If anyone has any input on whether I'm doing something wrong here, I'd love to try anything at this point.
I unfortunately can't post the contents of fstab from work right now, but if needed, I can when I arrive home tonight. But I can say that it's pretty much default + that one addition.

Thanks in advance for any advice!

-Tim / InsertPineapple

---

### Post by Bachstelze on 2012-09-07
> **InsertPineapple said:**
> 
I started with chmod 777 on /etc/fstab, to open it in nano.
sudo nano /etc/fstab

It's a bad idea to chmod /etc/fstab (or anything else outside /home really, unless you really need to and know what you are doing. Running your editor with sudo, as you did, is enough.

> I reboot with init 6

You should never call init directly. The command to reboot is simply [font=monospace]reboot[/font].

---

### Post by InsertPineapple on 2012-09-10
> **Bachstelze said:**
> It's a bad idea to chmod /etc/fstab (or anything else outside /home really, unless you really need to and know what you are doing. Running your editor with sudo, as you did, is enough.
Good advice. I think I can into a problem with permission the last time I tried, I think that's why I resorted to chmod.
I tried again and it allowed me to edit with sudo nano.


> **Bachstelze said:**
> You should never call init directly. The command to reboot is simply [font=monospace]reboot[/font].
I was convinced by a friend the exact opposite while I was using reboot. Thanks for clarifying :]


So to add to this problem, I ran memtest in a number of combinations and found a bad stick.

I removed this stick, reinstalled the OS, and tried the same thing using the advice given.
I experience the same issue as before :/

Maybe I'm that much of a noob...
If I'm logged in to the username 'serv', and editing fstab to mount a location... do I need to specify the location like this?...
/home/serv/bukkit/world ?
or is my location of /bukkit/world ok?

'bukkit' is the folder I created to hold the server when I was first logged in.

Any input? I said I'm new :]


Thanks!
-Tim

---

### Post by LHammonds on 2012-09-11
The best way to issue a reboot command is:
```
shutdown -r now
```

As for your CraftBukkit server using a RAMDisk, you are probably complicating it more than necessary.  Older versions were poorly optimized and using a RAMDisk helped somewhat.  However, with the current version of CraftBukkit, you probably will not see much performance gain doing this...unless you are running off a real clunker of a hard drive (pre 2003)

I used to use a RAMDisk for my server to reduce the console messages about not being able to keep up but now I don't have that problem with the newer versions.

If you are really curious how I setup the old server (with automation scripts), you can [find it here](http://forums.bukkit.org/threads/how-to-setup-a-custom-craftbukkit-server-1-2-5-r1-0.69825/).

LHammonds

---

### Post by Bachstelze on 2012-09-11
> **LHammonds said:**
> The best way to issue a reboot command is:
```
shutdown -r now
```

[font=monospace]reboot[/font] does the exact same thing with fewer keystrokes.

---

### Post by InsertPineapple on 2012-09-11
> **LHammonds said:**
> 
As for your CraftBukkit server using a RAMDisk, you are probably complicating it more than necessary.  Older versions were poorly optimized and using a RAMDisk helped somewhat.  However, with the current version of CraftBukkit, you probably will not see much performance gain doing this...unless you are running off a real clunker of a hard drive (pre 2003)

I used to use a RAMDisk for my server to reduce the console messages about not being able to keep up but now I don't have that problem with the newer versions.


I looked through the post, VERY nice! I'm surprised I didn't come across this in my google adventures. 

Are you fairly sure my WD 7200rpm drive could handle this? I don't want a huge amount of delay when 10 or 15 people are on at the same time in different parts of the world... 

I haven't heard anything with the improvements in the game using I/O... so I'm a bit curious now. I'm going to deploy without ramdisk tonight and see if I can get enough people on to test our highest load. I'd rather not have to mess with it but it just seemed like it would be needed for this many players on a single drive.

I'll update the post after we test some more. Thanks again for the input!

-Tim

---

### Post by LHammonds on 2012-09-11
I just started a new thread (on [Bukkit Help forums](http://forums.bukkit.org/threads/how-to-setup-a-trickd-out-craftbukkit-server-1-3-1-r2-0.100406/)) for a 1.3.1 server but this time without using a ramdisk.

I also replied my findings on [TnT's thread](http://forums.bukkit.org/threads/how-to-improve-mincraft-server-performance.662/page-10) which talks about performance and how to setup a ramdisk.

I would advise like you are doing now.  See if the KISS principle will allow your gameworld+you users+your hardware+your config setup to work in a simplified manner.

If not, see if you can isolate a problem child such as a poorly behaving plugin.

If all else fails, you could the rig it for a tempfs scenario and deal with the all the issues that come with that tweak.

LHammonds

---

