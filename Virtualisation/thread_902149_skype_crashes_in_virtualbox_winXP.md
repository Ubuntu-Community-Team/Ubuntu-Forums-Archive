---
title: "skype crashes in virtualbox winXP"
date: 2008-08-27
forum: Virtualisation
---

### Post by bro on 2008-08-27
I installed win xp pro as a guest in virtualbox. It works fine, guest additions are installed to. Seamless works quite well (sometimes with some delay or flashing of the desktop). However seamless or not, Skype crashes about 20 seconds after it started. 

could it be that the microphone is not working for example? How check/enable that?

---

### Post by Marc Higgins on 2008-12-06
> **bro said:**
> I installed win xp pro as a guest in virtualbox. It works fine, guest additions are installed to. Seamless works quite well (sometimes with some delay or flashing of the desktop). However seamless or not, Skype crashes about 20 seconds after it started. 

could it be that the microphone is not working for example? How check/enable that?

try using Skype 3.8.0.115, 

[http://www.filehippo.com/download_skype/4090/](http://www.filehippo.com/download_skype/4090/)

using this older version worked for me

---

### Post by cudjoe on 2009-06-16
It worked, thanks !

---

### Post by Clorow on 2009-06-17
Try using Skype directly inside Linux. There are .deb packages you can install, and Skype even has its own repository.

---

### Post by rykel on 2009-12-28
> **Clorow said:**
> Try using Skype directly inside Linux. There are .deb packages you can install, and Skype even has its own repository.

I wish I can...

BUT the dialpad buttons of the USB Skype Phone (similar to the IPEVO FR-33.1) I bought would NOT work in Linux, and there are no easy solution in sight... that is why I am resorting to installing Windows Skype in Windows XP in Virtualbox, just so that I can dial out - until a driver or whatever is found.

Just to highlight that there ARE instances where using Skype in Windows is called for...

---

### Post by areteichi on 2010-03-14
I was actually able to run the newest, up to date version of Skype (4.2) in Windows XP guest OS. I simply had to run it in the compatibility mode for Windows 2000 by going into 'properties' for Skype.exe by right-clicking on the file. The video works very nicely on my webcam and sound quality is superb!

---

### Post by sampyboy on 2010-11-24
Setting skype.exe to open in Windows 2000 compatibility mode indeed STOPS ITS CRASHING! Thanks areteichi! This trick works well even for Skype version 5.0 !!

---

### Post by kamikaz23 on 2010-12-06
thank you it works perfectelly

---

### Post by snowdancer on 2011-04-22
Hi all,

I tried another approach to solve this problem and
it works for me. So maybe you guys can try this.

01.Turn off firewall of guest Windows XP

02.Modify the max number of tcp half-connections by EVId4226_patch
at [http://www.lvllord.de/](http://www.lvllord.de/)

03.I modified the max number to 100 and my skype 5.3 works smoothly

---

