---
title: "Ubuntu 14.04 and my own spin ?"
date: 2015-06-10
forum: Ubuntu, Linux and OS Chat
---

### Post by GakuWai on 2015-06-10
Hello,

So I want to take ONLY Ubuntu 14.04 kernel with drivers (without all that programs which are included in Ubuntu such as LibreOffice etc) and make my own version of Ubuntu using OpenBox + Tint2 and install programs which I normally use and customise them. The question now is how do I do it ? I'm tech savvy user who is very comfortable in using Linux and is not scared to break that or this along the way. Also I want to be able to install it as that's the whole point of doing it :D. Are there any tutorials I can relay on ? I heard that there is Remastersys, will that be the right tool to use in this case ?

Every help is appreciated.
Thanks

---

### Post by voitrix on 2015-06-10
Hi,

You can try Ubuntu Customization Kit ([https://apps.ubuntu.com/cat/applications/precise/uck/]("https://apps.ubuntu.com/cat/applications/precise/uck/")), uninstall the apps you don't want and install the ones you'll need.

---

### Post by v3.xx on 2015-06-10
For a first try, you could go easy on yourself and use the mini iso.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

And install something that has the bare bones minimum (openbox).  LXDE
[http://packages.ubuntu.com/trusty/lxde](http://packages.ubuntu.com/trusty/lxde)

Just one of many ways to go.

---

### Post by GakuWai on 2015-06-10
> **v3.xx said:**
> For a first try, you could go easy on yourself and use the mini iso.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

And install something that has the bare bones minimum (openbox).  LXDE
[http://packages.ubuntu.com/trusty/lxde](http://packages.ubuntu.com/trusty/lxde)

Just one of many ways to go.

Sounds good but that MinimalCD doesn't support UEFI mode. Does making a gpt device partition label and /BIOSGRUB and /boot partition works in this case ? Also after customising this installation, how do I make ISO out of it so later on I can burn it to a CD/DVD ?

---

### Post by v3.xx on 2015-06-10
No, it will not do efi.

I think that the 'Alternate Install CD' will, but I am not sure as I do not use efi.

Someone else will have to step up with that info.

Edit
I think the server iso will do efi, but again unsure.

---

### Post by grahammechanical on 2015-06-10
I am not sure that the mini ISO will be useful for creating a customised ISO image for this reason,

> The minimal iso image will download packages from online archives at  installation time instead of providing them on the install media itself

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Something more suitable might be Ubuntu core.

> Ubuntu Core is a minimal rootfs for use in the creation of custom images  for specific needs.  Ubuntu Core strives to create a suitable minimal  environment for use in Board Support Packages, constrained or integrated  environments, as the basis for application demonstration images, or  Linux containers such as [LXC]("https://linuxcontainers.org/") or [Docker]("http://docker.io")

[https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core)

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Regards.

---

### Post by v3.xx on 2015-06-11
Ok, since no one is answering the efi thing ..

Oldfred is the resident efi man.  You need to research his post.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+oldfred&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+oldfred&sa=Search&cof=FORID:9)

Looks like the server iso will do efi.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+server+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+server+iso&sa=Search&cof=FORID:9)

The server iso can be used just like the mini iso.  I can lay the steps out for you, if interested, however you need to research efi and get it figured out.

---

### Post by GakuWai on 2015-06-11
> **grahammechanical said:**
> I am not sure that the mini ISO will be useful for creating a customised ISO image for this reason,



[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Something more suitable might be Ubuntu core.



[https://wiki.ubuntu.com/Core](https://wiki.ubuntu.com/Core)

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

Regards.

Thanks for sugestions and it looks interesting, I will need to check it out.
Shouldn't it be easier to install Ubuntu in VirtualBox, customise it the way I want it and pack it back for installation aka LiveCD using RemasterSys ? Sounds like good idea to me but I don't know how it would work out in technical reasoning. 

P.S I wouldn't worry about my computer for VirtualBox as I have 6 core processor and 16GB of ram which is enough for VirtualBox.

---

### Post by HermanAB on 2015-06-11
FWIIW, I usually start with the server version and then install whatever else I want.

---

### Post by GakuWai on 2015-06-11
> **v3.xx said:**
> Ok, since no one is answering the efi thing ..

Oldfred is the resident efi man. You need to research his post.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+oldfred&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+oldfred&sa=Search&cof=FORID:9)

Looks like the server iso will do efi.
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+server+iso&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=uefi+efi+server+iso&sa=Search&cof=FORID:9)

The server iso can be used just like the mini iso. I can lay the steps out for you, if interested, however you need to research efi and get it figured out.
I would do it but unfortunatelly I need Desktop version rather than Server version of Ubuntu.

> **HermanAB said:**
> FWIIW, I usually start with the server version and then install whatever else I want.
Does people really use Server version of Ubuntu on a Desktop environment ? I'm must admit that I'm surprised now.

---

### Post by v3.xx on 2015-06-11
> **HermanAB said:**
> FWIIW, I usually start with the server version and then install whatever else I want.
So do I.  Any desktop, any flavor.  Its faster to install the basic server.

---

### Post by v3.xx on 2015-06-11
Put in a different way

The server iso has all the basic stuff, but no GUI.  The desktop installers are basically a server install with a GUI.

I mention the 'alternate install cd' that Lubuntu puts out.  This installer can be used to install any desktop, any flavor without installing lubuntu.

The mini, the alternate install and the server iso can ALL do the same install.

Its just easier for most to use the mini iso when building there own.

---

### Post by GakuWai on 2015-06-11
So normally it's better to use Server version and then install stuff I want to have in it ? 
hmm, I was thinking that server version of Ubuntu was a different flavour of Linux, completely different from Desktop version.
That being said does Ubuntu Server can encrypt hard drive and support UEFI ? I know that Desktop version supports it but I don't know about server version.

---

### Post by cariboo on 2015-06-11
> **GakuWai said:**
> So normally it's better to use Server version and then install stuff I want to have in it ? 
hmm, I was thinking that server version of Ubuntu was a different flavour of Linux, completely different from Desktop version.
That being said does Ubuntu Server can encrypt hard drive and support UEFI ? I know that Desktop version supports it but I don't know about server version.

It isn't better to install the server version, just easier.

---

### Post by v3.xx on 2015-06-11
And your adding encryption.  The regular install will ask if you want Home encrypted, I don't know about the server install.  I would build something first, leave encryption off.  One less headache to contend with on your first build. Get something up and running using uefi.  Maybe cariboo has some insight on this.  

I still think lxde is a good option.  Once you achieve a console install, installing lxde is just a one line command.  And your up and running openbox.

If you would like a few bells and whistles, you could install lubuntu core (without recommends).  This would again give you openbox.
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)


You mention vBox, maybe start a thread on it, got enough going on here. 
You could post the link to it here.

---

### Post by GakuWai on 2015-06-12
Thanks guys for your support and help. I'm going to use Server Version, customise it and make livecd out of it.

---

### Post by leunam12 on 2015-06-12
Why don't you just use Arch?
I used it for many years with Openbox and LXDE, it only had what I put in there and nothing else. Pretty fast and sleek but more geek-oriented than Ubuntu

---

### Post by GakuWai on 2015-06-17
> **leunam12 said:**
> Why don't you just use Arch?
I used it for many years with Openbox and LXDE, it only had what I put in there and nothing else. Pretty fast and sleek but more geek-oriented than Ubuntu
Well let's start with that Arch is an advanced distro tho and I don't know if it's supports UEFI and encryption as Ubuntu does with easy steps and I would need to make a livecd to have it on CD/DVD for later re-installation. Arch is good but mainly I'm used to commands in Ubuntu/Debian and it would be difficult for me to change to it including that weirdly working depository and installation commands, I just don't get it really and it's not my cup of tea really otherwise I would try it for sure.

---

### Post by Bucky Ball on 2015-06-17
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Install with a mini.iso and DON'T choose a machine profile. Once finished and on reboot you will be at a CLI. You only have the Ubuntu kernel installed. Login, get online with a cable (which you need to be to install from the mini.iso anyway) then:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install openbox tint2
```

The rest is up to you. Install what you like. Add whatever you want to the install command I have given above, i.e. synaptic, gparted, thunderbird, firefox, whatever ...

Something basic would be just that:

```
sudo apt-get install openbox tint2 synaptic gparted firefox thunderbird
```

As you are intending to use openbox I'm presuming you are not going to need a desktop environment. If you want one, add that as well, i.e. add 'xfce4' or 'lxde' or whatever you want. Be aware that this is a VERY basic system before you add anything and you will need to research to find what you need if you require defaults from other desktop environments/flavours (Additional Drivers, clock, Network Manager, etc.).

I generally install xfce4, lxterminal, firefox, gparted and synaptic, reboot and take it from there. If you're comfy doing everything from a terminal you won't even need all that. Good luck.

---

### Post by v3.xx on 2015-06-17
> Something basic would be just that:

     Code:
     sudo apt-get install openbox tint2 synaptic gparted firefox thunderbird

Hey Bucky, how you boot this?

---

### Post by Bucky Ball on 2015-06-17
> **v3.xx said:**
> Hey Bucky, how you boot this?

I don't use openbox alone so can't help you. I was going to look into that for 16.04 LTS. 

At a guess I would imagine once installed, reboot, login and away you go. You would probably need to add obconf to that list of installs so you can configure openbox (from memory).

The original poster GakuWai may be a better person to respond to this question as an openbox setup minus a DE is what they appear to be looking to install. :)

So, install the mini.iso> reboot> login> execute the sudo line mentioned earlier> reboot> login.

PS: You may also want a desktop manager for a GUI login. There is lightdm, gdm, xdm, and others.

---

### Post by v3.xx on 2015-06-17
Thanks

---

### Post by Bucky Ball on 2015-06-17
> **v3.xx said:**
> Thanks

No problem.

```
sudo reboot -h now
```

... to reboot after you've installed your first apps on first boot, by the way. That should reboot and take you to a login screen if you've installed a DM.

---

