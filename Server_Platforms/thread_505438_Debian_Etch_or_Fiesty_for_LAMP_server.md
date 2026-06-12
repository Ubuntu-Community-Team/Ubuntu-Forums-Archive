---
title: "Debian Etch or Fiesty for LAMP server"
date: 2007-07-20
forum: Server Platforms
---

### Post by machoo02 on 2007-07-20
Hi,

I'm going to be setting up my first LAMP server in the next day or so, and I'm trying to decide between using Etch or Feisty as the OS.  What might be the advantages of either?  Any preferences or horror stories?  Thanks

---

### Post by elst on 2007-07-21
Debian and Ubuntu are very similar indeed. The obvious differences would be:

- Feisty has newer versions of the same software, but *potentially* more bugs, due to the shorter testing period.

- Feisty has an option to add all of the software needed for LAMP during the installation process. It's easy enough to add these yourself after installation, though.

- Debian doesn't setup sudo by default. Also easy to setup, but if you don't know how then it's another thing to learn.

If you want to start learning how to develop for the Web quickly then Ubuntu may be a little easier. If you want to learn how to maintain Linux systems, or run one as a production server, then I would personally pick Debian stable rather than Feisty.

---

### Post by ajehals on 2007-07-21
Just to say -

How current your Debian packages are will depend on whether you install stable, unstable or testing, I would suggest going with stable for a production box though, I believe unstable/testing is what ubuntu ships.

Debian will also allow you to install all the software needed for LAMP during the installation process, and you can do the installation mostly headless too..

Debian doesn't set-up sudo by default, however you may find that for a web server that sudo is more of a liability than a benefit anyway.  Whatever you go with I would suggest making sure that you take a look at the various guides out there to hardening Linux / Apache and MySql installations.

And I would agree with the poster above me that for a quick and working installation go for feisty, but if it is going anywhere near a production environment, I would go with Debian stable.

---

### Post by az on 2007-07-21
> **machoo02 said:**
> Hi,

I'm going to be setting up my first LAMP server in the next day or so, and I'm trying to decide between using Etch or Feisty as the OS.  What might be the advantages of either?  Any preferences or horror stories?  Thanks

I think the Ubuntu base server install is more lean. 

To set up and configure LAMP on Ubuntu:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by elst on 2007-07-21
> **ajehals said:**
> Just to say -

How current your Debian packages are will depend on whether you install stable, unstable or testing, I would suggest going with stable for a production box though, I believe unstable/testing is what ubuntu ships.

Debian will also allow you to install all the software needed for LAMP during the installation process, and you can do the installation mostly headless too..

Debian doesn't set-up sudo by default, however you may find that for a web server that sudo is more of a liability than a benefit anyway.  Whatever you go with I would suggest making sure that you take a look at the various guides out there to hardening Linux / Apache and MySql installations.

And I would agree with the poster above me that for a quick and working installation go for feisty, but if it is going anywhere near a production environment, I would go with Debian stable.

I think that each Ubuntu release is based on a snapshot of Debian unstable, which then has a lot of patches applied to stabilize and "Ubuntuize" it. IIRC, Ubuntu Server and the Alternate install CD use the Debian installer, so Ubuntu is about feature-equivalent in that respect.

I don't agree that sudo reduces the security of a server, and would actually say that in practice it increases it, particularly if the root account is locked as well (which Ubuntu does).

---

