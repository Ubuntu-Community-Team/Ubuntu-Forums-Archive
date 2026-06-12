---
title: "Can't get wifi to work on Ubuntu Server"
date: 2011-12-06
forum: Server Platforms
---

### Post by donniezazen on 2011-12-06
Hi,

I am using wpa_supplicant to run wifi on Dell Inspiron E1505. I suppose i have to install bcmwl-kernel-source like i did in Ubuntu Desktop. I can see the wifi on light but i can't connect to wifi. I get SIOCSIFFLAGS error.

I think my network card in not on. How can i turn it on? And is wpa_supplicant the best way to run wifi on ubuntu-server? How can i make it start automatic?

Thanks.

---

### Post by donniezazen on 2011-12-12
I install bcmwl-kernel-source and it breaks ethernet.

---

### Post by donniezazen on 2011-12-16
OMG!! not a single person is interested in helping.

Please help.

---

### Post by TFroehlich3 on 2011-12-19
Simple solution.
 
Hard wire is ALWAYS the best thing to use when it comes to servers. That way you don't have to worry about you getting disconnected or anything, not to mention that transfer speeds are way better as well.
 
So if it is at all possible, hard wire it. 
 
I used to have a dell as well running ubuntu, and I could **NOT** get the wifi to work for the life of me!!!! 
I hope you find a solution soon, but until then, just hard wire it if you can... ((very long ethernet cables are very cheap on eBay))

---

### Post by donniezazen on 2011-12-19
> **TFroehlich3 said:**
> Simple solution.
 
Hard wire is ALWAYS the best thing to use when it comes to servers. That way you don't have to worry about you getting disconnected or anything, not to mention that transfer speeds are way better as well.
 
So if it is at all possible, hard wire it. 
 
I used to have a dell as well running ubuntu, and I could **NOT** get the wifi to work for the life of me!!!! 
I hope you find a solution soon, but until then, just hard wire it if you can... ((very long ethernet cables are very cheap on eBay))

I did a headless install of Arch Linux and wifi works. I tried everything but just can't get it to work on Ubuntu. Forum seems to be pretty unenthusiastic about it.

---

### Post by arrrghhh on 2011-12-19
> **donniezazen said:**
> I did a headless install of Arch Linux and wifi works. I tried everything but just can't get it to work on Ubuntu. Forum seems to be pretty unenthusiastic about it.

Then use Arch...?

Honestly, I can't think of one good reason for putting a server on a wifi connection, unless you intend to use it not as a server but as a client - in which case, why are you going for a server distro?

Good luck.  Most server admins are not going to care about wifi/wlan cards, so you unfortunately won't find much help here.  Also, I am a strong proponent of use what works best for you - if another distro fits you better, feel free to use it.

---

### Post by donniezazen on 2011-12-19
> **arrrghhh said:**
> Then use Arch...?

Honestly, I can't think of one good reason for putting a server on a wifi connection, unless you intend to use it not as a server but as a client - in which case, why are you going for a server distro?

Good luck.  Most server admins are not going to care about wifi/wlan cards, so you unfortunately won't find much help here.  Also, I am a strong proponent of use what works best for you - if another distro fits you better, feel free to use it.

I am here to seek help and not get into arguments.

A good reason. My Router is in living room. I have a laptop hooked on to TV and want to run XBMC front-end and headless Ubuntu. I don't want to run cables all over my place.

I mentioned Arch not because Arch is the greatest linux distro in the world but to mention that wifi works on linux and something is not working in Ubuntu.

Why i would like to use Ubuntu? It is more noob friendly.

---

### Post by arrrghhh on 2011-12-19
> **donniezazen said:**
> I am here to seek help and not get into arguments.

A good reason. My Router is in living room. I have a laptop hooked on to TV and want to run XBMC front-end and headless Ubuntu. I don't want to run cables all over my place.

I mentioned Arch not because Arch is the greatest linux distro in the world but to mention that wifi works on linux and something is not working in Ubuntu.

Why i would like to use Ubuntu? It is more noob friendly.

Why not put the router near the server?  I have my server sitting next to my TV for this very reason - router, cable modem, PS3 - everything I want hard wired is all in the same place.  Wires don't go 'everywhere' this way.

Also, just install Ubuntu Desktop if you want wireless.  Honestly, it's much easier and you can run all the same services from a "Desktop" install that you can from a "Server" install.  The Server Edition is just stripped and setup to run lean&mean - only the bare essentials.  For example, wifi is not going to be simple/straightforward.

I'm not here to argue either, but your setup is not orthodox.  Good luck.

---

### Post by donniezazen on 2011-12-19
> **arrrghhh said:**
> Why not put the router near the server?  I have my server sitting next to my TV for this very reason - router, cable modem, PS3 - everything I want hard wired is all in the same place.  Wires don't go 'everywhere' this way.

Also, just install Ubuntu Desktop if you want wireless.  Honestly, it's much easier and you can run all the same services from a "Desktop" install that you can from a "Server" install.  The Server Edition is just stripped and setup to run lean&mean - only the bare essentials.  For example, wifi is not going to be simple/straightforward.

I'm not here to argue either, but your setup is not orthodox.  Good luck.

I am not really interested in floor plan. Thanks for your help.

---

### Post by arrrghhh on 2011-12-19
> **donniezazen said:**
> I am not really interested in floor plan. Thanks for your help.

Install Ubuntu Desktop.  Plug into router.  Get wifi working.  Done.

