---
title: "Linux Kernel 3.7"
date: 2012-12-11
forum: The Cafe
---

### Post by The Spectre on 2012-12-11
Just an FYI...

The new Linux Kernel 3.7 has just been released earlier today.

[http://kernel.org/](http://kernel.org/)

I have already Updated and everything seems to be running Rock Solid.

---

### Post by The Spectre on 2012-12-12
If anyone wants to update to Linux Kernel 3.7 this makes it very easy...

[http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html](http://www.upubuntu.com/2012/12/installupgrade-to-linux-kernel-37-under.html)

Of course always play it safe and Backup your data first.

---

### Post by mamamia88 on 2012-12-12
New kernels come out so often it's hard to get excited for me.  [http://kernel.org/](http://kernel.org/) Also you don't gain much by upgrading with every one.

---

### Post by Mikeb85 on 2012-12-12
3.7 does seem to be a huge step up.  Runs much quicker than 3.6 did, and much more stable.

---

### Post by The Spectre on 2012-12-12
> **mamamia88 said:**
> New kernels come out so often it's hard to get excited for me.  [http://kernel.org/](http://kernel.org/) Also you don't gain much by upgrading with every one.

They definitely do come out often.:roll:

And going from Kernel 3.6.1 to Kernel 3.6.5 probably isn't a big deal.

But the 3.7 Kernel update does seam to offer a lot of improvements, features and hardware support...
[http://kernelnewbies.org/Linux_3.7_DriverArch](http://kernelnewbies.org/Linux_3.7_DriverArch)

---

### Post by Eugene King on 2012-12-28
What are you doing about the 3.0.0 kernal updates? 

I installed 3.7 so I could USB tether with my iPhone 5. Now I'm not sure if I should allow updates.

---

### Post by monkeybrain2012 on 2013-01-02
> **Eugene King said:**
> What are you doing about the 3.0.0 kernal updates? 

I installed 3.7 so I could USB tether with my iPhone 5. Now I'm not sure if I should allow updates.

No problem. It will update 3.6 but it will not affect 3.7. Typically you can have multiple kernels installed. Of course you can also delete all the 3.6 stuffs if you decide that 3.7 is stable enough.

---

### Post by Eugene King on 2013-01-02
I've used it for 1 week now and seems good to go. I just don't want to have the 3.7 kernal messed up or reverted back. 

Ill allow updates tonight and see what happens. It was a simple upgrade.

---

### Post by The Spectre on 2013-01-02
> **Eugene King said:**
> I've used it for 1 week now and seems good to go. I just don't want to have the 3.7 kernal messed up or reverted back. 

Ill allow updates tonight and see what happens. It was a simple upgrade.

You shouldn't have any problem, the Ubuntu Update Center updated the Linux Kernel on my system to 3.5.0-21 but the Linux Kernel 3.7 continued to be used after the update.

If you want to play it Extra Safe you could make an Image of your Hard Drive before you do the Update...
Redo Backup & Recovery
[http://redobackup.org/](http://redobackup.org/)

There is also a Linux Kernel 3.7.1 Maintenance Release available... 
[http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html](http://www.upubuntu.com/2012/12/install-linux-kernel-371-on-ubuntu.html)

To confirm what Linux Kernel you are running use this command in Terminal...
```
uname -r
```

---

### Post by cariboo on 2013-01-02
I'd like to add a word of caution here, I don't know if it affects previous versions, but many of us running Raring on older AMD cpu's have not been able to boot any version of the 3.7 kernel.

We have had success booting 3.8 rc1 though.

---

### Post by Eugene King on 2013-01-02
> **cariboo907 said:**
> I'd like to add a word of caution here, I don't know if it affects previous versions, but many of us running Raring on older AMD cpu's have not been able to boot any version of the 3.7 kernel.

We have had success booting 3.8 rc1 though.

This version of Ubuntu with the 3.7 kernal is installed on a USB stick and I use it at work on a Dell Optiplex 980 as my personal computer. 


But thank you. It is weird though that I created the USB drive here at work and can't get it to boot up at home on my laptop. But works fine at work.

---

### Post by Eugene King on 2013-01-03
Well I just allowed Updates. 

I'm still on Kernel 3.7 because I'm still tethering via USB with my iPhone 5.

About to reboot.

Edit.......just rebooted and 3.0.0.29 didn't even show up as a boot option. It kept 3.7 which is good.

---

