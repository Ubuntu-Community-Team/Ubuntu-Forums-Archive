---
title: "Have installed xfce and having trouble starting X as non-root"
date: 2016-10-03
forum: Server Platforms
---

### Post by jim.hitch on 2016-10-03
Hi

It's a bit long-winded, but here's the background.

I've installed Ubuntu Server as a VM inside a FreeNAS jail (why? because I use  crashplan and this is an easier way to go with FreeNAS. BUT crashplan is super complicated to set up headless, so I have installed xfce4 in order to get the crashplan GUI working. The way FreeNAS works is that I'm having to do this remotely).

Installing ubuntu server was a breeze, as was installing xfce, though I couldn't get x to start without running 

```
$ sudo startx
```

Which I know isn't cool, but it wasn't working using my non-root account.

I've chowned .ICEauthority and .Xauthority but am not getting any luck still. It's a bit difficult to catch what the issue is as the error flies up the screen, but 'no screens found' does appear.

Another thread suggested trying

```
$ find -user root 2>dev/null
```

And printing the results to those that understand it:

```
$ find -user root 2>dev/null
./.dbus
./.cache/sessions
./Desktop
./.xsession-errors
./.config
./.config/xfce4/panel
./.config/xfce4/panel/launcher-9
./.config/xfce4/panel/launcher-12
./.config/xfce4/panel/launcher-10
./.config/xfce4/panel/launcher-11
./.config/xfce4/helpers.rc
./.config/xfce4/xfconf
./.config/xfce4/xfconf/xfce-perchannel-xml
./.config/xfce4/desktop
./.config/xfce4/xfwm4
./.config/Thunar
./.config/xfce4-session
./.config/mimeapps.list

```

Is that at all useful? What else can I try?

---

