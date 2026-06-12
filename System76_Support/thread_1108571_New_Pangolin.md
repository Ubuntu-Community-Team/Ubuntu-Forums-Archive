---
title: "New Pangolin"
date: 2009-03-27
forum: System76 Support
---

### Post by Talon2 on 2009-03-27
I ordered a new Pangolin for a niece.  It arrived this week and I made delivery today.  I tried to do some configuration work on it before turning it over but I'm not so sure in hindsight if I didn't do more damage than good.  I've been using small computers since CPM was king but, I guess, it is easy to get locked in.  Here is the story:

I read about the system before ordering it.  I knew it would come with 64 bit 8.10.  Two of the software packages I wanted to install included Realplayer and Skype.  I proceeded to real.com and skype.com where I proceeded to download the .debs of the latest versions.  They would not install as they are, apparently, the 32 bit versions.  No idea what to do about 64 bit versions.  Anyone?

I also wanted to add various codecs, DVD support and various other things that you get with restricted extras.  Now I'm wondering if I polluted the system with 32 bit code?

Oh, I was wondering why the graphics performance was so poor and I remember after the system was delivered that it had a Nvidia chipset.  I had to call and walk her through the process of activating the binary driver.  All systems I've used Ubuntu on have had either Intel or ATI chipset.  Geez I wish Nvidia would support an open source driver.  I think I'll stay with Intel (or ATI) when I order another system.

My final thoughts:  If I have made a mess out of this system, would I be better off doing a fresh 32 bit installation?  As far as I can tell all I would need to find and download are the System 76 driver and the finger reader driver.  I fail to see any advantage of 64 bit Ubuntu for this system and I've already run into headaches.  Tell me what you think?

Thanks.

Oh, the hardware is nice.

---

### Post by formol on 2009-03-27
hello Talon2,

when I received my Pangolin, the first thing I did was to install the 32bit version, for software compatibilty (wine, Floola for my iPod).
but I don't thing it can be contaminated one way or another, if it just refused to install.

for the nvidia driver, after many try, i suggest you the orignal nvidia driver with ubuntu 8.04 (with nvidia logo at boot) and the ubuntu one 8.10 (without the nvidia logo at boot)

personnaly I only use nvidia with linux, because they do a driver for every card when the release it, which not the case with ATI or Intel.

---

### Post by Talon2 on 2009-03-27
> **formol said:**
> hello Talon2,

when I received my Pangolin, the first thing I did was to install the 32bit version, for software compatibilty

Thanks formol,

I think I'll head toward the 32 bit option.  The more I look at what is going to happen the more it appears I can't overcome the 64 bit problems, at least at this point in time.  I'll probably wait until Jaunty is released then do it...well, I say that but I wonder if the System76 driver will be ready to do a "restore" with 32 bit Jaunty?

While I have you, have you set up and used the finger reader?

Thanks.

---

### Post by formol on 2009-03-27
> **Talon2 said:**
> 
While I have you, have you set up and used the finger reader?

yes I did, when I received it. but since, I never re-install the finger reader.  It was working fine, but you need to "scan" your finger the same way that you did the first time to log in, so I prefered the "old shool" log in method with username and password.

for Jaunty, I tryed the Alpha6 version on my pangolin for a couple of day, it was very fast, I was even surprise.  all hardware was working, including webcam.  since I tryed the alpha6 and beta version on another computer, EXT4 is great but VLC is full of bugs now.  but you're right, wait for jaunty, just for EXT4, it value the time you'll wait.

---

### Post by betrunkenaffe on 2009-03-27
Google "Skype Ubuntu 64 bit"
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

Google "Realplayer Ubuntu 64 bit"
[https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods)

---

### Post by Talon2 on 2009-03-28
> **formol said:**
> yes I did, when I received it. but since, I never re-install the finger reader.  It was working fine, but you need to "scan" your finger the same way that you did the first time to log in, so I prefered the "old shool" log in method with username and password.


Ok, finger reader is a rainy day project.  Thanks for the info.

ext4 has blown up on me twice.  I've been busy over the last few months so only tried alpha6 and now the beta as of today.  I installed the beta today and on reboot I had text errors and a requirement to fsck manually.  fsck couldn't fix it.  Same happened with alpha 6.  I formatted and reinstalled with ext3 and am using it now to type this reply.  To say I am not impressed with ext4 is an understatement.  Be careful.

---

### Post by Talon2 on 2009-03-28
> **betrunkenaffe said:**
> Google "Skype Ubuntu 64 bit"
[http://ubuntuforums.org/showthread.php?t=432295](http://ubuntuforums.org/showthread.php?t=432295)

Google "Realplayer Ubuntu 64 bit"
[https://help.ubuntu.com/community/RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealPlayerInstallationMethods)

I appreciate the help but this won't work.  The reason is that I'm working to convert someone to Ubuntu...and pages like this will only cause normal people to run.  They can handle downloading and installing a .deb.

---

### Post by betrunkenaffe on 2009-03-28
You said you are setting it up, hence you could do it, they could use it, win win situation until the companies in question fix their release version to work with 64 bit.

Switching someone to Linux without them understanding that sometimes things may take a little bit of fiddling and learning really doesn't do them justice. Even if you get everything working now, they may want something later and the install could be alot crazier than anything you've had and they'll want you to do it OR will want to go back to Windows anyways.

This is the way things are going to be until there is both better hardware support and better company software support for the OS.

PS: Skype for Linux is older than the Windows Skype because they still haven't bothered updating it.

---

### Post by thomasaaron on 2009-03-28
The PanP4 works great in 64-bit. nVidia would've been enabled by default when the machine arrived.

We have posted tutorials for installing Skype and restricted formats...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

Also, webcam and fingerprint drivers and software come already installed on it.

Please feel free to contact me any time via these forums or email (support(at)system76(dot)com) whenever you have questions.

---

### Post by Talon2 on 2009-03-28
> **betrunkenaffe said:**
> 
Switching someone to Linux without them understanding that sometimes things may take a little bit of fiddling and learning really doesn't do them justice. Even if you get everything working now, they may want something later and the install could be alot crazier than anything you've had and they'll want you to do it OR will want to go back to Windows anyways.

This is the way things are going to be until there is both better hardware support and better company software support for the OS.


I've got a good understanding of how to switch people from Microsoft products.  I've been doing it since before Linus had the idea to create a kernel.  I'm not saying I am doing a good job in this case...because I'm not so far.  I do intend to recover and give it the best shot I can.

Concerning the hardware support:  I consider Linux hardware support to be good.  Could it be better?  Sure.

---

### Post by thomasaaron on 2009-03-28
Here are our restore instructions...
[http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System)

Be sure to install the System76 driver and run the Restore functionality of it. That will bring it back to factory specs.

---

### Post by Talon2 on 2009-03-28
> **thomasaaron said:**
> The PanP4 works great in 64-bit. nVidia would've been enabled by default when the machine arrived.

We have posted tutorials for installing Skype and restricted formats...
[http://knowledge76.com/index.php/Installing_Restricted_Formats](http://knowledge76.com/index.php/Installing_Restricted_Formats)

Also, webcam and fingerprint drivers and software come already installed on it.

Please feel free to contact me any time via these forums or email (support(at)system76(dot)com) whenever you have questions.

I appreciate the information.

I'm sure the system works great in 64 bit.  The problem in this case is that the human (me) doesn't work great in 64 bit...yet <grin>.

---

