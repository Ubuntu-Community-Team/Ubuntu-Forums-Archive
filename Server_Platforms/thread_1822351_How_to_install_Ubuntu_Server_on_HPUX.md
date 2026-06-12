---
title: "How to install Ubuntu Server on HPUX?"
date: 2011-08-10
forum: Server Platforms
---

### Post by server_fan on 2011-08-10
Hey All,

 I am trying to setup a LAMP stack on an HP-UX server with the EFI Boot Manager that it comes with. Originally it ran Red-Hat Linux but I am now to cheap to pay the RHN Annual Fee and would like to use Ubuntu Server. I have burned a 64Bit Ubuntu Server disc on my computer and it boots fine on every computer I've tried except for this server. I think it may need a boot script, but I'm not sure. It will simply not boot and says "DVD Not Found" every time I try to boot.

Any Suggestions?

For the record, I also tried a Fedora DVD Server Disc and it will not boot either.

Any help would be highly appreciated. 

Server_Fan

---

### Post by server_fan on 2011-08-10
I hate to do this... but BUMP!

---

### Post by matthewm27 on 2011-08-10
Dumb question, do you have a DVD-ROM?

---

### Post by server_fan on 2011-08-10
I tried both the DVD and CD discs, as well as multiple drives... I used the discs on other machines without issues and thus I'm stuck. :D

---

### Post by matthewm27 on 2011-08-10
Did you try different brands of CDs/DVDs? I have multiple brands of disks in my house, and only one worked. The only difference is that a CD either worked on all computers or none at all.

---

### Post by server_fan on 2011-08-10
I thought that, but the CDs/DVDs working on my other machines.

---

### Post by reddevil2064 on 2011-08-11
> **server_fan said:**
> I thought that, but the CDs/DVDs working on my other machines.
Have you put the DVD drive on another sata controller/ide channel?

---

### Post by UltraTiga on 2011-08-11
Hi there.  I concur with the last person.   I would move the physical drive
to another machine.  If the drive doesn't work there, then the drive is dead.

Process of elimination. 

Now, the other issue could simply be if the drive has been in the machine for some time and it has never been used, possibly there is simply some dust on the lens of the reader.  The simple solution would be to clean it. 

I would suggest removing it from the machine without any power to it when you do this.

---

### Post by server_fan on 2011-08-11
Hey All,

 Thanks for the tips. I have also tried using an external USB drive with this machine. The BIOS detects the drive and does make an attempt to boot from it, however I get the same error as the other drive. "DVD Not Found". I have tested the discs in other computers and they work flawlessly. My sample discs include an Ubuntu Server 11.04 Server, and a Fedora 15(?) DVD disc as well. 

Still no solution.

---

### Post by bab1 on 2011-08-11
> **server_fan said:**
> Hey All,

 Thanks for the tips. I have also tried using an external USB drive with this machine. The BIOS detects the drive and does make an attempt to boot from it, however I get the same error as the other drive. "DVD Not Found". I have tested the discs in other computers and they work flawlessly. My sample discs include an Ubuntu Server 11.04 Server, and a Fedora 15(?) DVD disc as well. 

Still no solution.

My guess is this machine (HP-UX) boots more like an "Apple with Intel" than a normal Intel/BIOS setup.  Try looking at EFI BIOS stuff for the answer.  See [_[COLOR="Blue"]here[/COLOR]_]("http://www.google.com/search?client=ubuntu&channel=fs&q=EFI+Boot+Manager&ie=utf-8&oe=utf-8#pq=efi%20boot%20manager&hl=en&cp=22&gs_id=n&xhr=t&q=EFI%20Boot%20Manager%20HP-UX&qe=RUZJIEJvb3QgTWFuYWdlciBIUC1VWA&qesig=xAG-JqiJcOTd4KPe4zD-Og&pkc=AFgZ2tmPOsxhdgHTtNYu-qoVzWmiCsICbmKmAJC3bqBGGtLVPGC63R0ekcxaeu0oN33sxLMtWisNfGEsIUIWE6cOwMGxMUj0hA&pf=p&sclient=psy&client=ubuntu&channel=fs&source=hp&pbx=1&oq=EFI+Boot+Manager+HP-UX&aq=f&aqi=&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.&fp=e7cad2287860ab4d&biw=1141&bih=626") for basic information.

---

