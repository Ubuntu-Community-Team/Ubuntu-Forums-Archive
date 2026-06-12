---
title: "Another Miserable Experience"
date: 2012-11-07
forum: Testimonials &amp; Experiences
---

### Post by gmseed on 2012-11-07
Hi

A few weeks ago I posted in this thread my miserable experience using Ubuntu 12.04LTS on my Sony VAIO 32bit laptop.

Here I am again to moan about using Ubuntu 12.10/64bit on a newly purchased Samsung Chronos Series 7 laptop.

I've been using Ubuntu 12.10/64bit for a couple of weeks and it's been ~ok until I did an update of ~55mb of updates. When I boot up now I just get a purple screen.

The problem started earlier when I tried to run the Chromium Broswer by clicking on the icon on the left-hand-side panel, which was installed using the "Ubuntu Software Centre".

If I opened a terminal windows and typed:

$chromium-browser

I got:

Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 460: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

That was the last time I booted, and now I just get a purple screen.

When I previously installed 12.04LTS I used a downloaded CD and the laptop booted from the CD. However, I spent over 2hours trying to get the Samsung laptop to boot from the CD. I read all of the Ubuntu installation instructions and Googled about booting the Samsung, but no luck.

Thus, since Win7/64bit was installed on the laptop I decided to use the Windows Installer. What a mistake! Only after completing the installation did I realise that it had installed 12.10/64bit. I do think the Windows installer should give a user the option of installing 12.04LTS/32bit, which would probably be the recommended download when downloading the install CD.

The laptop is a new model and with an NVidia gpu card and I don't think Ubuntu's support for this device was/is very good.

As I said in my previous moan I do think that the Ubuntu Community should publish recommended desktop/laptop m/cs that are known to work well and upgrades are fully tested. I do think that unless it's a Dell laptop that's a year or so old then you'll have problems - not always but as a rule.

When I install Ubuntu I just want to get on with my own work. I don't want to serve as a guinea pig and spend my time firing up the terminal window and pissing around with low-level stuff. But, regrettably this what I always seem to end up doing.

It's a shame because I like Ubuntu and have tried to get a good build m/c ever since ~version9. I have now over the past 3/4 years attempted to get a laptop working with versions 9,10,11,12,04LTS and 12.10 and each time give up after a few weeks of time wasting.

There's nothing I'd like to more than use Ubuntu but it's back to Windows/Mac for me - again. And this is the key problem for Ubuntu/Linux - I'm confident it continues to lose users time and time again. It's been an experiment for the past 20years and has now reached ~5% of the OS community but I can't see it extending far from this level unless it is shipped with systems such as Nexus7 where all of these low-level driver issues have been thoroughly resolved, tested, tested, and tested again.

---

### Post by MG&amp;TL on 2012-11-07
Unless I'm missing the point: [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

---

### Post by cbennett926 on 2012-11-07
I used the guidelines that MG&TL posted and I have to say I have ran into only a couple problems, and that is because I knowingly bought an incompatible graphics card because I use it for Windows also.

---

### Post by mastablasta on 2012-11-08
> **gmseed said:**
>  
The laptop is a new model and with an NVidia gpu card and I don't think Ubuntu's support for this device was/is very good.

If it's with Nvidia Optimus techonology then support is bad. Nvidia decided nto to give any Linux support for this yet it is becomeing commong on laptops.
> 
As I said in my previous moan I do think that the Ubuntu Community should publish recommended desktop/laptop m/cs that are known to work well and upgrades are fully tested. I do think that unless it's a Dell laptop that's a year or so old then you'll have problems - not always but as a rule.

very much not true. was just checking yesterday on a local webshop they have 17 models preloaded with linux. mostly they are dells form low to higher end and a few "business" HP laptops. Additionally i also saw entry Acer models prelaoded with Ubuntu in shops. however you are correct in your estimate that it is difficult to find which notebook that is not linux preloaded works well in Ubuntu. some AMD hybrid grpahics models have AMD support with proprietary drivers.
 
> **MG&TL said:**
> Unless I'm missing the point: [http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)
 
the problem with Ubuntu certified list is that is has for the most part last years or 2 year old models that are not available in shops anymore. i've been through what OP says myself. despite the flood of available no-OS preinstalled laptops i eventually ended up buying one with Windows starter as it was the only one that fit my needs and could also run linux relatively flawlesly.
 
as i said above i have a better choice in local webshopp however they are also bigger and more expencive type (i.e. not for my and my needs) ;-)
 
also it seems HP has good suppoort as well as Lenovo (aside from selected models form Dell, Asus & Acer). i would avoid Sony since they are usually made for windows though i know some models work well.
 
aside form these major ones there is also ZaReason and System76 (they make good build notebooks but are also a bit expencive)

---

### Post by Tamlynmac on 2012-11-10
> mastablasta
aside form these major ones there is also ZaReason and System76 (they make good build notebooks but are also a bit expencive) 	

Just a heads up. Even ZaReason has hardware issues  (nothing major). I've got a zareason mini that has a hardware switch for  the wifi card. Kind of a pain, but certainly not a game stopper. Sad  part was, they didn't notify me at the time of purchase. Only after  receiving and contacting them, did they acknowledge the hardware key.  Should have asked and confirmed prior to purchase (my fault).

IMHO  it's important that hardware compatibility (including reverse) always  be a concern. I also think it's tough for new users that have limited  experience with PC hardware when trying to install Ubuntu or any other  Linux distro, should they have compatibility issues. It's unfortunate  that many hardware mfgs see the industry through $$$ covered glasses. I  understand why, doesn't mean I gotta like it.

Just my $0.02

---

### Post by uclugLee on 2012-11-10
> **gmseed said:**
> Hi
I've been using Ubuntu 12.10/64bit for a couple of weeks and it's been ~ok until I did an update of ~55mb of updates. When I boot up now I just get a purple screen.


From experience I must ask this question:
Did you look to see what the updates included, or did you see there were updates available and decided to install them?

> **gmseed said:**
> 
I do think that unless it's a Dell laptop that's a year or so old then you'll have problems - not always but as a rule.


I have a 6 month old Dell laptop and an 8 year old Dell laptop (and several models in between).  All Ubuntu versions from 9.04 to current have ran great.

> **gmseed said:**
> 
It's been an experiment for the past 20years and has now reached ~5% of the OS community but I can't see it extending far from this level unless it is shipped with systems such as Nexus7 where all of these low-level driver issues have been thoroughly resolved, tested, tested, and tested again.

I can almost guarantee that your specific laptop make/model wasn't tested during beta.  And the reason I say that is because the last email I got to all the testers only had 12 people on it.  The reason I joined the testing team is because I got tired of things not working correctly. Maybe you could rekindle your Ubuntu-ness and test upcoming versions and submit bug reports.  :)

---

### Post by stalkingwolf on 2012-11-12
i have 12.04 installed on one desktop an emachines with 2 gb ram 160 g hdd
with mate desktop all is fine so far.
I also did the non pae install again with mate on a dell d800  i have to reinstall that, i borked it.  but it was fine.

---

