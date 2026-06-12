---
title: "LXBuntu? New flavor of lightweight ubuntu-based distro usnig LXDE 0.3"
date: 2008-04-05
forum: The Cafe
---

### Post by PCMan on 2008-04-05
After the latest 0.3 release of LXDE or Lightweight X11 Desktop Environment ([http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)), many people are asking for a LXDE-based ubnutu distro.
Now, we are proud to announce this new flavor of ubuntu-based distro - [PUD GNU/Linux LXDE edition]("http://distrowatch.com/?newsid=04826").  

[[IMG]http://pud-linux.sourceforge.net/image/pud-lxde-2.jpg[/IMG]]("http://pud-linux.sourceforge.net/screenshot/pud-lxde-2.jpg")      [[IMG]http://pud-linux.sourceforge.net/image/pud-lxde-1.jpg[/IMG]]("http://pud-linux.sourceforge.net/screenshot/pud-lxde-1.jpg")

See the introduction on Distrowatch for detail:
[http://distrowatch.com/?newsid=04826](http://distrowatch.com/?newsid=04826)

[PUD]("http://pud-linux.sourceforge.net/index.en.html") is another project held by Pin-Shiun Chen (penk) trying to make lightweight,  useful, and user-friendly ubuntu-based distros.
The PUD series succesfully provides a minimalist desktop environment with a bundle of useful applications in a small installable ubuntu-based live cd. 
Previously it uses xfce4, and this time, a special edition for LXDE is created.

There are also some interesting sub-projects on the PUD project page, such as 
BootGear - a new project devoted to minimalize the boot time of Linux, and
Build-LiveCD" ToolKit - an easy-to-use toolkit help you build your own live cd.
Visit the project page of PUD for detail, if you are interested in it.

In addition to this new distro, you can install LXDE on your existing ubuntu.
An apt repository for LXDE 0.3 is provided in this thread.
[http://ubuntuforums.org/showthread.php?t=738958](http://ubuntuforums.org/showthread.php?t=738958)

More information and screenshots are available on the LXDE project page.
[http://lxde.sourceforge.net/](http://lxde.sourceforge.net/)
The official packages of LXDE are now getting in debian sid, and will be available on ubuntu in the near future.

---

### Post by POW R TOC H on 2008-04-05
Hm... Maybe I can use this to make that old trashcan PC of mine do something useful... Nice job!

---

### Post by misaine on 2008-04-11
lxde 0.3  with compiz-fusion on parsix(debian) and ubuntu 8.04
[[img]http://pix.nofrag.com/5/6/f/0fb1195a8358e2695953c129d0203t.jpg[/img]](http://pix.nofrag.com/5/6/f/0fb1195a8358e2695953c129d0203.html) [[img]http://pix.nofrag.com/c/7/1/92bad421b7b267d10a8d0547789c3t.jpg[/img]](http://pix.nofrag.com/c/7/1/92bad421b7b267d10a8d0547789c3.html) [[img]http://pix.nofrag.com/6/8/d/a7114e0ae5222b01f85dea0b206cet.jpg[/img]](http://pix.nofrag.com/6/8/d/a7114e0ae5222b01f85dea0b206ce.html)

---

### Post by kagashe on 2008-04-21
The LCD screen of my Laptop is broken and I use an external VGA monitor and using the Laptop as a Desktop.

Till Gutsy Gibbon there was no problem and the VGA monitor was automatically detected without any manual settings. I also use other distributions like Mandriva, Fedora, Puppy, DSL, Slax and no settings are required to be done in any of them.

Yesterday I downloaded PUD LXDE edition (which is based on Hardy Heron Beta) Live CD and tried it. Although the screen of Laptop is broken I could see on some patches of it that the distribution's blue desktop but the external monitor which was working showing the progress of booting (there is no splash image) becomes blank as the GDM starts. After pressing Ctrl alt F1 I could see the console with Ubuntu Live CD user.

First I tried by copying the xorg.conf file from Gutsy Gibbon install, it did not work. Then I noticed that the external monitor was configured through xrandr on Gutsy Gibbon. I tried xrandr --auto command on PUD Live CD console but it resulted into error (Can't open display).

After pressing Ctrl alt F1 on Gutsy Gibbon I tried xrandr -q on console. This also resulted into error "Can't open display". This means xrandr command does not work in console even on Gutsy Gibbon (HD install).

Please note that xrandr is working on Gutsy Gibbon Desktiop Terminal and the output is as follows:
> $ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1280 x 1200
VGA-0 connected 1024x768+0+0 (normal left inverted right) 270mm x 200mm
   1280x768       60.0  
   1152x768       54.8  
   1024x768       60.0* 
   800x600        75.0     60.3     56.2  
   640x480        85.0     75.0     72.8     75.0     60.0     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)

I tried to do the above configuration in xorg.conf file of Gutsy Gibbon but could not succeed.

Please help me to write the above configuration in xorg.conf of Gutsy Gibbon. If it works on Gutsy Gibbon, I will copy it on PUD Live CD and see whether I can make the external monitor work there.

kagashe

---

### Post by Ptero-4 on 2008-05-03
Wow, nice distro. I'm gonna try it on my college's dinoputers.
BTW. Is that a chick in the second pic?

---

### Post by shae on 2008-06-08
Ubuntulite 0.8 is currently beta and will feature LXDE.
[http://ubuntulite.tuxfamily.org](http://ubuntulite.tuxfamily.org)

---

### Post by sargetech on 2008-09-27
This looks cool, I have a bunch of Old P3 Frankenputers to install it on
and giveaway as Christmas gifts for my Grandchildren.....:)

---

### Post by Johnsie on 2008-09-27
How much diskspace does it take up. I have a 4g eeepc and have got normal Ubuntu to fit on 1gb

---

