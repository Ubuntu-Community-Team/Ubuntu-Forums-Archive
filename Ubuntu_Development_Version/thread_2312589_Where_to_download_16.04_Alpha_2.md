---
title: "Where to download 16.04 Alpha 2?"
date: 2016-02-05
forum: Ubuntu Development Version
---

### Post by PsychedelicWonders on 2016-02-05
I want to download Ubuntu 16.04 Alpha 2 and was given this link:

[http://www.omgubuntu.co.uk/2016/01/ubuntu-16-04-alpha-2-released-available-download](http://www.omgubuntu.co.uk/2016/01/ubuntu-16-04-alpha-2-released-available-download)

[COLOR=#000000]But am I blind? I don't see a link to download Ubuntu 16.04 Alpha 2?[/COLOR]

[COLOR=#000000]I only see Ubuntu Mate, Kylin & Lubuntu, but not just the regular Ubuntu 16.04 A2?

Does anyone have a link to a good download?


[/COLOR]

---

### Post by oldfred on 2016-02-05
Ubuntu does not have alphas, just daily updates.
 Daily builds
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Then you can use zsync to update your daily ISO so you do not download full ISO each day.
 I have my ISO in a separate folder. Run zync from location of ISO.

```
cd /ISO
zsync [http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync)
```

Forum shortens http entries, so one above is not shown on screen correctly. It should be one line with full zsync & http: entry without ... in midde.

---

### Post by PaulW2U on 2016-02-05
> **PsychedelicWonders said:**
> I only see Ubuntu Mate, Kylin & Lubuntu, but not just the regular Ubuntu 16.04 A2?
There was no alpha 2 release of Ubuntu. Only three flavours participated in the release and those were the three that you quoted.  :)
A misleading headline. Ubuntu now only participates in the second beta release.

The release schedule for Ubuntu is [here]("https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule").

if you want to test the the latest daily build of the Ubuntu ISO then you can find that at [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

Edit: Beaten to it by oldfred. :)

For the flavours that released an alpha 2 the build is now a week old. There have been many updates since then so testing the daily build is the way to go whether an alpha was released or not.

---

### Post by PsychedelicWonders on 2016-02-05
> **oldfred said:**
> Ubuntu does not have alphas, just daily updates.
 Daily builds
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Then you can use zsync to update your daily ISO so you do not download full ISO each day.
 I have my ISO in a separate folder. Run zync from location of ISO.

```
cd /ISO
zsync [http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync)
```

Forum shortens http entries, so one above is not shown on screen correctly. It should be one line with full zsync & http: entry without ... in midde.

It's been years since I've been on Ubuntu, so I'm extremely rusty, so please bare with me.

I still need to download the iso for initial installation on a USB, then once I do that I want to keep a copy of it on the desktop so I can update it daily via zsync?  

I'm completely lost with your last sentence about the forum shortening http entries and I need to get the one without the entry in the middle?

> **PaulW2U said:**
> There was no alpha 2 release of Ubuntu. Only three flavours participated in the release and those were the three that you quoted.  :)
A misleading headline. Ubuntu now only participates in the second beta release.

The release schedule for Ubuntu is [here]("https://wiki.ubuntu.com/XenialXerus/ReleaseSchedule").

if you want to test the the latest daily build of the Ubuntu ISO then you can find that at [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

Since it's been so long since I've been on Ubuntu and I need 16.04 because my new EVGA 970 video card & Dell u3415w monitor have too new of drivers for 14.04

Would I be better off with trying out Ubuntu Mate or do you still suggest to go with the daily update of regular ubuntu?

---

### Post by PsychedelicWonders on 2016-02-06
> **oldfred said:**
> 

```
cd /ISO
zsync [http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync)
```

So wait, I want to download and use this iso file?  It's only 2.8mb while the file from this link is 1.4gb:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

So which one do I want to use?  The bigger file right?

---

### Post by mikewhatever on 2016-02-06
If you just want to download an ISO once, then get a 1.4GB file. zsync is for updating a downloaded ISO, however, if it does not find one, it will just download the whole 1.4GB thing. Either way, you end up with a 1.4GB ISO file.

---

### Post by oldfred on 2016-02-06
The zsync is to create a new ISO without redownloading the entire ISO.
But you really only need that if you want to re-install.
But it also does a verify, so md5sum check not required separately. 

If only installing once, you can just run updates from the install.
But I reinstall, so I can also see how that changes, and test may own after install scripts that reconfigure my system quickly. 

I also will reinstall once it is released as the dailies have so many changes and log files that a new install will house clean out all that cruft.

If using Firefox you can move cursor over one of the shortened links, and see full link at bottom of screen. Added extra space so it does not shorten this, but you must remove space to be correct.
zsync [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) current/xenial-desktop-amd64.iso.zsync

---

### Post by zika on 2016-02-06
[http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync)
I think it will not shorten it if You use proper tag...
It will, even though it did not in preview. Mea culpa.
```
http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync
```
Code-tag is OK... ;)

**&#8203;**http://cdimage.ubuntu.com/daily-live/current/xenial-desktop-amd64.iso.zsync
If You untick „Automatically parse links in text“ it seems OK also.

Erasing this post of mine is totally OK with me... ;)

