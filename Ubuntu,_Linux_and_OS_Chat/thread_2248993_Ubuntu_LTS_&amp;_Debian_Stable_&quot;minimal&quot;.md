---
title: "Ubuntu LTS &amp; Debian Stable &quot;minimal&quot; with Xfce or Full Desktop.iso's. Which?"
date: 2014-10-18
forum: Ubuntu, Linux and OS Chat
---

### Post by mikodo on 2014-10-18
Hi,

I know the question is subjective, as each person's hardware & set up of apps and libraries vary. My system, can handle pretty much any desktops and apps.

I have asked before but, I am again trying to decide, which to do. I have done the minimal installs with Ubuntu & Xfce and Debian & Xfce, and compared them with multiboot Xubuntu, and really didn't see much difference. But, I was pulling in Kde and Gnome libraries and dependencies willy-nilly. I want to keep the next installs of Ubuntu LTS and Debian Stable, pretty much just Xfce and ([Xfce extras, like this]("http://goodies.xfce.org/")). I will try to stay away from other libraires like Kde & Gnome.  I am trying to simplify my installs, to be as least diverse & complicated. 

So, you know what I want to do. 

W**hat can you tell me from experience, that can help me decide. I am interested in opinions.**

Not really as minimal with minimal kernels and such, but something like this:

[Ubuntu]("https://help.ubuntu.com/community/Installation/MinimalCD")

[Debian]("https://www.debian.org/CD/netinst/")

[&&]("https://wiki.debian.org/Xfce#How_to_install_Xfce")

Or, just be lazy and:

[Xubuntu]("http://xubuntu.org/getxubuntu/")

[Debian live-7.6.0-amd64-xfce-desktop]("http://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/")

Thank you.

---

### Post by ian-weisser on 2014-10-18
I don't understand the question.
It's all free, there is not single right answer, and you seem to want to experiment.

Try a few different setups, and recommend a best solution to us.

I've done Xubuntu. I've done XFCE. I've done Debian. I've done Ubuntu. I've done them from Minimal. I've done the full-blown xubuntu-desktop install.
They're all fine. I found the differences to be mostly cosmetic and minor - a package or two, different wallpapers, font settings, plugin choices. Easy to change and customize. Nothinq worth writing home about - the packagers did a great job.

---

### Post by mikodo on 2014-10-18
> **ian-weisser said:**
> 

<snip>

They're all fine. I found the differences to be mostly cosmetic and minor - a package or two, desktop images, font settings, plugin choices. Easy to change and customize. Nothinq worth writing home about - the packagers did a great job.

Thank you.

While waiting for a response and watching NHL on TV, I've had time to reflect. And now this response, quoted.

As an old-guy casual user, who is trying to simplify things going into the future I think, if no one gives me a compelling reason for the minimal installs, (I have seen respected people advocating them), I will just install the full .iso's. I can't really go wrong doing that. Experience has shown, I can screw things up when playing with my installs so, it is probably best, I let the packagers attend to them.

---

### Post by ibjsb4 on 2014-10-18
I find that package count is only a reference point and seems to have little to do with performance.  Example (I'm a gnome guy):

MY main build (12.04), a build that I have been running for a few years uses startx and metacity.  I have managed to keep the package count to a little less than 1300.  Its fast, but Mate with a package count of 2300+ is a little faster than my build and Bodhi linux is a little faster than both.

Another example:
Using startx and xserver.xorg adds up to be about 120M, where installing lightdm is 300+M.  You would think that boot time would be faster, but its really hard to tell the difference between the two.

Whats the best way to go?  I don't know as I will probably spend the rest of my days looking for it :)

---

### Post by mikodo on 2014-10-18
ibjsb4,

You made me laugh!

---

### Post by mips on 2014-10-19
I find net/base installs withe minimal xfce lighter/faster. Just compare all the packages between say xubuntu and your install.

---

