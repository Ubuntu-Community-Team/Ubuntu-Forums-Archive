---
title: "Is &quot;Remove unused programs&quot; a good rule of thumb?"
date: 2012-12-18
forum: Security
---

### Post by tartalo on 2012-12-18
I've always had the intuition that removing unnecessary software was a good thing to do from a security point of view. (Except things like Apparmor, of course)

So I was surprised today when I came across this tip for beginners:

[https://sites.google.com/site/easylinuxtipsproject/fatalmistakes](https://sites.google.com/site/easylinuxtipsproject/fatalmistakes)

> Never remove any application that's part of the default installation of Ubuntu
9. Even when you never use a particular default application: don't remove it. Reason: the default installation is an intertwined system that's dependent on shared supporting files, which makes the operating system run stable.

When you remove a default application, you run a risk of seriously damaging the system. With some default applications this risk is bigger than with others, and with some there's no risk at all. But it's best to avoid this risk altogether.

So, what do you think? Is removing unused software a good rule of thumb, or is it an overkill?

And if you think that removing unused software is good, what would you remove first from a default Ubuntu installation?

---

### Post by tgalati4 on 2012-12-18
That's generally good advice.  There's not much of a security risk of having extra packages installed.  The only security risk is from what is actually running.

If you remove a package that is a critical part of Ubuntu, then you will break things. (But you get to keep both pieces.)

A good way to see a package's dependencies:


tgalati4@tpad-Gloria7 ~/Desktop $ apt-cache depends xserver-xorg
xserver-xorg
  Depends: xserver-xorg-core
 |Depends: xserver-xorg-video-all
  Depends: <xserver-xorg-video-5>
    virtualbox-ose-guest-utils
    xserver-xorg-video-ivtv
    nvidia-glx-173
    nvidia-glx-180
    nvidia-glx-71
    nvidia-glx-96
    xserver-xorg-video-apm
    xserver-xorg-video-ark
    xserver-xorg-video-chips
    xserver-xorg-video-cirrus
    xserver-xorg-video-dummy
    xserver-xorg-video-fbdev
    xserver-xorg-video-geode
    xserver-xorg-video-glint
    xserver-xorg-video-i128
    xserver-xorg-video-i740
    xserver-xorg-video-intel
    xserver-xorg-video-mach64
    xserver-xorg-video-mga
    xserver-xorg-video-neomagic
    xserver-xorg-video-nouveau
    xserver-xorg-video-nv
    xserver-xorg-video-openchrome
    xserver-xorg-video-r128
    xserver-xorg-video-radeon
    xserver-xorg-video-radeonhd
    xserver-xorg-video-rendition
    xserver-xorg-video-s3
    xserver-xorg-video-s3virge
    xserver-xorg-video-savage
    xserver-xorg-video-siliconmotion
    xserver-xorg-video-sis
    xserver-xorg-video-sisusb
    xserver-xorg-video-tdfx
    xserver-xorg-video-trident
    xserver-xorg-video-tseng
    xserver-xorg-video-v4l
    xserver-xorg-video-vesa
    xserver-xorg-video-vmware
    xserver-xorg-video-voodoo
 |Depends: xserver-xorg-input-all
  Depends: <xserver-xorg-input-4>
    virtualbox-ose-guest-utils
    xserver-xorg-input-acecad
    xserver-xorg-input-aiptek
    xserver-xorg-input-elographics
    xserver-xorg-input-evdev
    xserver-xorg-input-evtouch
    xserver-xorg-input-fpit
    xserver-xorg-input-joystick
    xserver-xorg-input-kbd
    xserver-xorg-input-mouse
    xserver-xorg-input-mutouch
    xserver-xorg-input-penmount
    xserver-xorg-input-synaptics
    xserver-xorg-input-tslib
    xserver-xorg-input-vmmouse
    xserver-xorg-input-void
    xserver-xorg-input-wacom
  Depends: xserver-xorg-input-evdev
  Depends: hal
  Depends: libc6
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Depends: xkb-data
  Depends: x11-xkb-utils
  Recommends: libgl1-mesa-dri
  Recommends: udev
  Conflicts: x11-common
  Conflicts: xserver-common
  Conflicts: <xserver-xfree86>
  Replaces: x11-common
  Replaces: xserver-common

(Hint:  Don't mess with anything to do with xserver!)

Another no-no is to remove languages.  Yes, you can save space, but you will surely break things that require multilanguage support.

---

### Post by mikewhatever on 2012-12-19
I think not removing application is a good rule of thumb. If one knows what to remove, it's not a problem. 
What advantage do you try to get security wise, and what do you remove, for example?

---

### Post by Hungry Man on 2012-12-19
Well, it depends.

If the package just contains a bunch of text files or icon packs it's no real risk, it doesn't take in data, it probably doesn't even run any processes.

But if it's a running service, such as cups-d, you should absolutely remove it if you have no need for it. Cupsd is a great example of attack surface that is locally accessible (assuming you're behind NAT) and unnecessary for many users.

Reducing attack surface is always good, but some is more important than others. If code isn't running and an attacker can't get it to run, it's not as important. If code isn't running but an attacker can force it to launch (like dropping a .py file and exploit python vulnerabilities), that's more important. And if the code is always running and even internet facing that's critical.

---

### Post by oldos2er on 2012-12-19
> **tartalo said:**
> So, what do you think? Is removing unused software a good rule of thumb, or is it an overkill?

I think the warning you quoted is somewhat overblown. I routinely remove a few applications after a fresh install that I know I will never want, e.g. kmail is the first one that springs to mind. In the past when I ran Gnome 2.x I would remove Evolution, all but one package that wanted to take some important dependencies with it, evolution-data-server-common. I have no idea how this would work on Unity or Gnome 3.x. I think as long as one pays attention to dependencies, removing packages isn't that big of a deal, but it does require some knowledge and experience to aid one's judgment.

---

### Post by snowpine on 2012-12-19
A beginner should not remove packages willy-nilly in my opinion. I see that rookie mistake a lot on these forums. But if you know what you are doing (having a strong understanding of APT) then go for it---you'll get a few more mb free space on your hard drive (but I doubt any serious security benefits). For example I don't smoke, but removing the cigarette lighter from my car probably won't make the car faster, safer, or more fuel efficient. Easiest just to ignore the unnecessary feature in my philosophy. ;)

If you are interested in Ubuntu security topics then a far better use of your time is to read here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by thnewguy on 2012-12-20
For a beginner, I would say leave the packages in place. Someone without much experience with Linux is far more likely to damage their operating system removing pieces than an attacker exploiting installed packages.

Once a person has a bit more experience and knows what is essential and what is not, then I think removing packages is a good idea.

---

