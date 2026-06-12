---
title: "Ubuntu Cli Install and Server"
date: 2010-04-14
forum: Server Platforms
---

### Post by arthurjohnson on 2010-04-14
Can anyone tell me the difference between Ubuntu Server and the Alternate Installer's Command Line Only install?  

To install Ubuntu for my Server clients, I've been using the alternate installer and installing a command line only system.  After I boot the machine, I install the linux-server package.  I'm just curious if there is a benefit to using the ubuntu server cd over this method.

Thanks in advance

Arthur

---

### Post by arthurjohnson on 2010-04-14
Mainly wondering if I'm doing the server edition right or not, and what the possible side effects might be.

---

### Post by volkswagner on 2010-04-14
Installing via the server CD may keep the size down (a little) since you wont have the generic or non-server kernel installed.  There may be other things added also like additional ACPI.  I believe you should use the server disk unless there are hardware issues stopping you from using it.  Plus it's one less step since the server kernel will be there from the start.  Server install is a CLI install optimized for running a server environment.

---

### Post by dudumomo on 2010-04-14
Actually the main difference is the kernel.
As told volkswagner, The server version is more optimized.

---

