---
title: "Hidden files"
date: 2010-11-18
forum: Security
---

### Post by duduntu on 2010-11-18
Hi,

I tried to check whether there are more files at hard disk when it is read from "outside" (loading OS from USB flash in my case) than it appears when OS is loaded from the hard disk itself.
I think it does not need to explain in this forum why such check is important and interesting.

My system is fresh enough. Just installed Kubuntu 10.10.

To my surprise I found 5 files:
/dev/.blkid.tab
/var/run/init.upgraded
/var/run/reboot-required
/var/run/reboot-required.plgs
/var/run/samba/upgrades/smb.conf

Content of all of them look innocent, some are empty.
The longest is the last. This is some script related to samba. Having little time I cannot study it in detail.
It is started with "Sample configuration file for the Samba suite...".

The strangest thing is that the dates of modification of all files are older than the date and time of last
shutdown of system when it was loaded from hard disk. So the hypotesis that the system writes them when shutting down can scarcely explain their presence. 

Even more strange: all have "modified" before installation of the system itself.

Is there any explanation of all this?
 
        New Kubuntu user.

---

### Post by pricetech on 2010-11-18
Files with names that begin with a dot are hidden.  You can view hidden files if you want and that may be the default with a "live" OS, though I've never looked at that.

Ubuntu doesn't "touch" much less modify, each file at shutdown, nor does any other OS.  The modification date is just that; the last time the file was modified.  If the modification date predates the install, that's normal since the file wasn't modified during installation, it was just placed there as part of the install.

I hope that answers your question.

---

### Post by duduntu on 2010-11-18
> **pricetech said:**
> Files with names that begin with a dot are hidden.  You can view hidden files if you want and that may be the default with a "live" OS, though I've never looked at that.

Ubuntu doesn't "touch" much less modify, each file at shutdown, nor does any other OS.  The modification date is just that; the last time the file was modified.  If the modification date predates the install, that's normal since the file wasn't modified during installation, it was just placed there as part of the install.

I hope that answers your question.

As I clearly explained, I don't mean that kind of "hidden" which when file names are started with dots.
I mean by hidden that the files  are not seen at all, neither by "ls -a", no by any (from which I tried) other means of the system.

For example, when I run the system from HD, not only the file, but the whole directoiry
/var/run/samba is absent.
So in /var/run there is no entry "samba". Please note that this name does not start from dot,
so it is not hidden directory even from this point of view.

But when loading the system from USB flash, this directory in hard disk magically appears.
And the file in there dated back in the past.
How this can happen?

---

### Post by cariboo on 2010-11-18
I have /var/run/samba on my Maverick install, the file in that directory is just the same as the smb.conf file that is in /etc/samba

---

### Post by duduntu on 2010-11-18
> **cariboo907 said:**
> I have /var/run/samba on my Maverick install, the file in that directory is just the same as the smb.conf file that is in /etc/samba
I have too /etc/samba/smb.conf
I have too /usr/share/samba/smb.conf

These two are almost the same.

But I do not have /var/run/samba directory while I am loading the system from HD.

PS: Just checked that when booting from USB flash
the file  /var/run/samba/upgrades/smb.conf is seen as identical to /etc/samba/smb.conf.
All dated 2010 October 7. Might be date of compilation of this system?

---

### Post by duduntu on 2010-11-18
So can anybody convince me that this bizarre things are of no harm.
Don't want to say bad words about what could hidden files mean. 
Possibly this is not about it. But do anybody here have consistent information?
Might it be some algorithms which are responsible for upgrading?

---

### Post by cariboo on 2010-11-18
I don't know if this will be any of any help to you, but have a look [here]("http://www.pathname.com/fhs/2.2/fhs-5.13.html"). It explains what the purpose of the /var/run directory is.

---

### Post by pricetech on 2010-11-18
Okay, maybe I understand what you're saying now.  I hope so anyway.

When you boot to the live OS, you're looking at the directory structure of the live OS, not your hard drive install.  As such, you'll see different contents.

Is that more what you're asking ??

---

### Post by duduntu on 2010-11-18
> **pricetech said:**
> Okay, maybe I understand what you're saying now.  I hope so anyway.

When you boot to the live OS, you're looking at the directory structure of the live OS, not your hard drive install.  As such, you'll see different contents.

Is that more what you're asking ??

No, no, this is no so simple.
But you are thinking in the right way.
It is very easy to make this kind of error even if you already mounted hard drive and "cd" to there.
I don't touch the issue if you don't know about necessity to mount hard drisk or if you din't know
about hard disk at all. Let me not consider this sorrow.
So if one mounts hard drive,
say, 
mount -r /dev/sd...  /media/blu-blu
cd /media/blu-blu
cd /dev
Oops!, and you are back to you live CD.
This happened with me too quite some times.
The difference between  correct and incorrect command is one extra character: "/"
cd dev  - is OK.
So you are thinking right. I could make this error. But I did not make it.

So when in my posts before I give hard disk directories as seen from live CD, I imply that in reality they go with prefixes like /media/disk  depending on where and how you mount them.

So I really looked at the hard disk, not at live CD, and not at the moon or anything else, believe me.

---

