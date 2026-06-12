---
title: "I Love Ubuntu but .... can't use it!"
date: 2012-08-25
forum: Testimonials &amp; Experiences
---

### Post by fryups on 2012-08-25
I want to use Ubuntu as my primary OS rather than Windows 7 but just can't make it work properly.  I have installed as dual boot and am impressed with speed and features.  However, 2 specific issues are preventing me from making the jump permanent.  First, and most worrying, is that my Dell XPS 17 Laptop (i5 M560 2.67Ghz 4Gb 64bit) gets far too hot when running Ubuntu 12.04.  It gets so hot that the fan runs almost continuously at high spped and is very hot to touch - it doesn't do this on Windows 7 and I'm concerned it will damage my hardware.  Secondly, I can't seem to install my Lexmark X3600-4600 wireless printer.  There don't seem to be any Ubuntu 64 bit drivers and the time wasted seeking a solution is frustrating.  These aspects are a great shame because Ubuntu seems so good as far as it goes and would release me from Windows BUT it's far too user intensive at present, especially as I'm not that computer literate.  So I'm stuck with Windows ..... because despite all it's over control and weaknesses, it works out of the box, if only Ubuntu did I'd move today!

---

### Post by tartalo on 2012-08-25
Your computer has an Nvidia Optimus, right? Check it with
```
lspci
```

If so, use bumblebee:

