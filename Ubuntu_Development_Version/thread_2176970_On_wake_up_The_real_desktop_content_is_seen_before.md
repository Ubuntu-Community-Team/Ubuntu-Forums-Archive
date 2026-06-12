---
title: "On wake up: The real desktop content is seen before lock screen"
date: 2013-09-26
forum: Ubuntu Development Version
---

### Post by sacridex on 2013-09-26
Hi,

well the title says it all.
When I open up my laptop lid, I can see my desktop for a very short moment before the lockscreen overlays it.
That's kinda unnice, if you have some delicate stuff there. :S

---

### Post by cariboo on 2013-09-26
I saw the same thing earlier, when waking Lubuntu after it being in sleep mode for a couple of weeks. I don't see it on Ubuntu though.

---

### Post by Toz on 2013-09-26
Xubuntu/Xscreensaver bug report [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1229486").

---

### Post by sacridex on 2013-09-27
I'm using regular Ubuntu with Unity.
Xfce is not installed.

---

### Post by tgalati4 on 2013-09-27
There are some settings in the sleep/resume scripts to reload the video drivers after coming out of sleep--that will normally clear the video screen, but it will take longer to come out of sleep.  You will have to search for them, because I'm not running Unity, so I'm not sure where they are located.

```
cat /etc/default/acpi-support
```

---

### Post by Elfy on 2013-09-28
> **sacridex said:**
> I'm using regular Ubuntu with Unity.
Xfce is not installed.

Then perhaps the bug is more generic, assume it was you that posted to the bug report.

---

### Post by Toz on 2013-09-28
> **Toz said:**
> Xubuntu/Xscreensaver bug report [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1229486").

> **sacridex said:**
> I'm using regular Ubuntu with Unity.
Xfce is not installed.

As it turned out in my case, pm-utils was not installed by default on the latest beta of Xubuntu 13.10. After installing it (pm-utils), the issue as I was experiencing it, was resolved. Note: pm-utils will now be added as a dependency to xubuntu-meta so that it is installed by default. 

However, my issue was specific to Xubuntu/Xscreensaver, I haven't tested Ubuntu/Unity.

---

### Post by cariboo on 2013-09-28
I should amend my post [here]("http://ubuntuforums.org/showthread.php?t=2176970&p=12799946&viewfull=1#post12799946"), as I actually was running Xubuntu, at the time when it came out of sleep, and I saw the desktop before seeing the password dialogue box.

---

