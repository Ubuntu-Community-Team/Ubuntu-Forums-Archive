---
title: "Do viruses migrate?"
date: 2010-05-12
forum: Security
---

### Post by ImageAcoustique on 2010-05-12
Hi,
a friend of mine, whom I haven't managed to convince in migrating to Linux yet, has a Pc that runs Windows Xp. His machine is full of viruses and, everytime I copy files from his laptop with a Usb stick, file names change and sometimes they get corrupted and don't work any longer after I pass the Usb stick to my Pc. I was wondering whether the viruses are actually doing any harm to my machine or not.

---

### Post by lisati on 2010-05-12
> **ImageAcoustique said:**
> Hi,
a friend of mine, whom I haven't managed to convince in migrating to Linux yet, has a Pc that runs Windows Xp. His machine is full of viruses and, everytime I copy files from his laptop with a Usb stick, file names change and sometimes they get corrupted and don't work any longer after I pass the Usb stick to my Pc. **[COLOR="Red"]I was wondering whether the viruses are actually doing any harm to my machine or not.[/COLOR]**

Probably not. Many (most?) viruses are aimed at Windows, and in the unlikely event that they would work with Ubuntu, they'd usually need your permission to do their mischief.

---

### Post by ImageAcoustique on 2010-05-12
Ok. But why do files change their names, get corrupted or disappear? The first time I plug in the stick, nothing happens. When I connect it the second time I always have some surprises. And eventually I have to format it.

---

### Post by OpSecShellshock on 2010-05-12
The reason the files get altered is because their types are recognized by both Windows and Linux. The drive itself is also probably formatted in a type that works on both. The malware is probably searching for files of a certain type and then appending its code to everything it finds. It depends on what the malicious binary file type is, but in most cases while its mounted on Windows it will do everything it's designed to do. When you mount it on your Linux system, the file type of the malware might not be recognized (it's hard to say without knowing what it is/does). However, any files that you've carried over from your friend's machine to your USB drive, and any files on that drive that were infected by the new files, will remain infected once you copy them over to your machine. They won't hurt you, but if you pass them along to a Windows system they'll probably run.

---

### Post by ImageAcoustique on 2010-05-13
Ok. So that means that, in a way, viruses do work, even in waht isn't their "natural environment". You're right: I format the USB key in FAT 32, readable by both. Is it possible to analyze my files and see if they got corrupted somehow? Should I use an antivirus?
Moreover, why Windows viruses don't work under Linux? Is it only because of the permission thing? Or because of the different file system, too? Would it be possible to develop a cross virus that could work in both the environments? (I don't want to make one...) And one that works for ALL OSs?

---

### Post by OpSecShellshock on 2010-05-13
There's not really any way to do cross-platform malware, at least if you're targeting the OS, for the same reason that legitimate software has to be compiled differently for each OS it runs on. Now, if it's running entirely in the browser or is Java-based I suppose that's kind of possible. But even that's not going to be persistent on Linux unless the user installs something--which is always a manual process on Linux to an extent. As long as you don't run the browser or other network-accessing applications under elevated privileges there's no way for something to get automatically and silently dropped like there is with Windows.

Ultimately most malware is written to use .exe files and/or to infect .dll files at least at some point in the process. Some will also try to make changes to the registry. All of those things are exclusive to Windows.

If the act of copying files from your friend's computer to your USB drive caused all of the files already there to be altered, then you'll be dealing with a worm. It won't subsequently alter files on your Linux disk, nor will its code run. However, it can be passed to any Windows machine you connect the drive to from now on. To stop that you should format the drive and restore the files from known-clean backups.

---

### Post by koanhead on 2010-05-13
Inasmuch as the Windows machine is known to be compromised, I would recommend booting it from a live CD in order to accomplish the file transfers. That way whatever infections / exploits are present will not get a chance to run, and the files (hopefully) will not be modified.

---

### Post by ImageAcoustique on 2010-05-13
I wish I could convince my friend to let me put a Live Cd! There's no chance, he's lost in Windows...

---

### Post by Wistful on 2010-05-14
> **ImageAcoustique said:**
> I wish I could convince my friend to let me put a Live Cd! There's no chance, he's lost in Windows...

Why the heck he would not allow you to help him? You're just booting of a LiveCD which won't do any damage or modifications AT ALL, is your friend 'nuts' or just a 'computer layman', hmm ? :confused:

---

### Post by zexelon on 2010-05-14
Yes, I would recommend the LiveCD approach also. It will not affect the computer in any manner and would definitely be the safest way to back files up off the machine, short of pulling the drive out. 

Also as was said earlier, any virus written for a windows environment (basically this covers 99% of the viruses out there) will not run in a Linux environment so you are safe. However once you do back up your friends files make absolutely certain you virus scan your usb stick before you put it in any other computer, or even back into your friends computer after he re-installs. 

Many windows based viruses can and do migrate and it could re-infect your friends machine if the virus transfers over to the usb stick.

---

### Post by ImageAcoustique on 2010-05-14
He's just lazy... He doesn't want to learn more about PCs..

---

### Post by Chayak on 2010-05-14
I work with malware for a living.  The forensic approach of digging it out it taking longer because of more sophisticated hiding techniques.  Tell your friend that if he doesn't want to be part of a botnet and/or have every personal detail he enters in the computer to be sent off to someone he needs to let you get his data off using a live CD and then reinstall his machine.

---

