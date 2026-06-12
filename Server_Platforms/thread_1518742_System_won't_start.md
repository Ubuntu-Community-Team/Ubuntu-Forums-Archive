---
title: "System won't start"
date: 2010-06-27
forum: Server Platforms
---

### Post by happyhacker on 2010-06-27
I cannot see my server on the network. I had to repair the hda1 with GParted and that ran OK. I intend to reload the latest server but I need to get at a backup folder (hdb1) on the drive. When the system starts now there are many errors reported e.g bad sectors and Apache [FAIL] etc.

When I put in the Ubuntu live cd and go to open the hdb1 - a second drive where I keep the backups (but was mounted from a folder on hda1 but not suer where Ubuntu live mouts it), I get the message "Device is mounted and no online capability in fsck tool for filesystem". If I open GParted and unmount the drive it disappears from the browser. The drive (ext3) is reported as OK.

How do I get the files off to USB drive?

PS alternatively if I reinstall Ubuntu server will that drive then become available with the old (Client PC) backups preserved?

---

### Post by CharlesA on 2010-06-27
If you don't format that partition during the reinstall, the data will still be there.

Also, what version of Ubuntu are you using? They switched everything to using sdxx a while ago.

If you boot off a livecd and run the *mount* command from a terminal, that will tell you where everything is mounted.

---

### Post by robsoles on 2010-06-27
Hey, if you have SATA drives you will see SDA, SDB, SDA1 etc etc. If you have IDE drives then you will see HDA, HDB, HDA1 etc etc - don't rush into thinking what you see in your /dev/ directory makes the contents of other people's /dev/ directory wrong or outdated!

Boot off the LiveCD and checkout the contents of your hard drive(s)! Too easy!

Also easy enough to gain network access and copy/backup vital files to a remote location - if wondering, vital files are stuff you make or download that you can't easily remake or re-download, if it comes off the installation CD/DVD then it is far from vital (unless you broke the CD/DVD!)

I should be subscribed by posting this, lemme know how that goes for you.

---

### Post by koenn on 2010-06-27
nope, CharlesA is right, Ubuntu has been using a unified driver for scsi, ide and sata drives, with sd_ device names for quite a while now (since the 07 or 08 releases, i think)

---

### Post by robsoles on 2010-06-27
> **koenn said:**
> nope, CharlesA is right, Ubuntu has been using a unified driver for scsi, ide and sata drives, with sd_ device names for quite a while now (since the 07 or 08 releases, i think)

Wow, I'd almost swear that when I had an IDE drive in my current PC under 10.04 LTS about a month ago it was in /dev/ as hda with it's two partitions as hda1 and hda2 but maybe I just didn't check that closely and I am just used to it being that way.

Actually, I think it's kinda fried (Whether the Debian developers or Canonical or even Berkeley did it) if they've done as you say just due the differences in architecture being a good enough reason to keep them as seperate device types under /dev/

 I'm going to have to grab that IDE drive back off my kid's machine for a few minutes and see - I'll do it straight away and post my apology if I see it with my own eyes.

---

### Post by robsoles on 2010-06-27
> **robsoles said:**
> ...

 I'm going to have to grab that IDE drive back off my kid's machine for a few minutes and see - I'll do it straight away and post my apology if I see it with my own eyes.

I apologise.

I can't see a 'value add' from this being done, more a loss at not being able to spot HDD architecture of a closed case at a glance in /dev/ - I think I will have to check exactly who has done this and if it's just Canonical I will look for a new favorite distro!

Um, seems a more relevant question to me now: What is that LiveCD you are booting from? LiveCDs that are capable of a GUI/Desktop usually list my partitions under 'Places' with a complete ability to mount them without having to refer to a terminal.


Here is my edit: When your server crashes or otherwise won't boot you can use a 'desktop flavored' LiveCD to see what is going on with your system using a GUI - just don't install from it if you really want a 'server flavored' machine.

---

### Post by koenn on 2010-06-27
> **robsoles said:**
> I apologise.

It's called 'abstraction of the undelying hardware', i.e. your OS doesn't need to know the technology used in storage devices, and neither do you. After all, it's just an arbitrary name.
Compare to RAID, LVM, SAN, ... technology : you have no idea where your file is anymore.  
Streamlining those things probably made sense from a dev POV.

