---
title: "Unable to Install the VirtualBox Guest Additions to My Ubuntu VM"
date: 2022-07-17
forum: Ubuntu, Linux and OS Chat
---

### Post by hashiru2 on 2022-07-17
[COLOR=#000000][FONT=&quot]Hi All,[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]I am trying to setup my virtual box lab environment, but I am unable to install VirtualBox Guest Additions. Host (PC) is Windows and Guest is Ubuntu.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]I already went through these steps.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]1. Update Ubuntu[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]$ sudo apt update[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]$ sudo apt install build-essential dkms linux-headers-$(uname -r)[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]2. On the virtual machine window, click on Devices > Insert Guest Additions CD Image.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]3. On the command line type the command:[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]$ sudo ./VBoxLinuxAdditions.run[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Error Message: sudo: /.VBoxLinuxAdditions.run: command not found[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Alternatively, I used sh ./VBoxLinuxAdditions.run[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Error Message: sh: 0: cannot open ./VBoxLinuxtAdditions.run: No such file[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]From the disk image from the desktop, I click VBoxLinuxAdditions.run to no avail. What do I do now?[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]References used:[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]a.[(https://www.youtube.com/watch?v=Kbez-XdXqrw&t=120s)  b.[https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/guestadd-install.html#mountingadditionsiso](https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/guestadd-install.html#mountingadditionsiso)  c. [https://linuxconfig.org/install-virtualbox-guest-additions-on-linux-guest](https://linuxconfig.org/install-virtualbox-guest-additions-on-linux-guest)  d. https://help.ubuntu.com/community/VirtualBox/GuestAdditions?_ga=2.178508516.1731500707.1658085098-1775230561.1658085098"] ]("http://Hi All,  I am trying to setup my virtual box lab environment, but I am unable to install VirtualBox Guest Additions. Host (PC) is Windows and Guest is Ubuntu.  I already went through these steps.  1. Update Ubuntu  $ sudo apt update $ sudo apt install build-essential dkms linux-headers-$(uname -r)  2. On the virtual machine window, click on Devices > Insert Guest Additions CD Image.  3. On the command line type the command:  $ sudo ./VBoxLinuxAdditions.run  Error Message: sudo: /.VBoxLinuxAdditions.run: command not found  Alternatively, I used sh ./VBoxLinuxAdditions.run  Error Message: sh: 0: cannot open ./VBoxLinuxtAdditions.run: No such file  From the disk image from the desktop, I click VBoxLinuxAdditions.run to no avail. What do I do now?  References used:  a. [https://www.youtube.com/watch?v=Kbez-XdXqrw&t=120s)[/FONT][/COLOR][https://www.youtube.com/watch?v=Kbez-XdXqrw&t=120s](https://www.youtube.com/watch?v=Kbez-XdXqrw&t=120s)[COLOR=#000000][FONT=&quot][/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]b.[/FONT][/COLOR][https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/guestadd-install.html#mountingadditionsiso](https://docs.oracle.com/en/virtualization/virtualbox/6.0/user/guestadd-install.html#mountingadditionsiso)[COLOR=#000000][FONT=&quot][/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]c. [/FONT][/COLOR][https://linuxconfig.org/install-virtualbox-guest-additions-on-linux-guest](https://linuxconfig.org/install-virtualbox-guest-additions-on-linux-guest)

[COLOR=#000000][FONT=&quot]d. [/FONT][/COLOR][https://help.ubuntu.com/community/VirtualBox/GuestAdditions?_ga=2.178508516.1731500707.1658085098-1775230561.1658085098](https://help.ubuntu.com/community/VirtualBox/GuestAdditions?_ga=2.178508516.1731500707.1658085098-1775230561.1658085098)

---

### Post by Perfect Storm on 2022-07-17
Hi,

You need to 

```
cd <distination>
```

before you run that command.

---

### Post by grahammechanical on 2022-07-17
Did you change directory to where the CD drive is mounted?

> Change to the directory where your CD-ROM drive is mounted               and run the following command as root:

It might be a typing error but there should be a space between sh and ./VBoxLinuxAdditions.run

```
sh ./VBoxLinuxAdditions.run
```

[https://www.virtualbox.org/manual/ch04.html](https://www.virtualbox.org/manual/ch04.html)

See section 4.2.2.1 Installing the Linux Guest Additions

Regards

---

### Post by hashiru2 on 2022-07-17
Thanks Perfect Storm and grahammechanical. It worked

---

