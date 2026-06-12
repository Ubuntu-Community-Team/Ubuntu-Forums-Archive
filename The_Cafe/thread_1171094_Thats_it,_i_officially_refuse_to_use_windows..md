---
title: "Thats it, i officially refuse to use windows."
date: 2009-05-27
forum: The Cafe
---

### Post by Grukmuck on 2009-05-27
I decided to make the switch to Ubuntu several months ago, and the experience has been great so far. I had some problems with my laptop and the wireless connection, and some sound problems but so far thats it. So here is a lil back story to catch you all up on what I'm about to tell you. 

I love computers and electronics, but my curiosity always seems to get the better of me and I end up taking them apart and breaking them. Due to my ignorance, I lose screws, break unknown (to me anyway) components and tear ribbon cables. One of my class mates gets a real kick out of the all the electronics I have killed. Anyway, I had a laptop that I took apart and broke. The hard drive still worked and I decided that I would try and get my desktop to boot it up. After I bought an adapter I tried booting up and I got grub error 18. I looked up the error and found out it had something to do with the drive being larger than my desktop BIOS could handle. That didnt make sense to me because it was the same size as the one in the desktop. Anywho, I made the decision I didnt want the data on the laptop hdd anymore, so I was going to reformat it and put a fresh copy of XP on it (my college classes are teaching everything on XP so I wanted a copy to work with.) I put my copy of XP in and rebooted. Everything seemed to be going great. Suddenly a message displayed on the screen. It only lasted long enough for me to read most of it. I dont remember exactly what it said, but it basically was telling that the windows couldnt find an existing copy of windows on the hdd (even though XP was already on it) and that it was going to do something do it. I didnt catch what it said but it shut my computer down. Now the hdd is fried. I have no idea why or how, but thats the last straw for me. Im officially done with windows.

I was kind of excited about windows 7 and really wanted to give it a try, but this little debacle has changed my mind.

Has anyone else had this, or something similar happen to them?

-gruk

---

### Post by drawkcab on 2009-05-27
are you sure the drive didn't just fail?

---

### Post by pwnst*r on 2009-05-27
> **Grukmuck said:**
> I decided to make the switch to Ubuntu several months ago, and the experience has been great so far. I had some problems with my laptop and the wireless connection, and some sound problems but so far thats it. So here is a lil back story to catch you all up on what I'm about to tell you. 

I love computers and electronics, but my curiosity always seems to get the better of me and I end up taking them apart and breaking them. Due to my ignorance, I lose screws, break unknown (to me anyway) components and tear ribbon cables. One of my class mates gets a real kick out of the all the electronics I have killed. Anyway, I had a laptop that I took apart and broke. The hard drive still worked and I decided that I would try and get my desktop to boot it up. After I bought an adapter I tried booting up and I got grub error 18. I looked up the error and found out it had something to do with the drive being larger than my desktop BIOS could handle. That didnt make sense to me because it was the same size as the one in the desktop. Anywho, I made the decision I didnt want the data on the laptop hdd anymore, so I was going to reformat it and put a fresh copy of XP on it (my college classes are teaching everything on XP so I wanted a copy to work with.) I put my copy of XP in and rebooted. Everything seemed to be going great. Suddenly a message displayed on the screen. It only lasted long enough for me to read most of it. I dont remember exactly what it said, but it basically was telling that the windows couldnt find an existing copy of windows on the hdd (even though XP was already on it) and that it was going to do something do it. I didnt catch what it said but it shut my computer down. Now the hdd is fried. I have no idea why or how, but thats the last straw for me. Im officially done with windows.

I was kind of excited about windows 7 and really wanted to give it a try, but this little debacle has changed my mind.

Has anyone else had this, or something similar happen to them?

-gruk

hardware problem.  don't blame windows, thanks.

---

### Post by The Toxic Mite on 2009-05-27
> **drawkcab said:**
> are you sure the drive didn't just fail?

I think it's actually broken.

> **pwnst*r said:**
> hardware problem.  don't blame windows, thanks.

gruk, I was like you when I was a little bit younger. I was hoping to create some weird invention with all the parts I took out, but it never came to reality :P

---

### Post by MaxIBoy on 2009-05-27
Doesn't seem physically possible.


Anyway, you'll have a lot of fun with the various Linux distros, because you can do all kinds of insulting things to them, and they almost always still work. (No fair reinstalling a fresh copy!)

---

### Post by Tipped OuT on 2009-05-27
> **pwnst*r said:**
> hardware problem.  Don't blame windows, thanks.

+1.

