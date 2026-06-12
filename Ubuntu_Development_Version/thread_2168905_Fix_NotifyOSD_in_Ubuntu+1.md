---
title: "Fix NotifyOSD in Ubuntu+1"
date: 2013-08-19
forum: Ubuntu Development Version
---

### Post by quequotion on 2013-08-19
I'd like to see [this bug]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/390508") finally resolved in the next Ubuntu. I care about this *much* more that whatever display stack or anything else is implemented.

It's very important for users and developers to have notifications that are useful and convenient. It's also important to follow the freedesktop.org standards *and your own documentation*.

Fix NotifyOSD in Ubuntu+1--add respect for the timeout parameter.

---

### Post by cariboo on 2013-08-19
I don't know who this post is directed at, as most developers rarely post here or read this sub-forum. If you read [Sebastion Bacher]("https://launchpad.net/~seb128")'s last post in the report, there is no maintainer for notify-osd, and if there is no one to fix the bug, it won't get fixed.

The only way to solve the problem is to fix the problem yourself, or find a developer that is willing to take on maintaining it.

---

### Post by mc4man on 2013-08-19
Actually I'd say the only bug there under 'some' consideration for being fixed is to patch the manpage to reflect **no **-t option.
As far as officially it's been fairly well established what deviation from the current hard default of 10000ms is acceptable & nothing in that vein has occurred
[lpbug]723980[/lpbug]
Here I settle for 2700ms which is about right for me, I've no apps that require control of timeout

---

### Post by tgalati4 on 2013-08-20
I've patched notify-osd and change hard-coded values to ones that were useful to me.  It's not that difficult.  Why some of these values are hard-code is a mystery.  So rather than fight the design decisions, I fixed it myself.  I think I still have 9.04 on a system somewhere.  I don't remember what I set the expire time, but I'm pretty sure I still have the build evironment.

Here's a PPA for a more customizable notify-OSD, although my quick search shows that it may not work in 13.04:  [http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html](http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html)

The pop-up locations were dumb--covering window controls and not user-changeable.  There were several notify-osd design issues that were never addressed.  If U remember, at that time, there was a desktop environment under development with similar design decisions.

---

### Post by cariboo on 2013-08-20
Thanks mc4man and tgalati4 for providing the op with the information he needs to solve his problem.

---

### Post by quequotion on 2013-08-20
> **tgalati4 said:**
> Here's a PPA for a more customizable notify-OSD, although my quick search shows that it may not work in 13.04:  [http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html](http://www.webupd8.org/2011/05/configurable-notifyosd-bubbles-for.html) I have been using ths PPA for a few years already, but thanks for posting the link in case anyone else needs it.

> **cariboo907 said:**
> Thanks mc4man and tgalati4 for providing the op with the information he needs to solve his problem. I think you misunderstood. I don't need help; *the bug needs to be fixed*. It's been going for years now and all the previous developers will say is that Canonical choose this design and won't accept any changes to it.... that's *rediculous*, it's a terrible design.

---

### Post by quequotion on 2013-08-20
> **cariboo907 said:**
> I don't know who this post is directed at, as most developers rarely post here or read this sub-forum.

That's rather unfortunate. I would think a forum about the development of the next distribution would be something developers are at least reading....

---

### Post by vasa1 on 2013-08-20
In case anyone's interested, there's another option [described here]("http://askubuntu.com/a/88648/25656"):
```
sudo apt-get install xfce4-notifyd
```

---

### Post by VMC on 2013-08-20
So the timeout is the only issue here? As mac4man stated, just change the man page.
 I didn't realize that I "me too" on the bug report. I guess it was when I was studying the Zenity program that I ran across it.

---

### Post by philinux on 2013-08-20
> **quhttp://ubuntu-discourse.org/quotion said:**
> I have been using ths PPA for a few years already, but thanks for posting the link in case anyone else needs it.

 I think you misunderstood. I don't need help; *the bug needs to be fixed*. It's been going for years now and all the previous developers will say is that Canonical choose this design and won't accept any changes to it.... that's *rediculous*, it's a terrible design.

Try here. 

