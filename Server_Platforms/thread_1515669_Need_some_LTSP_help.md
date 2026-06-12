---
title: "Need some LTSP help"
date: 2010-06-22
forum: Server Platforms
---

### Post by lykwydchykyn on 2010-06-22
Sorry if this post end up being a book, I'll try to make it a good one. :)

I have an old LTSP setup running on an old workstation that powers about 15 OLD thin clients at the public library.  The current server runs Dapper with an LTSP 4.1 (pre-muekow) setup; the clients are Affirmative Yestation thin clients with 200MHz processors and 64 MB of RAM.

Everything runs fine now, but dapper is going EOL and the server hardware is flaking out.

I want to re-do everything on better server hardware with Lucid and all the nice features of LTSP 5.x that obviate the need for most of the hacks I had to do on LTSP 4.1.

Upgrading the thin client hardware is not an option, BTW (that's foreshadowing, that is...)

I did a quick setup on a test server which may potentially be the production server if funding doesn't come through.  Now here are my questions/issues:

 - SLOOWWWWW: the thin client takes around 5 minutes to boot, and there is noticeable latency in the GUI.  Even web pages load up slowly.  Is there any way to trim down the default client image? I tried:
  - going into the chroot with aptitude and removing what little was removeable, then updating the image
  - Activating nbd swap
  - Adding the LDM_DIRECTX=True directive to the lts.conf
  - Turning off the plymouth boot splash
  - building the client image from karmic (didn't boot) or debian lenny (wouldn't build)
  Is there anything else I can do here to cut down the fat and make this client image peppier?

 - Guest login: I tried using guest logins, and would like to make this work, but it just blacks out when I try to do guest logins.  I can't find any documentation on how to use these, or configure the session, etc.  Anyone managed to use the Guest login feature?

 - NFS: The old school LTSP setup used NFS rather than NBD, I'm wondering if this would speed things up a bit.  Is it still possible to use NFS?  I see nothing about it in the current lts.conf manpage.

That's all I can think of for the moment.  Any advice you can give would be appreciated.

---

### Post by lykwydchykyn on 2010-06-23
ka-bump...

---

### Post by lykwydchykyn on 2010-06-23
Another issue, if anyone knows; when I assign a screen to "shell", the shell is all messed up.  It keeps logging out, and it shows a login prompt but if I type something in it takes it as a command.  Then it cuts off my commands at random and is generally unusable.

Anyone else having a problem with using the "shell" session in LTSP?

---

### Post by lykwydchykyn on 2010-06-25
bump...

---

### Post by dannyfel on 2010-06-25
For guest logins you need to edit your  /var/lib/tftpboot/ltsp/i386/lts.conf:

In the default section:
[default]
LDM_GUESTLOGIN = True

Then for every thin client you need to define the username and  password:
[MAC ADDRESS]
LDM_USERNAME = guestuser
LDM_PASSWORD = guestuser

To find the thin clients MAC addresses you can compare the IP they  receive when they load with the IP and MAC specified in  /var/lib/dhcp3/dhcpd.leases

Good luck

---

### Post by lykwydchykyn on 2010-06-25
> **dannyfel said:**
> For guest logins you need to edit your  /var/lib/tftpboot/ltsp/i386/lts.conf:

In the default section:
[default]
LDM_GUESTLOGIN = True

Then for every thin client you need to define the username and  password:
[MAC ADDRESS]
LDM_USERNAME = guestuser
LDM_PASSWORD = guestuser

To find the thin clients MAC addresses you can compare the IP they  receive when they load with the IP and MAC specified in  /var/lib/dhcp3/dhcpd.leases

Good luck

I tried the LDM_GUESTLOGIN bit, but all I get is a black screen. Do I literally need to put "guestuser" or is that a place holder?

The documentation says it will default to "ltspXXX" where XXX is the last octet of the IP.  I've gotten it working ok for autologin if I just create accounts on the server for those users.

I guess I was hoping guestlogin would create some kind of temporary account.

---

