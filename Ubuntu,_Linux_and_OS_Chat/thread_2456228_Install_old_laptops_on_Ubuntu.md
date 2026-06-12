---
title: "Install old laptops on Ubuntu?"
date: 2021-01-07
forum: Ubuntu, Linux and OS Chat
---

### Post by spoodle2 on 2021-01-07
**Apologies for mixing my grammar up in the title - great start!**

Hi there I'm new to this forum and Ubuntu itself,

As the title says and no doubt has been discussed many times, I'm collecting as many laptops as I can to send to the Philippines to give to kids in a town that I know.

It may be a project that has a big fly in the anointment but I'm assuming that if I install a Linux OS then it could bring some life to the laptops and make some kids very happy! 

Firstly, is this feasible or am I too naive to believe that this could work? If it is feasible, could you be kind enough to point me in the right direction to get a decent understanding and instruction in what to do?

I am very use to installing a Windows OS, troubleshooting, repairing and building PCs & laptops.

Thanks very much and hope you can help.

---

### Post by CelticWarrior on 2021-01-07
Welcome.

Well, it depends.

It depends on how old and/or underpowered those laptops are.
If it's 32-bit hardware - worst case scenario - probably better not to use Ubuntu or Ubuntu based distros because the last still supported 32-bit Ubuntu release is 18.04. That means support until April 2023 only for standard Ubuntu. Flavors (Lubuntu, Xubuntu, Kubuntu, etc.) have only 3 years so they all will be out of support next April. For those cases Debian or AntiX are preferable.
If it's 64-bit hardware then you have options. You may try Ubuntu 20.04 (5 years support > April 2025) but if old/underpowered you may need a lighter flavor instead (3 years support > April 2023).

---

### Post by grahammechanical on 2021-01-07
The matter of installation is less complicated if you are not wanting to dual boot with Microsoft Windows. The process will then be

1) Download and burn an ISO image of Ubuntu (for example) to DVD or USB memory stick.
2) Boot the machine from the DVD/USB memory stick.
3) At the Ubuntu welcome screen select Try Ubuntu. This is called a Live Session and you can test to see if the operating system has drivers for the hardware.
4) Select Install Ubuntu.
5) At the options screen select Erase disc and Install Ubuntu and the installer should take care of everything.

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

[https://ubuntu.com/tutorials/burn-a-dvd-on-windows#1-overview](https://ubuntu.com/tutorials/burn-a-dvd-on-windows#1-overview)

[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview)

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

This is something that you need to think about. When we install Ubuntu we are asked to set up a user name and password. Whoever has the knowledge of that user name and password has authority not only to use Ubuntu as an ordinary user but to gain administrator privileges. Do you see the problem? Without passing on to the recipients of your gift the user name and password no one can use the machine. But if too many people know this user name and password the operating system will soon be messed up by people acting irresponsibly.

Before shipping the machines abroad you should set up a second user that cannot gain administrator privileges and only give the original user name and password to someone who will take responsibility for maintaining the machine.

An OEM install might be the solution. This tutorial will explain how to do it.

[http://ubuntuconfig.com/ubuntu-oem-install-using-any-ubuntu-iso-image/](http://ubuntuconfig.com/ubuntu-oem-install-using-any-ubuntu-iso-image/)

Regards

---

### Post by DuckHook on 2021-01-09
My only observation would be to not mix&#8209;and&#8209;match OSes. It makes it needlessly hard to maintain. You should aim for the lowest common denominator, in this case, 32-bit support. As CelticWarrior has pointed out, Ubuntu 32-bit support is lacking. I recommend either of the following:

[https://www.bunsenlabs.org](https://www.bunsenlabs.org)
[https://www.bodhilinux.com](https://www.bodhilinux.com)

Both are light and (what seems to matter for ease of adoption) pretty.

---

### Post by spoodle2 on 2021-01-10
Thank you very much for your time and replies, this has helped tremendously.

I will try to install Ubuntu on one machine and see how I get on before coming back with anymore questions or issues.

Thanks again.

---

### Post by kurt18947 on 2021-01-10
First Spoodle2, good on you for helping those less privileged. In addition to the 32/64 bit issue, make sure the wifi is supported without extraordinary effort. Ubuntu has an 'additional drivers' screen which can help with wifi drivers but those who are maintaining the machines in the Philippines has to know about that. Having to use a ppa for drivers would make it very difficult for less knowledgeable users to maintain. I guess an option would be to include a USB wifi device that is known to be well supported if that's practical.

---

### Post by GhX6GZMB on 2021-01-10
I wouldn't choose Ubuntu for old HW, it will bring it to its knees.
Choose a lightweight dialect like Lubuntu or Xubuntu instead.

---

### Post by mastablasta on 2021-01-11
what will the laptops be used for? school work? games? will users have internet connection? is connection via USB key/mobile phone? does the USB /mobile connection have linux support? if they will use USB keys for mobile internet connection make sure they support linux. otherwise windows is better option.

how old is old? even 8 or 10 years old it really depends - what configuration is it? old core i5 is very different from old Atom. i have 17 years old single core desktop, but it has newish GPU, so many games (up ot about 2013) run and everything is faster on linux than it ever was on windows. but if i had lower end 17 year old PC with old GPU, all i could do is cry. 

but even 8 years old laptop core i3 is at least 5x faster than my PC. add SSD and more than 4 Gb ram to it and it will fly compared to my old box.

laptops - they usually have one GPU chip  that is on CPU. old intel is well supported. old AMD support is mixed.

---

