---
title: "Installing desktop Ubuntu on a server"
date: 2007-06-19
forum: Server Platforms
---

### Post by jrjazzman on 2007-06-19
Are there any downsides to installing Ubuntu Desktop on a server?  I'm leaning toward Desktop because I'm more comfortable doing certain things in a GUI environment and I'll have VMWare intalled running a Windows VM, which will need graphics.  I'd think VMWare requires X, and I think Gnome that comes with Ubuntu Desktop would be the easiest way to have X.  Does anyone have any thoughts or suggestions on this?

thanks

Jeremy

---

### Post by JanvL on 2007-06-19
Hi,

I have a Samba-server also Apache running for testing
and loads od desktop-apps. Both Gnome and KDE.
All on Kubuntu Dapper LTS.

No problem at all.

Depends of course how havy the system will be used and
how much hardware you have.

Jan

---

### Post by Znupi on 2007-06-19
I used Xubuntu for the same purpose (except for the Windows VM, I really don't see why you'd have that on a server :|). After I set everything up, to save some RAM and CPU I rebooted, at the login screen I hit Ctrl+Alt+F2, logged in and typed
```

sudo /etc/init.d/gdm stop

```
That should work for you, too.

---

### Post by bukwirm on 2007-06-19
A GUI adds more stuff to a server install -> consumes additional resources. If you really need a GUI i'd suggest something lighter than GNOME, such as Xubuntu or Fluxbox.
Also, it adds more potential security exploits (That's probably not a huge deal, though).

---

### Post by MrHorus on 2007-06-19
> **bukwirm said:**
> 
Also, it adds more potential security exploits (That's probably not a huge deal, though).

Err it's absolutely a huge deal.

You should never run any unwanted daemons on a server as anything that you install that you don't need could potentially be exploited and used to attack you.

Look at OpenBSD for am example - quite apart from comprehensive code audits, part of the reason they have only ever had 2 (yes TWO) remote exploits in the default install is because the default install ships with everything turned off - you have to explicitly enable something if you need it.

---

### Post by psusi on 2007-06-19
> **MrHorus said:**
> 
Look at OpenBSD for am example - quite apart from comprehensive code audits, part of the reason they have only ever had 2 (yes TWO) remote exploits in the default install is because the default install ships with everything turned off - you have to explicitly enable something if you need it.

Nifty that Ubuntu is the same way isn't it?

A desktop install is fine on a server... a few extra megs of disk space being used shouldn't even be noticed, and if you aren't using the gui actively it will be swapped out if needed.  If you really want to you can always shut it down when not in use.

I like to run the gui on my server and use tightvnc to connect to it like a terminal server.

---

### Post by dysolve on 2007-06-21
I have installed ubuntu desktop on my server so I can VNC in and update/check etc. I removed m/s NT4 to install ubuntu. The "windows" drive in NT4 took up something like 26gig ubuntu running all the same stuff still has not reached a gig. I had bought 2 16gig SCSI drives and 2 80 gig ide drives and each ran stand  alone.. I think I might start the ubuntu install all over again and raid the two scsi drives and mirror the two ide drives.. that should make for an interesting machine. now before I do this I would like to know something.. is the gui the only real differance between server and desktop??

---

