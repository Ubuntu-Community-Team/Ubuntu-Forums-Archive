---
title: "Firefox, GTK2, and GTK3"
date: 2015-12-15
forum: Ubuntu, Linux and OS Chat
---

### Post by vasa1 on 2015-12-15
There were indications that Firefox 43 would ship with GTK3. This bug points to the GTK3 version being delayed a bit: [https://bugzilla.mozilla.org/show_bug.cgi?id=1227024](https://bugzilla.mozilla.org/show_bug.cgi?id=1227024)

I couldn't find any mention of whether GTK2 would be an option that end-users could somehow choose when Firefox ver.XX ships with GTK3.

I'm also wondering if Mozilla has bitten off a bit too much. From what I've understood of what I've read, the GNOME developers have a vision and those using GTK3 need to follow. So what would happen to Ubuntu 12.04 and 14.04 users with older versions of GTK3? Would Mozilla be able to provide a GTK3 Firefox compatible with the GNOME versions in 12.04 and 14.04?

---

### Post by vasa1 on 2016-01-12
> **vasa1 said:**
> There were indications that Firefox 43 would ship with GTK3. This bug points to the GTK3 version being delayed a bit: [https://bugzilla.mozilla.org/show_bug.cgi?id=1227024](https://bugzilla.mozilla.org/show_bug.cgi?id=1227024)

... So what would happen to Ubuntu 12.04 and 14.04 users with older versions of GTK3? Would Mozilla be able to provide a GTK3 Firefox compatible with the GNOME versions in 12.04 and 14.04?
This bug indicates that even Firefox 44 will be gtk2 but Firefox 45 will be gtk3: [https://bugzilla.mozilla.org/show_bug.cgi?id=1227024](https://bugzilla.mozilla.org/show_bug.cgi?id=1227024)

To see if Fx 45 (gtk3) works in _14_.04, I installed it from here: [https://download-installer.cdn.mozilla.net/pub/firefox/nightly/latest-mozilla-aurora/firefox-45.0a2.en-US.linux-x86_64.tar.bz2](https://download-installer.cdn.mozilla.net/pub/firefox/nightly/latest-mozilla-aurora/firefox-45.0a2.en-US.linux-x86_64.tar.bz2). Works well. 

```
$ apt-cache policy libgtk-3-0
libgtk-3-0:
  Installed: 3.10.8-0ubuntu1.6
  Candidate: 3.10.8-0ubuntu1.6
  Version table:
 *** 3.10.8-0ubuntu1.6 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.10.8-0ubuntu1.4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     3.10.8-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
$
```

---

### Post by v3.xx on 2016-01-12
You got me wondering about firefox, gtk3 and mate 16o4.  So I installed FF45 and find it runs without issue in my 5 minute test on Mate :)

---

### Post by vasa1 on 2016-01-29
Couldn't wait so I moved from stable (v44) to beta (v45). Nothing broke so far.

---

### Post by kansasnoob on 2016-01-29
> **vasa1 said:**
> Couldn't wait so I moved from stable (v44) to beta (v45). Nothing broke so far.

Does it seem to work more appropriately with various default themes? I'm sooooooooooo tired of it not obeying the scrollbar settings in Ubuntu and Ubuntu GNOME ;)

---

### Post by vasa1 on 2016-01-29
> **kansasnoob said:**
> Does it seem to work more appropriately with various default themes? I'm sooooooooooo tired of it not obeying the scrollbar settings in Ubuntu and Ubuntu GNOME ;)

They're pretty conventional, not different in any way that I can tell from good old gtk2 scrollbars.

I use just one theme and it's based on Greybird, part of the shimmer-themes package.

Still, If you have any specific issues, I *may* be able to help :)

And for those who want gtk2-type scrolling... add *gtk-primary-button-warps-slider=false* to *~/.config/gtk-3.0/settings.ini* while you can. Who knows when the GNOME devs may decide to improve things by removing the possibility.

My file looks like this:
```
[Settings] 
gtk-theme-name=freebird
#gtk-theme-name=Tempura
gtk-icon-theme-name=NoInherits
gtk-font-name=Ubuntu 12
gtk-cursor-theme-name=oxy-red-argentina
gtk-cursor-theme-size=18
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-toolbar-icon-size=GTK_ICON_SIZE_LARGE_TOOLBAR
gtk-button-images=0
gtk-menu-images=1
gtk-enable-event-sounds=1
gtk-enable-input-feedback-sounds=1
gtk-xft-antialias=1
gtk-xft-hinting=1
gtk-xft-hintstyle=hintslight
gtk-xft-rgba=rgb
gtk-primary-button-warps-slider=false

```

---

### Post by kansasnoob on 2016-01-30
> Who knows when the GNOME devs may decide to improve things by removing the possibility.

:lolflag: They've gotten pretty good at that haven't they?

Rather than practicing "if it ain't broke don't fix it" they seem to practice "no one's complaining let's break something" ;)

---

### Post by vasa1 on 2016-01-30
> **kansasnoob said:**
> :lolflag: They've gotten pretty good at that haven't they?

Rather than practicing "if it ain't broke don't fix it" they seem to practice "no one's complaining let's break something" ;)

Well, as a Lubuntu 14.04 Openbox session user, I've managed to limit my exposure to the joys of gtk3 ;)

---

### Post by vasa1 on 2016-02-05
The next beta, b4, will disable GTK3: [https://blog.mozilla.org/meeting-notes/archives/2330](https://blog.mozilla.org/meeting-notes/archives/2330) and [https://bugzilla.mozilla.org/show_bug.cgi?id=1239962](https://bugzilla.mozilla.org/show_bug.cgi?id=1239962)

So I've gone back to Fx 44 (GTK2).

Edit: v45 is still gtk2. v46 *may* have gtk3: [http://www.omgubuntu.co.uk/2016/03/new-features-in-firefox-45](http://www.omgubuntu.co.uk/2016/03/new-features-in-firefox-45)

---

### Post by vasa1 on 2016-03-29
Looks like they're going ahead with gtk3 this time: Fx 46 is now at beta 5 and they still haven't pulled the rug. It's working pretty decently. And I've got most things (other than some about: pages) to look the way I want them to.

My three extensions, CTR 1.4.9, uBlock Origin 1.6.6, and Stylish 2.0.6 are working well too.

Of course, this is all with GTK 3.10. 16.04 will leapfrog me to GTK 3.18 (and I'm getting acquainted with that via a live USB).

---

### Post by vasa1 on 2016-04-02
Firefox 46 maybe delayed: [https://blog.mozilla.org/meeting-notes/](https://blog.mozilla.org/meeting-notes/)

> beta 6 not released

    Multiple betas skipped this cycle. May want to start looking at schedule changes in advance in case we decide to postpone Fx46 shipping.


---

### Post by vasa1 on 2016-04-26
Well, it's almost certain that Fx 46 will be gtk3! I ran it for quite sometime when it was in beta. No major issues. I opted for legacy scrolling.

[http://www.omgubuntu.co.uk/2016/04/firefox-46-now-available-download](http://www.omgubuntu.co.uk/2016/04/firefox-46-now-available-download) 
[http://www.ghacks.net/2016/04/26/firefox-46-0/](http://www.ghacks.net/2016/04/26/firefox-46-0/)

I'll wait for the actual release.

And it's here! I know it's gtk3 because I have red scrollbars for gtk2 apps and blue ones for gtk3 apps ;)

---

