---
title: "Anyone else tried Longene (Linux Unified Kernel)?"
date: 2010-06-11
forum: Wine
---

### Post by beastrace91 on 2010-06-11
I am currently trying to get [Longene]("http://www.longene.org/en/index.php") up and running on a 9.10 install on my laptop just to try it out and see how it compares performance wise to normal Wine. Anyone else been successful in doing so? 

I am currently [having some issues with it]("http://www.longene.org/forum/viewtopic.php?f=19&t=4274") and would love a few pointers...

~Jeff

---

### Post by asdfoo on 2010-06-11
I'm tempted to say that this isn't the right place to ask, don't they have their own forum?

---

### Post by beastrace91 on 2010-06-12
> **asdfoo said:**
> I'm tempted to say that this isn't the right place to ask, don't they have their own forum?

Read my post and check the links in it. One of them is a link to the Longene forum. I more made this post to stimulate discussion/mention Longene in case others had not heard of it yet ;)

~Jeff

---

### Post by xtremesupremacy3 on 2010-06-16
I am currently trying the Longene kernel.
I am running Lucid and thought I would give the Ubuntu debian packages.

You are asked in the install file to run the kernel package first, which told me all dependencies were satisfied. I clicked on install and had the following output:

```
arthur@arthur-laptop:~/Downloads/longene-0.3.0-ubuntu$ sudo dpkg -i longene-0.3.0-kernel_i386.deb 
[sudo] password for arthur: 
(Reading database ... 269685 files and directories currently installed.)
Unpacking linux-image-2.6.30-longene-0.3.0 (from longene-0.3.0-kernel_i386.deb) ...
Done.
dpkg: error processing longene-0.3.0-kernel_i386.deb (--install):
 trying to overwrite '/lib/firmware/intelliport2.bin', which is also in package linux-firmware 0:1.34
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found linux image: /boot/vmlinuz-2.6.23-0.2.4uk
Found initrd image: /boot/initrd.img-2.6.23-0.2.4uk
Found memtest86+ image: /boot/memtest86+.bin
done
Errors were encountered while processing:
 longene-0.3.0-kernel_i386.deb
```

As you can see it mentions a problem with a conflict in the firmware and a broken pipe, unfortunately my knowledge does not extend to kernel modifications so this is unknown territory for me.

Is there anybody who might be able to tell me what this means and how I may be able to fix this?

Also, I seen there was a mention of the forums of the Longene project. Please note that the country of origin seems to be China and although there is a lot of English, this seems fairly broken and cryptic at times (Just take a look at the install instructions for the source and you will know what I mean). And considering this is output in relation to a debian package in reference to a part within an Ubuntu system, I thought the great people here would be more use to me.

Once I am able to test run the Longene project I will post my findings and whether I recommend it or not.

Arthur

---

### Post by xtremesupremacy3 on 2010-06-16
After having forced the overwrite, all went well and the kernel and then the longene wine package was installed.
I updated grub accordingly and restarted the system using the new longene kernel.

A long list of errors flashed across my screen about error 5, udev and i can't remember what else, and there seems no real mention of it in my logs.
When it stopped it loaded the log in screen and I was unable to use my mouse, touchpad or even keyboard. So for me, this was a complete failure.

Arthur

---

### Post by beastrace91 on 2010-06-16
If you read their website they only currently work with/support 9.10 and 9.04

That being said I am still fighting with getting it working.

~Jeff

---

### Post by xtremesupremacy3 on 2010-06-26
Just goes to show how lazy I am, that I didn't even read that.

The thing is though, I mean if it didn't work on Lucid, then how come I managed to login to it without problem, my graphics card and all worked except for input lol.

Well lets hope support for lucid is done soon and that it works as well as it sounds.

Regardless of the doubts and worries over it, this could just be the thing we need to compete with the biggest names.

Edit: Wow, they must have read my post really quick! There is now a binary package available with support for 9.04, 9.10 and 10.04...I am downloading it now, and will test it out and report my findings here.

---

### Post by xtremesupremacy3 on 2010-06-26
So I installed the debs according to the instructions inside the package file.

My Nvidia graphics card isn't supported there for some reason, the only mention I found back of it was that my log mentioned 'MSI Nvidia' was disabled :-S...I was able to login and then discovered that my WLAN card wasnt being recognised, I had ndiswrapper installed, removed the driver, tried to reinstall and got the weird message that the module wasnt found, was I sure I had ndiswrapper installed? 

I tried to at least test the support for more windows apps but to be honest didnt see much difference between a normal wine install and this one...so unless they fix the nvidia issue and the atheros issue, theres not much I can do.

---

### Post by beastrace91 on 2010-06-28
Did you install the closed source nvidia drivers? I found they where working under 9.10 with Longene for me.

Now that they have added support for a kernel that works with 10.04 I am going to build some kernel packages that add support for touch pads and intel + atheros wifi. Any requests for other hardware I should enable in their kernel that you noticed wasn't working? It seemed pretty limited by default :-/

~Jeff

---

### Post by xtremesupremacy3 on 2010-07-04
Well for me they seemed to be the most problematic.
I think the best idea is for people with an interest and a spare system to test it out and let you know the results. This is currently my only system so I can't test it on other hardware

Arthur

---

### Post by nicamarvin on 2010-07-31
How about Reactos and Colinux? I am using Reactos and portable Ubuntu and while I get all of the linux I want in ubuntu Reactos is still working to be more stable, but at the moment this seems to be a shorter road as to have a fully GPL system that is able to run windows and linux apps in one system...:razz:

---

### Post by beastrace91 on 2010-08-01
> **nicamarvin said:**
> How about Reactos and Colinux? I am using Reactos and portable Ubuntu and while I get all of the linux I want in ubuntu Reactos is still working to be more stable, but at the moment this seems to be a shorter road as to have a fully GPL system that is able to run windows and linux apps in one system...:razz:

ReactOS is a cute idea but is far from a practical operating system IMO

~Jeff

---

### Post by nicamarvin on 2010-08-02
> **beastrace91 said:**
> ReactOS is a cute idea but is far from a practical operating system IMO
 
~Jeff at this moment yeah, but it aims to be 100% in long run, something that wine will never be or longene for that matter

---

### Post by Sean.m on 2011-03-03
> **nicamarvin said:**
> at this moment yeah, but it aims to be 100% in long run, something that wine will never be or longene for that matter
That may be the long term goal of the ReactOS project but Microsoft is moving towards .Net as a universal api for all their supported platforms, which means Mono on the *nix side, not just Wine and definately not ReactOS. Meanwhile the OSS projects are still not fully win32 compatible and will always be catching up. The real question is, would you rather be using Windows? Probably not.

---

