---
title: "driver for Ubuntu 10.04 LTS &amp; nvidia GT 430"
date: 2012-03-28
forum: Testimonials &amp; Experiences
---

### Post by WasMeHere on 2012-03-28
Hi LTS users,

I thought that this information might be useful, if you want to improve the graphics of Lucid. There is a year to go for the desktop version of Ubuntu 10.04 LTS, and I have upgraded the nVidia graphics

- from the built-in chip GeForce 7050 PV / nForce 630a
- to a card with GeForce GT 430

For both chips the free driver can only show low resolution graphics, 800x600.

The built-in proprietary driver
- NVIDIA 195.36.24
can manage the built-in chip but not the new card. So I downloaded newer drivers from [[COLOR="RoyalBlue"]_http://nvidia.com_[/COLOR]]("http://nvidia.com")

The newest driver 'compatible' with GeForce GT 430 was
- NVIDIA-Linux-x86-295.33
but it did not work. So I tried one of the older versions
- NVIDIA-Linux-x86-275.28
and it works well with both graphics chips, the built-in one, and the card with GeForce GT 430.

It is necessary to stop the graphic desktop environment before running the install script. I followed the instructions in this link
[[COLOR="RoyalBlue"]_http://www.ubunturoot.com/2011/09/installing-latest-proprietary-display.html_[/COLOR]]("http://www.ubunturoot.com/2011/09/installing-latest-proprietary-display.html")
Skip to the part about nVidia (unless you want to do it for ATI) ;-)

- ***ctrl + alt + F1***

- login

- run the following commands
```
sudo /etc/init.d/gdm stop
```
```
sudo sh NVIDIA-Linux-x86-275.28.run
```
and follow the installation instructions.

- finally reboot ```
sudo reboot
```

Having fun finding out :-)
Olle

---

### Post by WasMeHere on 2012-04-02
It works: the graphics renders nicely in both computers.

But I found that the new driver had a disadvantage in the old computer with the built-in chip GeForce 7050 PV / nForce 630a.

When opening many windows (with pixel graphics not text), it reached a limit, when it stopped working. New windows were simply blank. For example: with Thunderbird and Firefox open, I could only open 2 or 3 pdf-files with evince. The next window of evince would be blank (white). It seems that there is some kind of memory limit.

So I have returned to the built-in driver NVIDIA 195.36.24 on that computer because I use the new graphics card in another computer.

---