---

### Post by robsoles on 2010-06-27
To the guy that just made a mobo h/w raid(1=mirror) work and had to find /dev/mapper/'insert-crazy-string-here' to get all the data in the right place to have the company's data in a mirrored raid (without breaking it by copying to sda nor sdb) it makes plenty of difference.

I may not exactly need to know diddly squat in most other circumstances but it sure is nice to be able to see stuff without having to undo screws!!!

This is edit: I hate that M$ hide lots of very relevant info from the end user in the name of simplification of Windoze, now I hate some hint of it in Ubuntu too!!!

---

### Post by koenn on 2010-06-27
yeah, whatever.
If you need to rely on an arbitrary symbolic name to know what your system is build off, you got other issues.

---

### Post by happyhacker on 2010-06-28
OK, a bit more info (no one seems to have locked on to the error message I got). When I boot from the live CD I have 3 drives available, a 40Gb = hda, a 80Bb = hdb (the one I cannot access) and a USB 60Gb drive. I can initially see the hdb on the "other places listed with the others (and according to GParted it is mounted). When I click on it to see the folders it just disappears and is no longer listed. The drive has only about 5Gb left of free space as it was used to backup some 15 windows PCs and I want to get access to those backups. I tried to GPart the free space to perhaps nudge the system into access the drive and although that worked (I shrunk the partition by 1Gb) same problem exists. PS I can browse hda.

Now, when I try to boot normally (Not Live CD) I notice now that the boot keeps reporting that something is read only and that it cannot write! So I assume hda is also corrupt in some way and maybe also this is preventing hdb from being available. I have tried to look at logs but have not found any (no write capability during boot?)!

Maybe there is something I can check/tweak on hda with the live CD?

---

### Post by robsoles on 2010-06-28
> **cantthinkofanickname said:**
> ... (no one seems to have locked on to the error message I got). ...

Maybe there is something I can check/tweak on hda with the live CD?

I apologise to you direct, complicated nickname after all.

Can you download a recent LiveCD of 10.04 Desktop, I understand you may want to grab 8.04 or 10.04 Server but with 10.04 Desktop you are in a better position to play with your drive - at least confirm which iso's you have and have burnt onto discs.


With a desktop session you can open 'System'->'Administration'->'Disk Utility' and from there you will probably be able to drive what you are looking at well enough to do filesystem check and ultimately mount the drive you want data from as read/write - although if you have read only access then you should be able to get the data to a 'safe' drive like your USB anyway.

Please tell us what LiveCD(s) you have buddy.



Ps: That's Ok Keonn, my networks and websites all think you got bigger problems than me too: I sys admin at work and take care of several websites for a bunch of poor buggers you no doubt think must be screwed to rely on me.

---

### Post by CharlesA on 2010-06-28
You could try to do a fsck on hda1 from the livecd and see if it finds any errors. 

If it's mounting the file system as read only, something is defintiely wrong.

As a general rule of thumb, never mess with partitions unless you have the data backed up.

---

### Post by robsoles on 2010-06-28
> **CharlesA said:**
> ... 

As a general rule of thumb, never mess with partitions unless you have the data backed up.

