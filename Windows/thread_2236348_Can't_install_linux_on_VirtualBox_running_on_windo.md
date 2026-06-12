---
title: "Can't install linux on VirtualBox running on windows 8.1"
date: 2014-07-26
forum: Windows
---

### Post by fernandojosecabral on 2014-07-26
Trying to install linux on VirtualBox running under windows 8.1 (Dell Inspiron) I get the followin error:

```
Failed opening virtual machine **Linux**.

The virtual machine **'Linux'** has terminated unexpectedly during startup with exit code 1.

[TABLE="width: 100%"]
[TR]
[TD]Código de Resultado:[/TD]
[TD]E_FAIL (0x80004005)[/TD]
[/TR]
[TR]
[TD]Componente:[/TD]
[TD]Machine[/TD]
[/TR]
[TR]
[TD]Interface:[/TD]
[TD]IMachine {480cf695-2d8d-4256-9c7c-cce4184fa048}[/TD]
[/TR]
[/TABLE]

```Image bellow (click to magnify) gives the full message.
[ATTACH=CONFIG]255043[/ATTACH]
Any hints on how to solve this most appreciated.

---

### Post by ajgreeny on 2014-07-26
How exactly are you trying to install the VM, direct from an .iso file or using a DVD or USB install disk?

Also which Linux is this; I assume probably Mint 17 from the mention of Qiana in the error, but is it 64bit or 32bit?

---

### Post by fernandojosecabral on 2014-07-26
> **ajgreeny said:**
> How exactly are you trying to install the VM, direct from an .iso file or using a DVD or USB install disk?

Also which Linux is this; I assume probably Mint 17 from the mention of Qiana in the error, but is it 64bit or 32bit?

This morning I downloaded this file straight from Virtuabox's page: **VirtualBox-4.3.14-95030-Win.exe**
Installation was eventless. Then I donwloaded Qiana's .iso file which I tried to run under VirtualBox under Windows 8.1.
I first configured it with 16 GB disk and 4 GB RAM. When I pointed to the .iso file to initiate the installation, I got the error.

It is probabily useful to let you know that I have also generated a live pendrive from the same iso. This works good on 
two different machines (which are very similar to each other). But, this same bootable pendrive won't boot on the
one I am currently running windows 8.1 + virtualbox. In this case (trying to boot from the pendrive without the virtual
machine) the error I get is that it cannot start the X-server (I see no relation between the two problems, but... who knows?)

Hardware: Dell Inspiron 15R 5537-A20

---

### Post by howefield on 2014-07-26
Thread moved to the "*Other OS/Distro Support*" forum.

---

### Post by coffeecat on 2014-07-26
> **fernandojosecabral said:**
> Trying to install linux on VirtualBox running under windows 8.1 (Dell Inspiron) I get the followin error:

```
Failed opening virtual machine **Linux**.

The virtual machine **'Linux'** has terminated unexpectedly during startup with exit code 1.

```

> **fernandojosecabral said:**
> 
Image bellow (click to magnify) gives the full message.
[ATTACH=CONFIG]255043[/ATTACH]

This is due to a VirtualBox bug, and nothing to do with the guest OS:

[https://forums.virtualbox.org/viewtopic.php?f=6&t=62615](https://forums.virtualbox.org/viewtopic.php?f=6&t=62615)

I got this using Windows 8 as the host OS trying to install Xubuntu 14.04.1 in VirtualBox 4.3.14. The 4.3.15 version of VirtualBox didn't work for me either, but the earlier 4.3.12 did, which you can get here:

[https://www.virtualbox.org/wiki/Download_Old_Builds_4_3](https://www.virtualbox.org/wiki/Download_Old_Builds_4_3)

I'm going to stick with 4.3.12 until the VB people have had a chance to sort this out. Not many people running Windows as the guest OS are not going to have AV software running, so I am sure the VB people are motivated to get this right.

---

### Post by fernandojosecabral on 2014-07-26
> **coffeecat said:**
> This is due to a VirtualBox bug, and nothing to do with the guest OS:

[https://forums.virtualbox.org/viewtopic.php?f=6&t=62615](https://forums.virtualbox.org/viewtopic.php?f=6&t=62615)

I got this using Windows 8 as the host OS trying to install Xubuntu 14.04.1 in VirtualBox 4.3.14. The 4.3.15 version of VirtualBox didn't work for me either, but the earlier 4.3.12 did, which you can get here:

[https://www.virtualbox.org/wiki/Download_Old_Builds_4_3](https://www.virtualbox.org/wiki/Download_Old_Builds_4_3)

I'm going to stick with 4.3.12 until the VB people have had a chance to sort this out. Not many people running Windows as the guest OS are not going to have AV software running, so I am sure the VB people are motivated to get this right.
  On the bull's eye. As soon as I downgraded to 4.3.12 it worked perfectly.
Thank you.

---

### Post by rleigh-debian on 2014-11-15
Note that the latest release (4.3.16) appears to have resolved the problem.  It certainly did for me with Windows 8.1, where 4.3.14 stopped working last week, probably after installing Windows updates.

---

