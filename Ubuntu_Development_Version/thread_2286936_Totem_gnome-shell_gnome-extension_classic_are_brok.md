---
title: "Totem: gnome-shell: gnome-extension classic are broken in 14.04.3"
date: 2015-07-15
forum: Ubuntu Development Version
---

### Post by mc4man on 2015-07-15
Why? - because libwayland-egl1-mesa-lts-vivid has been left out of the image
(is anybody minding the Desktop store anymore??
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1475038](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1475038)

---

### Post by mc4man on 2015-07-25
Also breaks gnome-shell & gnome-shell extensions. 
Don't get the hang up here, maybe it's too cloudy & snappy to see the Desktop?

---

### Post by dino99 on 2015-07-26
> **mc4man said:**
> Also breaks gnome-shell & gnome-shell extensions. 
Don't get the hang up here, maybe it's too cloudy & snappy to see the Desktop?

That is the sad reality since a year at least:
- devs seem to be all working on the 'next' projects
- mainly U & U+1 are well maintained, but the older releases are quite ignored (and the LTS is one of them)
- with the old releases, using the 'backported packages' is too often a nightmare: incomplete backport, cross dependencies not satisfied, and so on

Canonical have lot of projects, but not the required teams to support them all, resulting in their own image being destroyed. Lot of users have migrated either on Debian or Fedora/Arch and the others. Even the community is complaining about the lack of new coming leaders.

---

### Post by kansasnoob on 2015-07-26
I just tried the Ubuntu Trusty daily image and ubiquity fails to launch either from the live desktop, or from the advanced boot menu, or from the standard boot menu. And when I try to file a bug using ubuntu-bug ubiquity it says ubiquity is not an official ubuntu package.

I'm guessing that for 14.04.3 we've reverted to the fork & spoon method of OS installation :lolflag:

Actually iso-testing for 14.04.3 should start about 8 days from now so they'll catch this on the Jenkins - I hope.

I wanted to see if they remembered to turn off the proposed updates this time because 14.04.2 was delayed because trusty-proposed had to be turned off at the last minute and quite a few of the proposed updates had to be reverted because they hadn't passed the SRU process.

---

### Post by mc4man on 2015-07-26
The issue here may be that in vivid libegl1-mesa-drivers is a dummy transitional package. So there is no libegl1-mesa-drivers-lts-vivid package so nothing to pull in libwayland-egl1-mesa-lts-vivid which does exist. 
The sources needing this have already been built (totem, gnome-shell, ect.) so they 'expect' (ldd)   libwayland-egl1-mesa or in this case it's lts replacement.

So in 14.04.3 these sources cannot be (re)built as the deps are not satisfiable - eg. - 
libcogl15 : Depends: libegl1-mesa-drivers

Bit of a mess though as far as runtime installing   libwayland-egl1-mesa-lts-vivid or manually seeding it to the image would work..

Edit: some overly redundant bug reporting, don't care...(if you throw enough ...
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1478419](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1478419)
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1478420](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1478420)

---

### Post by mc4man on 2015-07-26
> **kansasnoob said:**
> I just tried the Ubuntu Trusty daily image and ubiquity fails to launch either from the live desktop, or from the advanced boot menu, or from the standard boot menu. And when I try to file a bug using ubuntu-bug ubiquity it says ubiquity is not an official ubuntu package.

I'm guessing that for 14.04.3 we've reverted to the fork & spoon method of OS installation :lolflag:

Actually iso-testing for 14.04.3 should start about 8 days from now so they'll catch this on the Jenkins - I hope.

I wanted to see if they remembered to turn off the proposed updates this time because 14.04.2 was delayed because trusty-proposed had to be turned off at the last minute and quite a few of the proposed updates had to be reverted because they hadn't passed the SRU process.

The images seem to be hit or miss as to whether they are boot-able to anything usable (busybox or whatever.
Thurs. image worked here though took 2 boot up tries...

---

