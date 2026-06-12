---
title: "Selinux"
date: 2011-02-22
forum: Security
---

### Post by buntuser2 on 2011-02-22
I have googled every keyword I can think of and there is no place that explains how exactly to configure selinux on ubuntu 10.04 - 10.10.  On Fedora there is a command for it. Is there a command for it on ubuntu 10.04-10.10 ?  I just now did: sudo apt-get install selinux  Then selinux installed.  How do I configure it though? I want to see the settings, maybe change some settings.

---

### Post by kemra on 2011-02-23
You won't find much info on using SELinux specifically with Ubuntu as Ubuntu uses [AppArmour]("https://help.ubuntu.com/community/AppArmor") instead. Maybe you should look there instead unless you have a very specific need for SELinux.

There is an Ubuntu page for SELinux [here]("https://help.ubuntu.com/community/SELinux") but it is not complete and hasn't been updated in a very long time. However I see no reason you shouldn't be able to use the command line tools any other distro uses in Ubuntu, so any tutoral etc should be good for Ubuntu as well.

---

### Post by wacky_sung on 2011-02-23
If you wanna use SElinux, i will suggest you to switch over the fedora.Personally i still like SElinux over apparmor which has more control over it.Beside that, SElinux can be configure through GUI which user less headache.:P

---

### Post by bodhi.zazen on 2011-02-23
> **wacky_sung said:**
> If you wanna use SElinux, i will suggest you to switch over the fedora.

+1.

Last time I tried selinux on ubuntu it did not work properly.

Ubuntu does not include any of the "modern" debugging or configuration tools included with fedora either.

If you insist on using selinux on Ubuntu, start reading the selinux documentation. I would start with the Centos and Fedora documentation as it is much more up to date and much more complete then the Debian or Gentoo or Ubuntu documentation.

Once you understand the Fedora selinux documentation you can then review the Ubuntu documentation to see if there are any specific Ubuntu differences.

You will also find little to no support for selinux on the ubutnu forums, but the fedora forums are extremely helpful for selinux.

---

