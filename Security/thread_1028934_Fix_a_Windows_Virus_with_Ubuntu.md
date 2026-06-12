---
title: "Fix a Windows Virus with Ubuntu?"
date: 2009-01-02
forum: Security
---

### Post by timcarroll on 2009-01-02
Hello!

I have picked up a pretty annonying virus that seems to be a couple steps a head of me everytime I try to remove it.  It blocks all access to AVG sites (can't update AVG) and it shuts down AVG after I start a scan.  Now my question is, if I boot up an Ubuntu Live C.D. (I'm on it now) can I remove the Windows Virus somehow?  My hard drive is not partitioned and is running Windows XP. 

Thanks

---

### Post by BGFG on 2009-01-02
When i was dual booting, i would mount and scan my windows partition with clamAV. you could look for a live cd distro that comes with clam pre-installed or get clam portable and run it for a usb key:

[http://portableapps.com/apps/utilities/clamwin_portable](http://portableapps.com/apps/utilities/clamwin_portable)

---

### Post by cariboo on 2009-01-03
Using the LiveCD you could install clamav in to ram and scan your windows partition. Of course once you shutdown clamav won't be there anymore.

Be sure to read the clamscan man page as there are a lot of options you can use. 

Jim

---

### Post by Rob_H on 2009-01-03
If something has dug its teeth in deep, though, you might be better off using a live CD to backup critical data and then reformat and reinstall the OS from scratch.

---

### Post by Piro24 on 2009-01-03
I agree with Rob_H. You might not be able to remove all aspects of this virus, and even if you apparently do, it might have snuck into one of your system restore files, so it would just come back if you ever tried to restore your system. 

From your description, it was probably a well written virus, not just some kid in the basement trying to be cool and call himself a h4x0r. So, it might also have affected parts of the registry that are basically impossible to diagnose without manually looking through a bunch of settings. 

I think you should do a scan, and if your computer still runs a bit slower than normal, or if you notice unusual behavior, just back-up files and do a quick re-install of Windows.

---

### Post by bodhi.zazen on 2009-01-03
The first step in removing a virus is identifying it. Once you have identified the virus you can then learn how to remove it.

Take care with Linux Antivirus programs, last time I looked they only give you the option to delete files, not restore them or remove the malignant code in any way.

---

### Post by HermanAB on 2009-01-04
Actually, the best way to fix Windows, is with a Windows Live CD:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

I always have one with ClamAV, Spybot S&D and Hijackthis.  Between those, I can fix anything after booting of the CD drive.

Cheers,

Herman

---

### Post by Vantrax on 2009-01-04
Avast actually made a good linux client that scans for windows viruses.

I use it regularly for exactly what your talking about, fixing windows drives that are so badly infected that virus scans dont work.

You can download it for free from their website and get a annual license for free by giving them your email address.

---

### Post by Sillywombat on 2009-04-23
Thanks a bunch! Going to show this trojan who is the boss!

---

### Post by wirechief on 2009-04-23
I think i got a trojan phishing virus on my vista partition, Avast did not
detect it however Avira did and after booting to safe mode it was able to 
remove the thing however I think it laid eggs as it is currently acting very strange and very slow (vista is always slow anyways) I am thinking my
best bet is to backup my Linux partitions using dd to a usbdrive and then
reinstalling the vista partition and reshrinking it back to what i have now.
This could get a little hairy as the partitions have to be the same size as they currently are...just a thought. anyone with some ideas ?

---

### Post by dino99 on 2009-04-24
hi,

have you it's name ? where is it ? (file system ,mbr, playing in ram an permuted ?

basicly, try to learn how it work.

You might want to clean your system with ccleaner for example, then deable java, javascript and kill all the unecessary process or unknown.

try to rebuilt the mbr to be sure it's not there, and run an online virus detection, better than your own installed antivirus because it can stop it.

But, the real question : why windows ?  :P:P

---

