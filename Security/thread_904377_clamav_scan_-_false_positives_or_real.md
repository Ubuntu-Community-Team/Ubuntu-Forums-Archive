---
title: "clamav scan - false positives or real?"
date: 2008-08-29
forum: Security
---

### Post by ubu2 on 2008-08-29
I installed clamav and did a routine antivius scan (did a recursive scan on the full filesystem). I have EdUbuntu Hardy 8.04 installed on an Acer laptop running Windows Vista (Wubi-based install).
clamav found the following 5 viruses-

Found 5 possible viruses (285641 files scanned).

/sys/slab/                                                  0000704/slab_size
/home/uu2/.clamtk/viruses/Spell_I...              Files number limit exceeded
/var/log/gdm/                                                           0.log
/var/lib/ucf/cache/                                                       etc
/media/ACER/Program Files/Norton ...               Exploit.JS.CVE-2005-1790.A
-----------------------------------------------------------------------------


I have the clamTK GUI for clamav. When you click on the Quarantine tab, and then Maintenance; it says sigs.dat.VIRUS is under quarantine.


Does anyone know if these could be real or false-positive; and what I should do from here. 
I am new to Ubuntu. Any help is much appreciated.
Thanks!

---

### Post by cariboo on 2008-08-29
I kind of like how it tagged Norton antivirus as a virus. To check out the others just open a terminal and cd into the directories in question and check the suspected files out.

btw they are all false positives

Jim

---

### Post by ubu2 on 2008-08-29
> **cariboo907 said:**
> I kind of like how it tagged Norton antivirus as a virus. To check out the others just open a terminal and cd into the directories in question and check the suspected files out.

btw they are all false positives

Jim

Thank you very much but how do you actually find out if they are viruses or not?

---

### Post by tamoneya on 2008-08-29
well i would actually investigate the last one.  The one in program files/norton.  While none of the norton files should be virii it could be some virus that norton has quarantined.  Since I cant see the full path I cant really tell.  The other ones though dont look viral to me.  The main thing that Im looking at is their location.  The norton one is on your windows drive.  The others are in linux locations and these are not locations in the path or highly sensitive areas.  Also clam scans for windows virii so even if they were it wouldnt matter because they are in a linux environment and then would be useless.

---

### Post by cariboo on 2008-08-30
I just did a little checking on:

>  Exploit.JS.CVE-2005-1790.A

It looks like it really looks like a false positive, see here:

[http://forums.clamwin.com/viewtopic.php?p=4246](http://forums.clamwin.com/viewtopic.php?p=4246)

Check out the last post in the thread.

Jim

---

