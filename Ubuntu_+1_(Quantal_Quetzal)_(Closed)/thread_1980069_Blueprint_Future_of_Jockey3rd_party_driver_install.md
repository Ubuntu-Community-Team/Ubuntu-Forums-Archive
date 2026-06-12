---
title: "Blueprint: Future of Jockey/3rd party driver installation"
date: 2012-05-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-05-14
Hi everyone,

This blueprint initially considered merging Jockey functionality into Ubiquity. Now Ubiquity is no longer mentioned and was replaced by software-center in specs.
 
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-third-party-driver-installation](https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-third-party-driver-installation)

There's a first draft and mockup at [https://wiki.ubuntu.com/SoftwareAndUpdatesSettings#drivers](https://wiki.ubuntu.com/SoftwareAndUpdatesSettings#drivers)

A large part of what we discuss here every cycle and the support requests we see everywhere are related to Grub after install, Ubiquity/Partitioning and Jockey/Drivers. A huge improvement to Ubuntu can come out of this effort.

I have already contacted developers to let them know we're available to test alpha/beta releases of this implementation, do custom testing, live testing at IRC, whatever they need from us in testing to make it as good as possible.

Regards,
Effenberg

---

### Post by dino99 on 2012-05-14
yes the first task is to fix all the ubiquity bugs around, get too many releases with this nightmare. Its good to built a great distro, but if the installer is a pure crap, then ...

---

### Post by ronacc on 2012-05-14
my test box has over a gig of space available for installs and another gig for persistent data , during any 6mo cycle I not only have a few Buntu,s on it I aslo do installs of several other distros , .deb based , .rpm based and  gentoo based , I am continually appalled at how much better the other distros handle the install especially networking and partitioning ( including grub ) .


edit: I will gladly test anything that might improve Ububtu in that respect .

---

### Post by balloons on 2012-05-14
As you've seen ubiquity and jockey are getting some major coding done this cycle. I'm glad to see everyone chipping in to help make sure this attention moves ubuntu forward instead of backwards :-) Kudos!

---

### Post by dnewkirk on 2012-05-14
Do we have plans to implement a db of hardware available with different users? For instance, I have several generations of nvidia hardware along with a radeon HD 7770, which might be useful. This was mentioned in passing at UDS, but it might help to make sure that the largest range of cards is tested so we get fewer "Card X doesn't seem to work" bugs because something was overlooked.

---

### Post by effenberg0x0 on 2012-05-14
> **dnewkirk said:**
> Do we have plans to implement a db of hardware available with different users? For instance, I have several generations of nvidia hardware along with a radeon HD 7770, which might be useful. This was mentioned in passing at UDS, but it might help to make sure that the largest range of cards is tested so we get fewer "Card X doesn't seem to work" bugs because something was overlooked.

Hi dnewkirk, I think that was the idea for a while with stuff like the "[COLOR="Red"]_[Friendly]("https://friendly.ubuntu.com/")_[/COLOR]" initiative (details [COLOR="red"]_[COLOR="red"][U][here]("https://wiki.ubuntu.com/UbuntuFriendly")_[/COLOR][/U][/COLOR]). 

Everyone that runs the "System Testing" and/or "Checkbox" applications also have a Hardware Profile uploaded to Launchpad at [https://launchpad.net/~YourLPUserName/+hwdb-submissions](https://launchpad.net/~YourLPUserName/+hwdb-submissions).

Now, to be honest, I have no idea on the amount and quality of data gathered, how it is stored, how it is used, etc. I have worked with data mart / data warehouse / data mining for a while and know that a lot of statistics must be applied to such a database in order to reach any safe conclusion. There's science in making it work reliably.

One of the comments I had added to this UDS QA-Related Blueprints suggested we do what Fedora does: When a user installs a Development Release, a hardware profile is automatically created and the user is only informed of that and asked to click yes to accept the upload of the info. Someone using the Development Release supposedly wants to help improve the final product. 

I'm kind of lost here which Blueprint it was and if it was discussed or not. I had problems accessing the pads, flaky and sometimes too low audio of the meetings, the Blueprints have been updated already and I'm still trying to understand and summarize what was accepted or not. 

Guitara is the man for all this info I think.

When I think of a working hardware database, the first think I imagine is that the installer could test the hardware compatibility before initiating the install/upgrade. A simple DB query would do. If we could warn the user to not proceed in specific cases, that would be great, avoid a lot of support and frustration/bad branding.

Regards,
Effenberg

---

### Post by grahammechanical on 2012-05-15
I am ready for testing this. I am also willing to test Nouveau. I have got reduced size launcher icons, transparent top panel and launcher panel along with wobbly windows under Nouveau and without Nvidia and I would like to keep it that way.

Regards.

---

### Post by Lyfang on 2012-06-22
Will future versions of Jockey add proprietary printer, scanner, webcam drivers too etc.?

---

