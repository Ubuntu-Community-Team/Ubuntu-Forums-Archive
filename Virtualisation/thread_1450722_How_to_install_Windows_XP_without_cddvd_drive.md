---
title: "How to install Windows XP without cd/dvd drive?"
date: 2010-04-09
forum: Virtualisation
---

### Post by vickoxy on 2010-04-09
Hi,
i would like to install in virtualbox windows xp. I have no external dvd drive, only one MacBook. Can i make any iso image from my original win xp cd, or can i copy win xp cd data to ubuntu and then make some bootable image?

Linux have all images prepared and i can run them in virtualbox, but would love to have win xp in virtualbox on my dell mini 10v. 

Something like that possible?

DualBoot is not an option here... :-)

---

### Post by dcstar on 2010-04-09
> **vickoxy said:**
> Hi,
i would like to install in virtualbox windows xp. I have no external dvd drive, only one MacBook. Can i make any iso image from my original win xp cd, or can i copy win xp cd data to ubuntu and then make some bootable image?


VMware allows you to define the CD device as an actual .iso file for installs, I assume that other VM environments allow similar things in their configuration.

---

### Post by vickoxy on 2010-04-10
> **dcstar said:**
> VMware allows you to define the CD device as an actual .iso file for installs, I assume that other VM environments allow similar things in their configuration.

I have no problem installin xp as guest machine in mac os-just put cd in drive and it goes. But, as said, i have no cd drive on dell mini 10v, and i don´t know if it is possible to make iso image from xp cd in mac os-or, maybe, to copy cd data to Ubuntu and from there make bootable cd image?

---

### Post by dcstar on 2010-04-10
> **vickoxy said:**
> I have no problem installin xp as guest machine in mac os-just put cd in drive and it goes. But, as said, i have no cd drive on dell mini 10v, and i don´t know if it is possible to make iso image from xp cd in mac os-or, maybe, to copy cd data to Ubuntu and from there make bootable cd image?

