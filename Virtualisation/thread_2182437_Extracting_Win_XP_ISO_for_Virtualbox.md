---
title: "Extracting Win XP ISO for Virtualbox"
date: 2013-10-21
forum: Virtualisation
---

### Post by avantgardaclue on 2013-10-21
Hi guys, I have one program I need to use which is a Win XP prog. I can't get it to work on Wine.

So installed Virtualbox and dug out my old Win XP disk.

OK that's as far as I've been able to get!

Is there a simple procedure to create an XP iso that can be installed into Virtualbox? Or is there a fundementally easier way to achieve what I'm trying to do?

I don't really want to sully this PC with a windows partition!

Hey ho, advice gratefully received!

---

### Post by JKyleOKC on 2013-10-21
> **avantgardaclue said:**
> Is there a simple procedure to create an XP iso that can be installed into Virtualbox? Or is there a fundementally easier way to achieve what I'm trying to do?Is the XP disk a CD? If it is, you can use the "dd" command from a terminal to create an ISO file from it. Assuming that your cd drive is /dev/sr0, the command is ```
dd if=/dev/sr0 of=$HOME/xp.iso
```Best use copy and paste for this command to be sure you don't add any extra spaces. An added space after "$HOME" could cause it to destroy your home directory!

Of course the CD must be in the drive. It will take a couple of minutes, and there's no progress bar, but I've used this to copy quite a few installation CDs into my home directory...

You can use "ls -l /dev | grep cd" to verify the name that /dev uses for your cd; "sr0" is what mine shows (among others).

---

### Post by KillerKelvUK on 2013-10-21
Hi, the Brasero app which comes with Ubuntu can rip a CD/DVD to an .iso file with ease (copy disk option-->image file), there are other ways to do this also using the CLI and dd, google away as you desire.

However you should be able to get Virtualbox to read the disk that's in your drive and install from that without needing to rip it to an .iso first.

---

### Post by avantgardaclue on 2013-10-21
> **JKyleOKC said:**
> Is the XP disk a CD? If it is, you can use the "dd" command from a terminal to create an ISO file from it. Assuming that your cd drive is /dev/sr0, the command is ```
dd if=/dev/sr0 of=$HOME/xp.iso
```Best use copy and paste for this command to be sure you don't add any extra spaces. An added space after "$HOME" could cause it to destroy your home directory!

Of course the CD must be in the drive. It will take a couple of minutes, and there's no progress bar, but I've used this to copy quite a few installation CDs into my home directory...

You can use "ls -l /dev | grep cd" to verify the name that /dev uses for your cd; "sr0" is what mine shows (among others).

Hmmmm, this looks a bit scary for me!! But thanks anyway

---

### Post by avantgardaclue on 2013-10-21
> **KillerKelvUK said:**
> Hi, the Brasero app which comes with Ubuntu can rip a CD/DVD to an .iso file with ease (copy disk option-->image file), there are other ways to do this also using the CLI and dd, google away as you desire.

However you should be able to get Virtualbox to read the disk that's in your drive and install from that without needing to rip it to an .iso first.

So simple when you know, many thanks.

Anyhow, despite being my old XP disk from 10 odd years ago naturally it wont accept any product keys as it looks like it is a Dell OEM installation and is tied to that machine.

Hey ho!

---

### Post by avantgardaclue on 2013-10-21
At the point of giving up on this so uninstalled the installed wine and reinstalled the latest ver direct from wine, 1.7 something and.... it bloody well works on the program that was previously not working! Hooray. Now how do I get back the afternoon that has been lost to me! Actually knowledgewise I have learnt something new, so thanks for that!!

---

### Post by TheFu on 2013-10-23
> **avantgardaclue said:**
> At the point of giving up on this so uninstalled the installed wine and reinstalled the latest ver direct from wine, 1.7 something and.... it bloody well works on the program that was previously not working! Hooray. Now how do I get back the afternoon that has been lost to me! Actually knowledgewise I have learnt something new, so thanks for that!!

Glad you got it working.  Always check **winehq** for the status and any tricks to get any specific program working.

---

### Post by SeijiSensei on 2013-10-23
Just thought I'd mention that VirtualBox can boot directly from the CD/DVD drive as well as an ISO image.

---

