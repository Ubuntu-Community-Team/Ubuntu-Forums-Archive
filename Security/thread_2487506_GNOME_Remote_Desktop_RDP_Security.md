---
title: "GNOME Remote Desktop RDP Security"
date: 2023-06-07
forum: Security
---

### Post by mihail-mm on 2023-06-07
Ubuntu 23.04 How to enable two-factor authentication for g-r-d 44.0?Or what ways of additional authorization security are there?

---

### Post by TheFu on 2023-06-07
VNC and RDP both need to use ssh tunnels to be secure.

Or you can use an NX-based remote desktop like **x2go** (F/LOSS). There are commercial versions of NX too.  x2go has clients for the main 3 OSes.  To my knowledge, the server only runs on Linux.  There are alternative clients. I've never used any except the x2go-client.  Tried to get remina (or whatever it is called) to work, but it just seemed like bloat for the needs.  The x2go-client has a sufficient GUI that nobody really should be unhappy with it.  Just find the project website, add their PPA to your server and client, then install as normal.

Or if not going over the internet, just use X11-forwarding through ssh.  This is the normal way that remote programs are run on any LAN.
```
ssh -X user@remote-server command
```
ssh has supported this mode since the mid-1990s.  It is kinda sad that normal people don't know how good this is.

Then you would use 2FA with ssh, like normal.

The way to know if you are doing RDP/VNC security correctly, is if those servers only allow **localhost** connections and each client is connecting to the remote system using a localhost port.  Effectively, RDP and VNC don't know about the tunnels.  ssh is the most common tunnel used, but a full VPN like wireguard or openvpn can be used as well.  On computers, ssh is the easiest to setup, but if you want/need access to a remote desktop from a tablet, then the VPNs are easier.

Obviously **ssh** is needed for most of these.  Since ssh is how Unix systems are connected and managed, that should already have been put in place by any competent admin.  ssh is the only package I install on all my servers that is technically "optional".  No admin would consider ssh optional. Heck, on my workstation right now, I have about 15 terminals connected to other systems all over ssh using key-based authentication.

Full remote desktops only get used for remote internet connections here, almost never on the LAN (except for testing). They are extremely inefficient.

---

### Post by mikodo on 2023-06-07
> **TheFu said:**
> 
All that you wrote here ...

I just want to complement you. It seems lately, your posts have been more detailed oriented. With you offering different options and suggestions, as to why you think some are more viable. Maybe, it is only me here paying more attention, to what you have posted lately, but I really think not. I have always read your posts with carefulness.

This post of yours is a fine example, of what I wrote above.

Thank you.

---

### Post by vbgf3 on 2023-06-13
In addition, there is TeamViewer Free for Linux, And it has 2FA . The password can be made  to be valid for 1 time use only.

---

### Post by TheFu on 2023-06-14
> **vbgf3 said:**
> In addition, there is TeamViewer Free for Linux, And it has 2FA . The password can be made  to be valid for 1 time use only.

The only problem with Teamviewer is that it requires trusting an outside company for their security and nobody gets to audit their code for poor security.
I have that issue with wiz-bang VPN services too.  If I can't use a standard VPN client, not from the VPN service, but from the Canonical repos, then I'm not interested.  I want to know that they haven't molested the software for their gain.  If they want to charge me money, just charge money after a free trial.  Having a nearly unlimited "free trial" bothers me.  Seems very much like a drug pusher.  Lots of companies follow the "drug pusher" model, which I avoid.  

Remember, if you aren't paying for a service, then you and your data are the product being sold.  That's nearly always true.

---

