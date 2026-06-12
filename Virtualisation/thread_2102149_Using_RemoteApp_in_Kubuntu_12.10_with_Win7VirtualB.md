---
title: "Using RemoteApp in Kubuntu 12.10 with Win7/VirtualBox"
date: 2013-01-06
forum: Virtualisation
---

### Post by Nathanael Culver on 2013-01-06
My host system is 64-bit Kubuntu 12.10 with all the latest updates installed. I'm running VirtualBox 4.12 with a 32-bit Windows 7 Ultimate guest. I've installed FreeRDP 1.01 (the latest in the repositories). I'm using Kim Knight's RemoteApp tool to configure remote apps in the W7 VM.

I've spent most of the weekend trying to get RemoteApp functioning, first with an XP guest, and now with W7. I feel like I'm close. I've enabled remote apps in the Win7 guest. I start the Win7 VM headless, and can open a FreeRDP connection to it. Using the RemoteApp tool I've configured Notepad as a remote app in Win7.

But when I try the following:

```
xfreerdp -u myID -p myPWD --app --plugin /usr/lib/freerdp/rail.so --data "||Notepad" -- localhost
```

rather than getting Notepad on my desktop, I just get an RDP window with the W7 desktop.

What am I doing wrong?

--Nathanael

---

### Post by Nathanael Culver on 2013-01-07
BUMP.

Oh, and BTW I did use my actual username after -u in the command line I gave.

---

### Post by Nathanael Culver on 2013-01-08
Ne1?

---

### Post by Nathanael Culver on 2013-01-10
Bump bump

---

### Post by Nathanael Culver on 2013-01-11
Bump

---

### Post by mcirillo on 2013-04-23
Try using this tool on the guest:

[https://sites.google.com/site/kimknight/remoteapptool](https://sites.google.com/site/kimknight/remoteapptool)

---

