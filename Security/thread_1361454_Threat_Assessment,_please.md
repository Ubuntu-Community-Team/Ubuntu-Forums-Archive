---
title: "Threat Assessment, please"
date: 2009-12-22
forum: Security
---

### Post by teward on 2009-12-22
Got a computer that showed up with a Windows Trojan Horse.  I've got an Ubuntu box, and I'm wondering how I can scan the drive with it, and clear the windows virus.  How do I go about doing this?  Also, what threat does this pose to the Ubuntu box?  (it has Wine installed, hence the post).

---

### Post by wilee-nilee on 2009-12-22
If your talking about the computer in your signature with a dual boot do you have any av programs in Xp malwarebytes is a good one if you don't have it already. you could install clamav in Ubuntu and let it scan the xp partition.

---

### Post by teward on 2009-12-22
no, I'm talking about another computer, with an infected drive in it.  I need to clear it of the viruses, but the desktop I use for that has a dead windows partition.  So I need to use Ubuntu to clean the infected drive.

---

### Post by Grenage on 2009-12-22
Try installing clamav (it's in the repos).  You can then scan it using the command clamscan.

---

### Post by teward on 2009-12-22
no risk to the ubuntu install, right?

---

### Post by Grenage on 2009-12-22
No, it will be coded for windows; you'll be fine.

---

### Post by teward on 2009-12-22
alright.  thanks.

---

### Post by 3rdalbum on 2009-12-22
If you can determine what virus it is (for instance, if it extorts you to buy "anti-virus software" and you google the name of the fake anti-virus software) you can find out what files to remove from the Windows disk. Without those files, the machine will safely boot up and you can remove the remaining parts of the infection (proxy settings, registry entries) from within Windows.

I've done this twice.

---

### Post by EJeanmaire on 2009-12-22
> **TrekCaptainUSA said:**
> Got a computer that showed up with a Windows Trojan Horse.  I've got an Ubuntu box, and I'm wondering how I can scan the drive with it, and clear the windows virus.  How do I go about doing this?  Also, what threat does this pose to the Ubuntu box?  (it has Wine installed, hence the post).

Wipe the Windows box; only way to be sure its gone.

---

### Post by teward on 2009-12-24
@EJeanmaire:  I'm trying not to wipe the windows box, as its my girlfriend's laptop, and she needs the files on it.  Nevertheless, thats the last resort.

@Everyone else:  Once I get a name on the virus, I know how to find and remove it, I have access to virus databases and how to get rid of the viruses.

Also, this is marked as **solved**, so this topic is technically closed.

---

### Post by Joker512 on 2009-12-24
I am trying something similar, except clamav freezes whenever I start a recursive scan. I did notice that the gui was out of date though, does anyone know what causes this?

---

### Post by teward on 2009-12-24
Okay, final thought: this thread is marked as *_**solved**_*, and will NOT have any more updates.  You have questions, you should post your own thread and not hijack this one.

ADMINS: Unless you're going to make this a sticky or something, feel free to *_**lock**_* this thread.

---

