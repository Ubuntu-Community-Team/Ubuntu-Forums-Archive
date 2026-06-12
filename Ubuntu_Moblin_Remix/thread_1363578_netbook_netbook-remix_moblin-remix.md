---
title: "netbook? netbook-remix? moblin-remix?"
date: 2009-12-24
forum: Ubuntu Moblin Remix
---

### Post by jerrylamos on 2009-12-24
# ubuntu-moblin-remix/
# ubuntu-netbook-remix/
# ubuntu-netbook/

Hi, any clue from anyone what the differences are between the three?
Do I download all 3 and burn them to CD's to find out?

Thanks much, Jerry

---

### Post by pwnst*r on 2009-12-27
i'm not sure of the differences, but i can tell you that i've been using moblin for the past few days and am absolutely loving it.  netbook remix was okay, but moblin is definitely more polished.

---

### Post by aljoriz on 2009-12-27
> **pwnst*r said:**
> i'm not sure of the differences, but i can tell you that i've been using moblin for the past few days and am absolutely loving it.  netbook remix was okay, but moblin is definitely more polished.


Moblin is indeed good but how do you install open office and other applications on it?

---

### Post by pwnst*r on 2009-12-27
there's an installer, but i've not used it at all.  as far as open office, this may still be relevant:

[http://moblin.org/community/blogs/imad/2009/moblin-v20-beta-netbooks-and-nettops-its-here](http://moblin.org/community/blogs/imad/2009/moblin-v20-beta-netbooks-and-nettops-its-here)

> Update 2
Submitted by rvndmnmt on 15 December 2009 - 12:01am.
BOOYAH!!!!

After many hours I think I finally figured out how to install Open Office on Moblin. Well you can do the install from the file browser but it does it in usr. Not good since it wont install the shortcuts or java.

Go here [http://wiki.services.openoffice.org/w/images/7/7e/Installation_Guide_OOo](http://wiki.services.openoffice.org/w/images/7/7e/Installation_Guide_OOo)... and get the installation pdf. Go into the terminal and su into root and scroll down to the RPM install section. The su part is doubly important since you need to be in root to install java. I tried adding the symbolic link from a previous install of java and it wouldn't recognize it.

Follow the RPM directions up to the desktop-integration command. When you get to step 7 they give you this command string rpm -Uvh openoffice.org-dist-menus-release.noarch.rpm. Use this for dist and release rpm -Uvh openoffice.org3.1-redhat-menus-3.1-9420.noarch.rpm.

Since this version of Moblin is based off of Fedora and since Fedora was bought out by Redhat. It's the logical choice.

Anyways. The icons popped up in the office section of the applications menu and the program seems to work.

Figured since this was a point of contention some people would like to know.


---

### Post by zeroseven0183 on 2009-12-27
Would you know if Moblin works well with Acer Apsire One? We've tried creating a live USB following the instructions on [this page]("http://moblin.org/documentation/test-drive-moblin/using-moblin-live-image") but it stops after selecting the Boot Only option from the menu.

We used the same application to create UNR and was able to run (live) smoothly on the same netbook.

What could be the problem?

---

### Post by aljoriz on 2009-12-27
what software did you use to 'byte-copy' the files?

to test if your live is done correctly, try running moblin w/o installing it to the HDD? 

Use ubuntu Imagewriter and make sure that the checksum is the same.

---

### Post by pwnst*r on 2009-12-28
> **zeroseven0183 said:**
> Would you know if Moblin works well with Acer Apsire One? We've tried creating a live USB following the instructions on [this page]("http://moblin.org/documentation/test-drive-moblin/using-moblin-live-image") but it stops after selecting the Boot Only option from the menu.

We used the same application to create UNR and was able to run (live) smoothly on the same netbook.

What could be the problem?

not sure on that one.  aljoriz has some valid tips though.  try those first.

---

### Post by maethor on 2009-12-31
> **aljoriz said:**
> Moblin is indeed good but how do you install open office and other applications on it?

If you're using the Ubuntu Moblin Remix, then it's pre-installed - everything you're used to using in Ubuntu is available in UMR (though I've noticed a few things are a bit odd thanks to the Moblin UI). You can find Synaptic by going to Application page, going to settings and selecting Package Manager.

If you're using "pure" moblin, have a look at the Moblin Garage App installer [http://garage.moblin.org/](http://garage.moblin.org/) as it looks like that will have it.

---

### Post by aljoriz on 2010-01-02
> **pwnst*r said:**
> there's an installer, but i've not used it at all.  as far as open office, this may still be relevant:

[http://moblin.org/community/blogs/imad/2009/moblin-v20-beta-netbooks-and-nettops-its-here](http://moblin.org/community/blogs/imad/2009/moblin-v20-beta-netbooks-and-nettops-its-here)

Installing open office on moblin2.1 is easy but the standard tool bar becomes an entire black stuff, let your mouse go over the invisible standard tool bar and it becomes 'visible' still why would I suffer with moblin when UNR 9.10 does the job better?

Improved boot time does not justify the inability to install most of the open source software available but I admit that a social networking based GUI seems to be the trend of tomorrow.

---

### Post by cyberghoser1 on 2010-01-07
I used both Moblin & Moblin-Remix(Ubuntu) and i still like UNR on my AAO 110L, i don't really like a Social networking GUI, well if moblin add a facebook on desktop show instead of Tweeter i might reconsider it ;-)

---

### Post by aljoriz on 2010-01-09
I think that's the plan for 10.4, social networking gui seems to be the on going trend nowadays.

---

### Post by maverick340 on 2010-01-24
The original question remains still remained unanswered! Whats the difference between ubuntu-netbook/ and ubuntu-netbook-remix/

---

### Post by danageis on 2010-04-14
> **maverick340 said:**
> The original question remains still remained unanswered! Whats the difference between ubuntu-netbook/ and ubuntu-netbook-remix/

I'm fairly certain there is no difference, although I am kind of confused as to what the thread is talking about? Are they like IRC channels or something? If you are talking about the URLs of the Ubuntu images at cdimages.ubuntu.com, then I would imagine that ubuntu-netbook and ubuntu-netbook-remix are both for ubuntu netbook remix. They seem to do this a lot, for example they have two pages for 9.10, one has 9.10 in the url and one has Karmic, but they have the same downloads on both pages.

Kind of off topic, but I only came across this thread because I am trying Ubuntu Moblin 9.10 right now and since 10.4 is only a ways off, I was wondering if I should install 9.10 or not. Ubuntu doesn't list anything about Moblin on their site, does anybody know if there will be a 10.4 version of UMR when netbook remix and the desktop version are released?

---

### Post by rudihawk on 2010-04-16
You could wait about 14 days until 10.04 is released, the UNR is exactly the same as the desktop version with a few extra packages.

---

### Post by skorange on 2010-04-19
Ubuntu Netbook is shorthand for Ubuntu Netbook Remix.

As for difference between UNR and regular Ubuntu, the biggest difference is in the desktop GUI.  UNR defaults all windows to full screen, and combines the application title bar with the menubar.  This saves vertical screen real estate, which is handy for netbooks as most come with widescreen displays.  Windows can be made non-full screen by right clicking the title and selecting or just pressing alt-f10.

Additionally, the application menu is much larger, with larger icons and covers the entire display (I think this is making it's way into 10.4 standard Ubuntu?).

As for the actual binaries, does anyone know if they're compiled differently than standard Ubuntu? Do they have 'atom' optimizations turned on?

---

