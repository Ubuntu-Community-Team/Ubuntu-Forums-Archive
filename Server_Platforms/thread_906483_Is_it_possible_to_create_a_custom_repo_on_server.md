---
title: "Is it possible to create a custom repo on server?"
date: 2008-08-31
forum: Server Platforms
---

### Post by PryGuy on 2008-08-31
Good day everyone! I want to create a small repository on my server. I googled a bit and found solutions based on debmirror and apt-cacher. But as far as I learnt they just grab all the files located on the ubuntu servers and store them locally or on a local server. But I do not want to download over 12Gb of deb files! All I want is to create a small custom repo with my files that I have downloaded. Is it possible?

---

### Post by tamoneya on 2008-08-31
You could try messing with aptonCD.  It allows you to make a repo of all of your debs and burn it onto some form of media (typically a cd/dvd).  The idea is that then you can bring your apps to a computer without internet.  However I bet you could probably get it to "burn" your debs to a harddrive instead of a optical disc.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by PryGuy on 2008-08-31
I know aptoncd perfectly! It's a fine tool, but I wanted to create a LAN repo on my server.

---

### Post by tamoneya on 2008-08-31
yes i realize.  But what I am saying is you should repurpose the tool and "burn" to your harddrive.  Then you can share it over http or something with apache.

---

### Post by PryGuy on 2008-08-31
Okay, I'll try to mess with it ;)

---

### Post by tamoneya on 2008-08-31
your other option is PPA but that wont be local.  Although you could try setting up a PPA on launch pad and then mirroring your PPA instead of mirroring the ubuntu servers.

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

### Post by PryGuy on 2008-09-01
Cool! Thank you! This is a nice option! ;)

---

