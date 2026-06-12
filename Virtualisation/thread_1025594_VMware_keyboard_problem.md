---
title: "VMware keyboard problem"
date: 2008-12-30
forum: Virtualisation
---

### Post by Levo on 2008-12-30
I have a problem with my keyboard when using VMware Workstation 6.5.1 (I had the same problem with 6.5, but NOT with 6.0.5). The buttons are not working properly. For example, I have to press numpad 3 instead of down arrow, etc. And most of them don't even work. OS: Ubuntu Intrepid, fully updated. Any suggestions? Thanks in advance.

---

### Post by nbotticelli on 2008-12-30
I have a very similiar problem with my keyboard also.

I have a Nexlink EL80 laptop (manufactured by Compal) where the arrow keys work fine on the host OS but on an VM they don't work. Don't know about using the numpad since there is no separate numpad on this laptop.

I've had no issues on a other hardware but this machine is one of those custom generic builds so it may have some funky hardware.

---

### Post by Dedoimedo on 2008-12-30
Did you test with any other keyboard to see if the problem is with software or the specific keyboard?
Dedoimedo

---

### Post by Levo on 2008-12-30
> **Dedoimedo said:**
> Did you test with any other keyboard to see if the problem is with software or the specific keyboard?

No, I didn't. VMware 6.0.5 used work fine. Version 6.5.0 and 6.5.1 have those issues. I believe that I need some kind of configuration. Something changed in the last release.

---

### Post by yulian on 2009-02-19
To fix this, you need to run the following command from terminal:

echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config

and if VMware Player/Server/Workstation was running, just restart it.

Yulian

---

### Post by Levo on 2009-02-28
> **yulian said:**
> To fix this, you need to run the following command from terminal:

echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config

and if VMware Player/Server/Workstation was running, just restart it.

Yulian

I tried it and it works. Thanks!

---

### Post by chemburn on 2009-03-23
hey all, having the same problem, this is my lenovo Y30, dual boots with winxp, running hardy 64bit 8.10. i just had to do a reinstall, had this problem last time with it and this solution worked just fine, this time however, same build and hardware, same version of vmware, it say premission denied unless I go at it as SU, then it spits out no such file or directory. I have tried this from my /etc/vmware, i know its there, i can see the config file. I am a bit stressed at this point, if anyone could give me a hand i would greatly appreciate it. Thanks in advance
J-

---

### Post by mcativa on 2009-04-27
> **yulian said:**
> To fix this, you need to run the following command from terminal:

echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config

and if VMware Player/Server/Workstation was running, just restart it.

Yulian

Worked also for me. Lenovo T60. Ubuntu 9.04, vmware 6.5.1, latest vmware tools installed.

---

### Post by cbhargava on 2009-05-06
Worked for me too.

Since I upgraded my host os from 8.04 to 9.04, all my Linux guest VMs started having trouble with the keyboard. When I pressed up arrow key inside the VM it would open the screen-shot dialog.

App: Vmware Player 2.5.1 build-126130
Keyboard: Dell SK-8135

Thanks :KS

> **yulian said:**
> To fix this, you need to run the following command from terminal:

echo 'xkeymap.nokeycodeMap = true' > ~/.vmware/config

and if VMware Player/Server/Workstation was running, just restart it.

Yulian

---

### Post by davekenny on 2009-07-28
fixed my problem

THANKS :)

vmware server 2.0x in ubuntu 9.04 for a host and Windows XP as a guest.

---