Now I've had plenty of truth serum (beer), CharlesA here is the only one who didn't make a c___ of himself, pay more attention to him than me or keonn. Although I will stick by my 'GUI (Graphical User Interface = '''Desktop''') LiveCD' should be easier, anyday - drunk or sober, to find out what is wrong with a HD_ or SD_ 'whatever' you actually got :lolflag:

Ps: (Intended for O/P: ) What is that LiveCD you have that lists 'HDA' - Oh please I gotta know!!!

---

### Post by happyhacker on 2010-06-28
> **robsoles said:**
> Can you download a recent LiveCD of 10.04 Desktop, I understand you may want to grab 8.04 or 10.04 Server but with 10.04 Desktop you are in a better position to play with your drive - at least confirm which iso's you have and have burnt onto discs.

With a desktop session you can open 'System'->'Administration'->'Disk Utility' and from there you will probably be able to drive what you are looking at well enough to do filesystem check and ultimately mount the drive you want data from as read/write - although if you have read only access then you should be able to get the data to a 'safe' drive like your USB anyway.

Please tell us what LiveCD(s) you have buddy.

Thanks I have the Live you quote. I have now mounted the hdb1 and can see the files. However I cannot copy or move it. It says "You do not have permission to read this file". I do not know how to get to user 1000 (which it says owns this drive (or its folders/files)). I am ready to copy it's whole 75Gbyte to my USB drive but don't know how.

How do I get the data moved if the OS (server 8.04 I think) will not boot?

The PC only has a CD ROM so if I installed a server or desktop version of Ubuntu would I then be able to read/write it?

---

### Post by robsoles on 2010-06-28
Ok, you can mount the partition and it will most likely be under /media in the file system you are playing and so will your USB drive.

Open terminal (Applications->Accessories->Terminal)

Type in; 

# cd /media
# ls

Look at the response and try to identify which is your USB drive and which is the drive you want files from, using 'myusbdrive' and 'this-bizarre-string-of-numbers' as example details use the following command to copy the files:

$ sudo cp -R this-bizarre-string-of-numbers myusbdrive

That should work a beauty but I won't be surprised if something manages to gag about it - please let me know.


If you intend to use this drive in the new installation then there is an OK chance you don't have to format this partition but the files will belong to the wrong user - that is 'fixable', after installing and keeping this partition intact just use simily of following command syntax:

$ sudo chown -R me:mygroup /that-directory-with-my-old-files

but replace words 'me' with your new username, 'mygroup' with your group and '/that -directory-with my-old-files' with the directory name of these user locked files.


When you use 'sudo' on the livecd it shouldn't prompt for a password, when you use 'sudo' in a fresh install it will prompt you for the password you logged in with.

> **cantthinkofanickname said:**
> ...

The PC only has a CD ROM so if I installed a server or desktop version  of Ubuntu would I then be able to read/write it?

If the PC literally only has a CD ROM then you won't be able to install to it, I think you mean that it doesn't have a DVD ROM so I have to answer that once you install from the LiveCD to a HDD the system that boots off the HDD will be all read/write unless something nasty goes wrong with it!

---

### Post by CharlesA on 2010-06-28
> **cantthinkofanickname said:**
> Thanks I have the Live you quote. I have now mounted the hdb1 and can see the files. However I cannot copy or move it. It says "You do not have permission to read this file". I do not know how to get to user 1000 (which it says owns this drive (or its folders/files)). I am ready to copy it's whole 75Gbyte to my USB drive but don't know how.

How do I get the data moved if the OS (server 8.04 I think) will not boot?

The PC only has a CD ROM so if I installed a server or desktop version of Ubuntu would I then be able to read/write it?

If you have 75GB of data, you would need to copy it to another hard drive, using anything else would be a pain in the butt. If you've got another machine on the network, you can connect to it and throw the data on it, then move it back after the system is reinstalled.

Best bet would be to do that. If you don't have another machine, I'm not sure what you will be able to do.

---

### Post by robsoles on 2010-06-28
> **CharlesA said:**
> If you have 75GB of data, you would need to copy it to another hard drive, using anything else would be a pain in the butt. If you've got another machine on the network, you can connect to it and throw the data on it, then move it back after the system is reinstalled.

Best bet would be to do that. If you don't have another machine, I'm not sure what you will be able to do.

Although I don't disagree with your networked solution I feel inclined to point out that I have USB cage capable of 'nursing' SATA and IDE 3.5" drives which transfers faster than a network at 100Mbps and only a little slower than a Gigabit connection.

---

### Post by CharlesA on 2010-06-28
> **robsoles said:**
> Although I don't disagree with your networked solution I feel inclined to point out that I have USB cage capable of 'nursing' SATA and IDE 3.5" drives which transfers faster than a network at 100Mbps and only a little slower than a Gigabit connection.

Those work too. :) Altho, if you are stuck using USB 1.1,  it's going to go insanely slow even compared to 100Mbps connection.

I was under the impression that the OP didn't have an external drive handy, but if they did, that would probably be the best option.

---

