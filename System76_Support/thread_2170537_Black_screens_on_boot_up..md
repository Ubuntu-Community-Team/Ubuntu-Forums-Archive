---
title: "Black screens on boot up."
date: 2013-08-26
forum: System76 Support
---

### Post by isantop on 2013-08-26
We've released a fix for the black-screen-on-boot issue. You are experiencing this bug if you boot your computer and see either:

A. A black screen with a flashing cursor in the upper right.
B. A black screen with the mouse cursor in the center. 

The fix is being distributed through the System76 PPA, which should be installed if you have the latest driver (13.04.8 as of the time of writing). The update will be distributed through your Software Updater application with your regular software updates. If you're experiencing the black-screen issue, then after booting up and getting to the black screen, you can type your password, followed by enter, to log in and update.

If you don't have the latest driver, you can add the PPA for it by running these commands:

```
sudo add-apt-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get install system76-driver
```

You can then install any available updates to install the fix.

---

### Post by Dave_L on 2013-08-26
If a "black screen with a flashing cursor in the upper right" occurs once in a while when resuming from suspend, is that the same bug?

---

### Post by isantop on 2013-08-26
It definitely could be. Go ahead and install the updates, and let me know if you're still having problems.

---

### Post by Dave_L on 2013-08-26
If it messes up the system, is there a procedure for reverting to the old version of the driver?

---

### Post by isantop on 2013-08-26
It won't mess up the system, as this is a non-invasive fix. We're actually rolling it out to all customers, whether they've reported it or not. The driver also doesn't specifically provide the fix; it's just a handy way to tell if the PPA is installed or not (which is where the fix really is).

---

### Post by Dave_L on 2013-08-26
So there's no problem with applying this fix on Ubuntu 12.04 LTS (with "raring" kernel 3.8.0-29)?   This recent post confused me on that issue: [http://ubuntuforums.org/showthread.php?t=2165676&p=12747835#post12747835](http://ubuntuforums.org/showthread.php?t=2165676&p=12747835#post12747835)

---

### Post by Dave_L on 2013-08-26
> $ sudo apt-get update
...
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                                                   404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                                   
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages              
  404  Not Found
...
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/source/Sources)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
W: Failed to fetch [http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/system76-dev/stable/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

I suppose that answers my question, and that the fix is NOT compatible with Ubuntu 12.04 LTS?

---

### Post by isantop on 2013-08-27
12.04 shouldn't have the problem. This is a bug with 13.04's version of LightDM.

---

### Post by CrammitTheFrog on 2013-08-27
Thank you isantop. I too have those issues.

---

### Post by Edward_G_Prentice on 2013-08-29
I'm sorry, but I'm curious and I have to ask.  If you get the black screen on boot, how are you supposed to download the updates?  I suppose a pre-emptive strike to download before seeing the symptom would be good, but if you can't boot, you can't download, right?

---

### Post by isantop on 2013-08-29
Good point. I've updated the original post.

You can type your password at the black screen and hit enter to log in (which will take you to the normal desktop). Basically, the log in screen is there, it's just not visible.

---

### Post by Edward_G_Prentice on 2013-08-30
I learned a tidbit from system76 support. If you *do* get the black screen before you've updated the drivers, it is waiting for your login password, but you can't see the prompt because the graphics driver hasn't been loaded yet. Go ahead any type your password anyway and it should log you in. *Then* go ahead and update the drivers.

---

### Post by rumpumpel1 on 2013-09-01
I'm on Ubuntu 13.04, I've applied the patch, I still get the black screen with the cursor in the upper left corner and when typing my password I'm not logged in.

---

### Post by isantop on 2013-09-03
It sounds like you're experiencing a different issue. You should contact us via your account on our website. We'll be able to diagnose the problem there.

Just to recap, if you run these commands:

```
sudo add-apt-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get upgrade
```

then reboot your computer, youre still seeing black screens?

---

### Post by kptsuresh on 2013-09-05
updating to grub2 may solve the problem..

---

### Post by isantop on 2013-09-05
I'm assuming every user out there is running grub2 at this point.

---

