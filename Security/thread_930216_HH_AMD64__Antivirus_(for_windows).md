---
title: "HH AMD64  Antivirus (for windows)"
date: 2008-09-25
forum: Security
---

### Post by mkham on 2008-09-25
I want to scan a window partition under linux
Want to scan sick Windows by just booting into Linux and to scan files when swapping them between dual boot OS's. Have Hardy Heron updated 8.04 AMD64 on a Acer 5003WLMi AMD Turion 64 ML32 1.8gh, 512L2 cache, 1 gig RAM; with XP Home SP3. First installed ClamAV, which showed up as installed on Add/Remove, but when rebooted it was gone. Also interested in what scans Linux- Clam is supposed to be pretty lousy. Please spare me the Ubuntu can't get infected lecture- it took me 3 hours to properly update it, and now will get mouse lock-up and HD just buzzing for up to to an hour. 

I've tried Linux AVG, but it just says wrong architecture, Avast 64bit does the same thing (maybe not for AMD); see a big Avira Linux, but doesn't say AMD or 64. Downloaded Linux F-Prot, which I once used with Windows- nice cause you could do it in DOS, where viruses were inactive. It claims 64bit function (but not AMD), and saw some complex instructions on how to install it from Jan 2006, but would like something newer. Or any other AV that you KNOW works on HH AMD64. Like I said, I'm more interested in dealing with Windows viruses to avoid being a Typhoid Mary and clean my sick Windows partitions. 

Do Ossec, chrootkit, snort, RKH scan for Windows viruses, trojans, exploits.. or only Linux problems?

PS I'm in Kiev, which is a high threat environment- my Windows lasted 2 months in Moscow using sporadic WiFi before it was fried.
[email]mkham6@juno.com[/email]

---

### Post by hyper_ch on 2008-09-26
don't use windows and you can stop worrying about malware ;)

but have a read here:

[http://www.linuxquestions.org/questions/linux-distributions-5/live-cd-with-antivirus-tools-189722/](http://www.linuxquestions.org/questions/linux-distributions-5/live-cd-with-antivirus-tools-189722/)

[http://www.linuxquestions.org/questions/general-10/live-cd-with-antivirus-266988/](http://www.linuxquestions.org/questions/general-10/live-cd-with-antivirus-266988/)

[http://www.wilderssecurity.com/showthread.php?t=103600](http://www.wilderssecurity.com/showthread.php?t=103600)

[http://kennethhunt.com/archives/001725.html](http://kennethhunt.com/archives/001725.html)

--> you'll find a lot more if you google for "antivirus live cd"

---

### Post by HermanAB on 2008-09-26
In general, it is easier to fix Windows using Windows.  Make yourself a BartPE CD with all your favorite tools on it:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

I suppose another way is to run Windows in a VM and use that to fix the other Windows system.

Cheers,

Herman

---

