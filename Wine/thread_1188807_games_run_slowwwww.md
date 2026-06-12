---
title: "games run slowwwww"
date: 2009-06-16
forum: Wine
---

### Post by Kasra97 on 2009-06-16
I have installed chicken invaders 3 on my sony fw 290 using wine. but after I want to play it is just too slow. I have installed other games but all of them are like this. 
Why is that?

---

### Post by Duskao on 2009-06-16
Hey Kasra. Sorry, we need a bit more information to be able to help your or let you know what the problem might be. 

What version of Wine are you using, also what video card is in your computer and what are your computer specs.

---

### Post by halovivek on 2009-06-16
Hi 
can you post more details about your system.
whether you are using ubuntu 8.10 or latest one.
Please give full details so it will easy for us to help you.

---

### Post by Kasra97 on 2009-06-16
wine 1.1.23
ubuntu 8.10
ati radeon hd 3650

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> wine 1.1.23
ubuntu 8.10
ati radeon hd 3650

because ATis Linux drivers suck.

but even then, it shouldnt be that slow. did you install the official driver?

---

### Post by Kasra97 on 2009-06-16
Where can I download it?

---

### Post by Kasra97 on 2009-06-16
What do you mean?

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> What do you mean?

lol soz, that wasnt ultra clear. I meant how long have you used Ubuntu for?

how comfortable are ya with the Terminal?

---

### Post by Kasra97 on 2009-06-16
yesterday.
But i have used terminal for downloads and to install wine.
I can't write codes but I copy them from internet.

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> yesterday.
But i have used terminal for downloads and to install wine.
I can't write codes but I copy them from internet.

okkkk, do you have MSN? 
it would be easier to talk you through it in realtime.

---

### Post by Kasra97 on 2009-06-16
No, I don't.

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> No, I don't.

ughhhh, ok.

are you using 32Bit or 64Bit?

---

### Post by Kasra97 on 2009-06-16
64

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> 64

kk, download this file to your desktop;

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-6-x86.x86_64.run)

and come back here when its finished downloading...

---

### Post by Kasra97 on 2009-06-16
It does not comes it says Data transfer interrupted.

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> It does not comes it says Data transfer interrupted.

oh mannnnnnnnnnnn.

do you have **ANY** IMing account like AIM or something?

---

### Post by Kasra97 on 2009-06-16
no

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> no

ugh then Im sorry. I cba to write out a detailed guide at the mo.

good luck (y)

---

### Post by Kasra97 on 2009-06-16
where?

---

### Post by nolliecrooked on 2009-06-16
> **Kasra97 said:**
> where?

hmmm?

---

### Post by Meow27 on 2009-06-16
kasara, he meant if you have a 
hotmail account (msn)
msn account(msn)
yahoo account(YIM)
gmail account (Gtalk)

if you do just log in pidgin in respect to the above then contact him.

---

### Post by nolliecrooked on 2009-06-16
> **Meow27 said:**
> kasara, he meant if you have a 
hotmail account (msn)
msn account(msn)
yahoo account(YIM)
gmail account (Gtalk)

if you do just log in pidgin in respect to the above then contact him.

I think he/she understood dude.

---

### Post by Hairy_Palms on 2009-06-16
i dont have ATI but shouldnt the driver be available under jockey in System->Administration->Hardware Drivers

---

### Post by nolliecrooked on 2009-06-16
> **Hairy_Palms said:**
> i dont have ATI but shouldnt the driver be available under jockey in System->Administration->Hardware Drivers

yea, but that driver in 8.10 is really, really bad.

---

### Post by Hairy_Palms on 2009-06-16
could try the .debs from 
[http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/)

there updated to driver 602 whereas the repos have 600, i had to get the updated nvidia driver from there because i compiled the 2.6.30 kernel and it seemed to break with the current jaunty version.

---

### Post by nolliecrooked on 2009-06-16
> **Hairy_Palms said:**
> could try the .debs from 
[http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/](http://archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/)

there updated to driver 602 whereas the repos have 600, i had to get the updated nvidia driver from there because i compiled the 2.6.30 kernel and it seemed to break with the current jaunty version.

its **ALWAYS** best to stick with the vanilla drivers, downloaded **DIRECTLY** from the card makers/manufacturers site.

---

### Post by Hairy_Palms on 2009-07-03
yea but, vanilla drivers arent handled with DKMS and if the OP is new you have to drop to a tty and kill X to install them. :P making the updated debs far more useful imo

---

### Post by Th3_uN1Qu3 on 2009-07-03
Umm, i did not have to kill X to install the latest ATi drivers and i have a similar card.

---

### Post by Torgas Prim on 2009-07-03
I would suggest switching to 8.04 and install the restricted driver and the ATI control panel.Move the slider to Performance. I play GW, WoW, D2, NWN and they are all rockin' with this setup.

My system:
Intel Dual Core 3.0 processor
1mb DDR2 ram
ATI HD2400 AGP 128
SATA drives

It is not perfect but this is the only distro I found to work with the HD2000 - 3000 series cards.

---

