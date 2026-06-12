---
title: "Buying a new PC for Studio - quad core etc advice sought!"
date: 2011-01-29
forum: Ubuntu Studio
---

### Post by pr2 on 2011-01-29
Hi 

I'm about to buy a new machine, old one is getting very old now. I would like to use my Delta 44, that I have just managed to get working with Studio 10.10 in my current setup. Thanks to help from forum :)

But I don't want to buy a machine thats not going to work properly. I would like to buy something with high specs to last for some years to come. Its purely to run Ubuntu studio. I'd be happy doing the same workarounds for current problems, but would prefer not to encounter any new ones.

Suggested ram size 4GB ram. ?
Do I go with 64bit or 32bit?
I'm happy to do the same fixes I did with my current 32bit 10.10 install, but I would rather max. out the 32bit system and have no issues.
Will everything still run ok with a Dual or Quad core? Will this help things to run quicker etc?
Are there any of the newer processors that I should NOT buy- i.e that have issues?
Intel or Athlon?

Thanks all 
br
Paul R

---

### Post by cchhrriiss121212 on 2011-01-29
Regarding CPUs: the newest ones will run fastest due to improved architecture, but these will be the most expensive, multiple cores will help when running many processes but won't give extra speed. The only issues I have seen seem to be around integrated graphics, so get a dedicated PCIe card, Nvidia gt2xx preferably.

4GB is fine for RAM, more than that is overkill. 64bit is what I use, there are only a handful of things that work better on 32bit now.

If you want better performance, look into an SSD which would mean your system and programs boot in seconds. With Linux all you need is 10GB for a root partition, and you can get 30GB SSDs for quite cheap now. 

A lot of this will depend on your budget of course, and before buying a new machine you could try tweaking the current one. You might be surprised the difference a lightweight DE can make to performance. For audio work you really don't need a high end machine anymore, low to mid end hardware is now quite powerful enough for it. 

If you are building this yourself, don't skimp on things like the power supply and case. For audio work you don't want something that will give you excess noise, and cheaper PSUs are very loud.

---

### Post by JRV on 2011-01-29
Use Nvidia graphics cards.

The Linux drivers for ATI cards never seem to work right.

---

### Post by pr2 on 2011-01-29
Thanks Chris/JRV
 
I like the idea of upgrading current rig. Main processor can be upgraded from a 2.8 to a 3.2 Pent 4 cheaply I think.I replaced the fans recently as they drive me up the wall!
 
Replacing the ATA IDEs with SDD seems a great idea. Its not a cheap option as I make fairly big audio files often 100MB/piece as high resolutions. I'd want at least 128GBs of space - I fill 80Gb with data at the moment. But I think the Disk response time is what is really slowing down this machine.
 
Do I just need a serial ATA connector on the motherboard in order to plug it in?
 
many thanks
PR

---

### Post by pr2 on 2011-01-29
Not having fans at all would be so nice! Have you seen the mineral oil things on Youtube?!

---

### Post by cchhrriiss121212 on 2011-01-29
Upgrading from one P4 to another won't really make much difference. You are better off saving the cash up and buying something more recent. But if it is cheap enough then it couldn't hurt. 
> I like the idea of upgrading current rig.
What I meant was that you change the software and not the hardware, one advantage of Linux is that you can run a lighter system and still have all the features you need.
> Do I just need a serial ATA connector on the motherboard in order to plug it in?
Yes, most SSDs will be SATAII. If your board is old it might not have SATA ports, so check before you buy anything.
> Its not a cheap option as I make fairly big audio files often 100MB/piece as high resolutions. I'd want at least 128GBs of space - I fill 80Gb with data at the moment.
The thing is you don't need to rely on just one drive. What I meant earlier is that you have just the OS and programs on one small SSD, and then use another drive for data and such. This is easy with linux as you can specify separate root and /home partitions when you install.
> Not having fans at all would be so nice! Have you seen the mineral oil things on Youtube?!
Yes, but they are not worth it when you consider maintenance and cost. As long as you get decent fans and keep temperatures low, noise should not be an issue.

---

