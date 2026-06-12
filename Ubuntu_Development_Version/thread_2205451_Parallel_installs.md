---
title: "Parallel installs"
date: 2014-02-13
forum: Ubuntu Development Version
---

### Post by felgro on 2014-02-13
Hi,

I ended up installing Trusty alpha because it was the only thing I could get to run with my new laptop's vid card - and that was a tortuous process I do not wish to go through again. As newer releases of Trusty come out, I would like to have a staging partition to test their compatibility. So this would entail a triple boot configuration with Trusty's Grub implementation - Win8.1/Trusty (current)/Trusty (updated).

My question is - are there any dangers I need to be aware of? Is this a safe thing to do?

---

### Post by Bucky Ball on 2014-02-13
Not that I can think of. Yes, safe thing to do. Running Trusty in the first place at this stage is probably not a 'safe' thing to do and I wouldn't be using this as a work/production machine or in any environment that need reliability and stability. 

Install Trusty to its own partition and install its grub to the SAME partition. Then boot back into the original install and 'sudo update-grub'. That will pick it up and add.

For the second install, you don't need another /swap. Just choose 'Something Else' and partition/install manually. Mark the /swap partition to use. The install will automagically default to the existing /swap. This can be done with the /home partition also, if you have one.

---

### Post by felgro on 2014-02-14
> **Bucky Ball said:**
> Running Trusty in the first place at this stage is probably not a 'safe' thing to do and I wouldn't be using this as a work/production machine or in any environment that need reliability and stability. 

I don't have a choice. Neither 12 nor 13 will run on my hardware.

> Install Trusty to its own partition and install its grub to the SAME partition. Then boot back into the original install and 'sudo update-grub'. That will pick it up and add.

For the second install, you don't need another /swap. Just choose 'Something Else' and partition/install manually. Mark the /swap partition to use. The install will automagically default to the existing /swap. This can be done with the /home partition also, if you have one.

OK, thanks. That's what I needed to know.

---

### Post by Cavsfan on 2014-02-15
You could also have a go with a custom grub menu from the wiki in my signature after you get it all installed. All you have to do is specify partitions.

Seems a shame you can't find a stable version of Ubuntu to install though. Like Bucky Ball said it is not a good idea to have a development OS as your main OS.

Here is what mine currently looks like. I have Precise 12.04, Mint 13, Windows 7 along with Trusty installed.

[[IMG]http://www.zimagez.com/miniature/20140130153140.jpg[/IMG]]("http://www.zimagez.com/zimage/20140130153140.php")

---

### Post by grahammechanical on 2014-02-15
It is fine to have more than one version of Trusty installed. I only issue I have is identifying which install is which at the Grub menu. Cavfans's suggestion is a good idea. I also notice an improvement with Grub 2.20 that Trusty now has. We get labels that tell us which partition the OS is on. So, if (for example) the "staging" Ubuntu is on sda6 then Grub will say so.

I do think that it a good idea to test the next version of Ubuntu to see if we can make the modifications we like before we upgrade or install it as our main Ubuntu. I used to do this before I started using the development version.

Regards.

---

### Post by Cavsfan on 2014-02-16
> **grahammechanical said:**
> It is fine to have more than one version of Trusty installed. I only issue I have is identifying which install is which at the Grub menu. Cavfans's suggestion is a good idea. I also notice an improvement with Grub 2.20 that Trusty now has. We get labels that tell us which partition the OS is on. So, if (for example) the "staging" Ubuntu is on sda6 then Grub will say so.

I do think that it a good idea to test the next version of Ubuntu to see if we can make the modifications we like before we upgrade or install it as our main Ubuntu. I used to do this before I started using the development version.

Regards.

Thanks grahammechanical. Yes, you label each entry with whatever text you want and you completely control what displays on the grub screen.
Then on the inside, you could label each partition with this command (this can also be done in Gparted):
```
sudo tune2fs -L "Trusty-main" /dev/sda3
sudo tune2fs -L "Trusty-backup" /dev/sda4  
```

This makes them much more easy to identify.
This is how Nautilus looks in Trusty and you can see the three partitions I labelled this way:
[ATTACH=CONFIG]250389[/ATTACH]

---

