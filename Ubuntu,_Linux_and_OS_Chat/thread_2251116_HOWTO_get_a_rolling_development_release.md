---
title: "HOWTO get a rolling development release?"
date: 2014-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by amjjawad on 2014-11-02
Hi,

There was a discussing between myself and one of the developers within Ubuntu Community.
We were talking about [this post]("http://ubuntugnome.org/to-upgrade-or-not-to-upgrade/").

Then IIRC, I think we talked about:

> just edit /etc/apt/sources.list and replace 'utopic' with  'devel'

and

> by setting 'devel', apt always tracks the development release no need to  edit sources.list every cycle or run do-release-upgrade etc.

My question here is: have you tired this? if yes, did it work or not?

I have problems with my Oracle VirtualBox (always small screen even after installing the extensions) and I have moved to different place and I just have one machine at the moment .. all my testing machines are not yet here. Until I manage to do it myself, I was wondering if someone has done it before?

Why I need that?
[http://torios.org/](http://torios.org/) - we are working on an LTS release but at the most recent weekly team meeting, we were discussing the ability to have two versions: LTS stable and a rolling release.

Also, because I am a leader of Ubuntu GNOME, that would save my time whenever I want to test :)

Thanks a lot in advance!

---

### Post by sudodus on 2014-11-02
Some systems get 'a small screen' in VirtualBox:

Maybe you have the following problem and can use the following solution

The screen size is limited to 640x480 unless I activate

```
GRUB_TERMINAL=console
```

in **/etc/default/grub** and run

```
 sudo update-grub
```

---

### Post by Bucky Ball on 2014-11-02
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by craig10x on 2014-11-02
Development is not ubuntu's rolling release in the sense that it is geared for TESTERS not the general ubuntu population who need stability and don't want to be concerned about possible breakages...

