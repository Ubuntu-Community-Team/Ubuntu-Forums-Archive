---
title: "No Snappy Personal images until 16.10 Update!!"
date: 2016-02-01
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-02-01
Hi,

 For any and all who have been testing the snappy_personal images (personal_x86.img)... I have just received an e-mail from Canonical's chief ubuntu-desktop engineer, Will Cooke, which basically states  that  the snappy personal desktop is on the shelf until the 16.10 cycle. So basically , those of us in testing and development version should test and experiment with the current LTS cycle. Perhaps work and test for LXD on xenial snappy core could provide some surprises.

Thanks and..

Regards..


From Will Cooke:

> 
  Hi Dale, 
 
 Thanks for your emails.
 
 
 So we stopped the Snappy builds of the U8/Mir desktop around  October last year when it became clear that having the two options was  confusing people, also there was a pretty big bug which would result in  your boot partition being over-written if you tried to install the Snappy version alongside the classic .deb based version.
 
 
 The decision was made to stop building the Snappy version while the bugs were being ironed out.
 
 
 Right now we're all focusing on getting the LTS out in the best  possible shape we can, and so we will be rebooting the Snappy images  work from the beginning of the 16.10 cycle.  All the machinery is still  in place to build those images, so it won't be long before we see them being generated again.
 
 
 I'll let you know as soon as we flip the switch back on again.
 
 
 Cheers, Will



---

### Post by grahammechanical on 2016-02-01
I was starting to think along the lines that they would build Ubuntu Personal on the stable 16.04 LTS code rather than on the moving 16.04 development code. This email seems confirmation. And the plane seems sensible.

Personally, I cannot see how the specialised partition layout of personal_x86 can be made compatible with the traditional Ubuntu partition layout. After installing personal_x86 on a hard disk using Disks>Image restore. I ended up with a hard disk that had GPT partitioning and I was able to create another partition and install traditional Ubuntu in it but I had to install Grub into the partition as it would have over-written the Grub of personal_x86.

I found no way to update the personal_x86 grub so that it detected the new Ubuntu installation. And the Grub in traditional Ubuntu does detect the Linux in personal_x86 but cannot load it due to the different locations that personal_x86 has for the Linux kernels. There are radical differences between traditional Ubuntu and snappy Ubuntu personal that will have to be fudged.

I can see snappy Ubuntu personal being a great OS that comes pre-installed on Ubuntu laptops and notebooks and even desktops. It will be very secure and very locked down. At the moment I am not seeing it as an ISO image that can be downloaded and installed like the present versions of Ubuntu. I see rough waters ahead.

Regards.

---

### Post by sammiev on 2016-02-01
Breakage... can not wait. :P

---

### Post by ventrical on 2016-02-01
I think perhaps that a 'shift' may take place where we will be using LXD containers on snappy-core where unity8 (or a facsimile thereof)  can be loaded and run as a viable desktop. Or a modified unity7th desktop can be run in a concurrent session where the hypervisor can allow for literal 'kernel slamming' or they can modify xorg or create and new non-mir switchable compositor with the snappy core that can jockey between mutiple desktops.

There are currently a lot of tools available for testing so, time providing, I am going to experiment a little with a  few things .  I sure hope we get an .iso after 16.04lts release.  I like your conventional wisdom about grub though. This is a big bug that will take a lot of resource to resolve. They might have to find another way to implement it.

Regards..

---

### Post by ventrical on 2016-02-01
> **sammiev said:**
> Breakage... can not wait. :P

+1 :)

---

### Post by grahammechanical on 2016-02-01
> I think perhaps that a 'shift' may take place where we will be using LXD  containers on snappy-core where unity8 (or a facsimile thereof)  can be  loaded and run as a viable desktop.

+1 But why only Unity? Why not any DE? I was reading somewhere about running apps like Firefox in LXC for better security. It would be something like what can be done with Docker. Now if these pre-scripted containers were snaps & installed through an app store then all this could take place without the user noticing anything technical going on.

I am going to have to get back into snappy Ubuntu core and LXC/LXD. Keep your eyes open for something called libertine. I saw it at the last Online Summit. It is the thing being developed to run x11 apps in containers on Xmir for Unity 8. Not to be confused with the Libertime fonts package. 