[http://www.tautvidas.com/blog/2012/04/disabling-nvidia-optimus-enabled-card-on-ubuntu-12-dot-04/](http://www.tautvidas.com/blog/2012/04/disabling-nvidia-optimus-enabled-card-on-ubuntu-12-dot-04/)

---

### Post by fryups on 2012-08-25
Thanks, it's actually an NVIDIA GeForce GT 435M if that makes any sense if it's the graphics card we are talking about?  Does that make sense, I'm out of my depth here.  Will bumblebee stop the overheating or just the fan?

---

### Post by tartalo on 2012-08-25
According to this your card has the Nvidia Optimus technology:

[http://www.geforce.com/hardware/desktop-gpus/geforce-gt-435m](http://www.geforce.com/hardware/desktop-gpus/geforce-gt-435m)

These cards have actually two graphic chips, one for low power usage and another one for full performance.

Nvidia has not developed the software to control this for Linux, so the graphic card is running at full power all the time, draining the battery and heating the computer.

Bumblebee fills that gap and alows you to set the graphic card in low power mode. More info: [http://bumblebee-project.org/](http://bumblebee-project.org/)

Sorry that I can't help with the printer, perhaps someone else jumps in.

---

### Post by fryups on 2012-08-25
Thanks very much!  That makes sense, I'll reinstall and give it a try

---

### Post by Darren Sparrow on 2012-08-25
As for the Lexmark printer, try here:

[http://support.lexmark.com/index?page=content&id=HO3310&actp=search&viewlocale=en_US&segment=SUPPORT&productCode=LEXMARK_4600_MFP&locale=EN&userlocale=EN_US&searchid=1298654076183#](http://support.lexmark.com/index?page=content&id=HO3310&actp=search&viewlocale=en_US&segment=SUPPORT&productCode=LEXMARK_4600_MFP&locale=EN&userlocale=EN_US&searchid=1298654076183#)

It's an old solution but may stil work with your new install.

---

### Post by fryups on 2012-08-25
Thanks Darren

---

### Post by Bucky Ball on 2012-08-25
> **tartalo said:**
> Bumblebee fills that gap and alows you to set the graphic card in low power mode. More info: [http://bumblebee-project.org/](http://bumblebee-project.org/)



Nice tip. I'll file that. BTW, you aren't really using 6.10, are you?

---

### Post by fryups on 2012-08-26
tartalo, tried that but bumblebee wouldn't install properly.  Seemed to unpack but when I tried to install said it wasn't present.  Laptop runs hot on mains and batttery whenever Ubuntu is used so for now I hate to say I'll revert to Windows.  Sadly Ubuntu is proving too time-consuming.  Thanks nevertheless for your help.

---

### Post by fryups on 2012-08-27
Update for all:

I've been trying to install my Lexmark 3600-4600 series printer for 2 days now.  I've tried every option I can find on the forums but none work.  There does not seem to be a 64 bit driver for Ubuntu 12 so it's proving to be time wasted.  As I said in my 1st post, for Ubuntu to be a genuine replacement for the hated Windows it needs to work without continual 'faffing'.  I accept it's free but regrettably it won't attract Luddites like me when even simple tasks actually aren't simple at all.  I can't use a sytem that I can't print from and one that overheats the laptop.  I also lose other functionality that Windows provides like my built in DVB TV tuner (UK) and a good face recognition program.

As I said, it's a great shame as Ubuntu has got lots going for it but it just doesn't work for me - maybe I'll have to buy a Mac to escape Windows?

Thanks again for the community help!

---

### Post by SeijiSensei on 2012-08-27
Complaining about this to Lexmark would probably be a better investment of time and energy than complaining about it here.

Did you try installing the 10.04 driver that Lexmark reports for your printer [here](http://support.lexmark.com/index?page=content&id=OS4&locale=EN&userlocale=EN_US)?

---

### Post by fryups on 2012-08-27
Thanks SeijiSensei, I didn't complain to Lexmark as they have no incentive to fix this!  I'm not 'complaining' about Ubuntu, merely commenting or observing, there is a difference.  I didn't try the 10.04 driver becaiuse I can't understand the table you posted.  It is a list of drivers but I can't find the site to download them from.  The Lexmark site only has 32 bit drivers so I'm stuck with Windows.

---

### Post by Bucky Ball on 2012-08-27
One solution: Support hardware manufacturers who support Linux and whose equipment is known to work with Linux. That's what a lot of us here do.

You can complain to manufacturers, buy compatible hardware and/or join a dev team (probably out there right now attempting to get this working although Lexmark are a bit of a lost cause when it comes to Linux and avoided).

The Linux community spends hours trying to get these things working. A manufacturer only needs to port an existing driver to Linux. Your issue has nothing to do with Ubuntu but everything to do with Lexmark making it virtually impossible for the outside world to have any idea how to write drivers for most of their hardware. Brother and HP on the other hand; hard to go wrong. 

As for DVB-T, install MeTV, it has an autoscan for channels. Do that and  you should be up and running in no time. I was. As for DAB+ radio,  though, forget it. 

Good luck.

---

### Post by fryups on 2012-08-27
Fair point, if I'm in the market for a new printer I'll do just that.  Thanks for the advice on the tuner!

---

### Post by Bucky Ball on 2012-08-27
*Moved to **Testimonials & Experiences.***

---

### Post by gandaran on 2012-08-27
> **fryups said:**
> Thanks SeijiSensei, I didn't complain to Lexmark as they have no incentive to fix this!  I'm not 'complaining' about Ubuntu, merely commenting or observing, there is a difference.  I didn't try the 10.04 driver becaiuse I can't understand the table you posted.  It is a list of drivers but I can't find the site to download them from.  The Lexmark site only has 32 bit drivers so I'm stuck with Windows.
why not install Ubuntu 32-bits version instead?

---

### Post by fryups on 2012-08-27
Stupid question but will it work properly on a 64 bit laptop?

---

### Post by sffvba[e0rt on 2012-08-27
> **fryups said:**
> Stupid question but will it work properly on a 64 bit laptop?

Yes.


404

---

### Post by fryups on 2012-08-27
OK, I installed using the wubi Windows installer so how do I make it 32 bit?  Do I have to do the (complicated) install via DVD with partitioning etc?

---

### Post by nothingspecial on 2012-08-27
Please start a new thread in one of the support areas. This thread is messy and the title has nothing to do with your current question.

Closed.

---

