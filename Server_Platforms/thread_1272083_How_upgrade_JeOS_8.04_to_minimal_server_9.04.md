---
title: "How upgrade JeOS 8.04 to minimal server 9.04?"
date: 2009-09-21
forum: Server Platforms
---

### Post by sforces on 2009-09-21
I have a couple of JeOS 8.04 installs. I know that JeOS has been discontinued and there is now a minimal install option as part of a new Ubuntu server 9.04.

But I don't want to do a new install. I need to upgrade an existing JeOS 8.04 to Ubuntu Server 9.04. How can I do that? ](*,)

===
Edit:
Because JeOS 8.04 is an LTS (Long Term Support) release, no updates are offered until the next LTS is released. So you first have to modify a setting to allow it to pick up other releases. Then I was able to upgrade to Intrepid 8.10 server and then to Jaunty 9.04 server (couldn't skip directly to Jaunty).

I found info about it on the upgrade from 8.04 LTS to 8.10 site here: 
[https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended](https://help.ubuntu.com/community/IntrepidUpgrades#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended))

Which describes:
Network Upgrade for Ubuntu Servers (Recommended)
   1. Install update-manager-core if it is not already installed:
      sudo apt-get install update-manager-core

   2. Edit /etc/update-manager/release-upgrades and set:
      Prompt=normal

   3. Launch the upgrade tool:
      sudo do-release-upgrade

   4. Follow the on-screen instructions.

---

### Post by Lars Noodén on 2009-09-23
Well, I would not advise trying to upgrade a running system.  Can you take down one of the machines and do a fresh installation?

That would be best.  Use the "alternate" installation to get more choices about what is or isn't installed.

*Sometimes* you can do a distro upgrade by changing source.list to match the new distro, then do apt-get udpate && apt-get dist-upgrade

[http://www.debian.org/releases/lenny/i386/release-notes/ch-upgrading.html](http://www.debian.org/releases/lenny/i386/release-notes/ch-upgrading.html)

Note! That does not work all of the time.  



/etc/apt/sources.list:

deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic main 
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic main 
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe

---

