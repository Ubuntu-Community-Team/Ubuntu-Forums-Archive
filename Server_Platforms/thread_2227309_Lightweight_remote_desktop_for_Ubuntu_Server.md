---
title: "Lightweight remote desktop for Ubuntu Server"
date: 2014-06-01
forum: Server Platforms
---

### Post by mike200 on 2014-06-01
Hi, I'd like to have a way to have a gui installed on my Ubuntu Server so ic an access it remotely. I'd like to use it mainly to upload YouTube videos because I already have two servers running 24/7 and I don't like to keep my 1000W PC running over night. 
I can't use SSH X server forwarding since that stops when I disconnect the session. 
**What would you recommend for a lightweight desktop for my server and a VERY secure remote desktop protocol? **

If possible, I'd like to be able to access my terminal directly fom the machine in case of any network problems and not have the desktop giving me a hard time while I fix thing in the CLI.

---

### Post by TheFu on 2014-06-01
How remote?  On the same LAN and security becomes less important.
Over the internet and then a VPN becomes more important (mandatory, IMHO).

So, I would normally say to use NX (freenx as server, whatever NX client you like), but I understand that the F/LOSS implementation are dying in 14.04.  I've read that x2go has embedded the NX code into their stuff and that others have gotten it working on 14.04. NX included ssh as the connection/tunnel and I feel it is 2-3x more network efficient than RDP, VNC, and other non-commercial remote desktop protocols.

NX does allow reconnection to a session from anywhere (resizes down based on the local screen resolution).  I've never setup an NX server on a physical server, so I don't know if the NX session impacts local X/Windows login action or not.  I've only used FreeNX inside virtual machines.  BTW, my daily-use desktop runs inside a KVM-VM and I access it through NX.  

Video doesn't work well under any of these remote desktops.  The best hope for that is SPICE over SSL ... but I think Spice only works for virtual machines, not on physical hosts. Don't quote me here, I've just never seen it deployed any other way.

---

### Post by mike200 on 2014-06-05
I don't need to have it over the internet if security is an issue (I can still use an SSH tunnel).
All I need is a way to access a gui remotely, drag & drop a file into firefox, disconnect and let the server upload my video to YouTube over night.

As far as I understand, I need to install a desktop first, then a remote desktop app. What desktop would you recommend? I'm looking for minimal graphics and not a lot of CPU usage.

---

### Post by TheFu on 2014-06-05
A pure window-manager would be the lightest. They can be unfriendly to new users.  LXDE or XFCE4 are the easier-to-use alternatives that are just a little heavier - nowhere near as heavy as Unity.

If you ever plan to access the desktop over the internet ... even just once a year ... I'd go with FreeNX for 12.04 or x2go for 14.04. These use the NX protocol and ssh is part of the connection protocol for NX. A new x2go how-to was posted in these forums recently for 14.04.  I haven't tried it, but when I update my 2 VM desktops in the next few months, I will.  

I've been using FreeNX for years - it is fast, stable, secure, so I don't take this change lightly.  I've connected back to my daily driver desktop from 5 continents over NX. It also works well from inside the LAN, though I generally use **ssh -X** instead, except from 1 Windows desktop with dual monitors. ;)

---

### Post by steeldriver on 2014-06-05
I use an LXDE desktop via tightvnc tunnelled over SSH almost daily - it's probably good enough as long as you're not actually trying to *view* the video over the connection. Depending on what VNC client you use, you may be able to  set up the SSH tunnel automatically from the client. I haven't tried NX but that's only because it's not my box so I don't get the choice. I used to use XFCE4 as the desktop but had some problems with it after the last-but-one upgrade.

The absolutely bare version would be something like [FONT=courier new]apt-get install **--no-install-recommends** lxde-core[/FONT]  

FWIW have you looked at whether a CLI based upload solution (using curl maybe?) might be possible?

---

### Post by Robin_Wilson on 2014-06-05
From experimenting I have found that I can only view the screen if I switch to the xfce window manager and then xrdp works and I can connect in the same way as a windows computer using the Windows RDP Client minus network-level authentication.
This lets me view the desktop and the full GUI.

First install xfce and xrdp:
```
[FONT=Calibri]sudo apt-get install xfce4 xrdp

```

Then log into the terminal using the account you plan to use and run this to switch the session to using xfce (otherwise you just get a grey screen) and restart the xrdp service:
```
[/FONT]
[FONT=Calibri]echo xfce4-session>~/.xsession[/FONT]
[FONT=Calibri]sudo service xrdp restart[/FONT]
[FONT=Calibri]
```

This works externally though so you might want to block it with the firewall.

Hope it helps.
Robin[/FONT]

---

