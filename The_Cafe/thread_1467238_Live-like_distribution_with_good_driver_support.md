---
title: "Live-like distribution with good driver support"
date: 2010-04-30
forum: The Cafe
---

### Post by adam.ec on 2010-04-30
I used to understand a lot about Linux distributions... when there was a handful of them. Suse was used in the office, Red Hat or Debian was your server distro (or Slack if you had a decent quality geek in your IT dept) and Knoppix was THE live-distibution.

I've just found myself popping a distro onto a USB hard drive, mainly for accessing a data partition on the same drive from anywhere with the tools I use daily. The distro needs to have good driver support and just load up whichever drivers are needed into whichever system the drive is plugged into, kinda like a Knoppix livecd. Thing is, I would also like an easy-to-use packaging system to install whatever software I need as well as system recovery and analysis tools could come in useful. Speed isn't necessarily an issue, flexibility is much more important but I would like to be able to run the distro on a variety of different systems (some 5/6 years old).

So what would you recommend? What is the new 'Knoppix' distro or is Knoppix still king as far as drivers are concerned? Does synaptics run on the Ubuntu LiveCD or do you have to install applications in a special way? Lastly, do i need a live-type install or will full install distros just load in whatever drivers are needed for a specific system anyway?

Thanks for your input.

---

### Post by snowpine on 2010-04-30
Ubuntu would be my suggestion. :) System->Administration->USB Startup Creator.

---

### Post by adam.ec on 2010-04-30
> **snowpine said:**
> Ubuntu would be my suggestion. :) System->Administration->USB Startup Creator.
And this would create a live-like system on a USB hard drive? Will Synaptics also work like it does on an ordinary system, and does it save settings properly (like network for instance)?

Thanks for the quick response by the way.

---

### Post by snowpine on 2010-04-30
Yes, Synaptic Package Manager should work fine. If you choose Persistent it will remember applications you install, settings you tweak, and documents you create; if you choose Non-Persistent it will be just like a Live CD and all changes will be lost when you power down.

---

### Post by adam.ec on 2010-04-30
Thanks Snowpine, Ubuntu is the guy then. Looks like nobody else is offering any competition this afternoon either.

---

### Post by snowpine on 2010-04-30
Well, there are other distributions that have this capability too. But since you are already familiar with ubuntu, it is my recommendation. :)

By the way, here is a great site on this very topic: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

(note: some of their tutorials are outdated now that Ubuntu has such an excellent usb-creator application built in)

---

### Post by cariboo on 2010-04-30
The USB Startup Creator only works for Ubuntu iso's if you want put any other distro on a usb thumb drive, use unetbootin, it is in the repositories.

---

### Post by jerenept on 2010-04-30
You _MUST_ have a usb drive with at least about 700 MB free space.
If there is enough space, USB Startup Creator will offer you the option: "When starting up from this disk, documents and settings will be-
1)**Stored in reserved extra space** and a slider showing how much space will be reserved. Set this to a decent amount, based on personal preference.
!!The reserved space is unavailable for use when not in Live System!!!
The Synaptic Package Manager should work perfectly on a live USB
The USB Startup Creator uses the *Ubuntu CD, or the .iso file (click "other" and browse to the iso file.

---

