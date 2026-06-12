---
title: "Failed to start ubuntu in Oracle Virtual Box"
date: 2020-04-26
forum: Virtualisation
---

### Post by fuzmic on 2020-04-26
Hi gurus

This is first attempt to use Ubuntu, i start with v20.04  (AMD.iso for 64 bit).  I install it in a Oracle Virtual Box from Oracle 64bit v6.1.6.

The installation i think went smoothly after retrieving all files, run dpkg, config hardware, etc, downloading etc, finally end up with message that installation is complete with button to close the installation in the VirtualBox.  

After pressing this button, a black dialog box reporting repeately failure to write plus some squash... with a series a numbers.  Thus i finally shut down this virtual machine and restart the VBox.  The error message from VBox is as follows:

Failed to open a session for the virtual machine **ubuntu 20.04**.
The object is not ready.
[TABLE="width: 100%"]
[TR]
[TD]Result Code:[/TD]
[TD]E_ACCESSDENIED (0x80070005)[/TD]
[/TR]
[TR]
[TD]Component:[/TD]
[TD]MediumWrap[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IMedium {ad47ad09-787b-44ab-b343-a082a3f2dfb1}[/TD]
[/TR]
[/TABLE]

The VBox files are as follows:
Directory of d:\VMc\ubuntu 20.04
27-04-20  08:10 AM    <DIR>          Logs
27-04-20  07:12 AM    <DIR>          Snapshots
27-04-20  08:10 AM             2,795 ubuntu 20.04.vbox
27-04-20  07:57 AM             2,795 ubuntu 20.04.vbox-prev
27-04-20  07:56 AM     7,206,862,848 ubuntu 20.04.vdi

Please help.  Thank you for reading up to here from freshie Mike.

---

### Post by wildmanne39 on 2020-04-26
*Thread moved to **Virtualisation for a more appropriate fit**.*

---

### Post by SeijiSensei on 2020-04-27
So it looks like you're trying to run VirtualBox on Win10. The "access denied" error likely has to do with Windows permissions. It's not an Ubuntu problem.

---

### Post by fuzmic on 2020-04-27
Sensei..this happened in win7.  However when try again & stay patience Ubuntu did work.  Virtual Mc bit slow. Thread closed.

---