Google is very handy for this sort of thing:
[http://www.ubuntu-unleashed.com/2007/12/have-cd-or-dvd-lying-around-that-you.html](http://www.ubuntu-unleashed.com/2007/12/have-cd-or-dvd-lying-around-that-you.html)

---

### Post by wilee-nilee on 2010-04-10
Which version of XP do you need I know a legit link to a XP Home sp3 slipstreamed ISO.

---

### Post by vickoxy on 2010-04-10
> **wilee-nilee said:**
> Which version of XP do you need I know a legit link to a XP Home sp3 slipstreamed ISO.

I have Windows XP Home Edition Service Pack 3 - German Version.

So, that would be nice. Thanks!

---

### Post by vickoxy on 2010-04-10
> **dcstar said:**
> Google is very handy for this sort of thing:
[http://www.ubuntu-unleashed.com/2007/12/have-cd-or-dvd-lying-around-that-you.html](http://www.ubuntu-unleashed.com/2007/12/have-cd-or-dvd-lying-around-that-you.html)

Well, i tried that, but in linux mint xfce and on my ubuntu 9.10 i can´t make it. Actually, i made from folders one iso image, but no way i can start installing from it:
```
mkisofs -r -o file.iso /location_of_folder/
```

---

### Post by varunendra on 2010-04-10
If I'm not misinterpreting something, you do, or can have your XP as guest in some Virtual platform already installed on your macbook.
As you said, your virtual machine in this macbook can easily read your XP cd directly.

Then why don't you just create a virtual XP machine on your macbook & then transfer/copy this vm on your ubuntu machine. Then you can run this vm on your ubuntu virtual box (or anywhere you wish). Obviously I'm assuming that you are using same virtualisation software (Virtualbox) on both your macbook & dell mini 10v.

If this isn't the case, then here's another possible workaround:

[LIST=1]
[*]Install XP or ubuntu in virtualbox on your macbook.
[*]Install nero (XP) or brasero (ubuntu)
[*]Insert your XP disc, making sure it is detected as local disc (CD) in virtualbox.
[*]Using nero/brasero, create an iso image of your original XP cd
[*]copy this (bootable) iso to your desired machine.
[/LIST]
Here I'm assuming that your XP cd is already bootable. If not, then reply. I've a solution for that also.

---

### Post by varunendra on 2010-04-10
Hey wait... I read your last reply a bit late.
If you can use mkisofs & copy all the files from your XP cd, then it's extremely easy to create a bootable image.

you just have to download xp boot-sector (.bin) from microsoft's website (around 4kb I think) and tell mkisofs the following:
-no-emul-boot -boot-load-size 4 -b <location of the boot-sector file>

---

### Post by vickoxy on 2010-04-10
> **varunendra said:**
> Hey wait... I read your last reply a bit late.
If you can use mkisofs & copy all the files from your XP cd, then it's extremely easy to create a bootable image.

you just have to download xp boot-sector (.bin) from microsoft's website (around 4kb I think) and tell mkisofs the following:
-no-emul-boot -boot-load-size 4 -b <location of the boot-sector file>

Thanks-i am trying to copy from my macbook xp.vdi, but i can not do it-some error when i try to copy it.

Could you be more specific what should i write to terminal? <location of the boot-sector file> is the location of copied folder?

---

### Post by varunendra on 2010-04-10
He-he...
actually I don't remember the exact command myself:lolflag:
but let me try...

Say, you have following scenario:

[LIST]
[*]you've copied all the XP cd contents to your **/Home/ubuntu/xp** folder
[*]the downloaded boot sector file (say bootsect.bin) to **/Home/ubuntu **folder
[/LIST]
then the command should go as follows:
> mkisofs -b /Home/ubuntu/bootsect.bin -no-emul-boot -boot-load-size 4 **/Home/ubuntu/XP.iso** /Home/ubuntu/xp/
This should create XP.iso file in /Home/ubuntu folder. You may also need to add "-joliet-long" option.

But I repeat, I don't remember the exact command although I've done it successfully a few months ago. So you may have to struggle a bit.
Good luck !:popcorn:

---

### Post by varunendra on 2010-04-10
Here's exactly what I was trying to explain (but beware! The author here too, says that he hasn't tested it yet):
> [http://www.macosxhints.com/article.php?story=20080416134218](http://www.macosxhints.com/article.php?story=20080416134218)

It is especially meant for using mkisofs on mac. However, what I had tried successfully was not that lengthy command !

---

### Post by vickoxy on 2010-04-10
> **varunendra said:**
> He-he...
actually I don't remember the exact command myself:lolflag:
but let me try...

Say, you have following scenario:

[LIST]
[*]you've copied all the XP cd contents to your **/Home/ubuntu/xp** folder
[*]the downloaded boot sector file (say bootsect.bin) to **/Home/ubuntu **folder
[/LIST]
then the command should go as follows:

This should create XP.iso file in /Home/ubuntu folder. You may also need to add "-joliet-long" option.

But I repeat, I don't remember the exact command although I've done it successfully a few months ago. So you may have to struggle a bit.
Good luck !:popcorn:


I think i made it-i am running installation. I run in mac os linux mint as guest, and made there with brasero .iso image. Copied it on dell min 10v, and now i am running installation from it.

Hope it will succesfully end it!

Thanks!:popcorn:

---

### Post by varunendra on 2010-04-10
Hooorrrrayyy....
now as soon (if) as the installation finishes, mark this thread as [SOLVED].

congrats in advance ...!

-Varun

---

### Post by vickoxy on 2010-04-10
Thanks-working beautiful...

---

### Post by wilee-nilee on 2010-04-10
Sorry it took this long to get back you have it set but here is the link, don't worry I have installed this version on computers other then the manufacturer who is providing the ISO, it is just XP no key you have to use your own legal one. I realize you have this fixed but it helps to have a ISO at times.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

---

### Post by Jpenguin on 2010-04-11
Mac--
[LIST]
[*]\Inser XP CD
[*]OPEN /Applications/Disk Utility
[*]Select the XP CD
[*]File -> New -> Image from XP SP3
[*]Image format (CD/DVD Master)
[*]Create yor ISO
[/LIST]

---

### Post by vickoxy on 2010-04-14
Jpenguin, wilee-nilee-thanks for answers. I will surely save this threads for the future. I am just glad that i solved my problems using linux. In the last 12 Months i am intensivly using linux (ubuntu derivations) so i just lost touch with other os. 
:popcorn:

---

