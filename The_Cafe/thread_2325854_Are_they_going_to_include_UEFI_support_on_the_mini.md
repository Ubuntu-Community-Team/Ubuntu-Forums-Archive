---
title: "Are they going to include UEFI support on the minimal iso images at some point?"
date: 2016-05-26
forum: The Cafe
---

### Post by user1397 on 2016-05-26
Seems a bit weird to me that they haven't done this yet.  Does adding the UEFI files to the mini.iso add a lot of MB?  Or is there some technical issue holding it back?

Just curious!

---

### Post by sudodus on 2016-05-26
If you want to create a minimal system or a custom system with your own selection of program packages, you can get almost the same result, if you start from the **Ubuntu Server iso file** (as if you start from the **mini.iso** file). And the Ubuntu Server 64-bit iso file can install also in UEFI mode.

-o-

I used this method to create compressed image files, that can be used to install a mini system with a text interface (no graphical desktop enviroment). This system can be installed into internal drives as well as into USB pendrives, and it boots in both UEFI and BIOS mode. This can be a shortcut to get your particular system.

See the following links

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[Two updated compressed image files are uploaded](http://ubuntuforums.org/showthread.php?t=2213631&page=8&p=13494760#post13494760)

and the following links describe the tool to install from these compressed image files, ***mkusb***,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb version 10.6.6 and mkusb-nox version 7.5.9.7](http://ubuntuforums.org/showthread.php?t=1958073&page=18&p=13494051#post13494051)

It is easiest if you use the bleeding edge version 10.6.6 of mkusb, that you get from ppa:mkusb/unstable via the following command lines. If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update
sudo apt-get install mkusb

# if you want mkusb-nox
sudo apt-get install mkusb-nox

# or if you want both mkusb and mkusb-nox
sudo apt-get install mkusb mkusb-nox
```

---

### Post by grahammechanical on 2016-05-26
Why have a mini ISO image in the first place?

They are useful for machines that lack the RAM & video memory to run the standard Installer and which also have hard drives that are too small for a standard Ubuntu installation. Those type of machines will have BIOS boot systems. Machines that come with UEFI boot systems will have enough resources to cope with the requirements of the standard Ubuntu install method. So, it is the standard ISO images that need EFI boot files.

There are two reasons why programmers develop for LInux. 1) They are paid to do it. In which case they do what they are told. And it seems that no one is willing pay an engineer to do the work which also includes Quality Assurance testing of the images. 2) They are volunteers & do it for their own satisfaction. In which case they work on projects of their own choosing.

What you see as a need, others see as unnecessary work. There is a similar situation with regard to giving 32 bit Linux support for secure boot. Machines that are so old that they have 32 bit CPUs do not have motherboards that do secure boot.

---

### Post by user1397 on 2016-05-26
@sudodus Yes, I am aware that you can achieve basically the same result with the server iso.  In my understanding though, the server image base install installs a few server-specific packages that wouldn't be present on the desktop image (perhaps this has changed?), and which maybe wouldn't even matter to the end user but maybe to the power user building his system from the ground up would like to not have extra stuff in there that he/she didn't need.  

I have seen that other solution that you wrote about and it does seem like it is basically what I'm talking about. Did you make those .iso's or did you just create the thread?  Either way, cool stuff.  Wiki page could be a bit more user friendly imo.  

@grahammechanical Why not have a mini iso image in the first place? :P  I don't know, some people just like building up from the very minimal to whatever they want, I just see it as more choice.  By the way I never said it was a "need", I was just curious to know *why *this hadn't been done yet. You do make a good point though...maybe this isn't really necessary anymore just as 32 bit support is fading.  Maybe we should just point people to the server iso if they want to build from ground up?  

I always thought it was cool to download a 40MB image and go from there, but maybe that's just me :)

---

### Post by oldfred on 2016-05-26
I believe the server installer does not install much at all by default.
You select from this. And then still have to add your own desktop/gui.

 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel 

Step 19 shows 14.04's tasksel.
[http://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/](http://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/)

---

### Post by sudodus on 2016-05-26
> **user1397 said:**
> @sudodus Yes, I am aware that you can achieve basically the same result with the server iso.  In my understanding though, the server image base install installs a few server-specific packages that wouldn't be present on the desktop image (perhaps this has changed?), and which maybe wouldn't even matter to the end user but maybe to the power user building his system from the ground up would like to not have extra stuff in there that he/she didn't need.  

I have seen that other solution that you wrote about and it does seem like it is basically what I'm talking about. Did you make those .iso's or did you just create the thread?  Either way, cool stuff.  Wiki page could be a bit more user friendly imo.  

...

I always thought it was cool to download a 40MB image and go from there, but maybe that's just me :)

I suggest that you make ***test installations*** starting from the mini.iso file and the 32-bit server iso file and compare the result. There are differences, but those differences are very small. There is one definite advantage with the server iso file: If you intend to use it more than once, there are several program packages, that you only need to download once, while you must download them every time you install from the mini.iso. This makes it overall faster and more efficient.

Yes I made those compressed image files. (They are not iso files.) There is a problem with the wiki page: Regular mortal users like me cannot edit it because of a raised security level after repeated hacker attacks against the Ubuntu help pages. This makes it very cumbersome to edit it (via a trusted person), and therefore it is not as good as it should be.

Yes, I agree, it is cool to download a 40MB image and go from there, but I think not really important, because there is this alternative with the server iso file.

---

### Post by sudodus on 2016-05-27
> **oldfred said:**
> I believe the server installer does not install much at all by default.
You select from this. And then still have to add your own desktop/gui.

 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel 

Step 19 shows 14.04's tasksel.
[http://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/](http://www.tecmint.com/ubuntu-14-04-server-installation-guide-and-lamp-setup/)

```
sudo tasksel
``` is what I wanted to invoke via the install sub-menu of my UEFI-n-BIOS systems (but did not know how to do it). There will soon be updated and improved compressed image files.

Thanks a lot *oldfred* :-)

---

