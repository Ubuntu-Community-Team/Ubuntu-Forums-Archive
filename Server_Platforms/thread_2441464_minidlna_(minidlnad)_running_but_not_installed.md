---
title: "minidlna (minidlnad) running but not installed?"
date: 2020-04-23
forum: Server Platforms
---

### Post by awbmilne on 2020-04-23
Hey!

I recently setup a new home server with Ubuntu Server edition.
I have been messing around with Rasbian on my Raspberry Pi 4 for fun and decided to push for a better NAS solution using Ubuntu Server.
Yes, I know it would be easier to use OMV for this sort of stuff, but Im enjoying learning everything along the way.

The Issue I have come across is that I noticed in my Windows File Explorer that my server was showing up as a media device, and was showing media folders.
This is without any setup or install of a DNLA or UPNP host.... So im wondering where it came from.

Using `top`, i found that `minidlnad` was running. I killed it using `top` and it showed up again, so I figure it is running as a service. I couldnt find it with `systemctl`, so im pretty confused as to what is going on.

I have tried `apt-get purge minidlna` and `apt-get auto-remove` but they didnt make a difference (no packages removed).

Im not concerned about the files being shared, I just want to know what it is and what is happenin so I can manage it. Dont need a rouge service sharing data I dont know about.

Anybody know whats going on?

(Also, why is Markdown in my post not working?)

---

### Post by SeijiSensei on 2020-04-23
I installed minidlna from the repositories on my 20.04 system.  It is configured to start up automatically out-of-the-box.

```

$ systemctl list-unit-files | grep minidlna
minidlna.service                       generated       enabled  

```

It still uses SysV start-stop mechanics.  I can start and stop it with
```
sudo service minidlna [start|stop]
```

I can remove it with 
```
sudo apt purge minidlna
```

Unless you edit /etc/minidlna.conf and define the media directories, it won't serve anything. See the "media_dir" directive in minidlna.conf.  You can have as many of them as you need.

---

