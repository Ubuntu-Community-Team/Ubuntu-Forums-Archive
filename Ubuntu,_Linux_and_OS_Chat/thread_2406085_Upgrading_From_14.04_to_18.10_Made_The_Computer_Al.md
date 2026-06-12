---
title: "Upgrading From 14.04 to 18.10 Made The Computer Almost Unusable"
date: 2018-11-15
forum: Ubuntu, Linux and OS Chat
---

### Post by braznyc on 2018-11-15
I had a computer that worked ok with Ubuntu 14.04.
After upgrading it to Ubuntu's newest version it became almost unusable.

If I have Libreoffice, Chrome and Gimp open at the same time I just can't do anything. The memory is completely used.


What are you trying to do?


To me it seems more like bloat than something the users really need. The use of RAM is ridiculous.

---

### Post by QIII on 2018-11-15
"We" are not trying to do anything.  "We" are volunteer end-users such as yourself who are neither employed by nor compensated by Canonical.

Your problem is likely not bloat, but a consequence of upgrading rather than re-installing.  A number of factors can play into that, including the failure to first remove any proprietary drivers prior to upgrade.  Upgrading from one LTS to another is risky enough.  Upgrading when passing over an intermediate LTS is more risky still.

While upgrading works for many people, it causes headaches for many and we often provide support for those people.  For that reason, you will find that most of us here recommend a fresh re-installation of the newer release rather than an upgrade.

Would you please run top or htop and, at the point where you encounter a slowdown, copy and paste the results ***in a support sub-forum*** so that we can take a closer look?

---

### Post by braznyc on 2018-11-15
I just think the developers should consider the history of Linux that could be used in older computers. The use of memory of the new Gnome and KDE are too much. There must be something that could give us the latest technology and at the same time keep the usage of memory in a acceptable level.
Desktop environments should not be competing with programs for the processor and RAM.

---

### Post by QIII on 2018-11-15
Again -- the excessive use of memory may be the result of upgrading rather than reinstalling.  Please start a thread in an appropriate support sub-forum.

If you would like to contact the developers and deliver your message (they don't hang out here), I suggest joining [this mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-devel-discuss").  The Ubuntu Forums are a peer-to-peer support venue, not a bug reporting or developer contact venue.

There are official Ubuntu flavors that use lighter DEs, such as Xubuntu and Lubuntu.

GNOME, KDE and other DEs are developed by communities outside of Canonical, which simply includes them as interfaces.  Canonical tried to develop its own in-house DE and that did not turn out well in the end.

---

### Post by angisky on 2018-11-18
I wonder why it's such a bad experience upgrading from 14.04 to 18.04 when I just recently upgraded one of my systems from 16.04 to 18.04 and it worked flawlessly. The only issues I had was rdp server was no longer supporting h264 but I looked it up and it seems to be a general 18.04 problem not even being caused by the upgrade. I just changed the colors on the client side and it worked perfectly fine. I haven't had any issues with the upgrade after that. Im probably gonna do the same upgrade sometime in the near future on one of my laptops.

---

### Post by mastablasta on 2018-11-19
because there were plenty of major changes between the versions (a large number of AMD chips are for example no longer supported with proprietary drivers with 16.04). upgrade from 14.04 to 16.04 and then to 18.04 should still work well. however, it should be noted that upgrades work well only if the user hasn't made any major changes to the OS (e.g. installed customised stuff, made major changes to system settings...).

to the OP - open a new thread in appropriate forum for proper troubleshooting. also commands like top or htop (or using the gnome system monitor) will show you what process is consuming the RAM.

---

### Post by HermanAB on 2018-11-20
Install xfce4, then log out and log in again with the XFCE desktop.  The machine should be nice and fast then.

---

### Post by RabbitWho on 2018-11-24
I only every do clean installs of new operating systems, purely because the number of troubleshooting threads for people who didn't put the fear in me. If it is at all possible for you to do it, I bet it will be fine with a clean install. Also there is a minimal install button now which is FANTAMAZING I love it.

---

### Post by k9r4n on 2018-12-05
What is the general amount of storage and RAM requirements for 18.10? I ran 18.10 on my TOSHIBA 660D and, while it was quite slower than Windows 10, did a good job, especially since this computer is like 8 years old now. I think Ubuntu is doing pretty good for an open source OS that still supports devices like mine that are super old and still run some good technology. My overall experience with Ubuntu has been less than Windows and ChromeOS, but it's definitely something I would consider should they ever bring more apps. Though I would love to learn how to develop apps for Ubuntu, so I'll go and do just that.

---

### Post by mastablasta on 2018-12-06
not sure what apps you need. there are plenty alternatives for the tasks done in windows freely available (repositories, via PPA, snap packages). so far some specialised software is an issue (MS Office, Adobe, CAD/CAM stuff) as well as most Windows games. but things are changing and there is more and more software with Linux version including games. additionally wine can also run some windows software well. 

you need 2 GB ram, the OS will install to about 7-8GB hard disk, so to be able to add more stuff and some data 20-30 GB is recommended.

Xubuntu will do with 1 GB ram or even less, Lubuntu should fit on 256 MB RAM, but the issue is that applications now need plenty of ram. so again having at least 1 GB ram is good to have.

there are other distros like TinyOS or Slitaz that will need less than 100 MB ram to run and install ona few 100 MB of ram. they are interesting to try if nothing else. Bodhi is a very light interface placed on Ubuntu. it is also interesitng to try out.

---

