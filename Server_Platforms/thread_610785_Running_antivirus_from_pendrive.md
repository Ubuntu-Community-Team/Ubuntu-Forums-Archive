---
title: "Running antivirus from pendrive"
date: 2007-11-12
forum: Server Platforms
---

### Post by Zuppo on 2007-11-12
Hi there! Is it possible to have an antivirus program installed on a pendrive and run it from LiveCD to scan any computer I want? And is it easier for Linux Antiviruses to find and remove threats from Windows partitions/HDs?
Thanks for the help!
I'm a newbie, BTW. Remember that when(if) you answer...:)

---

### Post by reckless2k2 on 2007-11-12
you can do all this already for a liveCD. not sure if you can do it with ubuntu but i use to do it with knoppix all the time. i'm sure you can do it with ubuntu live. and you don't have to carry around definitions like with old school norton. you can do a live download using the livecd. 

or are you saying you don't want net connection even running livecd?

---

### Post by Zuppo on 2007-11-12
Thanks for the answer!
Well, I guess it's fine to use LiveCD to connect to the internet. My question is: where is Ubunto going to install the antivirus' files, in case I have to download them? That's why I asked about running it from a pendrive.

---

### Post by reckless2k2 on 2007-11-12
it just loads to ram like in knoppix. use synaptic to install clamav. probably the best. then it'll pull the defs and then scan.

---

### Post by HermanAB on 2007-11-12
Well, I presume that you wish to scan Windows PCs.  To do that, you should look at Bart Lagerwei's BartPE with ClamAV, since it does NTFS: [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

Cheers,

Herman

---

### Post by Zuppo on 2007-11-13
Thanx again for the help!

---