---

### Post by oldfred on 2016-02-06
Thanks zika.
I did use code tags in first post and it still shortened. 
I do not normally use forum's advanced editor so have not even learned all the extra functions it has.
It must be removing the parse links in text that works.

---

### Post by grahammechanical on 2016-02-06
When we install any Ubuntu ISO image we have an option to download & install updates at the same time. So, even if a daily ISO image is a few days old, or older, a new installation from it will be up to date. Especially if we run the Update Manager after installation. After all, with a daily image of the development release there are always updates available every day.

With a released Ubuntu ISO image we still have to install updates as we install or run Update Manager after installation. The released ISO will become out of date in time. The 15.10 ISO image has not been rebuilt since released day. And it will not be.

Milestones such as Alpha 2; Alpha1; Beta2; Beta1 and Release Candidate are really daily built images with a label. Ubuntu does not label certain daily build images as Alpha or Beta any more but some of the flavours of Ubuntu still do. With Ubuntu we download the current daily image. We can do the same with the images of the flavours.

If we want to test the daily images for the purpose of reporting bugs, we may also want to avoid downloading the full ISO image every day. And that is when we use zsync. That utility compares the ISO image we have on the hard disk with the latest daily image and calculates the differences and it is only the code differences that are downloaded. It saves time and data download and we end up with the latest daily image.

Run zsync without having an older version of the daily image present and the full ISO image is downloaded.

Regards.

---

### Post by este.el.paz on 2016-02-06
> **PsychedelicWonders said:**
> It's been years since I've been on Ubuntu, so I'm extremely rusty, so please bare with me.


Would I be better off with trying out Ubuntu Mate or do you still suggest to go with the daily update of regular ubuntu?

@PW:

I just did an install of U-MATE 16.04PPC a week ago, after zsyncing prior daily's a few times until it was able to properly boot up I got one that worked . . . .  I have liked the MATE DE for quite awhile in my LM installs . . . according to them it's based on the "popular GNOME2 desktop" . . . .  MATE does show an "alpha 1 & 2" release . . . possibly you have to get it from the daily . . . try it.

e...

---

### Post by PsychedelicWonders on 2016-02-06
> **grahammechanical said:**
> When we install any Ubuntu ISO image we have an option to download & install updates at the same time. So, even if a daily ISO image is a few days old, or older, a new installation from it will be up to date. Especially if we run the Update Manager after installation. After all, with a daily image of the development release there are always updates available every day.

With a released Ubuntu ISO image we still have to install updates as we install or run Update Manager after installation. The released ISO will become out of date in time. The 15.10 ISO image has not been rebuilt since released day. And it will not be.

Milestones such as Alpha 2; Alpha1; Beta2; Beta1 and Release Candidate are really daily built images with a label. Ubuntu does not label certain daily build images as Alpha or Beta any more but some of the flavours of Ubuntu still do. With Ubuntu we download the current daily image. We can do the same with the images of the flavours.

If we want to test the daily images for the purpose of reporting bugs, we may also want to avoid downloading the full ISO image every day. And that is when we use zsync. That utility compares the ISO image we have on the hard disk with the latest daily image and calculates the differences and it is only the code differences that are downloaded. It saves time and data download and we end up with the latest daily image.

Run zsync without having an older version of the daily image present and the full ISO image is downloaded.

Regards.

Ok so I installed the full iso image onto my SSD and everything seems to be running just fine.

GREAT to finally be back on Ubuntu and away from Windows!!!

Now that I have the main iso image installed onto my SSD, how do I setup the zsync so it updates the files daily and keeps me running smoothly?

---

### Post by cariboo on 2016-02-06
Check out the zsync howto[ here]("https://help.ubuntu.com/community/ZsyncCdImage")

---

### Post by este.el.paz on 2016-02-06
> **PsychedelicWonders said:**
> Ok so I installed the full iso image onto my SSD and everything seems to be running just fine.

GREAT to finally be back on Ubuntu and away from Windows!!!

Now that I have the main iso image installed onto my SSD, how do I setup the zsync so it updates the files daily and keeps me running smoothly?

@PW:

Now that you are done with installing the system there is no need for zsync . . . until the next system cycle upgrade or some other flavor that you would want to burn to DVD or flashdrive.  If you are testing out some other system via liveDVD, then you want zsync . . . otherwise for the already installed system, use the Terminal for regular upgrades . . . via "apt-get" . . . or use the GUI "Software Updater" . . . .  You can use SU to move up to the next LTS whenever it would be ready . . . that would be 18.04 LTS . . . start zsyncing 18.04 now get ahead of the other guys . . . .  : - )))))

e.....

---

