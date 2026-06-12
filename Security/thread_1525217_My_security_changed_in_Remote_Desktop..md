---
title: "My security changed in Remote Desktop."
date: 2010-07-06
forum: Security
---

### Post by irv on 2010-07-06
This was strange. I always use VNC to check my server for updates, and this morning I started the xvnc4viewer to vnc into my server and it keep asking for a password. I never setup a password because I do this local from my laptop, and I am the only one who uses my laptop. I had to go to my server and check the setting in System > Preferences > Remote Desktop and found them all changed. There was a password setup and there was a check mark in the you must confirm each access to this machine. Was there some security update that changed all these setting? Sometimes when I do updates I don't know what is being changed on my server. I found this to be very strange if this is the case.

---

### Post by yeleek on 2010-07-06
Is this 'server' accessible via the internet?  And if so on what ports?

I struggle to believe an ubuntu update would set a password on your vnc settings.  More likely to have been an individual - malicious or otherwise.

---

### Post by cdenley on 2010-07-06
> **yeleek said:**
> Is this 'server' accessible via the internet?  And if so on what ports?

Also, if your router allows upnp, then it will automatically port-forward if you check the "configure your network" checkbox.

---

### Post by HermanAB on 2010-07-06
Uhmmm, you are running VNC on a server and it is on the internet?  Your server will be rooted sooner or later.  Rather switch to SSH while it is still working.

---

### Post by irv on 2010-07-06
> **HermanAB said:**
> Uhmmm, you are running VNC on a server and it is on the internet?  Your server will be rooted sooner or later.  Rather switch to SSH while it is still working.

The remote desktop says:
> Your desktop is only reachable over the local network. Others can access your computer using the address 192.168.1.105 or irv-server.local.

I have tried to access my server over the Internet via VNC and it says that it is not available. The setting in remote desktop is clear on this with the above statement.
[ATTACH]162632[/ATTACH]

---

### Post by irv on 2010-07-06
> **cdenley said:**
> Also, if your router allows upnp, then it will automatically port-forward if you check the "configure your network" checkbox.

I checked my router and can not find upnp setting, and I am not sure what you are talking about "check in configure your network checkbox". I have a Linksys router.

---

### Post by irv on 2010-07-06
> **yeleek said:**
> Is this 'server' accessible via the internet?  And if so on what ports?

I struggle to believe an ubuntu update would set a password on your vnc settings.  More likely to have been an individual - malicious or otherwise.

Are you talking about FTP: port 21
or HTTP: port 80
or HTTPS: port443.

---

### Post by cariboo on 2010-07-06
The setting they are talking about is in System->Preference->Remote Desktop, see the screen shot.

---

### Post by cdenley on 2010-07-06
> **irv said:**
> i checked my router and can not find upnp setting, and i am not sure what you are talking about "check in configure your network checkbox". I have a linksys router.

[attach]162629[/attach]

---

### Post by Rubi1200 on 2010-07-06
> **irv said:**
> I checked my router and can not find upnp setting, and I am not sure what you are talking about "check in configure your network checkbox". I have a Linksys router.

Hi irv, I am not familiar with Linksys routers but I believe uPnP is accessible via the Administration tab.

---

### Post by irv on 2010-07-06
> **cdenley said:**
> [attach]162629[/attach]

Here are my setting on the server.
[ATTACH]162633[/ATTACH]

---

### Post by irv on 2010-07-06
> **Rubi1200 said:**
> Hi irv, I am not familiar with Linksys routers but I believe uPnP is accessible via the Administration tab.

Yes I found it, and it is Enable.

---

### Post by cdenley on 2010-07-06
Well, whether you allowed VNC connection over the internet or not, if someone set a password for "remote desktop", they probably had access to your system somehow at some point. My guess would be that you had previously checked the box I mentioned.

---

### Post by irv on 2010-07-06
> **cdenley said:**
> Well, whether you allowed VNC connection over the internet or not, if someone set a password for "remote desktop", they probably had access to your system somehow at some point. My guess would be that you had previously checked the box I mentioned.

When I checked it this morning it was checked but I don't remember doing it. But I guess I can not say 100% that I didn't do it. I do forget things once in awhile and I am always fooling around with settings etc.

---

### Post by HermanAB on 2010-07-07
Hmm, if your password is 8 characters or less, then chances are that an automated VNC script already compromised your machine for you.

The bottom line is that VNC behind a home router is an eeevulll combination.  There are many tales of VNC woe on these forums.

---

### Post by movieman on 2010-07-07
> **HermanAB said:**
> The bottom line is that VNC behind a home router is an eeevulll combination.

And UPnP is an insane idea, at least for routers.

---

