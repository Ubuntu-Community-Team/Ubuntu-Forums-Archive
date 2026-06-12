---
title: "Please recommend a software to clean Windows virus under Ubuntu"
date: 2010-11-16
forum: Security
---

### Post by zhaotianwu on 2010-11-16
I've just installed Ubuntu and my windows partition is loaded with malware and virus. Can anyone recommend a software (preferrably free and opensource) to clean Windows virus under Ubuntu? thanks.

---

### Post by wilee-nilee on 2010-11-16
I would use a stand alone bootable cd that updates AV definitions. Here is a link to a thread where I gave links to such setups.

[http://ubuntuforums.org/showthread.php?t=1623314](http://ubuntuforums.org/showthread.php?t=1623314)

Really if you have a problem, a AV should be run from the safe mode=f8 prompt in windows or a bootable cd.

Avast has a Linux load but you need to set a command up for it to always open.
A quote here.
I have Avast in Lucid 10.04, had the same problem, lots a workarounds out there, but I have found after experimenting with 3 different computers and several versions of Linux, that all you need to do is edit /etc/sysctl.conf by adding this:
kernel.shmmax = 128000000

I have avast on my computer but it is prone to false positives I think your better off with the other links provided.

I would also warn against thinking that any AV will actually remove everything, there are rootkits at the least that are not detectable with even the best AV software, I would back it up and reinstall if it was me, and run it in a limited account with a strong password on it in the the admin and limited.

---

### Post by zhaotianwu on 2010-11-17
> **wilee-nilee said:**
> I would use a stand alone bootable cd that updates AV definitions. Here is a link to a thread where I gave links to such setups.

[http://ubuntuforums.org/showthread.php?t=1623314](http://ubuntuforums.org/showthread.php?t=1623314)

Really if you have a problem, a AV should be run from the safe mode=f8 prompt in windows or a bootable cd.

Avast has a Linux load but you need to set a command up for it to always open.
A quote here.
I have Avast in Lucid 10.04, had the same problem, lots a workarounds out there, but I have found after experimenting with 3 different computers and several versions of Linux, that all you need to do is edit /etc/sysctl.conf by adding this:
kernel.shmmax = 128000000

I have avast on my computer but it is prone to false positives I think your better off with the other links provided.

I would also warn against thinking that any AV will actually remove everything, there are rootkits at the least that are not detectable with even the best AV software, I would back it up and reinstall if it was me, and run it in a limited account with a strong password on it in the the admin and limited.


Is Avast Linux able to kill virus residing in Windows partition as well? I thought it can only scan/kill Linux based virus.

---

### Post by wilee-nilee on 2010-11-17
> **zhaotianwu said:**
> Is Avast Linux able to kill virus residing in Windows partition as well? I thought it can only scan/kill Linux based virus.

Avast just finds stuff you have to decide whether it is a false positive or a real threat, and act accordingly. It runs a little differently then the Windows version. Avast is not OS centric it looks for the critters that effect all OS's like rootkits and the ones OS centric. 

I don't bother using the avast installed in Linux unless I'm bored and want to see some false positives. I ran it just a couple of days ago it said I had a back door Trojan in a virtual XP setup. There isn't one the one identified can be dealt with fairly straight forward.

This was a fresh install of XP that hasn't been onto the web for more the MS updates.

---

### Post by HermanAB on 2010-11-17
Howdy,

The best way to clean Windows is with a Windows live CD.  You can do that with BartPE.  Google for it.

---

### Post by Rubi1200 on 2010-11-17
There are also some very useful rescue CDs out there that may be able to assist in this task:
[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)

---

