---
title: "Upgrade VS clean install"
date: 2016-04-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Chelidze on 2016-04-07
I have more then on machine to upgrade, every single one is customized, few of them are even under-powered machines that can't afford to lose performance.
There are all kind's of ubuntu official flavors the oldest version is 14.04 but the laptops are mostly on 15.10 

I am not a fan of upgrades but its 2016 and I've seen windows 10 upgrades.

So can i just upgrade this systems or it's still not yet there.

If my question isn't apparent i am wondering if system upgrade with **ubuntu software and updates is** effective or such an upgraded system will lose performance, compared to fresh installed version.

---

### Post by sammiev on 2016-04-07
Hi,

It seems your only talking about Windows 10.

If this is the case, you are likely asking this question in the wrong forum.

---

### Post by Bucky Ball on 2016-04-07
*Thread moved to **Ubuntu, Linux and OS Chat**.*

No idea what you're asking, sorry, so here for now.

---

### Post by deadflowr on 2016-04-07
> **Chelidze said:**
> 
So can i just upgrade this systems or it's still not yet there.

Upgrade from what to what?

---

### Post by Chelidze on 2016-04-07
> **deadflowr said:**
> Upgrade from what to what?

The oldest version is 14.04 but there are all kinds of ubuntu flavors, but as the lts release is  knocking on the door i want to upgrade those pc to that release.

I didn't wrote the amount of PCs because i don't want to sound pretentious

---

### Post by deadflowr on 2016-04-07
[COLOR=#000000] > as the lts release is knocking on the door i want to upgrade those pc to that release.[/COLOR]
Don't
Not yet.
Wait until Fall, or Late August, when the upgrade channel is officially open for upgrades from 14.04

If you want to upgrade sooner, then do a clean install.

---

### Post by Geoffrey_Arndt on 2016-04-07
OK Chelidze - - - here is your answer.   The PC's (laptops and desktops) will run at least as fast, and perhaps slightly faster. But that depends to a great degree, on error free upgrades.   The upgrade process in some ways is easier than a full re-install from a new ISO device (dvd or usb-flashstick), but not as reliable.

For instance, to upgrade from 14.04 to 16.04 . . . it's best to clean up the 14.04 PC's so they do not have any PPA's or unofficial sources enabled.   And to make the OS's as "vanilla" (plain/basic) as possible.   And to make 100% sure they are completely 100% updated with zero updates pending.   And to make sure you have very reliable power source.   And very, very, very reliable internet source (wired best, but wireless OK if it's 100% stable).   really, when I think about it, this is also true of all versions past 14.04 - - the same principles apply for each version.

Personally, I think a new install is easier on the front-end but a little more work on the back-end (add media codecs and other cutomizations).

Hope this clarifies your concerns.

PS . . . I just noticied DeadFlowrs response above - - that's even better advice - - as it takes 3-6 months for an LTS release to remove all the various things not working correctly (for production PC's - - hobbyist PC's not such a big deal)

---

### Post by grahammechanical on 2016-04-07
Whatever you do don't upgrade 14.04 to 15.10. There are posts on this forum of users doing that and ending up with a broken OS. Personally, I cannot understand why people would want to upgrade 14.04 to 15.10 when 16.04 is just a few weeks away and 15.10 is only supported until the summer. But. there you go. That's people for you.

Regards.

---

### Post by Chelidze on 2016-04-07
So i see, I guess such upgrade process is quite risky, so I guess i am going to fresh install new version whenever the systems will require them.

Thank you everyone for the help

---

### Post by deadflowr on 2016-04-07
> **Chelidze said:**
> So i see, I guess such upgrade process is quite risky, 
At the this point and time, yes.
The Ubuntu developers hold back the ability to upgrade from LTS to LTS until the new release hits the first point release.
they do this so that as many bugs as possible can be ironed out and will cause less problems.
That is important because most production systems are running the LTS versions.
And they would prefer breaking as few of those as possible.

If, from some reason you would want to try to upgrade now, you would need to run the update-manager command with the -d option (for development)
as the process of upgrading from 14.04 to 16.04 is still under development, it self. And will be until July or August.

(Unlike an official release date, which Ubuntu devs are very good at keeping, point releases can, and have been, delayed, so that they can do even more extra work to 
ensure the smoothest of upgrades.)

Does any of that make sense?

---

### Post by Chelidze on 2016-04-07
> **deadflowr said:**
> At the this point and time, yes.
The Ubuntu developers hold back the ability to upgrade from LTS to LTS until the new release hits the first point release.
they do this so that as many bugs as possible can be ironed out and will cause less problems.
That is important because most production systems are running the LTS versions.
And they would prefer breaking as few of those as possible.

If, from some reason you would want to try to upgrade now, you would need to run the update-manager command with the -d option (for development)
as the process of upgrading from 14.04 to 16.04 is still under development, it self. And will be until July or August.

(Unlike an official release date, which Ubuntu devs are very good at keeping, point releases can, and have been, delayed, so that they can do even more extra work to 
ensure the smoothest of upgrades.)

Does any of that make sense?


Yes perfectly, i not in a hurry i just was interested if it is a viable option to upgrade is such way, guess i will avoid it such an upgrade, just backing up customizing systems get really tedious.  
 Just wandering what about from 15.10 to 16.04 ?

---

### Post by neu5eeCh on 2016-04-08
[FONT=verdana]For the record, I've upgraded all my systems from 14.10 onward (rather than a new install). Before upgrading I was careful to uninstall the Intel Linux Graphics Installer. If you have any non-open source graphics drivers, remove them.

I've also had poor experiences using Ubuntu's GUI package managers. I recently upgraded both my Kubuntu installations using the kubuntu-devel-release-upgrade package and in both instances it locked up when configuring MIME types. At the Kubuntu forum I was told this is probably because the package manager can't handle "required input". 

Henceforth, I'll only be doing upgrades via command line (which with I've never had problems):
[/FONT][FONT=verdana]
```
do-release-upgrade -d
```

In my experience there's no difference in the end-product between a fresh/new install and an upgrade. If you decide to use a package manager, and if it locks up, be prepared to:

1.) Logout (if possible)
2.) CTRL+ALT+F1 (TTY)
3.) (Login) (Staying in TTY)
4.) sudo rm /var/lib/dpkg/lock (This will release the -false- lock kubuntu-devel-release-upgrade had.)
5.) sudo dpkg --configure -a (This will continue the installation.)
6.) sudo apt-get autoremove
7.) sudo apt dist-upgrade (normally nothing needs updating)
8.) sudo apt-get autoclean
9.) shutdown -r now
                        
This is worked on both my systems. 

 [/FONT]

---

### Post by brandon48 on 2016-04-12
A fresh install can be helpful and damaging depending on what drivers and important files are needed. For me Windows 10 performed better with a clean install because it got rid of weird Windows 8.1 Drivers. Just check what needs to be kept.

---

