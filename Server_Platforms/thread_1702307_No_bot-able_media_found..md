---
title: "No bot-able media found."
date: 2011-03-07
forum: Server Platforms
---

### Post by Rivin2e on 2011-03-07
compaq presario sr2150nx <-- my computer.

[http://tinyurl.com/45bb5hv]("http://tinyurl.com/45bb5hv") <-- its specs.

NO operating system but vista home appears to work with this computer. I know my CD/DVD im burning server 10.10/04 (have tried both) work, the HDD is bran new and works in my other server and desktop.

Any input would be much appreciated. Im willing to give any other info needed assuming i can find it.

------
Using google ive found you can downgrade to windows xp... but does that also mean ubuntu as well?

--------
EDIT:

On boot. this is there error the computer give me.

"Reboot and Select proper Boot device. or Insert Boot Media in selected Boot device and press a key"

caps and everything...

---

### Post by arrrghhh on 2011-03-07
Sounds like the BIOS isn't picking up the CD.

Do you have the CD listed in the boot section of your BIOS?  This really isn't a problem with Ubuntu per se, but the settings on your machine (BIOS).

Some PCs have a "boot menu" option as well, so you can choose which device to boot from on the fly without modifying any BIOS settings.

---

### Post by Rivin2e on 2011-03-07
> **arrrghhh said:**
> Sounds like the BIOS isn't picking up the CD.

Do you have the CD listed in the boot section of your BIOS?  This really isn't a problem with Ubuntu per se, but the settings on your machine (BIOS).

Some PCs have a "boot menu" option as well, so you can choose which device to boot from on the fly without modifying any BIOS settings.

Its found the CD and everything, will go through ALL the install processes on every OS CD ive given it.. but will only boot up in vista home.

---

### Post by arrrghhh on 2011-03-07
> **Rivin2e said:**
> Its found the CD and everything, will go through ALL the install processes on every OS CD ive given it.. but will only boot up in vista home.

If it found a **valid **Ubuntu boot disk, you wouldn't get the error "Reboot and Select proper Boot device. or Insert Boot Media in selected Boot device and press a key".

So it's either not picking up the CD like you say, or that disc is bad in some way shape or form.

---

### Post by Rivin2e on 2011-03-07
> **arrrghhh said:**
> If it found a **valid **Ubuntu boot disk, you wouldn't get the error "Reboot and Select proper Boot device. or Insert Boot Media in selected Boot device and press a key".

So it's either not picking up the CD like you say, or that disc is bad in some way shape or form.

HDD and disks work on other computers, All are valid, the computer has been determined the only thing causing a problem.

---

### Post by arrrghhh on 2011-03-07
> **Rivin2e said:**
> HDD and disks work on other computers, All are valid, the computer has been determined the only thing causing a problem.

Since you've got it all figured out, why do you need help?

---

### Post by Rivin2e on 2011-03-07
> **arrrghhh said:**
> Since you've got it all figured out, why do you need help?

Why does the computer not boot into ubuntu if others will? what is causing this. its not disks or HDD

---

### Post by arrrghhh on 2011-03-07
> **Rivin2e said:**
> Why does the computer not boot into ubuntu if others will? what is causing this. its not disks or HDD

RAM?  BIOS?  There's a ton of reasons, hardware support for some particular piece on the mobo?  Who knows.  Did you test it with a livecd first to see if the hardware would work under Linux?

---

### Post by Rivin2e on 2011-03-07
> **arrrghhh said:**
> RAM?  BIOS?  There's a ton of reasons, hardware support for some particular piece on the mobo?  Who knows.  Did you test it with a livecd first to see if the hardware would work under Linux?

Would have been the smart thing... ill do that, post results

----
EDIT:
If i did it right... it will run from the CD and from a USB (tried just for kicks) but wont boot of the HDD still.

---

### Post by Rivin2e on 2011-03-08
Bump. I still need help on this =(

Other things ive done, Ive downloaded a chipset for the motherboard, got it to run xp. Still no ubuntu.

---

### Post by arrrghhh on 2011-03-08
> **Rivin2e said:**
> Bump. I still need help on this =(

Other things ive done, Ive downloaded a chipset for the motherboard, got it to run xp. Still no ubuntu.

Try a fresh install... not sure what else you could be doing wrong TBH, unless there was a step you were skipping on the install like GRUB?  Are you setting the boot flag as well?

---

### Post by Rivin2e on 2011-03-08
> **arrrghhh said:**
> Try a fresh install... not sure what else you could be doing wrong TBH, unless there was a step you were skipping on the install like GRUB?  Are you setting the boot flag as well?

Just finished downloading ubuntu server 10.10 and burning it to a CD again, installed, installed GRUB, still same error =/ 

Ive never had this problem before... really bites...

---

### Post by arrrghhh on 2011-03-08
> **Rivin2e said:**
> Just finished downloading ubuntu server 10.10 and burning it to a CD again, installed, installed GRUB, still same error =/ 

Ive never had this problem before... really bites...

You've checked all the settings in the BIOS?  It's trying to boot from the correct HDD yes?

Really seems like the BIOS isn't picking up the right disk, or the disk with GRUB on it isn't set with the bootable flag.

I guess I should've asked, you don't have a RAID array do you?

---

### Post by Rivin2e on 2011-03-08
> **arrrghhh said:**
> You've checked all the settings in the BIOS?  It's trying to boot from the correct HDD yes?

Really seems like the BIOS isn't picking up the right disk, or the disk with GRUB on it isn't set with the bootable flag.

I guess I should've asked, you don't have a RAID array do you?

No raid, dont know how to set that up in ubuntu... or at all... But no its just one HDD. 

Im guessing the BIOS isnt picking up GRUB... or anything other then vista =/

---

### Post by arrrghhh on 2011-03-08
> **Rivin2e said:**
> No raid, dont know how to set that up in ubuntu... or at all... But no its just one HDD. 

Im guessing the BIOS isnt picking up GRUB... or anything other then vista =/

I'm still sticking to BIOS settings, unless someone else has another suggestion.  Without actually being able to troubleshoot myself, that's going to be my bet for the source of the problem.

---

### Post by Rivin2e on 2011-03-08
> **arrrghhh said:**
> I'm still sticking to BIOS settings, unless someone else has another suggestion.  Without actually being able to troubleshoot myself, that's going to be my bet for the source of the problem.

What would i check for in the BIOS settings? only thing OS wise is 'plug and play OS' and i have my boot priority, HDD, CD (empty), floppy (not even installed).

---

### Post by arrrghhh on 2011-03-08
> **Rivin2e said:**
> What would i check for in the BIOS settings? only thing OS wise is 'plug and play OS' and i have my boot priority, HDD, CD (empty), floppy (not even installed).

Boot priority, and hard disk configuration.  Order of hard disk appearance is important as well - although I would hope you pulled any additional disks for troubleshooting...

---

### Post by Rivin2e on 2011-03-08
> **arrrghhh said:**
> Boot priority, and hard disk configuration.  Order of hard disk appearance is important as well - although I would hope you pulled any additional disks for troubleshooting...

Only had one HDD anyways. Unplugged everything else as well.. still nothing =/

---

### Post by arrrghhh on 2011-03-08
> **Rivin2e said:**
> Only had one HDD anyways. Unplugged everything else as well.. still nothing =/

Same error?  Perhaps that rig doesn't like that hdd... I'm out of ideas.  Try a different hdd, if you're convinced the BIOS settings are indeed correct...

---

### Post by Rivin2e on 2011-03-08
> **arrrghhh said:**
> Same error?  Perhaps that rig doesn't like that hdd... I'm out of ideas.  Try a different hdd, if you're convinced the BIOS settings are indeed correct...

Just tried 2 different HDD that i know run ubuntu on other computers. Still the same error.

---

### Post by arrrghhh on 2011-03-09
> **Rivin2e said:**
> Just tried 2 different HDD that i know run ubuntu on other computers. Still the same error.

If it's not the BIOS, I have no clue to be honest.  It definitely sounds like there's a misconfiguration in there...

---

