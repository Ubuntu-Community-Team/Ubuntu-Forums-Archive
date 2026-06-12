---
title: "problem with virtual box"
date: 2018-02-03
forum: Virtualisation
---

### Post by an3as on 2018-02-03
I try to install VirtualBox but it can't start! it flashing and after 4-5 sec it's close.

When i try on termninal I recive this msg :


[INDENT]:~$ virtualbox[/INDENT]
[INDENT]WARNING: The vboxdrv kernel module is not loaded. Either there is no module[/INDENT]
[INDENT]         available for the current kernel (4.4.0-112-generic) or it failed to[/INDENT]
[INDENT]         load. Please recompile the kernel module and install it by[/INDENT]
[INDENT][/INDENT]
[INDENT]           sudo /sbin/vboxconfig[/INDENT]
[INDENT][/INDENT]
[INDENT]         You will not be able to start VMs until this problem is fixed.[/INDENT]
[INDENT]VirtualBox: Error -10 in SUPR3HardenedMain![/INDENT]
[INDENT]VirtualBox: Effective UID is not root (euid=1001 egid=1001 uid=1001 gid=1001)[/INDENT]
[INDENT][/INDENT]
[INDENT]VirtualBox: Tip! It may help to reinstall VirtualBox.


I'm new on ubuntu and I really don't understan a lot, could soem one help me? 

thank you[/INDENT]

---

### Post by wildmanne39 on 2018-02-03
*Thread moved to **Virtualisation, a more appropriate forum**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by QIII on 2018-02-03
Hello!

Would you please tell us how you installed VirtualBox?

---

### Post by an3as on 2018-02-03
sorry, 
thank you
> **wildmanne39 said:**
> *Thread moved to **Virtualisation, a more appropriate forum**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by an3as on 2018-02-03
[COLOR=#000000][FONT=Monaco][FONT=Arial][/FONT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][FONT=Arial]1
wget -q [https://www.virtualbox.org/download/oracle_vbox.asc](https://www.virtualbox.org/download/oracle_vbox.asc) -O- | sudo apt-key add -
1
sudo gedit /etc/apt/sources.list


1
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial contrib


1
sudo apt-get update && sudo apt-get install virtualbox-5.1


[/FONT]
[/FONT][/COLOR]

---

### Post by an3as on 2018-02-03
as it described here

[https://www.zoomingin.net/come-installare-virtualbox-5-su-ubuntu/](https://www.zoomingin.net/come-installare-virtualbox-5-su-ubuntu/)

---

### Post by QIII on 2018-02-03
Did a language barrier keep you from using the instructions [here]("https://www.virtualbox.org/wiki/Linux_Downloads")?

I'm not going to review a third-party page for accuracy.

What release of Ubuntu are you using?

There are a couple of ways of going about fixing this, but knowing which release of Ubuntu you are using might be helpful.

---

### Post by an3as on 2018-02-03
> **QIII said:**
> 

What release of Ubuntu are you using?

There are a couple of ways of going about fixing this, but knowing which release of Ubuntu you are using might be helpful.

ubuntu 16.04 lts

---

### Post by QIII on 2018-02-03
OK.

Let's try this.

1. Uninstall Virtual Box (it looks like you have 5.1 installed):

```
sudo apt purge virtualbox-5.1
```

2. The "purge" command does not remove anything in your /home directory, so you will have to be sure anything you may have put there is removed.

3. Check your BIOS/UEFI to be sure that virtualization is enabled.  This is different for every manufacturer and board, so you may have to consult your documentation.

4. Install some important packages (please copy and paste this exactly):

```
sudo apt install dkms build-essential linux-headers-`uname -r`
```

5. Attempt to install VirtualBox again by following the instructions at the link I posted earlier.

---

### Post by an3as on 2018-02-03
> **QIII said:**
> 
 Check your BIOS/UEFI to be sure that virtualization is enabled.  This is different for every manufacturer and board, so you may have to consult your documentation.



I really didn't understand nothing.

---

### Post by QIII on 2018-02-03
You will have to boot your machine and enter your BIOS setup.  I can't tell you any exact details about how to do that because each motherboard is different.  Usually it requires pressing a particular key during the BIOS splash.

Do you have a manual for your machine?

---

### Post by an3as on 2018-02-03
Unfortunately I'm not such an expert, althought I found " GDebi package instaler " and with this I've uninstall everything an re-install corectly .  Now is everything ok! - I think that the problem start because there is a problem when you try to install Third-Party Apps on Ubuntu 16.04.


Thank you everybody :)

---

