---
title: "New Features in Ubuntu 14.10 &quot;Utopic Unicorn&quot;?"
date: 2014-06-29
forum: Ubuntu, Linux and OS Chat
---

### Post by techcaptain on 2014-06-29
Hello, I've been using Ubuntu 14.04 for a while and I found out Ubuntu 14.10 Utopic Unicorn Beta 1 was out...
So I've been wondering.. what's new in this version?

I've tried searching OMG! Ubuntu! and it just shows up only information about it, not the features.

Can someone give me a brief explaniation about it please?

---

### Post by oldos2er on 2014-06-29
Have you read the [release notes]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes")?

---

### Post by philinux on 2014-06-29
> **Hyunwoo_Jo said:**
> Hello, I've been using Ubuntu 14.04 for a while and I found out **Ubuntu 14.10 Utopic Unicorn Beta 1** was out...
So I've been wondering.. what's new in this version?

I've tried searching OMG! Ubuntu! and it just shows up only information about it, not the features.

Can someone give me a brief explaniation about it please?

Beta 1 not out till August 28th.

Please see the relevant stickies and threads here. [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by techcaptain on 2014-06-30
Woops, i meant the daily builds @ [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

my apologies :)

---

### Post by techcaptain on 2014-06-30
Oh no - ugh, what has gone in to me - I meant 14.10 not 14.04 
sorry again

---

### Post by 3rdalbum on 2014-06-30
There is no alpha for Ubuntu 14.10, only for some of the derivatives with different desktops.

I don't think there are any major new features, just the usual stuff that comes with newer software. Any real new features will come later in the cycle. Two months is too short to develop a new feature and make it work well enough to go into the image

---

### Post by grahammechanical on 2014-06-30
I would say, that do not expect new features until 16.04 is released as 16.04 will be the first release of the Ubuntu where the phone/tablet code is converged with the desktop code. In 16.04 Ubuntu will be running on Mir and have Unity 8 and mobile device click packages and other mobile stuff. But this stuff will not come in to 14.10 or 15.04 as the code is in a parallel track. There is even a separate ISO image for it called ubuntu-desktop-next. It does not do much at the moment. In fact the last time I run the installation it froze just after the login screen accepted the password. Been like that for days.

[http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-desktop-next/daily-live/current/)

Regards.

---

### Post by craig10x on 2014-06-30
So, would you say that 14.10 is running pretty stable and reliable?  Would it work well at this point as a main system for someone with juts one computer who runs just one os?
Just wondering...i am still on 14.04 but was a bit tempted to switch over to 14.10 (w/unity of course)...but it would have to be reliable enough to use as my main system...

---

### Post by philinux on 2014-06-30
> **craig10x said:**
> So, would you say that 14.10 is running pretty stable and reliable?  Would it work well at this point as a main system for someone with juts one computer who runs just one os?
Just wondering...i am still on 14.04 but was a bit tempted to switch over to 14.10 (w/unity of course)...**but it would have to be reliable enough to use as my main system**...

Definitely not. You will get breakage and the system may not even boot.

You can follow the development here. [http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

See this [https://wiki.ubuntu.com/U%2B1/common-problems#My_testing_installation_is_badly_broken._Is_there_a_way_to_roll_back_to_the_stable_release]("https://wiki.ubuntu.com/U%2B1/common-problems#My_testing_installation_is_badly_broken._Is_there_a_way_to_roll_back_to_the_stable_release")

---

### Post by craig10x on 2014-06-30
Thank You, philinux...i will just stay with 14.04 and probably wait for the final release of 14.10 before upgrading...;)
I have the 3.15.2 kernel running on my 14.04 and it took care of certain problems i had with the 3.13 version that was running "stock"...i may do more manual upgrades on that kernel and eventually put the 3.16 on when it goes final...much safer doing that then going into development for someone like me that has just one computer and runs just One Os on his drive...

---

### Post by philinux on 2014-06-30
You're welcome. 

You could join the party by creating a partition for U+1 and dual boot.

---

### Post by fyfe54 on 2014-06-30
Craig10x - 
I'm running the 3.16.rc3 kernel in 14.04 and I must say it seems pretty solid and zippy.  Not a recommendation, just an observation.

---

### Post by craig10x on 2014-06-30
fyfe54...appreciate the observation...i would be more then willing to give it a go...i seem to have become quite an expert on adding and removing kernels all of a sudden (lol) ;) :D

---

### Post by monkeybrain20122 on 2014-06-30
New features in kernel 3.1.6 [URL="http://www.phoronix.com/scan.php?page=news_item&px=MTcyMDU"]http://www.phoronix.com/scan.php?page=news_item&px=MTcyMDU
[/URL]Not sure why you need a kernel module to tell you that your laptop is in free fall, you will find out soon enough when it hits the floor. :)

---

### Post by craig10x on 2014-06-30
Too Funny :mrgreen:

---

### Post by /ADM on 2014-07-03
> **monkeybrain20122 said:**
> New features in kernel 3.1.6 [URL="http://www.phoronix.com/scan.php?page=news_item&px=MTcyMDU"]http://www.phoronix.com/scan.php?page=news_item&px=MTcyMDU
[/URL]Not sure why you need a kernel module to tell you that your laptop is in free fall, you will find out soon enough when it hits the floor. :)

Too funny, though seriously (if it supports it) then it should work much like OSX that it will hibernate your HDD during freefall to avoid damage to it when it hits the floor.  Not sure what use it would be for SSD's since there is no moving parts to destroy.

---

### Post by 3rdalbum on 2014-07-03
> **abilbrou said:**
> Too funny, though seriously (if it supports it) then it should work much like OSX that it will hibernate your HDD during freefall to avoid damage to it when it hits the floor.  Not sure what use it would be for SSD's since there is no moving parts to destroy.

It actually parks the HDD's heads in a safe location, so when the impact occurs the heads won't slam into the platter.

I believe somebody wrote a game that is controlled by the drop-sensor; tilt your laptop to move left and right! Also, I heard a joke about using the sensor to generate encryption entropy: "Generating encryption key, please shake your computer".

---

### Post by monkeybrain20122 on 2014-07-03
Maybe to use the computer in a zero gravity (= free fall) environment like in an orbiting satellite. :)

---

### Post by gacb on 2014-08-19
I've been running Ubuntu Gnome 14.10 on newer and older (2006) laptop partitions since Alpha 1, and backward compatibility doesn't seem to be an issue. There is a problem with ttf-mscorefonts-installer but I expect it to be resolved long before the official release.

---

### Post by Cliff_Simonds on 2014-08-19
> **gacb said:**
>  There is a problem with ttf-mscorefonts-installer but I expect it to be resolved long before the official release.

That does get on the nerves after awhile, don't it though? After the fourth time it wanted to install ttf I just started closing the request.

---

### Post by 3rdalbum on 2014-08-20
14.10 has reached Feature Freeze!

Erm... *what* features?

Seriously though, what user-facing features have been added to 14.10? I haven't heard of anything apart from "new kernel, new GCC, we're still just working on Ubuntu Touch". I'd really like to know if anything useful has hit 14.10.

---

### Post by juan-carretero on 2014-08-21
I too am looking for the features.  I have spent the better part of 30 minutes trying to find a reliable source listing the features to no avail.  Any pointers?

---

### Post by d-cosner on 2014-08-23
I think the focus is on Unity 8 in the 14.10 cycle. 14.10 will have a newer kernel and applications but I expect Unity will remain the same as it is in 14.04. There will be the transition to systemd but we will not really notice much of a difference there. The developers are trying to get Ubuntu touch working for manufacturers, that is why it is getting more attention this time around.

---