[http://ubuntu-discourse.org/](http://ubuntu-discourse.org/)

According to Jorge Castro the devs pop in there.

---

### Post by cariboo on 2013-08-20
> **quequotion said:**
> I have been using ths PPA for a few years already, but thanks for posting the link in case anyone else needs it.

 I think you misunderstood. I don't need help; *the bug needs to be fixed*. It's been going for years now and all the previous developers will say is that Canonical choose this design and won't accept any changes to it.... that's *rediculous*, it's a terrible design.

I think you misunderstood me, there isn't anyone looking after the package, so it won't be fixed until someone takes over as the maintainer. If you want the bug fixed, and you don't need help, why not take over the maintaining of the package yourself, and apply the fix.

---

### Post by tgalati4 on 2013-08-20
Well, I'm confused.  If one were to install xfce4-notifyd will it conflict with notify-osd?  According to:

tgalati4@Mint14-Extensa ~ $ apt-cache depends xfce4-notifyd
xfce4-notifyd
  Depends: libc6
  Depends: libcairo2
  Depends: libdbus-1-3
  Depends: libdbus-glib-1-2
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libpango1.0-0
  Depends: libx11-6
  Depends: libxfce4ui-1-0
  Depends: libxfce4util6
  Depends: libxfconf-0-2
  Recommends: libnotify-bin
  Conflicts: xfce4-notifyd:i386
tgalati4@Mint14-Extensa ~ $ apt-cache depends notify-osd
notify-osd
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libdbus-1-3
  Depends: libdbus-glib-1-2
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk-3-0
  Depends: libpango1.0-0
  Depends: libpixman-1-0
  Depends: libwnck-3-0
  Depends: libx11-6
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Recommends: notify-osd-icons
  Replaces: notification-daemon
    colibri
    mate-notification-daemon
    notify-osd
    plasma-widgets-workspace
    xfce4-notifyd
  Replaces: notification-daemon:i386
    colibri:i386
    mate-notification-daemon:i386
    notify-osd:i386
    plasma-widgets-workspace:i386
    xfce4-notifyd:i386
  Conflicts: notify-osd:i386

Notify-osd will uninstall xfce4-notifyd but not the otherway around.  So, I'm not sure how applications that depend on notify-osd can use xfce4-notifyd.  But yea, a simple dialog box to control notify-osd would be helpful.

After looking at all of the different notification frameworks available, my head hurts.

---

### Post by quequotion on 2013-08-21
> **cariboo907 said:**
> I think you misunderstood me, there isn't anyone looking after the package, so it won't be fixed until someone takes over as the maintainer. If you want the bug fixed, and you don't need help, why not take over the maintaining of the package yourself, and apply the fix.

Isn't there some kind of authority/peer approval required to change packages that are part of ayatana?

---

### Post by cariboo on 2013-08-21
> **quequotion said:**
> Isn't there some kind of authority/peer approval required to change packages that are part of ayatana?

Yes there is, if you submit a patch, it has to be approved by one of the developers. BTW, ayatana has fallen by the wayside, and it is now just called unity-desktop.

---

### Post by mc4man on 2013-08-21
I believe you can still add "Ayatana Design" to any bug, whether that gets you anywhere is debatable, "As intended" rules the Ubuntu day.
(- current example - [lpbug]1209237[/lpbug], as an aside - note he says " but should also be easy to switch off via a dconf key for the purposes of user testing", -  so in that case it's possible one day the dconf key will  disappear


In this case I think you're likely beating a dead horse, though users are free to do (modify) as they want or can.

---

### Post by quequotion on 2013-08-22
> **cariboo907 said:**
> Yes there is, if you submit a patch, it has to be approved by one of the developers. BTW, ayatana has fallen by the wayside, and it is now just called unity-desktop.

No more Ayatana? It's actually a better name than "Unity" -- way too many things share that name.

There already is a patch in the bug report. I don't know if it's in a bzr branch yet. It'll take me a while to set up, but I'll see if I can get it into one. 

It's not a good idea for me to personally take over as maintainer. I don't (yet) have the skills and, after fixing this bug, I doubt that I would dedicate much time to it. I am interested in this issue and I'll do what I can concerning it, but after that I'll be moving on to the next crisis.

---

### Post by quequotion on 2013-08-22
> **mc4man said:**
> I believe you can still add "Ayatana Design" to any bug, whether that gets you anywhere is debatable One of my favorite bugs, a compiz display layering glitch, was "Fix Comitted" and then "Fix Relased" in "Ayatana Design".

The bug hasn't been fixed at all, but *the design apparently has*. As yet, no one has replied to my inquires as to what that actually means (ie *nothing*).

---

