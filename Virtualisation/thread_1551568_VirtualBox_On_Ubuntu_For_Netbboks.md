---
title: "VirtualBox On Ubuntu For Netbboks?"
date: 2010-08-12
forum: Virtualisation
---

### Post by HackerDromi on 2010-08-12
Hello i'm total n00b to ubuntu 
i installed ubuntu for netbooks and i installed virtualbox on it
but when i select iso of xp it doesn't boot just a black screen i checked the iso on another pc and it worked fine
i searched google and found nothing about this black screen 
no errors just black screen

please help!!

also i tried reinstalling the virtualbox didn't help still black screen

---

### Post by snowpine on 2010-08-12
What are the hardware specs of your netbook? How much RAM have you allocated to the Windows virtual machine? Have you contacted Microsoft technical support for assistance with this issue (since it is not an Ubuntu problem)?

---

### Post by HackerDromi on 2010-08-12
1024 RAM in my netbook and i gave the xp 256 RAM

No i didn't try to contact MS cause it's not MS problem i'm runing the virtualbox on ubuntu host

i'm definitly missing something here

any other ideas?

---

### Post by snowpine on 2010-08-12
Well, you paid a lot of money for that copy of Windows, so Microsoft should do the right thing and help you install it. That is my feeling on the matter. 

Sorry I could not be of further assistance. Perhaps you will find an answer in the VirtualBox documentation?

[http://www.virtualbox.org/manual/](http://www.virtualbox.org/manual/)

---

### Post by HackerDromi on 2010-08-12
thanks

---

### Post by HackerDromi on 2010-08-12
Fixed it 
 just run these commands one by one

[FONT=AR PL UMing TW, serif]sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup[/FONT]
 
source:
[http://ubuntuforums.org/showpost.php?p=7488070&postcount=5](http://ubuntuforums.org/showpost.php?p=7488070&postcount=5)

---

### Post by snowpine on 2010-08-12
Excellent, thanks for sharing that! It might be helpful to other users with the same problem. :)

---

