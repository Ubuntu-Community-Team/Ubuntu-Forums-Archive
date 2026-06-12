---
title: "snap packages: some useful links"
date: 2016-04-20
forum: Ubuntu Development Version
---

### Post by vasa1 on 2016-04-20
It would be nice to have a chatty thread about snaps and what they are and how to get them on all flavors of 16.04 in case someone thinks they're tied up to one specific flavor.

Here's a useful link: [Get started with snaps on the desktop]("https://developer.ubuntu.com/en/desktop/get-started/"). It includes a command-line approach as well.

---

### Post by grahammechanical on 2016-04-21
Thank you for the link. I have been looking for information like that.

The important command is "snap find" Keep in mind that very few of the snaps are suitable for a desktop. Many of those listed are for snappy Ubuntu core. Things will get better as app developers see advantages to converting their apps to snaps. 

Regards.

---

### Post by grahammechanical on 2016-04-21
Yesterday I installed ubuntu-clock-app which is a snap. I could not find  an icon for it in the Dash. I loaded it with a command and something  failed. So, I used a command to remove the snap. Today I found this:

[http://blog.labix.org/2016/04/20/snappy-changes](http://blog.labix.org/2016/04/20/snappy-changes)

I used a couple of commands as an experiment in diagnostics

> graham@sdb7-Dev:~$ sudo snap changes 1
Status  Spawn                 Ready                 Summary
Done    2016-04-21T04:05:41Z  2016-04-21T04:06:52Z  Download snap "ubuntu-core" from channel "stable"
Done    2016-04-21T04:05:41Z  2016-04-21T04:06:59Z  Mount snap "ubuntu-core"
Done    2016-04-21T04:05:41Z  2016-04-21T04:07:00Z  Copy snap "ubuntu-core" data
Done    2016-04-21T04:05:41Z  2016-04-21T04:07:02Z  Setup snap "ubuntu-core" security profiles
Done    2016-04-21T04:05:41Z  2016-04-21T04:07:04Z  Make snap "ubuntu-core" available to the system
Done    2016-04-21T04:05:41Z  2016-04-21T04:09:15Z  Download snap "ubuntu-clock-app" from channel "stable"
Done    2016-04-21T04:05:41Z  2016-04-21T04:09:23Z  Mount snap "ubuntu-clock-app"
Done    2016-04-21T04:05:41Z  2016-04-21T04:09:24Z  Copy snap "ubuntu-clock-app" data
Done    2016-04-21T04:05:41Z  2016-04-21T04:09:26Z  Setup snap "ubuntu-clock-app" security profiles
Done    2016-04-21T04:05:41Z  2016-04-21T04:09:27Z  Make snap "ubuntu-clock-app" available to the system

> graham@sdb7-Dev:~$ sudo snap changes 2
Status  Spawn                 Ready                 Summary
Done    2016-04-21T04:18:22Z  2016-04-21T04:18:22Z  Make snap "ubuntu-clock-app" unavailable to the system
Done    2016-04-21T04:18:22Z  2016-04-21T04:18:23Z  Remove security profile for snap "ubuntu-clock-app"
Done    2016-04-21T04:18:22Z  2016-04-21T04:18:23Z  Remove data for snap "ubuntu-clock-app"
Done    2016-04-21T04:18:22Z  2016-04-21T04:18:27Z  Remove snap "ubuntu-clock-app" from the system
Done    2016-04-21T04:18:22Z  2016-04-21T04:18:27Z  Discard interface connections for snap "ubuntu-clock-app"

......................................................................
Remove snap "ubuntu-clock-app" from the system

2016-04-21T05:18:26+01:00 INFO Waiting for snap-ubuntu\x2dclock\x2dapp-5.mount to stop.


Things are starting to get interesting.

Regards

[URL="http://blog.labix.org/2016/04/20/snappy-changes"]
[/URL]

---

### Post by vasa1 on 2016-04-21
Can you or anyone else post about a simple snap package (?) that will run on any 16.04 flavor?

And thanks for the link, even from a window shopper's POV.

---

### Post by grahammechanical on 2016-04-21
They should run. The snaps are contained and as we can see the installation process installs ubuntu-core. But over the next few days I will test this out.

Regards

---

### Post by grahammechanical on 2016-04-21
Firefox to be snap packaged. I got this from OMGubuntu

[https://blog.mozilla.org/futurereleases/2016/04/21/firefox-default-browser-for-linux-users-ubuntu-new-snap-format-coming-soon/?utm=omgubuntu](https://blog.mozilla.org/futurereleases/2016/04/21/firefox-default-browser-for-linux-users-ubuntu-new-snap-format-coming-soon/?utm=omgubuntu)

[http://www.omgubuntu.co.uk/2016/04/firefox-ubuntu-snap-package](http://www.omgubuntu.co.uk/2016/04/firefox-ubuntu-snap-package)

Regards

---

### Post by DuckHook on 2016-04-21
> **grahammechanical said:**
> Firefox to be snap packaged......hmmm. Will spin up a VM to see how all this new stuff works. Yum!

---

### Post by vasa1 on 2016-04-21
The Mozilla people weren't too clear about the schedule for snap packages. They've got a lot on their plate and an enthusiastic PR team ;)

---

### Post by ventrical on 2016-04-22
Here is more links for reading.

'Snaps for Classic Ubuntu'

[https://insights.ubuntu.com/2016/04/13/snaps-for-classic-ubuntu/](https://insights.ubuntu.com/2016/04/13/snaps-for-classic-ubuntu/)


Fully functional snappy on xenial.

[http://www.linuxinsider.com/story/83395.html](http://www.linuxinsider.com/story/83395.html)

---

### Post by QDR06VV9 on 2016-04-22
> **ventrical said:**
> Here is more links for reading.

'Snaps for Classic Ubuntu'

[https://insights.ubuntu.com/2016/04/13/snaps-for-classic-ubuntu/](https://insights.ubuntu.com/2016/04/13/snaps-for-classic-ubuntu/)


Fully functional snappy on xenial.

[http://www.linuxinsider.com/story/83395.html](http://www.linuxinsider.com/story/83395.html)
Thanks gooood read

This just sounds very interesting to me.
When i get a little free time i am going to give it go.
> More Features Added

Ubuntu 16.04 also includes support for ZFS-on-Linux, a combination volume manager and filesystem that enables efficient snapshots, copy-on-write cloning, continuous integrity checking against data corruption, automatic filesystem repair, and data compression.

Another storage improvement in Ubuntu 16.04 LTS is support for CephFS. This a distributed filesystem that provides an ideal platform for large-scale enterprise storage for cluster computing on open technology.
Plus I was reading last nite that if you plugged another drive in it just gets mounted and ready to use on the fly, unless I misunderstood,
[https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/](https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/)

---

### Post by ventrical on 2016-04-22
> **runrickus said:**
> Thanks gooood read

This just sounds very interesting to me.
When i get a little free time i am going to give it go.

Plus I was reading last nite that if you plugged another drive in it just gets mounted and ready to use on the fly, unless I misunderstood,
[https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/](https://insights.ubuntu.com/2016/02/16/zfs-is-the-fs-for-containers-in-ubuntu-16-04/)

There is also a link where you can install a  ppa  called appindicators or something  for the unity desktop and all the snaps will show up on the top bar.

 All of this sort of caught me by surprise and I have been reading snappy-dev email most everyday.

Surprise!  :)

Regards..

---

### Post by ventrical on 2016-04-22
Here is a recent blog links from the mailing list:

[http://blog.labix.org/2016/04/22/snappy-interfaces](http://blog.labix.org/2016/04/22/snappy-interfaces)

[http://blog.labix.org/2016/04/20/snappy-changes](http://blog.labix.org/2016/04/20/snappy-changes)

---

### Post by mc4man on 2016-05-01
snaps are in ubuntu-software now though it seems  one would need to know their  names to search out.  They continue to install duped libraries which probably should be addressed in some fashion.

---

### Post by ventrical on 2016-05-01
> **mc4man said:**
> snaps are in ubuntu-software now though it seems  one would need to know their  names to search out.  They continue to install duped libraries which probably should be addressed in some fashion.

Can you give us an example please ?


Thanks in advance.

Regards..

---

### Post by mc4man on 2016-05-01
> **ventrical said:**
> Can you give us an example please ?


Thanks in advance.

Regards..
This is on 16.04 (new ubuntu-software in proposed), should be the same as 16.10, new u-s is in main
(- on 16.04 after installing new u-s a reboot seems needed..

A tag of 'nonfree' seems to be par for course on snaps

---

### Post by grahammechanical on 2016-05-01
Some but not all of the snaps presently listed by "snap find" show up in Ubuntu Software. And it is not always indicated that they are snap packages. If an application does what a user wants is really necessary that user know whether it is deb or snap packaged? I don't think so.

Any evidence that snaps remove cleanly & completely?

Regards

---

### Post by mc4man on 2016-05-01
> **grahammechanical said:**
> Some but not all of the snaps presently listed by "snap find" show up in Ubuntu Software. And it is not always indicated that they are snap packages. If an application does what a user wants is really necessary that user know whether it is deb or snap packaged? I don't think so.

Any evidence that snaps remove cleanly & completely?

Regards
So far all found snaps with u-s have the nonfree tag & no repo app gets that tag.
They remove just fine thru u-s

---

### Post by ventrical on 2016-05-01
> **mc4man said:**
> This is on 16.04 (new ubuntu-software in proposed), should be the same as 16.10, new u-s is in main
(- on 16.04 after installing new u-s a reboot seems needed..

A tag of 'nonfree' seems to be par for course on snaps

I installed the Clock app for unity7 using snap install. So these are 'nonfree apps'?  I wonder if my ISP will req a service charge as a 'hidden service' charge. But then that's being paranoid I think :)

Was someone going to say something about the dream police :) jk

regards..

---

### Post by mc4man on 2016-05-01
> **ventrical said:**
> I installed the Clock app for unity7 using snap install. So these are 'nonfree apps'?  I wonder if my ISP will req a service charge as a 'hidden service' charge. But then that's being paranoid I think :)

Was someone going to say something about the dream police :) jk

regards..
I  wouldn't say that, It appears to be a generic 'catchall' that the snap *may* contain nonfree.  I guess there is currently no way for U-s to devine this info itself & the snap isn't providing that info either

---

### Post by grahammechanical on 2016-05-02
I first installed Gnome Software from the PPA. Back then the only stuff in the catalogue was the system utilities that were already installed and all of them were marked as "non-free" even Gnome utilities. Speaking out of my ignorance, the only way that Gnome Software can know that a package contains Free Software is by peeking into the package archive and seeing a reference to a Free Software licence. Perhaps, Gnome Software needs to be educated about snap packages.

I wonder if Gnome Software knows the difference between Free Software licensing and Free & Open Source software licensing? :) Some people have argued over such differences.

I wonder if users will understand that "non-free" does not mean "it is yours for a price." Things are going to get complicated when Ubuntu Software starts offering paid for apps.

Regards

---

### Post by ventrical on 2016-05-02
> **mc4man said:**
> I  wouldn't say that, It appears to be a generic 'catchall' that the snap *may* contain nonfree.  I guess there is currently no way for U-s to devine this info itself & the snap isn't providing that info either

I think I recall the same with wiley w.  Said it was a paid app. Actually the ones in the software center were/are diminished versions with the option of paying for the full app.  This is shareware. Came out about the late 80's early 90's. Download  working version with many tools missing and option to buy. 90 days trials .. etc..

 My opinion of those programs were mostly  in the crapware area. I hope were are not taking a back-step here.

regards..

---

