---
title: "System76 Driver 2.3.5 released - Starling Netbook &amp; Bonobo Brightness Hotkeys"
date: 2009-05-12
forum: System76 Support
---

### Post by crichell on 2009-05-12
System76 Driver 2.3.5 has been released.

This release includes drivers and patches for the Starling Netbook, Bonobo Brightness Keys fix in Jaunty, and now installs linux-backports-modules-jaunty to fix shutdown hangs when using the nVidia 180 driver.

We are currently only installing linux-backports-modules-jaunty on models panp4n, panp5, bonp2, serp5. If you have a different model and are experiencing shutdown hangs when using the nVidia 180 driver please let us know.

---

### Post by thomasaaron on 2009-05-13
The System76 Driver comes installed on your system and is located in your menu at System > Administration > System76 Driver. Any updates to the System76 Driver will be detected by Update Manager. 

If you have performed a fresh Ubuntu installation, you will need to install and run the System76 Driver. To install it, go to...

[http://planet76.com/repositories](http://planet76.com/repositories)

...and download the latest driver .deb package. The latest driver will always be the second link from the bottom. Save it to your Desktop.
Once it has downloaded, double-click the icon on your desktop and follow the prompts to install it. Once you are finished, it will appear at System > Administration > System76 Driver.

The first time you run the driver after a fresh installation, you will need to click the Restore System tab and the Restore button. This will modify your software sources file so that any future driver updates will be available via Update Manager.

After running the driver the first time, you no longer need to use its restore fucntionality. You can just use the Install Drivers tab and the Install button to install any necessary drivers.

If for some reason you get a GPG Key error when trying to update, open a terminal (Applications > Accessories > Terminal) and run this command to fix it.

wget -q [http://planet76.com/repositories/system76_dev.pub](http://planet76.com/repositories/system76_dev.pub) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by elusivespoon on 2009-05-20
> These drivers a designed for System76 computers.  If you purchased your computer from System76 and are receiving this message please contact customer support at [email]support@system76.com[/email]

I am receiving this message on a Daru2

---

### Post by thomasaaron on 2009-05-20
Did you flash the BIOS on your DarU2?
Also, what driver version are you using?

---

### Post by elusivespoon on 2009-05-21
Oops. I guess the page failed to load completely, only listing the oldest versions. I've just grabbed the latest and it worked fine.

Is flashing the BIOS highly recommended?

---

### Post by thomasaaron on 2009-05-22
You've lost me.

If you flashed the BIOS on your DarU2, the System76 driver may be having trouble identifying it.

Flashing the BIOS is not highly recommended. 

The latest version of the System76 Driver (2.3.5) should recognize your DarU2. If you've *not* flashed your BIOS, and you *are* using the 2.3.5 version of the driver, then there may be a bug in the driver.

Also, you are using Ubuntu, right?

---

### Post by retrovertigo on 2009-05-23
I tried installing the driver on a fresh Jaunty install, and let it run for 45 minutes, and it still said "Installing Driver".  I did have an internet connection.  I closed the system76 driver window and tried reinstalling, and it said that another package manager was running, even though none was.  I was able to do an apt-get update and even install a couple packages, but when I came back to the driver installer, it kept telling me there was a package manager running.  After a reboot, I was able to successfully install the driver.

---

### Post by ubermenschx on 2009-05-30
My System76 Starling is having a problem with the "driver" and wireless. The Restore function gets stuck and wont stop and the wireless isn't working properly. The icon/bars show I am connected to the router but no through put. I cant get a website up or get updates, so I have to hardwire it to get internet and when I ping other machines on my network, I only get a response when hardwired. Any help is appreciated. I have re-installed several times and meticulously followed the directions but keep getting stuck with the wireless and restore issues.

---

### Post by miniyak on 2009-05-30
Are s76 updates manual or is it suppose to come up in the update manager with all the other package updates?
 
Also, my update manager says "failed to detect distribution" would this this stop updates from automatically happening on the ubuntu side of things?

note: i have set update manager to notify me every week
I've had the panp5 for 2 weeks almost, still no updates. Have their been no updates from ubuntu in this time?

---

### Post by thomasaaron on 2009-05-30
> Are s76 updates manual or is it suppose to come up in the update manager with all the other package updates?

Read the second post down. It explains how the System76 driver is updated in detail.

> Also, my update manager says "failed to detect distribution" would this this stop updates from automatically happening on the ubuntu side of things?

It could definitely cause problems. What version of ubuntu are you using? What is the output of...

```
uname -a
```

---

### Post by elusivespoon on 2009-05-31
> **elusivespoon said:**
> Oops. I guess the page failed to load completely, only listing the oldest versions. I've just grabbed the latest and it worked fine.
To clarify, I have successfully downloaded the latest version of the driver and installed it. The reason it wasn't working was I had accidentally downloaded an old version as the web page only partially loaded, with only a few, old drivers showing as available for download.

---

### Post by miniyak on 2009-05-31
im using 9.04 64bit that came preloaded

output of uname -a= Linux system76-pc 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

---

### Post by thomasaaron on 2009-06-01
Hi, Miniyak.

I think I see what's going on. Some package that you downloaded may be having difficulty recognizing or finding updates pertinent to Jaunty. It shouldn't effect all of your Jaunty updates, just the ones pertaining to that one piece of software.

Please let me know the full text of the error.

---

### Post by miniyak on 2009-06-01
that was the full output.... was there suppose to be more? 

ive installed a lot of programs so if it is something else its probably redundant

just now one update came through for security after clicking check. does this sound right? its only been two weeks, so i may be over reacting

---

### Post by thomasaaron on 2009-06-01
Updates are pretty constant. That sounds normal.

Could you take a screenshot of that error message if it pops up again?

---

### Post by miniyak on 2009-06-01
after pressing "check" a couple times i have been unable to reproduce the issue so may be its magically ok now... lol

if it happens again ill post the screenshot/issue summery in a new thread and edit this post to link. since this isn't as relevant to the OP as i thought.

---

### Post by thinman1189 on 2009-06-02
I have serp4 and I just did a clean install of 9.04 and did the s76 driver install. Now my internet is messed up. I keep disconnecting every few minutes.

---

### Post by thomasaaron on 2009-06-03
The System76 Driver doesn't do anything to affect the connectivity. You probably should post a new thread on this so it doesn't confuse this thread. Please include a description of your wifi setup and logs from System > Admin > System76 Driver > Support > Create.

---

### Post by thinman1189 on 2009-06-03
Okay, thanks thomasaaron.

---

