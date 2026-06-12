---
title: "Openoffice installed on default Ubuntu Server?"
date: 2009-11-16
forum: Server Platforms
---

### Post by twisted_steel on 2009-11-16
I installed Ubuntu Server 9.10 via netboot (PXE) yesterday and noticed that Openoffice.org, Java, Xorg, and a few other packages were pulled in by default.  I found OO.o listed under editors in aptitude.  I didn't select any other roles (e.g. web server, etc) during the installation.  My server is headless, so this didn't make sense to me. Is this how things are supposed to work in Ubuntu Server?

---

### Post by cariboo on 2009-11-17
Did you install ubuntu-desktop? That will pull in everything that a normal desktop has. When doing that type of install you may just as well do a desktop install, then install the servers you want.

I would suggest seeing as it is a fairly new install, that you do a complete server installation and have a look at either [webmin]("http://www.webmin.com/"), or [ebox]("http:///www.ebox-platform.com/"). Ebox is in the repositories.

---

### Post by twisted_steel on 2009-11-17
No, I didn't install ubuntu-desktop, which is why this seemed weird to me.  In one of the final steps, the installer pulled down 125 or so packages and Openoffice.org, X, Java, and a few others were among them.  I had OpenBSD on the box before.  I do like byobu (formerly screen-profiles) so far.

---

### Post by twisted_steel on 2009-11-17
I figured it out.  When I did the network install, I used the default US mirror.  It turns out that I should have been using my local copy of the ubuntu-server mirror (from the mounted ISO), as the packages are different.  Once I selected that manually, the packages installed without bringing in OpenOffice.

---

### Post by bonfire89 on 2010-01-02
I just had this happen to me too.. Very Strange.

---

### Post by volkswagner on 2010-01-02
Is this due to language packs?

I saw a similar red flag while following a modest [how to]("http://tombuntu.com/index.php/2008/10/27/notes-from-setting-up-ubuntu-server-on-linode/").

If you follow the comments on the how to, a great comment is made how to avoid the extra packages.

>  broesch says:
November 20, 2008 at 6:16 am

Its not necesary to install the whole language-pack-en, its about 163megs of useless junk, dictionaries for openoffice, thunderbird etc.
just run:
sudo locale-gen en_US.UTF-8
or whatever locale you want

The above command will need to be modified your your correct locale.

---

### Post by Vegan on 2010-01-02
Since I get the Pentium IV and away from that BS 137GB disk limit, I am no longer so concerned about fluff on the server.

I put the desktop on the machine as I have tons of RAM on it, but its a full LAMP. Only reason for the desktop is for a browser in case the Windows box craps out.

Most of the time its beheaded.

---

### Post by [pl]ice on 2010-01-03
that's pretty bad, maybe complain to that mirror, otherwise lots of ppl will end up with OO . . .

---