[https://launchpad.net/libertine](https://launchpad.net/libertine)

[https://launchpad.net/~libertine-team/+archive/ubuntu/puritine-devel](https://launchpad.net/~libertine-team/+archive/ubuntu/puritine-devel)

[https://l3net.wordpress.com/2013/09/05/debian-virtualization-lxc-desktop-virtualization/](https://l3net.wordpress.com/2013/09/05/debian-virtualization-lxc-desktop-virtualization/)
[URL="https://launchpad.net/libertine"]
[/URL]Regards

---

### Post by ventrical on 2016-02-01
> **grahammechanical said:**
> +1 But why only Unity? Why not any DE? I was reading somewhere about running apps like Firefox in LXC for better security. It would be something like what can be done with Docker. Now if these pre-scripted containers were snaps & installed through an app store then all this could take place without the user noticing anything technical going on.

I am going to have to get back into snappy Ubuntu core and LXC/LXD. Keep your eyes open for something called libertine. I saw it at the last Online Summit. It is the thing being developed to run x11 apps in containers on Xmir for Unity 8. Not to be confused with the Libertime fonts package. 

[https://launchpad.net/libertine](https://launchpad.net/libertine)

[https://launchpad.net/~libertine-team/+archive/ubuntu/puritine-devel](https://launchpad.net/~libertine-team/+archive/ubuntu/puritine-devel)

[https://l3net.wordpress.com/2013/09/05/debian-virtualization-lxc-desktop-virtualization/](https://l3net.wordpress.com/2013/09/05/debian-virtualization-lxc-desktop-virtualization/)
[URL="https://launchpad.net/libertine"]
[/URL]Regards



 There is a forum here somewhere where I did some experiments with snappy core and LXD containers. I was able to actually install baked .isos and then run programs like Htop and Midnight Commander .. etc.. but I could not get xorg-server to install or (at least)  be recognized so even though I had all the parts I could not get the desktop to load. The main point is that you can use LXD containers, install an operating system on the container and run it using the deb repositories without interfecting  snappy-core as a whole.

> 
libertine


will be on the lookout. :)

 Regards..

---

### Post by ventrical on 2016-02-01
> **grahammechanical said:**
> +1 But why only Unity? Why not any DE? I was reading somewhere about running apps like Firefox in LXC for better security. I

I am going to have to get back into snappy Ubuntu core and LXC/LXD
[URL="https://launchpad.net/libertine"]
[/URL]Regards

@graham and other interested in testing snappy core -w LXD.

[http://ubuntuforums.org/showthread.php?t=2275971&p=13432678#post13432678](http://ubuntuforums.org/showthread.php?t=2275971&p=13432678#post13432678)

regards...

---

### Post by ventrical on 2016-02-01
Um.. I just noticed that there is no 16.04 snappy image?? Only 15.04!

Anyone know if there is a snappy 16.04 img?

thanks

regards..

---

### Post by grahammechanical on 2016-02-01
Although it says 15.04 there are builds dated as recently as 28th January 2016. I have no idea if they are installable. And not snappy core. I will look again later on.

[https://system-image.ubuntu.com/ubuntu-core/15.04/alpha/generic_amd64/](https://system-image.ubuntu.com/ubuntu-core/15.04/alpha/generic_amd64/)

Regards

---

### Post by cariboo on 2016-02-02
If you follow the [snappy-devel ]("https://lists.ubuntu.com/mailman/listinfo/snappy-devel")mailing list, you'll see that they are still basing snappy images on wily.

---

### Post by ventrical on 2016-02-02
> **cariboo said:**
> If you follow the [snappy-devel ]("https://lists.ubuntu.com/mailman/listinfo/snappy-devel")mailing list, you'll see that they are still basing snappy images on wily.

I am on the mailing list. I just forgot ;)

Thanks.
Edit:

The amd64-all-snap.img is xenial code. This is the one we want to work on with LXD.

regards..

---

### Post by sammiev on 2016-02-02
Time to start reading up on it then... :)

---

### Post by ventrical on 2016-02-02
> **sammiev said:**
> Time to start reading up on it then... :)

Ummm.. I think I misspoke here. I think it has to be snappy core to run LXD.

Regards..

---

### Post by ventrical on 2016-05-02
> **ventrical said:**
> @graham and other interested in testing snappy core -w LXD.

[http://ubuntuforums.org/showthread.php?t=2275971&p=13432678#post13432678](http://ubuntuforums.org/showthread.php?t=2275971&p=13432678#post13432678)

regards...

I just wanted to bump this thread because I was listening to Mark in California and he talked a lot about Lex-D! 'LXD' containers. It may be that snappy personal will be the 'desktop on a phone' and not a 'phone on the desktop'.

The core reason is not just because  of it's efficiency but also because of security. So perhaps there may be some breakage or experiments we can do with LXD and possible firefox ?

regards..

---

### Post by ventrical on 2016-05-17
I wrote to Canonical a bit ago about snappy personal images (during recent webinar). There could be hope that we may get an image this cycle.

  Ventrical to one of the devs at Canonical;

> 
Hi ,
 
 
  I am getting conflicting messages about Snappy Personal  Image.I read Daniel Holbach's blog;
 
 
 [https://daniel.holba.ch/blog/2016/05/ubuntu-core-at-uos-16-05/](https://daniel.holba.ch/blog/2016/05/ubuntu-core-at-uos-16-05/)
 
 
 but there is no mention of  Snappy Personal Image for amd64 desktop form factors. You had relayed to  me that you were waiting with great expectations  that  snappy-personal-image would be released in May. Is this still the case or will snapd on xenial 16.04 be the way that convergence will  go concerning traditional desktop form factors.
 
 
 Thank you and..
 
 
 Regards..
 
 
 Dale



from Canionical dev to Ventrical

> 
First step is to get Unity8 as debs on my laptop, which is happening
 this cycle. An all-snap Ubuntu Personal image might come this cycle too,
 but I'm mostly focused on the usability of U8.
 
 Canonical dev



 I also told devs that I cannot get libertine, (The app which makes .deb packages work on Unity8 desktop) and I advised him about other early adopters who are getting blackscreens that are using nVida graphical hardware .. so I put in a plug for those of us who use nVidia.

 Anyone else have success with he libertine apps?

Regards..


edit:

Could a mod please  fix the font size here please.

---

### Post by grahammechanical on 2016-05-17
> The amd64-all-snap.img is xenial code. This is the one we want to work on with LXD.

I might give it a try. Does it have Unity 8 or only command line. I forget.

[https://people.canonical.com/~mvo/all-snaps/](https://people.canonical.com/~mvo/all-snaps/)

Pity we don't have a Unity 8 snap to go with it. It would then the beginnings of a snappy version of the mini ISO.

Regards

---

### Post by ventrical on 2016-05-17
What I am doing is a mix of  what mhall did on 16.04 and what Mark is doing on yakkety. So I downloaded the daily yakkety-ubuntu-i386.iso and then installed:

```

sudo apt-get install unity8-desktop-session-mir
[CODE]

 I  DID NOT install the PPA.

 I did do:

[CODE]

sudo apt-get install phablet-tools phablet-tools-citrain
citrain host-upgrade 031

```

and by the way .. that above code has to be pasted as one command.

 I followed all the other steps but could not get the apps to stay open. 
This all done on nVidia graphics.

Regards

edit; i am going to try again and use the ppa this time.  

@graham.

The i386 iso of yakkety  will load up unity8 mir on nVidia.  Just give it a 
little bit of time to load if you have slow hdd. I cannot get the apps to stay open so i am going to try ppa from
dogfooding web page... and keep hacking at it :)

---

### Post by grahammechanical on 2016-05-17
I have just run the all-snaps image on a USB stick. Yes, it is command line and 16.04 with kernel 4.4.0-18. I tried out the Links text web browser. It works but we need to know the URLs of the sites we want to visit. Didn't try any of the snaps that have a GUI. 

Regards.

---

### Post by ventrical on 2016-05-17
> **grahammechanical said:**
> I have just run the all-snaps image on a USB stick. Yes, it is command line and 16.04 with kernel 4.4.0-18. I tried out the Links text web browser. It works but we need to know the URLs of the sites we want to visit. Didn't try any of the snaps that have a GUI. 

Regards.

So no desktop ?

ahhh .. ok. I see now.

Regards..

---

### Post by grahammechanical on 2016-05-17
No go. i386 Yakkety no go with Unity 8 on Nvidia.

One part of my mind says: At present Unity 8 does not compare in usefulness with Unity 7 and that is not a problem because the devs have until October to get it in shape. So, it is no big deal if Unity 8 does not load on different video hardware. The devs have until October to fix that also.

The other part of my mind says: Well, stop talking about Unity 8 being a login option as if it actually is a login option when in fact it is anything but an option.

Wake me up in October. Or when the first ISO image is released that is supposed to have the Unity session as an option built-in to the installation process. Then I will try it out and file a bug report.

Regards.

---

### Post by ventrical on 2016-05-17
I swapped harddrive to intel XEON graphics and it is now working!! I even got the terminal app working hehe :) this is amd64 bit mode. It worked on nVidia also but locked up every once in a  while. I am going to try  the libertine app.

Regards..

---

