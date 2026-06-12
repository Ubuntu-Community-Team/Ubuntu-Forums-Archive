---
title: "VirtualBox errors"
date: 2015-08-23
forum: Virtualisation
---

### Post by xedoc on 2015-08-23
Hi, the printscreen shows the problem.
Any idea how to fix it ?[ATTACH=CONFIG]264006[/ATTACH]

Thanks.

---

### Post by QIII on 2015-08-23
Hello!

What is the host OS, what version of VirtualBox are you using and how did you install it?

---

### Post by xedoc on 2015-08-23
Hi, Its Kali Linux,  Virtualbox version 4.3.26 ubuntu r98988, i did download and then i opened it with ubuntu software centre.

With thanks and regards.

---

### Post by QIII on 2015-08-23
So you are attempting to virtualize a Kali guest on a Kali host?

---

### Post by xedoc on 2015-08-23
Nop, i'm using Ubuntu-mate and i'm trying to virtualize Kali.

---

### Post by QIII on 2015-08-23
OK.  Just wanted to make sure what the host is.

Did you see the suggested command in the message box at the upper right of your image?  Did you try that?

---

### Post by xedoc on 2015-08-23
I tried to execute '/etc/... as it is indicated. Answer is: No such file or directory. Then i tried to do " apt-cache search DKMS " and i have installed everything related with DKMS and virtualbox.

---

### Post by Skaperen on 2015-08-23
what do you get from "ls -l '/etc/init.d/vboxdrv setup'" ? did you include the ' quotes when you did the command?

---

### Post by xedoc on 2015-08-23
Ls: cannot access /etc/init.d/vboxdrv setup: No such file or directory.

I am as root.

---

### Post by howefield on 2015-08-23
The command you should have used is

```
sudo /etc/init.d/vboxdrv setup
```

Is that what you did use ?

---

### Post by xedoc on 2015-08-23
I used only:
'/etc/init.d/vboxdrv setup'

Since i was root already.

---

### Post by howefield on 2015-08-23
> **xedoc said:**
> I used only:
'/etc/init.d/vboxdrv setup'

Since i was root already.

Yes I saw that after you edited your post.

You don't need the single quotation marks was really what I was getting at.

---

### Post by bisherbas on 2015-08-23
> **howefield said:**
> The command you should have used is

```
sudo /etc/init.d/vboxdrv setup
```

Is that what you did use ?

Having the same problem. Running that command gives me the following:

```
sudo: /etc/init.d/vboxdrv: command not found


```

Running Xubuntu 14.04.3

---

### Post by v3.xx on 2015-08-23
The package "linux-headers" installed?

---

### Post by bisherbas on 2015-08-23
> **v3.xx said:**
> The package "linux-headers" installed?

Absolutely. Uninstalled the Virtualbox which I had installed via the official repo. Installed 5.0 from the Virtualbox website and now everything looks great. Package manager has to look into it.

---

### Post by thiagomarcal1984 on 2015-09-06
I've got the same problem. A ran the command as follows:

```
thiago@gyodiver:~$ sudo /etc/init.d/vboxdrv setup
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMSError! Your kernel headers for kernel 3.16.0-30-generic cannot be found.
Please install the linux-headers-3.16.0-30-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
 ...failed!
  (Failed, trying without DKMS)
Recompiling VirtualBox kernel modules ...failed!
  (Look at /var/log/vbox-install.log to find out what went wrong)
```

And the log says:

```
Uninstalling modules from DKMS  removing old DKMS module vboxhost version  5.0.2


------------------------------
Deleting module version: 5.0.2
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS


Creating symlink /var/lib/dkms/vboxhost/5.0.2/source ->
                 /usr/src/vboxhost-5.0.2


DKMS: add completed.
Failed to install using DKMS, attempting to install without
Makefile:185: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Pare.
```

I've tried to run this command, but it still fails, as the dkms is already installed: 

```
thiago@gyodiver:~$ sudo apt-get install dkms build-essential linux-headers-generic
Lendo listas de pacotes... Pronto
Construindo árvore de dependências       
Lendo informação de estado... Pronto
build-essential já é a versão mais nova.
dkms já é a versão mais nova.
linux-headers-generic já é a versão mais nova.
0 pacotes atualizados, 0 pacotes novos instalados, 0 a serem removidos e 0 não atualizados.


```

---

