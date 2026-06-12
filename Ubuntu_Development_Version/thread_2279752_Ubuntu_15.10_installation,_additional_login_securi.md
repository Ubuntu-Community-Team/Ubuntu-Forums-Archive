---
title: "Ubuntu 15.10 installation, additional login security?"
date: 2015-05-25
forum: Ubuntu Development Version
---

### Post by neb8 on 2015-05-25
Ubuntu 15.10 DVD installation additional login security.  It was required to create a second four digit passcode to complete the installation.

What is this for? Why was it included to complete the installation?

[IMG]https://cms-images.idgesg.net/images/article/2015/05/swipe-to-open-launcher-on-unity-8-100584242-orig.jpg[/IMG]

---

### Post by grahammechanical on 2015-05-25
What you have installed is Ubuntu Desktop Next and not Ubuntu Desktop. What you are seeing is the Ubuntu phone OS running on a desktop/laptop machine.

With Ubuntu Desktop Next we first get the standard Ubuntu LightDM login screen where we login then we get the switch to the phone OS running on Mir and we have to login to that also. But first we have to set up the OS as if we were running Ubuntu phone for the first time.

You need to use the mouse pointer to grab the arrow in the orange circle and drag it to the right. That should get you to another stage where you can continue. This only happens once.

Better than that install Ubuntu Desktop. download it from here

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Ubuntu Desktop Next has a limited usefulness and a limited life span. Over the next 6 months it will be discontinued and replace by Ubuntu Snappy Personal. We have yet to see an ISO image for that.

Regards.

---

### Post by neb8 on 2015-05-25
Ok, thanks. 

The "Next" version installs a very limited desktop. I remember a few references to perhaps a touch screen laptop?

 I re-installed again using a 15.04 iso DVD.

Previously installed was Ubuntu 15.04 that was upgraded to 15.10. I needed to do a re-install (15.10) so I downloaded a daily build iso, but don't recall seeing anything  about a "Next" version from the download site. I must have missed  the title being a "Next" version.

15.10 was working fairly well. The last update produced some problems with the graphics driver that can be rectivied through settings. But still existed under one or two window managers.

 I had several window managers installed including lightdm and gdm, creating aprox. ~6 logins. After installing and using the Plasma window manager. Trying to switch from plasma back to lightdm or gdm as the default wm, produced errors and problems with booting and logon. Rather than trying to repair I decided to perform a re-installation. 

 Wily was working ok. However there were few problems while installing some "wily" unsupported packages. Usually I  was able to install an earlier package version.

---

### Post by coffeecat on 2015-05-26
*Thread moved to **Ubuntu Development Version**.*

---

### Post by ventrical on 2015-05-26
> **grahammechanical said:**
> 

Ubuntu Desktop Next has a limited usefulness and a limited life span. Over the next 6 months it will be discontinued and replace by Ubuntu Snappy Personal. We have yet to see an ISO image for that.

Regards.
@graham

whew ..! You have no idea how much work you have saved me ! :) 

Regards..

---

### Post by grahammechanical on 2015-05-26
@ventrical

When Ubuntu Desktop next first came out I remember someone saying that building those ISO images would only be for a short period of time. I do not know if the devs were thinking of snappy packaging back then. It could well be so. But now we know that a decision has been made that a converged Ubuntu will be built on Snappy Ubuntu core with the normal Debian packaged based Ubuntu continuing to be developed and supported at least for the life time of 16.04.

So, I see this form of Ubuntu Desktop next as a curiosity. My last vivid installs of it updated to a kernel panic. My one wily install updated to a broken login with the switch to Mir resulting in a black screen. So, I am not wasting much time with it. It was interesting when I had to use the mouse to do swipe gestures but that has gone.

Would to community fund stretch to giving me a free Ubuntu phone? Just kidding. Testing is limited to the hardware we can afford. 

Regards

---

### Post by craig10x on 2015-05-27
Ah...Snappy Personal....looking forward to checking that out...i hope that by 16.04's release, it will be "ready for prime time"...a stable but rolling ubuntu...sounds heavenly to me ;)
And i am sure you guys are anxious to test it and see it go through it's development stages...

---

### Post by ventrical on 2015-05-27
Iv'e downloaded the ubuntu-core from here:

[http://cdimage.ubuntu.com/ubuntu-core/daily/current/](http://cdimage.ubuntu.com/ubuntu-core/daily/current/)

and you can use this process:

[http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410](http://ubuntuforums.org/showthread.php?t=1970289&page=10&p=13145410#post13145410)

to install it on to a usb and then boot it from there.

  I am using amd64 version.

I have also run it in kvm.  There is not much on snappy just yet with exception for cloud computing and even that in limited.

  I recall during watching Mark during the conference.. he mentioned something to the effect ...'and I have ubuntu-next running also' while he was conferencing about wily announcments.

  It worked well there for a while but I think it has been tossed to the wayside because this is the second cycle where it is just a collection of breakage. Time will tell. Snappy sounds just about right ! :)

regards..

---

### Post by ventrical on 2015-05-27
and from will cooke

[https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo](https://plus.google.com/+WillCooke/posts/AxfoU3N1Ezo)

regards..

---

### Post by craig10x on 2015-05-27
Thanks for the update on it, ventrical...I know i can always count on you to be on top of things like this :D
I guess it shouldn't be too long before iso images for snappy personal desktop becomes available....although i will probably wait until later in the cycle to take a peek at it (after it's really starting to roll...if you will pardon the pun...lol)....

I recall reading that the plan was to offer 2 versions of ubuntu 16.04 when it is released...Standard LTS and Snappy Personal Desktop stable edition...

---

### Post by grahammechanical on 2015-05-27
I do not expect the first Snappy Personal images to have much in them. The kernel, the OS and some utilities at most. I do not think that the app store will have much in it as applications will need to be packaged as Snaps to be put in the app store. In the same way as the Ubuntu phone has Click packages in the app store.

The fun will come as the distro is built through transactional updates. As I see things the opportunity will come to test not only the daily images but the transactional updates and the installation and removal of apps as the app store becomes fuller.

There may even be opportunities for the community to do some conversion of debs to snaps to move things along. And I do not forget that Snappy personal should be running on Mir from the start of the loading process. I look forward to testing any special effects tweak tool that anyone comes up with.

Regards.

---

### Post by neb8 on 2015-05-27
I ended up installing gnome 15.10 wily from a dvd installed iso.  So far It's working out fairly well, better than my previous installations. Gnome development seems to stress simplicity for their desktop along with enough settings that can be easily modified through it's settings and tweak tool.

---

