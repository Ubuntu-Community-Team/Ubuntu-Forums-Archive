---
title: "AWN terminal acting funny"
date: 2011-03-01
forum: Security
---

### Post by distboy on 2011-03-01
Today suddenly my awn terminal started doing things by it selves.

Output..

                     p { margin-bottom: 0.21cm; }  erver@server-desktop:~$ ls  
 Bilder      examples.desktop  Musikk        Shared Files  Ubuntu One  
 Desktop     gebabbel          Nedlastinger  Skrivebord    Videoklipp  
 Dokumenter  Maler             Offentlig     tmp           wma.qgs  
 Dropbox     Maps              pitbull.tgz   trackonfly    æ.qgs  
 server@server-desktop:~$ tar zxvf pitbull.tgz  
 .k/  
 .k/stealth  
 .k/udp.pl  
 .k/kswap.levels  
 .k/std  
 .k/mech1.users  
 .k/kswap.pid  
 .k/crond  
 .k/LinkEvents  
 .k/randfiles/  
 .k/randfiles/randkicks.e  
 .k/randfiles/randsay.e  
 .k/randfiles/randsignoff.e  
 .k/randfiles/randinsult.e  
 .k/randfiles/randversions.e  
 .k/randfiles/randpickup.e  
 .k/randfiles/randnicks.e  
 .k/randfiles/randaway.e  
 .k/j  
 .k/pitbull.tgz  
 .k/kswap.set  
 .k/kswap.help  
 .k/go  
 server@server-desktop:~$ cd .k  
 server@server-desktop:~/.k$ ./go  
 EnergyMech 2.8, November 8th, 2000  
 Compiled on Dec 16 2002 09:26:13  
 Features: DBG, SDB, LNE, SEE, LNK, TEL, PIP, DYN, NEW, ALS, WIN, SEF  
 init: Mech(s) added [ psychoz ]  
 init: EnergyMech running...  
 server@server-desktop:~/.k$ cd 





Anybody knows whats going on?


Thanks
Erlend

---

### Post by scoz on 2011-04-28
You've been hacked. See [http://ubuntuforums.org/showthread.php?t=124108](http://ubuntuforums.org/showthread.php?t=124108)

A backdoor has probably been installed on your computer. Format the hard drive, re-install your OS, and try to secure it as much as you can.

---

