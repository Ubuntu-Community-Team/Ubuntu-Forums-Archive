---
title: "text based network configuration"
date: 2005-12-17
forum: Server Platforms
---

### Post by neilsly on 2005-12-17
Besides manually editing the configuration files is there a text based program that can be used to edit the network configuation?  Every tutorial or help tip points to using the GUI via either gnome or kde in kubuntu - but I've got neither installed as I'm using my ubuntu as a server and just have the default ubuntu-server install with no x, etc.

Certainly there's got to be a way to do this - you can configure it during setup from via a text based form.  I would imagine that you can do a whole lot of other stuff with neat fill in the blank curses based configuration screens - I just don't know what the commands are.  I went so far as to install webmin to see if that would help out configuruing my ubuntu-server, and either I grabbed the wrong version via apt-get or it's seriously messed up.  Speaking of.... how do you even use webmin on ubuntu?  I suppose you would have to sudo -s and enable the root user and change the root password and then login into webmin.

-neil

---

### Post by LordHunter317 on 2005-12-17
I'm not sure if there is an offical CLI tool for editing Debian/Ubuntu network configuration besides editing the /etc/network/interfaces file.

Anyway, why the complaint about that?  It's only one file you have to edit.

---

### Post by neilsly on 2005-12-17
It's not really a complaint per se' - it's more of a concern over the ubuntu-server project and documentation.  All of the ubuntu documentation points to GUI tools to change everything.  It's not my point to start a distro war here but redhat (fedora) has some really great cli curses based tools to configure various things and they're very powerful tools.

I see a really powerful and wonderful thing in ubuntu-server.  No other disto has the ease of use and installation along with the minimalist'ness of ubuntu-server.  I can possibly think of gentoo but the install just isn't there.

---

### Post by LordHunter317 on 2005-12-17
> **neilsly] All of the ubuntu documentation points to GUI tools to change everything.[/quote]Read the Debian documentation then, or the online documentation  said:**
>  It's not my point to start a distro war here but redhat (fedora) has some really great cli curses based tools to configure various things and they're very powerful tools.No, they're crap because in some cases, they generate very bad configurations: e.g., authconfig still fills in the krb5.conf file instead of using DNS (at the very least it should ask).  Also, the tools don't even attempt to preserve custom changes, meaning someone running them plows away all the manual work I had to do when the tools don't work.

Yes, they're great when they do work.  When they don't, they become infinitely more hassle then they should be.

---

