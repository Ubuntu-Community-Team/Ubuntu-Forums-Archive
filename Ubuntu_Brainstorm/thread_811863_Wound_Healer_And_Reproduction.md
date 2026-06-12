---
title: "Wound Healer And Reproduction"
date: 2008-05-29
forum: Ubuntu Brainstorm
---

### Post by msidhard on 2008-05-29
There should be a wound healer for corrupted files. which replaces a fresh file instead of a corrupted. the healer should able to produce files for  hardware change and capable of running os in any drastic condition. it replace with main backup OF os

---

### Post by msidhard on 2008-05-29
The Aim Is Survival Of Fittest. The Wound Healer Should Capable Of Reproduction As Live Or Alternative Bootable Cd. The Installer After Installation Could Be Used As Wound Healer With Some Alterations In It Wound Healing And Reproduction Makes It Living.

---

### Post by Mr.Macdonald on 2008-05-29
good, but unless you are a complete moron (or tester) and mess around with important files then you should be ok without it. and their is something like that, synaptic has a broken package fixer thing that is useful.

I also don't feel like sticking the cd back in to fix it, i would just use apt-get of dkpg (think i spelled it right) to see packages that might need to reinstalled.

i hope that programs would be able to fix themselves with a basic internet connection, by downloading broken or missing files(i don't know if this is possible, just what i would try and do)

---

### Post by gnomeuser on 2008-05-29
So you are proposing we invent a scheme to repair unknown damage of random data, in random segments based on their checksum not matching.

How are we supposed to know if a 0 or a 1 is correct? Bruteforce it.. that could take decades.

If I understand the suggestion correctly there is no way to make this work - impossible (within reasonable parameters).

---

### Post by msidhard on 2008-05-30
My Focus Is On  The Files Relating To Step 3 To Step 6 Of Booting In To Graphic User Interface. After Getting In To Gui We Can Do Any Thing Because It Supports Multi Tab Facility But  The Command Prompt Does Not Supporting It.

---

### Post by gnomeuser on 2008-05-30
> **msidhard said:**
> My Focus Is On  The Files Relating To Step 3 To Step 6 Of Booting In To Graphic User Interface. After Getting In To Gui We Can Do Any Thing Because It Supports Multi Tab Facility But  The Command Prompt Does Not Supporting It.

You sadly still make no sense, also your shift key seems to be full of fail

---

### Post by msidhard on 2008-05-31
i frequently use my mobile to browse. thats my hobby. so there is some problem in caps on and caps off. the matter what i meant was the healer should cure the corrupted files and enable to log in to graphic user interface. the error crroction is much easier than correcting in root@terminal.:)

---

### Post by insane_alien on 2008-06-01
and how do you propose we implement the error correcting.

if it is just a hash of the file then it will fail. it would have to brute force the creation of the new file. it would take forever, not to mention there would be a large number of files that would produce the same hash.

if you use an error correcting code like on CD's then what do you do if a block is so damaged that it can't be repaired?

what do you do if a vital part of the error correcting mechanism is so damaged that it is unusable?

there are so many issues with this. mostly physical limits.

Edit: i was thinking about this at work actually, and i thought of a way to make it sort of manageable -ish its not quite the same idea.

you have a live USB that you boot up when you have a working system, it takes a snapshot of critical static(i won't work so well with dynamic files) files(eg, kernel, config files) and produces their MD5 sums, when the system gets corrupted, you boot the live USB and it checks all the files it has snapshots of and replaces them if there is a hash mismatch. dynamic files will have to come from a backup though, maybe the functionality can be added for it to pull those files from a mirror that is kept up to date, or the usb could be a permanent attachement.

---

### Post by yelo3 on 2008-06-02
using
apt-get --reinstall install package_name
could be an idea

---

### Post by billenbois on 2008-06-04
this is what windows do with SFC (system file checker) by default. it keeps an extra copy of the files in cache at all time and when the original is replaced/changed by any means, it overrides it with the copy.

Now, I don't really think it's a good idea (its complicated, not very logical, you replace a file and puff.. its gone..)

Faulty hardware could corrupt the cached version anyway :/

---

### Post by msidhard on 2008-06-05
ya i accept it but the sfc has file name if it thinks the file is corrupted then it replaces the thing with a windows original cd or replaces from its back up . i need a thing like sfc which replaces the corrupted files with the ubuntu cd or from its back up. it can replace and makes the system more stable. what i say was there should be a application which installs new files like sfc. In windows if u put the bootable cd of same version it asks for upgrade . the upgrade replaces the corrupted registry and then the corrupted files. it is like upgrade of same version and replace of corrupted files without  reinsallation.:guitar:

---

### Post by billenbois on 2008-06-06
Well an alternative would be to have a hash for all important package files on the system and a tool to check if hash are correct, if not apt-get --reinstall install <package>
Of coruse this means hashing and rehashing package files at each update...

---

### Post by kahping on 2008-06-08
What happens if the healer is itself corrupted and tries to heal other corrupted files? :confused:

---

### Post by billenbois on 2008-06-09
actually i think that "corrupted" is a bit misleading.
if you are having problems with your hard drive/cd/etc and files get corrupted on either side, well, you should replace the hard drive/cd/etc. SFC shouldn't replace stuff here, it will get corrupted again anyway.

It's more for people who mess up their system and don't know how to fix it/ can't spend time to reinstall (that's why it won't have much support on linux :p)

fortunately the hash have low chance to be corrupted (even if it still exists), and if they do they still need to be md5/sha1 valid hashs else will be skipped

---

