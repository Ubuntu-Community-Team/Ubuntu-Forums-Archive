---
title: "apt source for individual packages?"
date: 2005-06-30
forum: Ubuntu Backports
---

### Post by sterwill on 2005-06-30
I've been using the Debian backports for woody (backports.org) for years, and I've just found the Ubuntu backports project, which is great for my desktop machine.  However, on my Ubuntu servers, I want newer versions of some packages (clamav), but certainly not the ones that already work without a problem (samba).  The problem comes after I install clamav, and later do an "apt-get upgrade" to pull down any official Ubuntu security updates.  Now apt wants to install all the other backports, and I have to sort through which ones aren't security updates.

I didn't see this in the FAQ: is there a way to construct my apt source line to pick a single package from the Ubuntu backports repository?  backports.org made this easy, since each package had its own directory (and Packages.gz and Release files).  Right now, I have to comment out the apt source line when I'm done installing from backports, and remember to put it back if I want a newer version of that package.

---

### Post by Xian on 2005-06-30
[QUOTE=sterwill]I didn't see this in the FAQ: is there a way to construct my apt source line to pick a single package from the Ubuntu backports repository?[/QUOTE]
You just need to create a apt.conf file in /etc/apt.

First, open a text editor with sudo privileges.
Paste the text below into the editor.
Then save it as /etc/apt/apt.conf.

```
APT::Default-Release "hoary";
```
Next you will want to reload your sources in either an Apt or Synaptic session.
```
$ sudo apt-get update
```
If you now try a dist-upgrade Apt should ONLY pull from the base Hoary pkgs.

However, if you want to install an individual pkg from the Backports repos you can easily do that by issuing a slightly different install command in a terminal session. Let's say that you want to install abiword and you want the Backport version which is as of this post abiword_2.2.7-3. If you look in Synaptic it will only show you version 2.2.2-1, which is the base Hoary release.

To install the 2.2.7-3 version this would be the command:
```
$ sudo apt-get -t hoary-backports install abiword
```

---

### Post by sterwill on 2005-07-01
Thanks!  This is exactly what I was looking for.  I should have read the apt.conf man page!

**Oops, I responded too soon.**

"apt-get upgrade" and "apt-get dist-upgrade" are still selecting packages from the backports source even with that line in /etc/apt/apt.conf.  Any suggestions?

---

### Post by sterwill on 2005-07-01
Nevermind.  My problems were caused by a configuration oddity that few other people share.  I was using Debian Woody on this server, then I added a deb source for dotdeb.org (for clamav and others).  Then I upgraded to Hoary, removing the dotdeb sources, but since the dotdeb packages were newer, they weren't replaced during the upgrade.

Now, Hoary has a clamav older than the dotdeb packages that are installed, but backports had a newer version, so those packages were selected for upgrading.  I'm not exactly sure why they were selected for upgrade (but I don't understand the package priorities well).  Simple enough to work around.

The other packages in backports were **not** being selected for upgrade, I was just alarmed about the clamav dependencies.

Thanks for your help!

---

