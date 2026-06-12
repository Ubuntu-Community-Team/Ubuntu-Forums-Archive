---
title: "Native Wine File Browser (to get Linksys QuickVPN working)"
date: 2009-04-29
forum: Wine
---

### Post by jmjohn on 2009-04-29
Hey all,

I'm looking for a native wine file browser that will accept UNC pathnames like \\10.10.10.10.2.  I've tried winefile but that doesn't allow UNC pathnames.

I'm trying to look through a VPN I've set up with the Linksys QuickVPN client under wine.  Nautilus and Konqueror know nothing of the wine-created tunnel, so I have to look through it some other way.

I know this can be done ( [http://joey.ubuntu-rocks.org/blog/2007/11/29/linksys-quickvpn-under-gutsy/](http://joey.ubuntu-rocks.org/blog/2007/11/29/linksys-quickvpn-under-gutsy/) ) but I'm just looking for the file browser to look through it.

Thanks,
glass.dimly

---

### Post by cogadh on 2009-04-29
Is there a reason you have to use a VPN client through Wine and can't just use one of the Linux native ones? Using Wine would seem to add an extra measure of frustration that just isn't necessary.

---

### Post by jmjohn on 2009-04-29
Yeah, I've definitely tried the native Linux VPN clients as described here: [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient) .  

I can't get them to work by plugging in the username and password provided by my wife's tech guy.  I can't generate a .pem file because I don't have access to the router.

However, QuickVPN under wine connects and creates the tunnel, I just can't browse through it.

So, does anyone know of a wine file browser that will accept UNC pathnames like \\10.10.10.10.2?

Thanks,
glass.dimly

---

### Post by asdfoo on 2009-04-29
UNC paths are for SMB networking (samba) which Wine doesn't handle yet

The only workaround is to mount/connect them outside of Wine then configure them as a drive letter in winecfg to access the contents.

---

### Post by jmjohn on 2009-04-29
If I were able to mount the drive I wouldn't need to use a wine-installed VPN client.  I want to go the other way, that is, make Nautilus aware of a wine VPN client.

Again, I need to look through a VPN tunnel created by a wine-installed VPN client.  My problem could be solved in three ways, as I see it:
[LIST=1]
[*]Make Nautilus aware of the VPN tunnel
[*]Install a file broswer in wine that would be privy to the same information that windows explorer were privy to
[*]Figure out how to set up the VPN with a native linux app.
[/LIST]

Can anyone help me with either of the first two?

Thanks,
glass.dimly

---

### Post by wsonar on 2009-04-29
> **cogadh said:**
> Is there a reason you have to use a VPN client through Wine and can't just use one of the Linux native ones? Using Wine would seem to add an extra measure of frustration that just isn't necessary.

I would love to find a nortel alternative that's open-source

that's what we use at my job

---

### Post by jmjohn on 2009-05-21
Hey all,

Does anyone have any idea how I might go about this?  Still searchin...

---

### Post by CescG on 2009-07-22
> **jmjohn said:**
> Hey all,
 
Does anyone have any idea how I might go about this? Still searchin...
 
 
Hi JmJohon
 
Have same problem here.  Do you solve it ?

---

### Post by jmjohn on 2009-10-14
No solution yet.  Anyone?

---

### Post by startlinuxtoday on 2010-07-04
LISTEN UP there if you are still there.... 
problem.... enable some sort of networking for file access between 2 devices where the devices are NOT of the same ip/mask!!

your attempts to use vpn via router and msos have serious comptibility and issues especially with msos updates forever and a day.

SOLUTION.... webmin.

---

