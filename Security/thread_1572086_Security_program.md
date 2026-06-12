---
title: "Security program"
date: 2010-09-10
forum: Security
---

### Post by Makosz on 2010-09-10
I was woundering if there is a program or a way that I can view if someone tried to enter a certain folder. I know you can go to properties and it says there but I also want to know if anyone even opens a folder from different OS or comuter

Also is there a way that i can put password for grub before it does anything on startup

---

### Post by bodhi.zazen on 2010-09-10
From the style of your post I advise encryption.

I do not think you can track access if somebody boots a live CD or another OS.

---

### Post by Bachstelze on 2010-09-12
> **bodhi.zazen said:**
> 
I do not think you can track access if somebody boots a live CD or another OS.

This. They can always mount the filesystem noatime. You can however always track modifications (at least on filesystems that support it, not on FAT/NTFS).

---

### Post by Makosz on 2010-09-13
> **Bachstelze said:**
> This. They can always mount the filesystem noatime. You can however always track modifications (at least on filesystems that support it, not on FAT/NTFS).

how do i do that?

---

### Post by Bachstelze on 2010-09-14
> **Makosz said:**
> how do i do that?

You can see when a file was last modified with stat:

```
firas@itsuki ~ % stat distance.hs
  File: `distance.hs'
  Size: 4009            Blocks: 8          IO Block: 4096   regular file
Device: 806h/2054d      Inode: 5849161     Links: 1
Access: (0644/-rw-r--r--)  Uid: ( 1000/   firas)   Gid: ( 1000/   firas)
Access: 2010-08-18 07:35:39.648948892 +0200
Modify: 2010-08-18 07:35:39.760948749 +0200
Change: 2010-08-18 07:35:39.760948749 +0200

```

Note that the "access" field will probably not be accurate if the filesystem is mounted noatime.

---

### Post by bodhi.zazen on 2010-09-14
> **Makosz said:**
> how do i do that?

If you are asking about monitoring files for changes, use HIDS, there are several options, everything from tripwire to OSSEC.

---

### Post by Makosz on 2010-09-14
is mounted noatime mean like a live cd? and It is against a person that at this moment does not know much about computers.

---

### Post by Bachstelze on 2010-09-14
> **bodhi.zazen said:**
> If you are asking about monitoring files for changes, use HIDS, there are several options, everything from tripwire to OSSEC.

I don't think those will work if the FS is mounted from e.g. a Live CD.

> **Makosz said:**
> is mounted noatime mean like a live cd?

It means mounted with the noatime option, from a Live CD or otherwise.

---

### Post by bodhi.zazen on 2010-09-14
> **Bachstelze said:**
> I don't think those will work if the FS is mounted from e.g. a Live CD.

If you change a file monitored by tripwire, AIDE, OSSEC, etc, from a live CD the changes will be detected.

You could detect the changes while running a live CD (assuming you have access to the original known good database).

---

### Post by wacky_sung on 2010-09-15
> **bodhi.zazen said:**
> If you change a file monitored by tripwire, AIDE, OSSEC, etc, from a live CD the changes will be detected.

You could detect the changes while running a live CD (assuming you have access to the original known good database).

Yeah it is good to detect the change but does it stop them?If not, then personally i find it is just another files monitor as good as a keylogger.

---

### Post by bodhi.zazen on 2010-09-15
> **wacky_sung said:**
> Yeah it is good to detect the change but does it stop them?If not, then personally i find it is just another files monitor as good as a keylogger.

No, it will not stop alterations of files. You would need encryption for that.

As you know, physical access == root access on any OS.

Just curious , keylogger ? To track users ?

---

### Post by BkkBonanza on 2010-09-15
> **Makosz said:**
> is mounted noatime mean like a live cd? and It is against a person that at this moment does not know much about computers.

Mounting a filesystem "noatime" means the "last access time" for each file is not updated. 

This is sometimes used to reduce disk activity, or even slightly improve performance since the atime value is (often) not stored in the same place as the file and (may) require extra disk head movement to update. 

Often it's recommended on flash drive filesystems since each atime update causes a whole sector re-write and on flash drives there is a theoretical limit to re-writes before the sector is mapped as dead. In this case it's considered a waste of overall drive longevity.

---

### Post by wacky_sung on 2010-09-16
> **bodhi.zazen said:**
> No, it will not stop alterations of files. You would need encryption for that.

As you know, physical access == root access on any OS.

Just curious , keylogger ? To track users ?

The keylogger which i am refering is function almost just like a IDS, if the IDS does not stop the execution of the user.

I just curious how does the IDS stop the execution.If an zero day worm hit a Ubuntu server and get through the firewall.I ponder how does the IDS stop the worm just like "I Love you" worm.

---

### Post by bodhi.zazen on 2010-09-16
> **wacky_sung said:**
> The keylogger which i am refering is function almost just like a IDS, if the IDS does not stop the execution of the user.

I just curious how does the IDS stop the execution.If an zero day worm hit a Ubuntu server and get through the firewall.I ponder how does the IDS stop the worm just like "I Love you" worm.

IDS detects, but does not stop an attack.

NIDS would detect suspicious network activity. If snort throws an alert you would need to follow up and determine if the "attack" (I use quotes as not all snort alerts are an attack, and there are false positives) was successful.

HIDS generally detects the attack after the fact.

To prevent an attack you need to be proactive - keep your system up to date, secure services, use iptables, etc.

Tools such as selinux or apparmor would also potentially help.

---

### Post by wacky_sung on 2010-09-17
> **bodhi.zazen said:**
> IDS detects, but does not stop an attack.

NIDS would detect suspicious network activity. If snort throws an alert you would need to follow up and determine if the "attack" (I use quotes as not all snort alerts are an attack, and there are false positives) was successful.

HIDS generally detects the attack after the fact.

To prevent an attack you need to be proactive - keep your system up to date, secure services, use iptables, etc.

Tools such as selinux or apparmor would also potentially help.
I do agreed with what you mentioned.The downside of using apparmor is that you require to set every single application for a apparmor profile in order for it to function as intended.Whereas SElinux,you mentioned before it is not practical to use it in Ubuntu.(Correct me if i am wrong).Personally i just find grsecurity work the best for a noob like me to use it to function for all appplications.

---

### Post by bodhi.zazen on 2010-09-17
> **wacky_sung said:**
> I do agreed with what you mentioned.The downside of using apparmor is that you require to set every single application for a apparmor profile in order for it to function as intended.Whereas SElinux,you mentioned before it is not practical to use it in Ubuntu.(Correct me if i am wrong).Personally i just find grsecurity work the best for a noob like me to use it to function for all appplications.

Ubuntu has apparmor profiles of most servers and many applications available (apparmor-profiles).

If you want selinux, use Fedora or Centos.

I have minimal experience with grsecurity, but if it works for you. The problem is grsecurity is a tad generic as well.

---

