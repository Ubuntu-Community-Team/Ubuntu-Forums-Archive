---
title: "VM ware error"
date: 2012-09-10
forum: Virtualisation
---

### Post by Joe mathew on 2012-09-10
i'm unable to install Virtual box 64bit in my Pc.

Specifications 
Ram: 4GB
processor : Core2Duo
Motherboard : ASUS P5G41T-MLX

my board supports 64Bit Os, i installed Ubuntu 12.04 64bit OS . The problem occurs when i try to install Virtual box , it automatically installs 32 bit virtual box instead of 64 bit Virtual box , even my system supports 64bit and i unable to install any 64 bit OS in my virtual Box. What is the problem?
some screen shots
[IMG][[img]http://s19.postimage.org/mltqxiyhb/Screenshot_from_2012_09_01_12_00_43.png[/img]](http://postimage.org/image/mltqxiyhb/)

[[img]http://s19.postimage.org/c1jtextzj/Screenshot_from_2012_09_01_12_00_34.png[/img]](http://postimage.org/image/c1jtextzj/)

[[img]http://s19.postimage.org/vd6a8a51r/Screenshot_from_2012_09_09_19_25_19.png[/img]](http://postimage.org/image/vd6a8a51r/)

[[img]http://s19.postimage.org/hxj9itwjz/SDC10481.jpg[/img]](http://postimage.org/image/hxj9itwjz/)


[[img]http://s19.postimage.org/u534i0vtb/Screenshot_from_2012_09_10_20_06_04.png[/img]](http://postimage.org/image/u534i0vtb/)

[[img]http://s19.postimage.org/yfhsdm0wf/Screenshot_from_2012_09_10_20_03_26.png[/img]](http://postimage.org/image/yfhsdm0wf/)

[[img]http://s19.postimage.org/4c39lnxn3/Screenshot_from_2012_09_10_20_02_44.png[/img]](http://postimage.org/image/4c39lnxn3/)

[[img]http://s19.postimage.org/qpb08gykv/SDC10490.jpg[/img]](http://postimage.org/image/qpb08gykv/)[/IMG]

---

### Post by Cheesemill on 2012-09-10
Why do you think you have the 32-bit version of VirtualBox installed?

I don't see anything in your screenshots that would suggest this.

---

### Post by Joe mathew on 2012-09-10
was installed using terminal ,the command is "sudo apt-get install virtualbox-4.1".

---

### Post by newb85 on 2012-09-10
Check the settings for the virtual machine you're trying to run.  By default, VirtualBox will only let it use one of your CPU cores.  That may not be good enough to run Windows 64-bit.  Also, you'll probably want to bump up the RAM allotment and turn on 3D graphics accelleration.

---

