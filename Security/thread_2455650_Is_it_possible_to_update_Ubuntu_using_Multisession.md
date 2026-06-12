---
title: "Is it possible to update Ubuntu using Multisession DVD?"
date: 2020-12-24
forum: Security
---

### Post by empleat on 2020-12-24
Hello,

i am looking for a security solution. Therefore LiveCD. I was recommended to use Multisession DVD, so i can burn data to it - multiple times and i don't have to burn new DVD again each time - i want to download updates!

I was reading LiveCD section. But there is nothing about Multisession DVDs. I don't know how system update would even work on that! As doesn't system need to modify/delete some files and replace them. On a Multisession DVD: you can only burn additional data to a remaining free space, but you can't overwrite an existing data! I will also want to setup a ramdisk. Not sure if you could update system into a RAM - just for one session.

Thanks for help.

---

### Post by crip720 on 2020-12-24
Think I read that liveDVD/USBs with persistence, don't do updates, just keep data/software changes.  If you want updates without redoing the system each time, can think about installing Ubuntu on a USB.  Need two USBs, one for the installer and the other to install on. For security live DVD/USBs are used because they do not keep any changes after shut down.  Any malware is wiped.

---

### Post by empleat on 2020-12-25
> **crip720 said:**
> Think I read that liveDVD/USBs with persistence, don't do updates, just keep data/software changes.  If you want updates without redoing the system each time, can think about installing Ubuntu on a USB.  Need two USBs, one for the installer and the other to install on. For security live DVD/USBs are used because they do not keep any changes after shut down.  Any malware is wiped.
Problem is: whole point of using DVD, is eliminate threat of virus stored in firmware. They told me i should use multi-session DVD so i don't have to burn new one, each time there is an update. So there is no way to update system on Live CD? What about other distros?

---

### Post by CelticWarrior on 2020-12-26
No way. And who are "they"?
Using a DVD for that purpose seems a bad joke.

---

### Post by empleat on 2020-12-26
> **CelticWarrior said:**
> No way. And who are "they"?
Using a DVD for that purpose seems a bad joke.
It is usually hard to get straight answer, i would suppose that's a no. But it can mean many things...

Don't know, someone who did end user security study - told me that. 

So to the point:

1. Is there no way to update system to a ramdisk on LIVE CD???

2. Or is there no way to update system on a multi-session DVD, which was burned as LIVE CD???

3. Is this case too on other linux distros?

Yes, or no?

Also you probably don't need to update every small update. Not sure, on windows there are many small security updates coming every now and then. And to burn each time new DVD for that is annoying. I don't know even how to include updates into that, when burning ISO. A lot of things to figure out... And i couldn't find basically anything about this issue so far...

Thanks much.

---

### Post by CelticWarrior on 2020-12-26
NO, there is no way, obviously, and this has been explained to you more than once in another of your threads.
Again, > [COLOR=#000000]For security live DVD/USBs are used because they **do not keep any changes after shut down**.[/COLOR]

If you want to run Ubuntu or any Linux distro in external media, both USB flash drive or external USB HDDs or SSDs can be used. And you can do a normal installation in any of the aforementioned options. Any live media with or without persistence is NOT for normal usage.

> [COLOR=#000000]Problem is: whole point of using DVD, is eliminate threat of virus stored in firmware.[/COLOR]
You don't know what you're talking about. If you have been talking to "[COLOR=#000000]someone who did end user security study", a security expert supposedly, then very likely they didn't know or didn't factor in just how little you actually know and then went on rambling of theoretical issues no normal user cares about (because they don't happen outside of very specific industrial cyber-attacks).[/COLOR]

---

### Post by grahammechanical on 2020-12-26
Question: Is it possible to update a Live session of Ubuntu with persistence?

[https://askubuntu.com/questions/202218/can-i-update-a-live-usb](https://askubuntu.com/questions/202218/can-i-update-a-live-usb)

The answer seems to be yes. This can easily be put to the test.

Question: Can I create a live session of Ubuntu with persistence using a R/W DVD?

[https://askubuntu.com/questions/614088/can-you-make-a-live-dvd-persistent](https://askubuntu.com/questions/614088/can-you-make-a-live-dvd-persistent)

The answer seems to be yes but a USB memory stick will do it better. There are limits and complications with either of these choices.

A DVD that is Read/Writeable can be written to more than once. If the write session of a DVD -R disc is finalized it cannot be written to any more. If the write session is not finalized more data can be added until the disc is full. This is multi-session. Such a disc cannot be re-written. But would be useful for creating a permanent record of data covering a particular time period. Think, accounts records that should not be edited once the audit period has closed.

Regards

---

### Post by empleat on 2020-12-26
And what about RAM? Answer said, problem is you can't delete/modify files on DVD R. Which i was wondering too, whether or not: this is a problem. But can't you update system, just for one session into ram? It probably doesn't work like that, but i am just asking about every possibility. Otherwise, i will have to just burn new one after awhile... And i don't know how to include updates into ISO, major release like: 20.04.1, it probably isn't updated every time, some small update comes up. Or is it?

---

### Post by deadflowr on 2020-12-26
Updating a system running in RAM is limited to only updates that can be applied immediately.
Updates that require a reboot cannot be applied in RAM.
Those mostly apply to kernel updates or services which would more or less be too inconvenient or too complex to simply reload.

---

### Post by empleat on 2020-12-26
> **deadflowr said:**
> Updating a system running in RAM is limited to only updates that can be applied immediately.
Updates that require a reboot cannot be applied in RAM.
Those mostly apply to kernel updates or services which would more or less be too inconvenient or too complex to simply reload.
I see, so will have to burn new dvd after awhile to get new updates. How do i include updates into ISO burned to DVD? And i would also like burn ramdisk to it, so when i boot it is installed, for installation of programs etc.

Thanks!

---

