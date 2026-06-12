---
title: "Strange Epiphany Error"
date: 2006-07-29
forum: Ubuntu System Panel
---

### Post by Jedeye on 2006-07-29
I get a error when I try to launch Epiphany from USP. It works fine when I first boot up, but if I close Epiphany, and then later try to relaunch it I get the following error
```

Startup failed because of the following error:
Failed to connect to socket /tmp/dbus-nfEATsHkpA: Connection refused
```
But I can still launch it fine from a launcher that I put on the panel. I attached a screen shot to make it easy to see what is happening. 

any clues? should this be in another forum?

Thanks

---

### Post by chanders on 2006-07-29
> **Jedeye said:**
> I get a error when I try to launch Epiphany from USP. It works fine when I first boot up, but if I close Epiphany, and then later try to relaunch it I get the following error
```

Startup failed because of the following error:
Failed to connect to socket /tmp/dbus-nfEATsHkpA: Connection refused
```
But I can still launch it fine from a launcher that I put on the panel. I attached a screen shot to make it easy to see what is happening. 

any clues? should this be in another forum?

Thanks

This thread is fine... Try removing the %U in the launcher let me know if it works...

(I am working on this as we speak so hopefully in a few hours everything should be good)

---

### Post by Jedeye on 2006-07-29
> **chanders said:**
> This thread is fine... Try removing the %U in the launcher let me know if it works...

(I am working on this as we speak so hopefully in a few hours everything should be good)

Nope... same error

---

### Post by chanders on 2006-07-29
> **Jedeye said:**
> Nope... same error

Hmmmm... see if it is still running when you close it (after running from usp)... will have to investigate further....

---

### Post by scxtt on 2006-07-29
looks to be more of a problem w/ a socket in your /tmp directory ... take a look (maybe an **ls -l /tmp**) at that file and see who owns it, should be your user (possibly delete it) or if anything looks out of place ...

---

### Post by Jedeye on 2006-07-29
> **chanders said:**
> Hmmmm... see if it is still running when you close it (after running from usp)... will have to investigate further....
Epiphany does not show up in processes after I quit
> **scxtt said:**
> looks to be more of a problem w/ a socket in your /tmp directory ... take a look (maybe an **ls -l /tmp**) at that file and see who owns it, should be your user (possibly delete it) or if anything looks out of place ...
I did not see anything strange but im not sure what im supose to be looking for
```
jon@dapper:/$ ls -l /tmp
total 44
drwx------ 3 jon  jon  4096 2006-07-29 12:37 gconfd-jon
drwx------ 2 root root 4096 2006-07-29 18:16 gconfd-root
srwxr-xr-x 1 jon  jon     0 2006-07-29 18:27 gnome-system-monitor.jon.786553109
drwxr-xr-x 2 jon  jon  4096 2006-07-29 18:03 hsperfdata_jon
drwx------ 2 jon  jon  4096 2006-07-29 18:03 keyring-NhyUrR
drwx------ 2 jon  jon  4096 2006-07-29 18:15 libgksu1.2-FrosMd
srwxr-xr-x 1 jon  jon     0 2006-07-29 18:04 mapping-jon
srwxr-xr-x 1 root root    0 2006-07-29 12:37 mapping-root
drwx------ 2 jon  jon  4096 2006-07-29 18:35 orbit-jon
drwx------ 2 root root 4096 2006-07-29 18:16 orbit-root
srwxr-xr-x 1 jon  jon     0 2006-07-29 16:53 OSL_PIPE_1000_SingleOfficeIPC_680-352b4d00
drwx------ 2 jon  jon  4096 2006-07-29 17:27 plugtmp
drwx------ 2 jon  jon  4096 2006-07-29 18:03 plugtmp-1
drwx------ 2 jon  jon  4096 2006-07-29 18:03 ssh-vMvDN19884
drwx------ 2 jon  jon  4096 2006-07-29 18:04 virtual-jon.OdFrmI

```

---

### Post by scxtt on 2006-07-29
have you restarted since this epiphany problem started?

---

### Post by Jedeye on 2006-07-29
> **scxtt said:**
> have you restarted since this epiphany problem started?
Yes... and the strange thing is I can launch it after a restart... but after shutting down Epiphany I am unable to relaunch it from USP... but a launcher that I just put on the panel works fine.

---

### Post by scxtt on 2006-07-29
maybe it's an issue w/ the dbus daemon ... ?

