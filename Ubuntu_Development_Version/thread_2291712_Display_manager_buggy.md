---
title: "Display manager buggy?"
date: 2015-08-22
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-08-22
I've been playing with Ubuntu GNOME the past few days since most of the remaining parts of GNOME 3.16 have landed in the repos and it looks like if you choose auto-login during installation, then open System Settings > Users it says auto-login is set to off even though its set to on. I'll be trying Ubuntu itself as well as the latest spins of Ubuntu GNOME over the next few days but wondered if others would watch for that behavior among any and all flavors :D

I've tried both gdm and lightdm with the gtk-greeter and they both seem goofy in that regard, but if you manually change auto-login back and forth from off to on, and vice versa, then it seems to work OK.

I remember something like that happening previously so I dug thru my old notes ......... not sure if it might be a regression to this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915)

Jump to comment #15 where Sebastien Bacher found some buggy code. So maybe an upstream import still has the buggy code? Or maybe it's an entirely new problem?

---

### Post by dino99 on 2015-08-22
There have been several users complaining about autologin issues recently
 [https://www.google.com/?q=autologin+bug#q=autologin+bug&tbs=qdr:m](https://www.google.com/?q=autologin+bug#q=autologin+bug&tbs=qdr:m)

---

### Post by kansasnoob on 2015-08-23
I tried fresh installations of both Ubuntu and Ubuntu GNOME yesterday and this appeared to affect only Ubuntu GNOME so I filed a bug report against gdm:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1487819](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1487819)

---

### Post by sgage on 2015-08-23
> **kansasnoob said:**
> I've been playing with Ubuntu GNOME the past few days since most of the remaining parts of GNOME 3.16 have landed in the repos and it looks like if you choose auto-login during installation, then open System Settings > Users it says auto-login is set to off even though its set to on. I'll be trying Ubuntu itself as well as the latest spins of Ubuntu GNOME over the next few days but wondered if others would watch for that behavior among any and all flavors :D

I've tried both gdm and lightdm with the gtk-greeter and they both seem goofy in that regard, but if you manually change auto-login back and forth from off to on, and vice versa, then it seems to work OK.

I remember something like that happening previously so I dug thru my old notes ......... not sure if it might be a regression to this:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/1245915)

Jump to comment #15 where Sebastien Bacher found some buggy code. So maybe an upstream import still has the buggy code? Or maybe it's an entirely new problem?

Yes, this happened to my latest install, from the August 19th build. I always install with auto-login, and sure enough, I was auto-logging-in... so I never even noticed...

---

### Post by kansasnoob on 2015-08-23
> **sgage said:**
> Yes, this happened to my latest install, from the August 19th build. I always install with auto-login, and sure enough, I was auto-logging-in... so I never even noticed...

I only happened to notice because I decided to try the flashback session for the first time in this cycle and, even though I'd logged out and selected flashback successfully, I decided to turn auto-login off just in case things were screwed on boot. It seems to sort itself out after toggling back and forth between off and on a couple of times but Tim Lunn at Ubuntu GNOME recently asked for thorough testing so I'm trying diligently to break things ;)

---

### Post by sgage on 2015-08-23
> **kansasnoob said:**
> I only happened to notice because I decided to try the flashback session for the first time in this cycle and, even though I'd logged out and selected flashback successfully, I decided to turn auto-login off just in case things were screwed on boot. It seems to sort itself out after toggling back and forth between off and on a couple of times but Tim Lunn at Ubuntu GNOME recently asked for thorough testing so I'm trying diligently to break things ;)

I've done a bit more testing. I set auto-login 'on' in the settings, rebooted, it auto-logged me in, but again reverted to 'off' in the settings.

I set it 'off', rebooted, and sure enough had to manually log in.

I set it back 'on', rebooted, got auto-logged in, but again showed as 'off'.

Very strange...

---

### Post by sammiev on 2015-08-23
> **sgage said:**
> I've done a bit more testing. I set auto-login 'on' in the settings, rebooted, it auto-logged me in, but again reverted to 'off' in the settings.

I set it 'off', rebooted, and sure enough had to manually log in.

I set it back 'on', rebooted, got auto-logged in, but again showed as 'off'.

Very strange...

I just updated after 10 days of been away.

No issues with the auto login in gnome here.

Shut off auto login and rebooted, typed in password and set it for auto again.

Rebooted computer again and it log in automatically.

So yes this is strange.

---

### Post by sgage on 2015-08-23
> **sammiev said:**
> I just updated after 10 days of been away.

No issues with the auto login in gnome here.

Shut off auto login and rebooted, typed in password and set it for auto again.

Rebooted computer again and it log in automatically.

So yes this is strange.

Yes, how you set it determines how it works. But when you set it 'on' and reboot (and auto-login), when you check your settings does it show as 'on'?

---

### Post by sammiev on 2015-08-23
> **sgage said:**
> Yes, how you set it determines how it works. But when you set it 'on' and reboot (and auto-login), when you check your settings does it show as 'on'?

It does shows off.

---

### Post by sgage on 2015-08-23
> **sammiev said:**
> It does shows off.

That's the bug. It wouldn't seem to be that hard to fix. Nor is it really all that pernicious in its effects. Just a strange glitch...

---

### Post by kansasnoob on 2015-08-23
Could I please get all affected to mark [the bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1487819") as so ............... that'll move it from New to Confirmed and hopefully garner more serious attention.

---

### Post by sammiev on 2015-08-23
> **kansasnoob said:**
> Could I please get all affected to mark [the bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1487819") as so ............... that'll move it from New to Confirmed and hopefully garner more serious attention.

Done...

---

### Post by kansasnoob on 2015-08-24
> **sammiev said:**
> Done...

Thank you :D

---

### Post by sgage on 2015-08-24
> **kansasnoob said:**
> Could I please get all affected to mark [the bug]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1487819") as so ............... that'll move it from New to Confirmed and hopefully garner more serious attention.

And done.

---

### Post by kansasnoob on 2015-08-24
> **sgage said:**
> And done.

Thanks, I PM'ed Tim Lunn so I'm sure he'll be looking into this ASAP.

---

