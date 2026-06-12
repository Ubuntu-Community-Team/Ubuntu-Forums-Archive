---
title: "Current State of Linux support for System76 laptops"
date: 2011-01-09
forum: System76 Support
---

### Post by elusivespoon on 2011-01-09
I'm curious what different users experiences have been with the latest System76 laptops. My DarU2 is giving up the ghost and I'm thinking about going 76 again. Though one frustration I have had is despite System76 supporting the Linux community, Linux has not done the best about returning the favor.

For example, as I upgraded Ubuntu, things like Hibernate and Suspend support got progressively worse. Also webcam support quickly came and went (though part of my frustration with that seems to have been hardware related). When I first got my laptop it seemed every successive upgrade would result in more and more hardware functionality lost. Though my last few upgrades have been a little kinder.

Are there any things on your current laptop that aren't working due to software issues? Or has Linux been better at letting System76 laptops live up to their potential?

---

### Post by jml on 2011-01-09
elusivespoon, I don't feel that this is a Linux issue per se, but one related to the choices and direction Ubuntu's creators are taking.  System 76 does a very good job of supplying computers that run Ubuntu very well.  They do this two ways, by selecting hardware that has good Ubuntu support, and also by writing custom drivers that support features and hardware not well supported by stock Ubuntu.  But it is a moving target.  When they sell a computer, it is optimally tuned to run the current version of Ubuntu.  However, Ubuntu maintains a 6 month release cycle, and tends to use very cutting edge apps.  So when an upgrade is done, it is not uncommon for some breakage to occur.  System 76's policy is to release custom drivers and patches once the new version of Ubuntu is officially realeased.

Here is what I have done to limit headaches when running Ubuntu on a System 76 laptop.  First I always run the current release on my primary computer.  If I want to experiment with a developmental version, or other distro, I run it on an extra laptop (a reatively old computer with modest resources,) that I keep for just this pursose.  Expect breakage if you need/want to run a version of Ubuntu that is under development.  System 76 dpes not release their custom drivers and patches until a version is officially released.

Second.  I value stability over cutting edge.  That is why the version of Ubuntu I run on one of my laptops is version 10.04 LTS.  But when I choose to take an upgrade, I usually wait for a few weeks to l;et the early adopters find and fix the bugs.  I also wait until the custom drivers and patches System 76 suppliess have been downloaded and used for a bit.  Once things quiet down and the number of issues go down, then I will do an upgrade.  Actualy, since I usually go from one long term support (LTS) version to another, I backup my data and do a clean install.  

Third, when I plan to buy a new laptop from them, if given the option, I will select hardware that is more linux friendly.  The intel wilrless cards that are offered as an upgrade to many loptops comes to mind.  While not supported either by System 76 or this forum, I have found that Debian GNU Linux works very well with several System 76 laptops.  I run Debian testing on my DARU1, and Debian Stable on my DARU3.

So, bottom line, I think System 76 computers  still are more Ubuntu/Linux friendly than many other brands of computer hardware.  For the recors, I am not a System 76 employee.  This is simply my opinion.

Joe

---

### Post by RedRat on 2011-01-10
I agree with jml above. My experience with System76 has been excellent. I recently had problems installing a driver for my new Lexmark printer and between System76 and help from Lexmark got the printer functional. I find the System76 people very helpful.

I agree that their machines are optimally tuned to Ubuntu. However, I am conservative and tend to stay with LTS versions of Ubuntu and not jump on every new release that comes down the pike. I would recommend System76 as a good source. Keep in mind that you have a forum here in the forums devoted to System76. 

So far, I give them 5 stars.

---

### Post by isantop on 2011-01-10
Thanks everyone for your kind words! We all appreciate this, and you wouldn't believe how quickly stuff like this circulates around the office!

I'd second what jml has said; Intel wireless cards the the biggie. The default cards are getting better every day, and I have a confirmation that they work in Puppy Linux now, but if you have any doubt, go with Intel. They are faster anyway. Everything else should be okay. 

Take into consideration what version of what distro you want to use; each choice has benefits and drawbacks. I'd recommend something based on Debian, as it's a lot easier to support a common format. I'm not sure anyone in the office has major experience with RPM, and I always think it's better not to tempt fate.

---

### Post by jml on 2011-01-12
I don't intend to start a flame war, but I have always had problems with RPM based distros, (Fedora, OpenSUSE, Mandriva, etc.)  The package management systems have always seemed extremely slow to me, and a bit buggy, not always correctly handling dependancies.

I agree with isantop.  .deb based distros just seem to work better for me both on System 76 hardware, and other manufacturer's machines as well.  Ironically, the one RPM based distro I do like, PCLinuxOS actually uses apt as its package manager.

Joe

---

### Post by jml on 2011-01-12
I don't intend to start a flame war, but I have always had problems with RPM based distros, (Fedora, OpenSUSE, Mandriva, etc.)  The package management systems have always seemed extremely slow to me, and a bit buggy, not always correctly handling dependancies.

I agree with isantop.  .deb based distros just seem to work better for me both on System 76 hardware, and other manufacturer's machines as well.  Ironically, the one RPM based distro I do like, PCLinuxOS actually uses apt as its package manager.

Joe

---

### Post by jml on 2011-01-13
Sorry for the duplicate post.  Can one of the forum admins delete the duplicate?

Joe

---

### Post by bill516 on 2011-01-15
My PanP4 has been through several versions of Ubuntu with no loss of functionality I can attribute to a hardware-software mismatch.  Do note that like several others I have tended to stay with the LTS releases.  I currently run 64 bit 10.04 and I see no reason to fool with it.  I have run this with and without the System 76 driver. It seems to make no difference. 

I also am having very good luck with Debian Squeeze, which seems similarly robust.

Mepis 8.5 is very nice, but while suspend to ram works, suspend to disk does not.

If I want to play out on the end of the diving board I install sidux/aptosid.  Again, everything typically works, though usually after some fiddling around.

Were I to purchase another machine, an Intel wireless card is a must-have.  I probably will look for an Nvidia driver unless somebody makes a compelling case for ATI.

Depending on where Ubuntu goes I may or may not stay there.  If it comes with my next System 76 I'll look at it.

As for System 76 if they continue to offer fair prices and outstanding technical support I will be back.

Of course, if they do a laptop with a 4 oz battery that lasts 24 hours between charges I'll be back sooner!  :)

---

### Post by isantop on 2011-01-17
> **bill516 said:**
> Of course, if they do a laptop with a 4 oz battery that lasts 24 hours between charges I'll be back sooner!  :)

Actually, we may be on to something there. The new Serval Professional, which, historically hasn't had great battery life, get's just shy of three hours of life on a single charge, whereas the old one was lucky to get one. If this trend continues, you can expect to see System76 as a real contender in the battery front.

---

