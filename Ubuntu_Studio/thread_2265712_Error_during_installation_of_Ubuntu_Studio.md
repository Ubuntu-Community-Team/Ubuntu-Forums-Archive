---
title: "Error during installation of Ubuntu Studio"
date: 2015-02-17
forum: Ubuntu Studio
---

### Post by Kai_Stahlenberg on 2015-02-17
Hello,

I'm new to Ubuntu (first post here...). I downloaded the Ubuntu Studio ISO and wrote the image to DVD.

I want to install Ubuntu on an "old" HDD of mine, computer is a white MacBook 4,1 (2.4GHz Intel Core2Duo, 4GB Ram, 13" Display).

I was able to start a Live Session from the DVD (held down Alt during bootup an choose "EFI" from the bootmenu). Within the Live Session I chose "Install Ubuntu Studio". Actually I tried different scenarios (trying to install straight after bootup from the DVD, from within the Live Session...)
I also tried to install to a seperate partition, but in the end I deleted all partitions from the HDD and choose "Delete HDD and install Ubuntu" from the installation menu.

Anyway, the result was always the same: at the end of the installation process I got the error message 
"**Das Paket grub-efi-amd64-signes konnte nicht in /target/ installiert werden.**
**Ohne den GRUB-Bootloader wird das installierte System nicht booten.**"
...and the installation failed.

I tried to google the error message and infos on the installation process, but couldn't really find a solution.

As far as I understand, the problem has something to do with the EFI boot. But I thought, the "delete HDD and install ubuntu" method, was kind of the straight forward and simplest way!?

Additional information: It seemed to me during the live session that WLAN was not working and I didn't find a way to activate it.

Any help is appreciated, I hope there is a relatively easy solution.
Right now I'm pretty frustrated, since I thought Ubuntu was more user friendly these days and kind of easy to install. But all I see is error messages and prompting in the terminal... :-(

Thanks.

---

### Post by multimuse on 2015-02-24
A couple things:

* It's said that it's pretty much a vital step to do the CHECKSUM hash verification step on any & all ISO downloads to assure it was both complete (uninterrupted download) and uncorrupted. (I'm still a newbie at learning that procedure too.) If the verification fails, then your download was no good, and should not be used. You'd then want to delete it and try again, perhaps from another download mirror.  So did you verify the validity of your newly downloaded ISO first?  If not, you can not be sure it is not corrupted or _incomplete_, eh? :( 

* My German translation is a little rusty, but my best translation of your error quoted below, reveals some vital info, that I summarize as follows:
A vital package called **grub-efi-amd64-signes **could not be installed in it's **/target/ **drive/path/folder.   As you may know, grub ...
**GNU GRUB** (short for **GNU GRand Unified Bootloader**) is a [boot loader]("https://en.wikipedia.org/wiki/Boot_loader") package from the [GNU Project]("https://en.wikipedia.org/wiki/GNU_Project").
Without that, the installation would not be able to boot. That's what the rest of the German error message says.

Of course, 2 reasons that might be the case are, that the grub package was missing from the distro, or whatever the /target/ was supposed to be, could not be created, or found, or perhaps written to, during installation. (permissions conflict, or possibly insufficient storage space remaining, or... ???)

Must confess, I don't know what EFI is.  Care to enlighten us on that?
Cheers, and good luck!
~~~~~~~~~~~~~~

> **Kai_Stahlenberg said:**
> Hello,

I'm new to Ubuntu (first post here...). I downloaded the Ubuntu Studio ISO and wrote the image to DVD.

I want to install Ubuntu on an "old" HDD of mine, computer is a white MacBook 4,1 (2.4GHz Intel Core2Duo, 4GB Ram, 13" Display).

I was able to start a Live Session from the DVD (held down Alt during bootup an choose "EFI" from the bootmenu). Within the Live Session I chose "Install Ubuntu Studio". Actually I tried different scenarios (trying to install straight after bootup from the DVD, from within the Live Session...)
I also tried to install to a seperate partition, but in the end I deleted all partitions from the HDD and choose "Delete HDD and install Ubuntu" from the installation menu.

Anyway, the result was always the same: at the end of the installation process I got the error message 
"**Das Paket grub-efi-amd64-signes konnte nicht in /target/ installiert werden.**
**Ohne den GRUB-Bootloader wird das installierte System nicht booten.**"
...and the installation failed.

I tried to google the error message and infos on the installation process, but couldn't really find a solution.

As far as I understand, the problem has something to do with the EFI boot. But I thought, the "delete HDD and install ubuntu" method, was kind of the straight forward and simplest way!?

Additional information: It seemed to me during the live session that WLAN was not working and I didn't find a way to activate it.

Any help is appreciated, I hope there is a relatively easy solution.
Right now I'm pretty frustrated, since I thought Ubuntu was more user friendly these days and kind of easy to install. But all I see is error messages and prompting in the terminal... :-(

Thanks.

---

### Post by multimuse on 2015-02-24
Found this on your issue. Don't know if it would help you. See: [http://askubuntu.com/questions/208405/how-to-efi-install-ubuntu](http://askubuntu.com/questions/208405/how-to-efi-install-ubuntu)

---

