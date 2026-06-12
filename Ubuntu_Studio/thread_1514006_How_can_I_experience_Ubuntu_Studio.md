---
title: "How can I experience Ubuntu Studio?"
date: 2010-06-20
forum: Ubuntu Studio
---

### Post by NigelLane on 2010-06-20
Hi. :)

I currently am using Ubuntu Lucid Lynx, but I would like to also install Ubuntu Studio. I read something about it, but I don't know if it will satisfy my needs...

I want to know hat is the best way to experience Ubuntu Studio? Does it have a Live CD or something?

And I need some advice of what are the most crucial applications i need to install so I can grasp all of what Ubuntu Studio can offer.

Thanks upfront! :D

---

### Post by cchhrriiss121212 on 2010-06-20
It would help if you explain what your needs are. Studio covers audio video and graphical programs that are bundled together in a 1.4GB image, and because of the size you can't put it on a cd. There is no live mode and it uses a text based installer.

Studio can also be obtained by upgrading from a regular Ubuntu which is what you might like to try, search for it in synaptic and select either the audio, video or graphical package. The only crucial app I can think of would be jack, which only applies if you are using audio.

Studio is not a completely different OS, it is just Ubuntu with the following changes:
Low latency kernel
A bigger collection of programs from an additional software repository
Different theme
No network manager

---

### Post by NigelLane on 2010-06-20
> **cchhrriiss121212 said:**
> It would help if you explain what your needs are. Studio covers audio video and graphical programs that are bundled together in a 1.4GB image, and because of the size you can't put it on a cd. There is no live mode and it uses a text based installer.

Studio can also be obtained by upgrading from a regular Ubuntu which is what you might like to try, search for it in synaptic and select either the audio, video or graphical package. The only crucial app I can think of would be jack, which only applies if you are using audio.

Studio is not a completely different OS, it is just Ubuntu with the following changes:
Low latency kernel
A bigger collection of programs from an additional software repository
Different theme
No network manager

Hi. :)

Thanks for your reply. Yes, I also thought that I should just upgrade and see how it goes. 
My needs of the Ubuntu Studio would be to express my creativity. I am a graphical designer, but I have worked on music too for about a year or so. I think that th Studio is just what I need.

There is just one thing I don't understand. 
What do you mean "no network manager" ? Does that mean I can;t have internet access? ( Sorry if this sounds a little n00bish xD )

---

### Post by cchhrriiss121212 on 2010-06-20
> What do you mean "no network manager" ? Does that mean I can;t have internet access? ( Sorry if this sounds a little n00bish xD )
Network manager causes conflicts with audio processing so it is left out of the build by default. If you have a wired connection present during installation then you can use internet just fine without nm. But if you rely on wireless then you need to manually install network manager from packages on the Studio image.
I use audio processing, and rely on wireless for my connection so my solution is to have network manager installed but not running from autostart. When I need new programs or something, I run nm-applet from a terminal, then reboot before doing any work.

---

### Post by NigelLane on 2010-06-20
> **cchhrriiss121212 said:**
> Network manager causes conflicts with audio processing so it is left out of the build by default. If you have a wired connection present during installation then you can use internet just fine without nm. But if you rely on wireless then you need to manually install network manager from packages on the Studio image.
I use audio processing, and rely on wireless for my connection so my solution is to have network manager installed but not running from autostart. When I need new programs or something, I run nm-applet from a terminal, then reboot before doing any work.

Okay, so I understand now. :) Thanks.
I've decided to install the Studio! Yay! :guitar:

I'll try to do it today, but I'm kinda busy, so I will probably do it tomorrow. If I have any problems I'll write here lol. xD

So, any other suggestions, tips or tricks? Anyone?

---

### Post by sgx on 2010-06-20
Hi. Mint9 is a customized Ubuntu that fits on a CD and runs live. If
you install it, and like it, the Ubuntu Studio meta-package can be installed from synaptic, it is the found Universe section of the meta-packages category.
I did this in a wubi type install, called mint4win.exe that will be on the CD you burn. Mint, is installed like an app, but inside a windows installation, and you can choose to boot either at startup. 17 gig is default size, but you can choose for more.
Cheers

---

### Post by mango42 on 2010-06-23
Is there any *surefire* way of booting any flavour of Ubuntu, including Mint9, off a usb flash drive? It's another area I haven't got working yet, despite UNetbootin and the one that says "If the above solutions are unsuccessful, you may need to use a different method than USB Startup Disk Creator to create a Live USB." ):P

---

### Post by sgx on 2010-06-23
Hi, once the install is done, booting it is a bios function. The boot order can be changed in the bios, if needed. If its a good modern bios, it should hit the first grub it finds.

But you made need to dance. On my wifes laptop, Mint9 and Vista are in grub, but to boot from the usbstick audio distro, I have to press
ESC to preempt grub, then F9 to get the early boot menu. Then if
xorg.conf on the usbstick distro is in agreement with the video hardware being accessed, its business as usual. 

For luck, when I make a bootable usbstick, I disconnect hardisks,
and install from CD/Dvd to usb. But not really necessary when sober.
Cheers

---

### Post by fusion2 on 2010-06-24
I'm sure that Ubuntu Studio is a good solution for a beginner.

---

### Post by mango42 on 2010-06-24
> **sgx said:**
> For luck, when I make a bootable usbstick, I disconnect hardisks, and install from CD/Dvd to usb. But not really necessary when sober.
Cheers

LOL - ya mean the laptop, General Error or the user?

Nope, I don't have an issue with booting from USB, I have an issue with the boot image on the stick actually doing anything useful, like booting... :confused:

@ **fusion2** - not just for beginners either - once it's working and well tweaked, it blows away *all* the commercial competition, IMO - not that you'd think so if you only judged UbuntuStudio by my recent posts (an aberration caused more by the hardware & largely clueless user than the Linux software)! :lolflag:

---

### Post by hate.mycrowsoft7 on 2010-09-12
Go to add/remove softwares and type Ubuntustudio in the search  box.U'll get the packages.Now Select the packages what u want and install.If u want only the looks of ubuntustudio then don't install audio,video,usplash,front 2D/3D packages.Have fun.

---