The general ubuntu population rolling style release will likely come once convergence takes places which will be when unity 8 desktop becomes the default (possibly by 15.10 and definitely by 16.04).
That is when the 6 month version will likely be morphing into it...read this article and especially the paragraph about why unity 8 desktop is so special:
[http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml](http://news.softpedia.com/news/Canonical-Details-Plans-for-Unity-8-Integration-in-Ubuntu-Desktop-462117.shtml)

As far as how it affects the other versions of ubuntu, i am not sure how that applies to them but certainly is worth discussing with the developers about...

---

### Post by kc1di on 2014-11-02
There is not Ubuntu rolling release at this time, the Developemnet repositories are not stable.

---

### Post by grahammechanical on 2014-11-02
> [COLOR=#000000]My question here is: have you tired this? if yes, did it work or not?[/COLOR]

It works. I have two installs of Ubuntu Desktop Next. One updates from the standard Ubuntu vivid archives. The other updates from the devel archive. There will be errors because not all of the repositories are open. This is normal when running any development release. For example, backports is not open. How can it be when the version has not been released yet. The Extras repository is not open either. That will open later on in the cycle. But those repositories is in the sources list so they throw up an error.

With devel you will see messages that apt-get update was expecting devel but got vivid instead. Again it is due to certain repositories not being open in devel. This does not prevent updating/upgrading.

I was running an install of saucy on the devel repositories and it moved from saucy on to trusty without any problems. Keep in mind that the Ubuntu developers see devel as being an update channel for Ubuntu for Devices. But that devel channel is prefixed with "ubuntu-touch." Do not use that prefix.

[http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/](http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/)

Try an experiment. Put in a fresh install of Ubuntu Gnome Vivid and run this command

```
sudo sed -i 's/vivid/devel/g' /etc/apt/sources.list
```

Then run update/upgrade as normal and see if you are getting all the updates that Ubuntu Gnome should be getting. Both those from Ubuntu and those from Ubuntu Gnome.

Regards.

UPDATE: I have an updated install of Ubuntu Gnome 14.10. I have just changed the repositories from utopic to devel and update/upgrade brings in 107 MB of updates and this install of Ubuntu Gnome is now

> graham@sda11-UGnome:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Vivid Vervet (development branch)
Release:    15.04
Codename:    vivid


Details still has the Ubuntu 14.10 logo but lists the Base system as: Ubuntu Vivid Vervet (Development Branch) 64-Bit

Does that answer your question?

---

### Post by amjjawad on 2014-11-07
> **grahammechanical said:**
> It works. I have two installs of Ubuntu Desktop Next. One updates from the standard Ubuntu vivid archives. The other updates from the devel archive. There will be errors because not all of the repositories are open. This is normal when running any development release. For example, backports is not open. How can it be when the version has not been released yet. The Extras repository is not open either. That will open later on in the cycle. But those repositories is in the sources list so they throw up an error.

With devel you will see messages that apt-get update was expecting devel but got vivid instead. Again it is due to certain repositories not being open in devel. This does not prevent updating/upgrading.

I was running an install of saucy on the devel repositories and it moved from saucy on to trusty without any problems. Keep in mind that the Ubuntu developers see devel as being an update channel for Ubuntu for Devices. But that devel channel is prefixed with "ubuntu-touch." Do not use that prefix.

[http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/](http://developer.ubuntu.com/start/ubuntu-for-devices/image-channels/)

Try an experiment. Put in a fresh install of Ubuntu Gnome Vivid and run this command

```
sudo sed -i 's/vivid/devel/g' /etc/apt/sources.list
```

Then run update/upgrade as normal and see if you are getting all the updates that Ubuntu Gnome should be getting. Both those from Ubuntu and those from Ubuntu Gnome.

Regards.

UPDATE: I have an updated install of Ubuntu Gnome 14.10. I have just changed the repositories from utopic to devel and update/upgrade brings in 107 MB of updates and this install of Ubuntu Gnome is now



Details still has the Ubuntu 14.10 logo but lists the Base system as: Ubuntu Vivid Vervet (Development Branch) 64-Bit

Does that answer your question?

Hi and thanks a million for the detailed answer. Indeed, this is what I was looking for. While I was reading your post, I have done it on one of my virtual machines and

```
sudo apt-get dist-upgrade
```

is installing now ...

I need to keep doing some tests until I find or get what I need .. we are on the right track, thanks to you :)

I will try that experiment hopefully later. I found an old virtual machine that I don't use any more and edited the sources list and it just worked :D

---

### Post by amjjawad on 2014-11-07
> **sudodus said:**
> Some systems get 'a small screen' in VirtualBox:

Maybe you have the following problem and can use the following solution

The screen size is limited to 640x480 unless I activate

```
GRUB_TERMINAL=console
```

in **/etc/default/grub** and run

```
 sudo update-grub
```

Hi and thanks for your post.

Edit:
You're right, it is working now with bigger screen :D

---

### Post by amjjawad on 2014-11-27
Hi,

I posted on Ubuntu GNOME Mailing List and the Social Media Channels about the idea and people were excited about that so I wrote this:

[http://ubuntugnome.org/howto-run-ubuntu-gnome-as-a-rolling-release/](http://ubuntugnome.org/howto-run-ubuntu-gnome-as-a-rolling-release/)

---

### Post by Elfy on 2014-11-28
Thread title edited to reflect the reality of the situation ;)

---

### Post by mikodo on 2014-11-29
That post about using /etc/sources.list with devel and the other postings, make this look like fun to play with.

I wish there were more hours in a day.

---

### Post by grahammechanical on 2014-11-29
As regards the stability of the development release, I have been using the development release as a daily driver for more than 2 years. It is now so stable as to be boring. Mind you. I keep my data on a separate partition just in case I need to re-install. And I always have an LTS release installed that I can use as a fall back OS just in case something does break. In this way I can continue with my personal projects until the broken development branch gets fixed.

Regards.

---

