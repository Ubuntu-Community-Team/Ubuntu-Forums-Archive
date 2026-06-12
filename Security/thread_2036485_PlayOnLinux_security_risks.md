---
title: "PlayOnLinux security risks"
date: 2012-08-02
forum: Security
---

### Post by aligator12 on 2012-08-02
Hi, is there any risks to PlayOnLinux? I am going to install itunes in it, besides that are there are exploits in it or anything?

---

### Post by claracc on 2012-08-02
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Specially, take a deep look to this part of the contents: 

. Windows mindset

    Antivirus

        Wine

I suposse what is valid for wine is for playonlinux

---

### Post by Hungry Man on 2012-08-03
Same issues as with WINE. It's designed to run Windows programs and Windows programs include malware.

Only run a trusted file in there and maybe consider creating an apparmor profile for WINE.

---

### Post by zombifier25 on 2012-08-03
As long as you
1. Don't run Wine as root
2. Remove the Z: drive symlink (which conveniently links to the rest of the drive)
3. Use PlayOnLinux for each software to isolate them (which is what you are doing, good)
then you're safe (AppArmor is a little Draconian at the moment considering the pathetic state of Windows viruses under Wine IMHO)

---

### Post by KenSharp on 2012-08-06
> **zombifier25 said:**
> 
2. Remove the Z: drive symlink (which conveniently links to the rest of the drive)

This does not deny access to the rest of the filesystem. Not all Windows applications require access via a drivename.

---