one idea i have, not sure if it would cause another problem (until a reboot), would be to do a **sudo /etc/init.d/dbus restart** after you get the error, then try again ...

---

### Post by _profox on 2006-07-29
Works fine here... (running the 0.29 version of USP)

---

### Post by Jedeye on 2006-08-03
Just a update. It has been working perfectly since I upgraded to .31

Dont know what the change was but nice work! Thanks :)

---

### Post by DBO on 2006-08-22
> **Jedeye said:**
> Just a update. It has been working perfectly since I upgraded to .31

Dont know what the change was but nice work! Thanks :)

I still get this issue after a log out of some form.

---

### Post by stalefries on 2006-08-27
Maybe I can help. I've had this problem also, but in a slightly different form. I use the Deskbar applet, mostly to open the one or two websites I visit each day without waiting for my browser to open. One day, seemingly randomly, Epiphany refused to oen in the same manner. But opening it from a launcher on the panel worked. Does USP use some sort of D-BUS method or something to launch it? That's what seems most likely to me.

---

### Post by chanders on 2006-08-27
USP doesnt use any bit of DBUS. DBO was getting this same error but it was solved by upgrading his kernel to 26 from the shipped 23... try it see if it helps...

---

### Post by mejy on 2006-08-29
Not sure if this will help, but I can launch epiphany from the terminal, menu bar and panel launchers, but I get that error when launching from SLAB, USP or the deskbar applet.

Also, a workaround involves changing the shortcut to 'dbus-launch epiphany %u'.  Any ideas?

Edit:  It's not actually a very good workaround, since each time you open epiphany from the menu while it's already running, it thinks the running instance has crashed and offers to recover it...

---

### Post by chanders on 2006-08-29
You are right, not a good work around... But since you are also getting the error in SLAB and deskbar, maybe you can send a bug report to the developers? Since USP doesnt use any DBUS stuff I think the error might originate in epiphany...

---

### Post by stalefries on 2006-08-29
I think that before we try this we should understand what's happening each time it gets launched. For example, mejy said that launching from the terminal, from a panel launcher, and from the menu bar all work. 

When launching from the terminal, one only uses "epiphany". In the other 2 instances, I believe they use "epiphany %u", the "%u" allowing you to, for example, drag some sort of file or url for epiphany to open onto the icon.

This is where my knowledge of these things stops. How does USP launch it? I think deskbar uses some sort of dbus method to communicate to epiphany, but you said that you don't. And what about SLAB?

---

### Post by mejy on 2006-08-29
> **stalefries said:**
> I think that before we try this we should understand what's happening each time it gets launched. For example, mejy said that launching from the terminal, from a panel launcher, and from the menu bar all work. 

When launching from the terminal, one only uses "epiphany". In the other 2 instances, I believe they use "epiphany %u", the "%u" allowing you to, for example, drag some sort of file or url for epiphany to open onto the icon.

This is where my knowledge of these things stops. How does USP launch it? I think deskbar uses some sort of dbus method to communicate to epiphany, but you said that you don't. And what about SLAB?

AFAIK, %u is generally the first argument passed to a menu item/launcher etc (ie. anything dragged onto it), and if the argument is empty, as is the case is nothing is dragged onto it, then "%u" will be converted to "", so the launch command will simply end up as "epiphany".  (Or atleast that's how it would work with C++/Windows - I'm not too sure about Python/Linux).

Also, removing %u with alacarte or manually at /usr/share/applications/epiphany.desktop has no effect on the error.

Does anyone know of any other d-bus applications, so we can tell if it is d-bus or epiphany at fault?  Also, seeing as running it from the terminal, is USP using a non-standard method to launch epiphany?  One more thing - alt+f2 epiphany works fine to.

Important EDIT:  In deskbar-applet, 'Execute epiphany' causes the error, but 'Launch Epiphany' doesn't.

---

### Post by mejy on 2006-08-29
I've filed a d-bus bug at [https://bugs.freedesktop.org/show_bug.cgi?id=8066](https://bugs.freedesktop.org/show_bug.cgi?id=8066).

---

### Post by chanders on 2006-08-29
USP removes all leading arguments so essentially it is just launching epiphany and not epiphany %u. This should cause epiphany to run normally just as if typed in a terminal, seeing that it isnt I am assuming the error lies in epiphany but maybe my logic is flawed somewhere..

---

