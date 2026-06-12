---
title: "Ubuntu Server vs. Oracle Enterprise Linux"
date: 2010-10-15
forum: Server Platforms
---

### Post by thuntley on 2010-10-15
Having been a long-time Linux supporter, it was a no-brainer for me to push Linux as the OS when it was time to move my company's website(s) from an external host to an internal server.  My company ponied up the bucks for an HP Proliant DL180 G5 server (this was about a year ago) upon which I installed Slackware 12.1 (I kinda default to Slackware, although in the past I've also used RedHat on the server and openSUSE on the desktop).

Well, it's now time to upgrade the OS on the server.  Perhaps I'm a little late to the game on this, but I just recently found out about Oracle Enterprise Linux 5.5.  Bad Oracle ju-ju aside, it looked to be a very good and stable server distro, especially when you consider the availability of Oracle support for it.  So I've since installed OEL to a non-production server and have been testing it out.  It looks to be a good match for my needs.

However, since installing OEL on my test server I've installed Ubuntu Desktop 10.10 on my home desktop (a 1.86ghz Intel Core 2 Duo HP xw4400 workstation) and in a VirtualBox VM on my work desktop (a 3.2ghz Intel Core i3 iMac) and... holy crap, it's the best desktop Linux I've ever had the pleasure of using.  It will certainly replace Slackware as my default "go-to" Linux distro.  Which has made me wonder about the Ubuntu Server offering and if it might not be a better fit for my webserver in the same way that Ubuntu Desktop is a better fit for my workstation.

Unfortunately, I don't have the time to pull down another server distro, install it, and test it unless I'm reasonably certain that it's going to give OEL a run for its money.  So I turn to the forums and the knowledge of the users who frequent them: is Ubuntu Server a strong enough contender to OEL that I should take a more serious look at it? Or, like I'm hearing about the latest Ubuntu Netbook edition, would it not be worth my time if I'm happy with OEL so far?

Thanks!

---

### Post by wirelessmonkey on 2010-10-15
OEL is primarily a rebranded RHEL, so your RedHat experience will be useful. Oracle juju aside, it's perfectly fine.

---

### Post by James78 on 2010-10-16
> **thuntley said:**
> ... and... holy crap, it's the best desktop Linux I've ever had the pleasure of using...

Heh, you got that right. Ubuntu and Kubuntu are both really great distros for desktops. I'm currently using Kubuntu 10.10, and an Ubuntu 10.10 Server (i686 though.. :()

While I can't tell you how Ubuntu server compares to some enterprise solutions, I can tell you that:
1. If you're looking for commercial support and backing, Canonical (Ubuntu's commercial backer) will do that if the price is right, as far as I know.
2. I am using Ubuntu Server on my server, for my website, and it works perfectly fine for me. Then again though, I haven't had the ability to compare with other distros. If you want some security insane server distro though, I hear SELinux takes the lead, and not only takes the lead, but DEMOLISHES the competition in that regard (I've also heard that it's TOO SECURE); I still prefer my own Ubuntu Server though, as most times, a regular Linux server is nearly always fine, as long as you're security conscious by default, and do things like using Fail2Ban, etc etc. :D

---

### Post by Sporkman on 2010-10-17
I've found Ubuntu Server to be fast and rock-solid.

The LTS version gets security update support for 5 years.

---

### Post by ythe1300 on 2010-10-18
Just a quick note. Ubuntu server has no default GUI, that being said. you can use apt-get to install one if you would like. I have used CentOS in the past (Red Hat based) and I can tell you that ubuntu server boots up in half the time, which is great.

Good Luck in whatever you decide.

---

### Post by thuntley on 2010-10-18
> **ythe1300 said:**
> Ubuntu server has no default GUI

Oh, good to know, thanks.  :)

---

