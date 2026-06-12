---
title: "Ubuntu Terminal Server"
date: 2007-05-05
forum: Server Platforms
---

### Post by bobsta63 on 2007-05-05
Hi all,

I would like to install a Ubuntu Terminal Server so that I can have thin clients connet to it and be able to manage all applications and storage centrally (on the Terminal Server). I found this page:-

[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

It says that LTSP support comes with Ubuntu Server editon. This sounds very good and I just wondered if anyone knew how to install it... Could someone please provide me with a list of **apt-get** commands or point me in the right direction to a tutorial or something.

Thanks in advance,

Bobby

---

### Post by smhickel on 2007-05-07
Please see:

[http://ubuntuforums.org/showthread.php?t=434648&highlight=ltsp](http://ubuntuforums.org/showthread.php?t=434648&highlight=ltsp)

---

### Post by bobsta63 on 2007-05-07
> **smhickel said:**
> Please see:

[http://ubuntuforums.org/showthread.php?t=434648&highlight=ltsp](http://ubuntuforums.org/showthread.php?t=434648&highlight=ltsp)


Yeah I know mate, thanks... I too was posting in that thread, thanks anyways :)

---

### Post by jimcooncat on 2007-05-09
I'm guessing it would be:

sudo apt-get install ltsp-server

then follow the guide below. I can't wait to try this out myself! Please post your findings, if you can:

---- ltsp.5.0.7/server/doc/Quickinstall ----

This document aims to describe the quickest way to get a ltsp server
running on an existing ubuntu or kubuntu (xubuntu comes with a ltsp
option in the installer, edubuntu even sets up ltsp in its default
install).

You need to set up one static interface where you will attach the
thin clients, install two packages and run one command.

Configure your spare interface for the thin clients to have the
IP 192.168.0.1, then run command below:

sudo apt-get install ltsp-server-standalone openssh-server

Now create your Thin Client environment on the server by running:

sudo ltsp-build-client

After that, you will be able to boot your first thin client.
Note that if you want to use another IP than the above, you need to
edit the /etc/ltsp/dhcpd.conf file to match the IP values and
restart the dhcp server.

If you change the IP data after you have done the initial setup,
please run the command sudo ltsp-update-sshkeys to make the ssh
server aware of the change.

---

### Post by MisterD on 2007-05-10
> **jimcooncat said:**
> Please post your findings, if you can:

Thanks for the info jimcooncat, I too am implementing a terminal server to provide the same benefits that bobsta63 listed, I will post my findings once the 7.04 ISO finishes downloading and I get it installed. Thanks again!

---

### Post by bobsta63 on 2007-05-11
Hi MisterD that would be really good if you could post your findings :D

---

### Post by jimcooncat on 2007-05-14
I don't know why I missed it before, the quickinstall stuff I posted here was already in the Wiki!

Here's a more comprehensive index of important docs:

[https://help.ubuntu.com/community/UbuntuLTSP?highlight=%28ltsp%29](https://help.ubuntu.com/community/UbuntuLTSP?highlight=%28ltsp%29)

---

