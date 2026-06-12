---
title: "Hooked up a classmate today"
date: 2007-02-21
forum: Testimonials &amp; Experiences
---

### Post by sgardne on 2007-02-21
I'm a computer tech at my day job, but I go to university classes as well, and today a guy who I've been partnering up with for lab was very depressed because his XP box barfed up a blue screen, and he couldn't get his homework off it. I asked him if he had an XP disk he could use to check the system and maybe repair it, but he said it was hundreds of miles away at his parents house. 

I happened to have a Dapper disk in my folder, so I gave it to him and told him to use it to boot his computer and how to back up his files. Anyway, I just got an email from him, that I thought I'd share. This message makes it obvious that he is not a computer savvy person, so it really struck me as ironic. Anyway, here it is:

[INDENT]subject	 thanks 
thanks a ton for letting me use the linux live or whatever its called. It feels awesome actually being able to use my computer.[/INDENT]

That put a big smile on my face. 

:D

---

### Post by JTP on 2007-02-21
At the risk of sounding like the linux noob I am, I'm curious about something here.  I've got an early Pentium4 Gateway running a now deceased version of Windows ME, but I need to save the pictures on it for my parents (since it is their old computer).  In the scenario you described, how do you go about backing up the existing files on the computer using the live dapper (or edgy) disc?  I'm stuck in DOS and don't want to mess with trying to get DOS to recognize a flash drive for the purposes of transferring the files.

Thanks in advance.

---

### Post by dasunst3r on 2007-02-21
[LIST=1]
[*]Make sure you have a USB hard drive or a pen drive.
[*]Go into your BIOS and make sure the first boot device is your optical drive (CD drive)
[*]Pop in the Ubuntu LiveCD and boot up the computer
[*]Open your terminal and mount your drive.  The command is typcailly:
```
sudo mkdir /mnt/src
sudo mount -t vfat /dev/hda1 /mnt/src
```
For more information about the command, type *man {command}*
[*]Open up navigation windows for your USB drive and your source drive
[*]Copy away!
[/LIST]

---

