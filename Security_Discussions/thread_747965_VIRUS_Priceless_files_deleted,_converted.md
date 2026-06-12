---
title: "VIRUS: Priceless files deleted, converted"
date: 2008-04-07
forum: Security Discussions
---

### Post by bprintz44 on 2008-04-07
Hello everybody, I'm pretty new to Ubuntu so please bare withe me.  I have 7.10 installed on my laptop and have it dual booted with win xp home (32).  I took it on a trip with me and used it to cache RAW pictures using my Ubuntu install.  After hibernating it, I could no longer open my pictures, the viewer would come up blank and subsequent pictures that I would open would then disappear from the files list and also not be opened.  I tried to access the files with my windows install as I have a Fat 32 shared partition, and the files were just not there. (it also did a scan of my Fat partition)  The RAW files are normally in *.NEF format, though after another hibernation and reboot into Ubuntu, the majority of them had been converted to *.rec, many of them simply not there.  A new folder off the root called "found.000" was created with 31 files in *.chk format (also pictures).  It appears that these files can be converted back through renaming them, though I have also lost a video.  Any ideas on how I can solve this, and make sure it doesn't happen again? -All help is greatly appreciated! 

(PS, there are some really funny pictures of a drunk kid on a tour bus in Vienna, help me recover the files, and I'll slide you some good photos!)

---

### Post by insane_alien on 2008-04-07
good news, its not a virus, bad news, ubuntu hibernate on your laptop is dodgy.

turn it off load a live cd and fsck your partitions. if that doesn't work try and find a system rescue CD.

---

### Post by Tomatz on 2008-04-07
In a terminal type this:

**sudo touch /forcefsck**

Then reboot hopefully that will recover your pics im only 50 50 it will though :(

---

### Post by brian_p on 2008-04-07
> **bprintz44 said:**
>  . . .  A new folder off the root called "found.000" was created with 31 files in *.chk format (also pictures). . . . .  

At first glance the loss of these files is not a security matter. Sticking 'VIRUS' into the message header doesn't make it so.

If this had happened to me I would be asking myself what *I* had done to cause a new directory to be created in the root file system

---

### Post by .nedberg on 2008-04-07
> **bprintz44 said:**
>  and make sure it doesn't happen again?


Did you unmount the camera/memorycard? In my experience Linux can be more picky about "safe remove" than Windows. It might not have finished copying the files over.

---

### Post by Tomatz on 2008-04-07
> **.nedberg said:**
> Did you unmount the camera/memorycard? In my experience Linux can be more picky about "safe remove" than Windows. It might not have finished copying the files over.

Yeah i bet it unmounted uncleanly when it went into hibernation.

Good point

---

### Post by HermanAB on 2008-04-07
Well, your real problem is that you are using the unreliable FAT file system.  You should use a reliable journaled file system such as NTFS or Ext3.

---

### Post by netlogic on 2008-04-07
People still use FAT file system?

---

### Post by cdenley on 2008-04-07
> **netlogic said:**
> People still use FAT file system?

My cell phone uses a FAT filesystem.

---

### Post by netlogic on 2008-04-07
> **cdenley said:**
> My cell phone uses a FAT filesystem.

I meant on a computer.

---

### Post by sekinto on 2008-04-07
I've always preferred XFS.

---

### Post by stinger30au on 2008-04-07
memory cards for the nintendo DS use fat 32

---

### Post by netlogic on 2008-04-07
> **stinger30au said:**
> memory cards for the nintendo DS use fat 32

Right. I meant on a computer.

---

### Post by nicedude on 2008-04-19
I use Fat32 for my storage partition ( just movies and music nothing sensitive or that can't be easily replaced ) on a dual boot laptop XP & Ubuntu since I want to be able to access files from both systems and I haven't had any troubles out of it. I had problems when I didn't unmount USB sticks and such before removing them but since I started unmounting before removal that has not messed up anything again.

---

