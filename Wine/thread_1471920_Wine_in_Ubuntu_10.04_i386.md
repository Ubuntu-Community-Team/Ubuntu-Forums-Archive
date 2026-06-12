---
title: "Wine in Ubuntu 10.04 i386"
date: 2010-05-03
forum: Wine
---

### Post by masaharustin on 2010-05-03
I decided to try out 10.04 today, previously I had been using 9.10. I downloaded the i386 version of 10.04, I had been using the i386 version  of 9.10. Wine ran well in 9.10 i386, but in the software center of Ubuntu 10.04 it is written that Wine is not compatible with my type of computer. Why is this?

---

### Post by kenweill on 2010-05-03
> **masaharustin said:**
> I decided to try out 10.04 today, previously I had been using 9.10. I downloaded the i386 version of 10.04, I had been using the i386 version  of 9.10. Wine ran well in 9.10 i386, but in the software center of Ubuntu 10.04 it is written that Wine is not compatible with my type of computer. Why is this?

add "ppa:ubuntu-wine/ppa" to your software sources, do "sudo apt-get update", then install wine... "sudo apt-get install wine"

---

### Post by masaharustin on 2010-05-03
Fixed the problem
In terminal: 

> Sudo apt-get update

thats all. :D

---

### Post by scradock on 2010-05-03
> **masaharustin said:**
> I decided to try out 10.04 today, previously I had been using 9.10. I downloaded the i386 version of 10.04, I had been using the i386 version  of 9.10. Wine ran well in 9.10 i386, but in the software center of Ubuntu 10.04 it is written that Wine is not compatible with my type of computer. Why is this?
We might be better able to help if you tell us what computer you are using - CPU type, RAM, video card/driver.....

I have been using Wine in 10.04 since January......

---

### Post by deuson on 2010-05-07
i update my ubuntu from 9.10 to 10.04 lts, my wine also could't work after my update, so i uninstall my old wine and install the wine-12. It work well.

---

### Post by dkd903 on 2010-07-08
You could also try the Wine 1.2 RC, has some very good integration features, try here: [http://digitizor.com/2010/07/03/how-to-install-wine-1-2-rc6-in-ubuntu-10-04-lucid-lynx/](http://digitizor.com/2010/07/03/how-to-install-wine-1-2-rc6-in-ubuntu-10-04-lucid-lynx/)

---

### Post by ghinix on 2010-07-26
> **kenweill said:**
> add "ppa:ubuntu-wine/ppa" to your software sources, do "sudo apt-get update", then install wine... "sudo apt-get install wine"

My Wine installation on Ubuntu 10.04 automatically installed Wine 1.2

Is this the recommended version?

Thank you

---

### Post by bruno martinho on 2010-08-01
Hi, can someone help me?i have installed ubuntu 10.04 for i386 platforms, and to install wine i went looking for wine 1.2 for i386, but i cant run the program i want...the message is this: "the program btnext has encounters a serious problem and needs to close. this can be caused by a problem in the program or a deficiency in wine". i also tried to meaku sudo apt-get update and i received this message : "               Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources               
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid Release.gpg                             
  Could not connect to pt.archive.ubuntu.com:80 (193.136.212.166). - connect (110: Connection timed out)
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates Release.gpg 
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com/ubuntu/](http://pt.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
  Unable to connect to pt.archive.ubuntu.com:http:
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid Release             
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates Release
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/main Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/restricted Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/main Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/restricted Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/universe Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/universe Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/main Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/restricted Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/main Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/restricted Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/universe Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/universe Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/main Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/main Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/restricted Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/main Sources
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/restricted Sources
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/universe Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/universe Sources
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/multiverse Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid/multiverse Sources
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/main Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/restricted Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/main Sources
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/restricted Sources
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/universe Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/universe Sources
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/multiverse Packages
  Unable to connect to pt.archive.ubuntu.com:http:
Err [http://pt.archive.ubuntu.com](http://pt.archive.ubuntu.com) lucid-updates/multiverse Sources
  Unable to connect to pt.archive.ubuntu.com:http:
W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to pt.archive.ubuntu.com:80 (193.136.212.166). - connect (110: Connection timed out)

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to pt.archive.ubuntu.com:http:

W: Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://pt.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Unable to connect to pt.archive.ubuntu.com:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.


Do i need tu update wine?if so, how can i updated him?

p.s.: sorry for the long message[IMG]file:///home/bruno/Desktop/Screenshot.png[/IMG]

---

### Post by bruno martinho on 2010-08-02
can anyone help me?i have hit Ctrl+Alt+F1 to enter console mode,but i cant get out of it...can anyone tell me how to get back to graphic mode?hitting Ctrl+Alt+F7 nothing happens.....tks

---

### Post by dino99 on 2010-08-03
open synaptic and change the server to "main" then update

---

### Post by mbahlukman on 2010-10-21
> **kenweill said:**
> add "ppa:ubuntu-wine/ppa" to your software sources, do "sudo apt-get update", then install wine... "sudo apt-get install wine"
YES  !!
i got it
thank You

---

