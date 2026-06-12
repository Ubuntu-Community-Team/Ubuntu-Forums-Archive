---
title: "Server 7.10 LTSP"
date: 2007-11-22
forum: Server Platforms
---

### Post by sigs on 2007-11-22
Hi everyone,

I'm setting up a LTSP server. I was reading the about [Ubuntu Server Edition page]("http://www.ubuntu.com/products/WhatIsUbuntu/serveredition") and it made it seem like you could automatically configure LTSP similar to how you can automatically configure LAMP or DNS.

Am I missing something completely obvious or do you have to follow some other process to get it working?

I've searched up and down for an answer but I've so far been unable to locate any info on this.

I'm fine with setting up a LTSP so don't bother linking to other how to articles or what not. I'm just curious.

Thanks everyone.

---

### Post by sciurus on 2007-11-22
Edubuntu 7.10 Classroom Server  is what is automatically configured as a LTSP server, not Ubuntu Server.

---

### Post by sigs on 2007-11-23
Ah, thanks for clearing that up.

---

### Post by keenboy on 2008-02-06
I also fell for this!!

After installing Kubuntu and not being able to get ltsp-manager working correctly I thought I'd use ubuntu.

The ubuntu website does give the impression that LTSP is an option during install.

> Ubuntu Server edition includes thin client support using LTSP (Linux Terminal Server Project). LTSP-5, the latest release, offers a simple installation and easy maintenance.

This is a bit vague to be honest.

I have two questions:

1. Is the ltsp tool that is used in edbuntu available for ubuntu? That would be handy.

2. After installing ubuntu server edition we have no running X, does this make installing LTSP even more problomatic??

I would think 1 of two things need to happen...........

Either add LTSP as a server option into the installation options of ubuntu server edition.

or

Re-write the website content to be a bit clearer.

---

### Post by UbuWu on 2008-02-06
Yes you can easily install an ltsp server on ubuntu and no you don't need X.

See [https://help.ubuntu.com/community/ThinClientHowto](https://help.ubuntu.com/community/ThinClientHowto)

---

