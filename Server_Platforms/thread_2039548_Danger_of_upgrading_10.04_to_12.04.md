---
title: "Danger of upgrading 10.04 to 12.04"
date: 2012-08-09
forum: Server Platforms
---

### Post by fjolle_dk on 2012-08-09
Hi,

We run an Ubuntu Server 10.04.4 LTS 64bit in a production environment.

It runs SSHd so I can remote into it using SSH. I have physical access as well.
It serves as a MySQL server, Apache server with PHP, a Samba file server and a MongoDB daemon.

It is essential that this machine is stable and secure. There is no access to the databases or samba from the outside, but the Apache server runs a simple site (with PHP).

I have been doing some exploit testing using Nexpose and it heavily recommended updating PHP and Apache versions.

What I'd like to know is if there are any potential (or often seen) problems with upgrading an Ubuntu Server 10.04 to 12.04 LTS. All the software is installed using apt-get, all are default versions (except MongoDB, which comes from their own repository). Will it just work? Are there any precautions to take, anything special regarding config files or so?

We do have a nightly backup of the databases and all the files (from the samba file server share), but it will take a long time for me to configure everything again so I'd really like to avoid that.

Thanks, and best regards,
Daniel

---

### Post by rubylaser on 2012-08-09
I always to a whole machine backup before I upgrade the OS.  I've upgraded a few of our servers at this point from 10.04 -> 12.04 and had no issues, but I have also seen a decent number of people on this forum having problems with the upgrade, so it's not bulletproof.

---

### Post by fjolle_dk on 2012-08-09
I'll make sure to backup everything, including config files.

I've read about one having problems, but that was due to the machine trying to boot a wrong partition or something like that (while using SSH). The ubuntu upgrade guide warns of this, and gives a solution (check that the boot manager is correctly set up before rebooting)

Good to hear that some have tried it successfully :)

---

### Post by 2F4U on 2012-08-09
I did an upgrade from 10.04 to 12.04 through ssh and it went without problems. The upgrade process recognizes that you do the upgrade though ssh and restarts the ssh daemon as late as possible.

---

### Post by fjolle_dk on 2012-08-09
Sounds good that they have thought of that. Calms me a bit :)

---

### Post by LHammonds on 2012-08-09
If I were you, I would make a full backup of the entire machine so that if it does not work, a restore can get you back exactly like you were before.

I have used FSArchiver to backup the boot partition and the LVM and was able to restore to a brand new box (well, virtual machine) without having to re-install an OS or mess with any config files.

How I setup my servers are documented in my sig.

LHammonds

---

### Post by fjolle_dk on 2012-08-09
I didn't know about FSArchiver, that seems like a great idea actually!
I'll check your setup out as well, perhaps I can steal a few ideas :)

---

### Post by fjolle_dk on 2012-08-10
I completed the upgrade 2 hours ago through SSH (after taking a full backup). While installing, I was asked multiple times if i wanted to keep my config files (e.g. for mysql, apache and so on) to which i simply answered yes.

After a reboot, everything is updated and runs with no problems. I have been testing all the services, and everything is configured just as I left it.

Thanks for all your comments :)

---

### Post by d4m1r on 2012-08-10
> **fjolle_dk said:**
> I completed the upgrade 2 hours ago through SSH (after taking a full backup). While installing, I was asked multiple times if i wanted to keep my config files (e.g. for mysql, apache and so on) to which i simply answered yes.

After a reboot, everything is updated and runs with no problems. I have been testing all the services, and everything is configured just as I left it.

Thanks for all your comments :)

Glad it worked out for you! Now please mark the thread as solved (thread tools at the top) :P

---

### Post by fjolle_dk on 2012-08-10
> **d4m1r said:**
> Glad it worked out for you! Now please mark the thread as solved (thread tools at the top) :P

Done, sorry I'm not used to these forums :)

---

