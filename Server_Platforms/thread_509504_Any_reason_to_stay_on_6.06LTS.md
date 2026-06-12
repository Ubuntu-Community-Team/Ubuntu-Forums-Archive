---
title: "Any reason to stay on 6.06LTS?"
date: 2007-07-25
forum: Server Platforms
---

### Post by Aberrix on 2007-07-25
I am currently running ['the perfect setup'](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) with [ispconfig](http://www.ispconfig.org). I noticed that there are packages like fail2ban that do not have the functionality I want (like banning ftp attempts) yet newer releases do. I am wondering, is there any reason for me to stay on 6.06LTS? I mean, I log into the server every day and always do apt-get update/upgrades so it's not like I am not going to get things updated within 24hr should a patch/fix be released. and am I going to harm anything by upgrading to a newer distro? thanks in advance.

---

### Post by Seisen on 2007-07-25
Its your server so do what you want with it. You just have to make sure that all your packages that you want will work nicely together. Here is two guides for the same setup in Edgy and Fiesty.

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10")

[http://www.howtoforge.com/perfect_setup_ubuntu704]("http://www.howtoforge.com/perfect_setup_ubuntu704")

---

### Post by Aberrix on 2007-07-25
I guess what I am asking is what is the benefit to staying on 6.06LTS?

I know its very stable, but besides that the con's are out weighing the pro's right now. I don't run anything too complex so I don't imagine there being any conflicts, only simply benefits to have up to date packages.

---

### Post by Seisen on 2007-07-25
Nothing really except they support 6.06 for 5 years for servers while 6.10 and 7.04 are only supported for 18 months.

---

### Post by Aberrix on 2007-07-25
I don't mind doing a distribution upgrade every 18 months.

btw, how 'bad' is that for the system, if at all to do a dist-upgrade to the next distro?

is it as bad as upgrading a windows box? I know in the windows wold you always wanna do a fresh install.

---

### Post by keithweddell on 2007-07-25
Do you have a spare machine/partition?  If so you could try setting it up with Edgy or Feisty.  Then cut across when  you are happy.

Keith

---

### Post by Brazen on 2007-07-25
I have not had problems doing dist-upgrades between versions.  I would never run anything other than Dapper on a server though, unless there was some new feature that I just HAD to have.

Stability and reliability are the major concerns for a server.  I run several linux servers at work and I don't want to be surprised by breakage introduced by some update introduced in Feistry.  Almost all big businesses exclusively run Dapper and pump a lot of money into support contracts on Dapper, which means a lot more time and testing goes into patches for Dapper and it will be the same with future LTS releases.

Even on my home server, I may be the only one it affects (and my wife and kids) but I still want to keep it updated but don't want to find out an update broke something and now I have to mess with fixing it instead of spending my free time doing other things.

That is why I stick with Dapper.  Plus not having to mess with doing a dist-upgrade to a new version for several years is a huge bonus.  It's not a terribly difficult process, but I have had some services that required quite a bit of reconfiguration when I've done them on Debian servers.  My server works so the longer I don't have to mess with it, the more work I can get done on other things and the more free time I have.

[https://help.ubuntu.com/6.06/ubuntu/about-ubuntu/C/about-ubuntu.html#lts](https://help.ubuntu.com/6.06/ubuntu/about-ubuntu/C/about-ubuntu.html#lts)

---

### Post by Aberrix on 2007-07-25
^ Bah, you bring up some good points...

I suppose I can wait until 08, that's when the next LTS is being released right?

---

### Post by srt4play on 2007-07-25
April of 08.   I've stuck with Dapper for servers too for stability reasons.

---

