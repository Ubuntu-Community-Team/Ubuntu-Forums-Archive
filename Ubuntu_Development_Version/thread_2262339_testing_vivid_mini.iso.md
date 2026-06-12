---
title: "testing vivid mini.iso"
date: 2015-01-24
forum: Ubuntu Development Version
---

### Post by sudodus on 2015-01-24
Finally it is possible to install with the Ubuntu Vivid ***mini.iso*** (netboot installer)

The 32-bit Ubuntu mini.iso dated 2015-01-22 from

[http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-i386/20101020ubuntu360/images/](http://archive.ubuntu.com/ubuntu/dists/vivid/main/installer-i386/20101020ubuntu360/images/)

with md5sum

```
79905f6372c83ad0da93cb25015029f9  ./netboot/mini.iso
```

works.

The red bug [http://launchpad.net/bugs/1403982](http://launchpad.net/bugs/1403982) is squashed :-)

-o-

I made a simple mini installed system (with no server or desktop system installed). [Target computer ]("http://www.toshiba.se/laptops/satellite-pro/c850/satellite-pro-c850-19w/")

1. The default installed system gets stuck at a completely black sceen. mini.iso of previous versions work well in this computer and Lubuntu Vivid works well too. nomodeset does not help.

2. The systemd grub option ends up with a black screen and a blinking cursor. nomodeset does not help.

3. I can get further and log in via recovery mode :-)

4. Later on I found that by pressing ***ctrl+alt+F1 ... F6*** I get to log in also in default mode and systemd mode (without any boot option). But a noob might not try that ...

5. And I see no plymouth screen except at poweroff and reboot.

6. After login in the default mode I get the following message:

```
[   67.141970] systemd-logind[943]: Failed to start user service: Unknown unit: user@1000.service
```

and then the usual bash prompt, and I can issue commands.

For example
**free -m** shows that 74 MB RAM is used, (a corresponding value for 14.04 LTS is 34 MB, less than half).
**uname -a** shows that the kernel **3.18.0-9-generic #10-Ubuntu SMP** is used.

There is no such message in systemd mode.

---

### Post by sudodus on 2015-01-24
I installed ***Xubuntu-Core*** into my minimal system (32-bit) using the following commands


 ```
sudo apt-get update
sudo apt-get upgrade  # nothing added
sudo apt-get install xubuntu-core
```

 
and a working Xubuntu Core system was created.

I found ***no problem  with the default boot***. There is a complaint that ***xscreensaver*** is old  (the message disappears after a few seconds).


 It works also with the grub alternative using ***systemd***.

---