---

### Post by donniezazen on 2011-12-19
> **arrrghhh said:**
> Install Ubuntu Desktop.  Plug into router.  Get wifi working.  Done.

Is their a huge difference in power/other-resources consumption between Ubuntu-Desktop and Ubuntu-Server? Or it is minor.

I have got wifi working in Arch. I just have to get proper resolution and i might just use that setup.

Thanks.

---

### Post by arrrghhh on 2011-12-19
> **donniezazen said:**
> Is their a huge difference in power/other-resources consumption between Ubuntu-Desktop and Ubuntu-Server? Or it is minor.

I have got wifi working in Arch. I just have to get proper resolution and i might just use that setup.

Thanks.

AFAIK power/other resource consumption is pretty similar.  The Desktop edition will have some overhead because it's running a lot more (no DE on the server edition).

Other than that, I don't think there's really any difference.

Also, resolution?  This is a server, right?  No GUI?

---

### Post by donniezazen on 2011-12-19
> **arrrghhh said:**
> AFAIK power/other resource consumption is pretty similar.  The Desktop edition will have some overhead because it's running a lot more (no DE on the server edition).

Other than that, I don't think there's really any difference.

Also, resolution?  This is a server, right?  No GUI?

XBMC frontend.

---

### Post by arrrghhh on 2011-12-19
> **donniezazen said:**
> XBMC frontend.

Why would you ever install the Server Edition then?!?  It comes with NO GUI, no DE, nothing.  CLI only.

OpenELEC, or Ubuntu Desktop.  Seriously...

---

### Post by donniezazen on 2011-12-19
):P> **arrrghhh said:**
> Why would you ever install the Server Edition then?!?  It comes with NO GUI, no DE, nothing.  CLI only.

OpenELEC, or Ubuntu Desktop.  Seriously...

I had this Ubuntu Server edition for a couple of months connected via Ethernet. I ran samba, print, subsonic, webmin, ps3-server, etc. server which worked just fine. Then i bought TV. The only reason i don't want Ubuntu Desktop is that it doesn't serve any purpose. Ubuntu server is lean. XBMC front-end over Ubuntu-Server or XBMC-Live sounds like a great idea.

I was unaware of OpenELEC. I will check it out.

My last resort is to just buy a USB WIFI card that works OOTB on Ubuntu.

---

### Post by arrrghhh on 2011-12-19
> **donniezazen said:**
> ):P

I had this Ubuntu Server edition for a couple of months connected via Ethernet. I ran samba, print, subsonic, webmin, ps3-server, etc. server which worked just fine. Then i bought TV. The only reason i don't want Ubuntu Desktop is that it doesn't serve any purpose. Ubuntu server is lean. XBMC front-end over Ubuntu-Server or XBMC-Live sounds like a great idea.

I was unaware of OpenELEC. I will check it out.

My last resort is to just buy a USB WIFI card that works OOTB on Ubuntu.

Well, you're trying to fit a round peg into a square hole.  Ubuntu Server has served you well, and now you want it to do something is was never designed to do.  It doesn't come with a UI, so XBMC is useless on it (as you would need a UI to display all the pretty info).

You really should just get a small HTPC to hook up to your TV.  That's what I'm looking at (pulse-eight.com, I am in no way affiliated just looking into this myself).

---

### Post by donniezazen on 2011-12-19
> **arrrghhh said:**
> Well, you're trying to fit a round peg into a square hole.  Ubuntu Server has served you well, and now you want it to do something is was never designed to do.  It doesn't come with a UI, so XBMC is useless on it (as you would need a UI to display all the pretty info).

You really should just get a small HTPC to hook up to your TV.  That's what I'm looking at (pulse-eight.com, I am in no way affiliated just looking into this myself).

Yeah their are plenty of those Google TV, Boxee, Roku, etc.

---

### Post by arrrghhh on 2011-12-19
> **donniezazen said:**
> Yeah their are plenty of those Google TV, Boxee, Roku, etc.

Yes...

---

### Post by donniezazen on 2011-12-20
It doesn't make sense but I did a desktop install. Installed firmware-b43-installer and the wifi popped up. It wouldn't work on server. It should they share the same base install. I might have to repeat the experiment.

---

### Post by arrrghhh on 2011-12-20
> **donniezazen said:**
> It doesn't make sense but I did a desktop install. Installed firmware-b43-installer and the wifi popped up. It wouldn't work on server. It should they share the same base install. I might have to repeat the experiment.

If you wish, but if it's going to be running XBMC, you kinda need a DE...

Also, it makes perfect sense... for all the reasons I mentioned earlier.  You can probably get it to work on the server edition, but what's the point?  A lot less effort on the desktop edition.

---

### Post by donniezazen on 2011-12-20
> **arrrghhh said:**
> If you wish, but if it's going to be running XBMC, you kinda need a DE...

Also, it makes perfect sense... for all the reasons I mentioned earlier.  You can probably get it to work on the server edition, but what's the point?  A lot less effort on the desktop edition.

I certainly don't need hefty Gnome. Xserver and graphic drivers should be enough as they run XBMC-LIVE without DE.

---

### Post by donniezazen on 2011-12-21
Yay! got it working.

```

1. Clean install of Ubuntu Server.
2. apt-get update && apt-get upgrade
3. apt-get firmware-b43-installer
4. apt-get wicd-curses
5. Restart
6. wicd-curses  ##to connect to your wireless.

```

---