---

### Post by The Toxic Mite on 2009-05-27
> **MaxIBoy said:**
> Doesn't seem physically possible.


Anyway, you'll have a lot of fun with the various Linux distros, because you can do all kinds of insulting things to them, and they almost always still work. (No fair reinstalling a fresh copy!)

LOL! I installed a copy of Ubuntu on a VM last night then I did the following terminal command:

```
[<censored>]("http://ubuntuforums.org/announcement.php?fhttp://ubuntuforums.org/announcement.php?f=11=11")
```... to test the severity of it, and it was pretty damning - background went and everything!

---

### Post by EmanresuusernamE on 2009-05-27
If you finished installing Windows, start mashing the F8 key after your BIOS screen fades to get the boot options.  Select Do not restart on system error, or something like that and windows should stop before it restarts itself.  

Also check your disk to see if it has scratches and make sure your BIOS is set to use SATA compatibility mode.  Windows XP can't detect the new SATAs sometimes if you don't install the drivers before you install XP.

Another thing you might try is starting up the recovery console from your Windows boot disk and then running chkdsk first, then "fixmbr C:", "fixboot C:" and then "bootcfg /rebuild"
I'm pretty sure that's the order those should be run in.  I've had a bunch of Windows problems I fixed like that with while here at my paid hobby.

If all else fails, refer to the old Windows 9x adage: "Reinstall Windows".

:D

---

### Post by lisati on 2009-05-27
<aside>One of my machines used to have XP on it. Other than troubles due to a virus (long story short: largely my fault) the nearest thing I can think of is when I first went to install SP3 on said machine. I'd installed all the updates for XP (updates are good, right?), restarted and went to install Ubuntu on the machine in its own partition. Something went wrong with the Ubuntu installation. So a lot of mucking around getting back to XP to do some troubleshooting from there, fixmbr and all that. Finally managed to get the XP boot screen up and running, but XP failed to complete its boot: it did a fine impression of being stuck in a restart loop. Initial reaction: blame Ubuntu!!!! Wrong answer! Turns out that this particular machine needed a patch to be applied before installing SP3. D'oh!</aside>

---

### Post by MaxIBoy on 2009-05-27
> **The Toxic Mite said:**
> LOL! I installed a copy of Ubuntu on a VM last night then I did the following terminal command:

```
[<censored>]("http://ubuntuforums.org/announcement.php?fhttp://ubuntuforums.org/announcement.php?f=11=11")
```... to test the severity of it, and it was pretty damning - background went and everything!But it still worked until you restarted, right? (I mean, just the parts that were already in memory.)

---

### Post by The Toxic Mite on 2009-05-27
> **MaxIBoy said:**
> But it still worked until you restarted, right? (I mean, just the parts that were already in memory.)

Nope - restarted the VM and I got GRUB Error 15

---

### Post by geogur on 2009-05-27
bout time you got it!

---

### Post by MaxIBoy on 2009-05-27
I said *until* you restarted. This is because Linux has the ability to run entirely from RAM.

---

### Post by The Toxic Mite on 2009-05-27
> **MaxIBoy said:**
> I said *until* you restarted. This is because Linux has the ability to run entirely from RAM.

Oh right - It was still running, but almost everything was gone.

When I tried clicking on one of the launchers on the panel, gnome-panel shut itself down, and the entire (VM) screen went grey, and the DMZ white pointer switched to a rather old-fashioned pointer. It was weird! :shock:

---

### Post by Grukmuck on 2009-05-28
Im pretty sure it wasnt a hardware problem because windows said it was doing something to the drive. I have decided to not be as upset with windows, though im still angry. I have come to the realization that no matter what, im still gonna need a working copy for one reason or another. Just because I have had too many problems with the OS doesnt neccessarily mean I have to stop using it all together. Windows holds over 90% of the marketshare and since im going to school to work with computers, I am gonna have to work with it.

since Im out of an extra drive to run windows, and I dont want to dual boot again, im going with virtualbox to run windows in. Im just gonna need to upgrade my memory for better performance.


-gruk

---

### Post by monsterstack on 2009-05-28
Y'know, this complaint sounds exactly like some of the reasons Windows users say they give up on Linux.

What can we learn from this? Installing an OS can be a nightmare if you don't have the right hardware, and it is a problem that affects all OSes. It is not generally a problem on Windows as manufacturers ensure they use compatible hardware and most Windows purchases are made when people buy a new PC with it pre-installed and pre-configured.

---

### Post by 73ckn797 on 2009-05-28
Drive broke, must replace.

---

