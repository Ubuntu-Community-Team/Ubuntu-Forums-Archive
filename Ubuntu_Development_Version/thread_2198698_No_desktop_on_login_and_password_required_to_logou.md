---
title: "No desktop on login and password required to logout."
date: 2014-01-10
forum: Ubuntu Development Version
---

### Post by Bucky Ball on 2014-01-10
Hi all,

I have 14.04 mini install with xfce4. Having a few probs. I have installed xdm, but when I login it doesn't take me to a desktop. Also, when I logout it asks for password. Have I missed something? I tried a few; slim, lxdm (which dragged in a lot of lxde stuff), but none take me to a desktop. 

When I don't use a login manager I boot to Trusty and am taken to a CLI screen where I can login, pw, then 'startxfce4' and it boots to a desktop. But now it has started giving me a choice of 'default' 'logout' or 'new session'. If I hit 'new session' I'm asked to input a name for the new session.

Having fun fiddling, nonetheless. ;)

PS: I have a feeling perhaps there should be something installed that's not because I lack permissions to do a few things. I'll post new threads about the major probs. :-k

---

### Post by Bucky Ball on 2014-01-10
This from dmesg:

```
[   14.444229] init: slim main process (817) terminated with status 127
[   14.538402] init: lxdm main process (889) killed by TERM signal
[   14.750947] init: plymouth-stop pre-start process (928) terminated with status 1
```

Even though slim and lxdm are no longer installed this is still showing up?

---

### Post by QDR06VV9 on 2014-01-10
> **Bucky Ball said:**
> This from dmesg:

```
[   14.444229] init: slim main process (817) terminated with status 127
[   14.538402] init: lxdm main process (889) killed by TERM signal
[   14.750947] init: plymouth-stop pre-start process (928) terminated with status 1
```

Even though slim and lxdm are no longer installed this is still showing up?
lightdm? Maybe.

---

### Post by Bashing-om on 2014-01-10
Bucky Ball;

Ya want to remove the xfce4 config files for the desk top and start all over from the default settings ?

Might want to try simpler things first:
I have seen problems in the xfce session and it is due to the window manager crashing . Because I run different sessions I see this once in a blue moon. The following command or restarting usually solves the problem.
xfwm4 --replace
else:++
xfwm is the window manager, it has nothing to do with the panels.
Maybe the session cache got corrupted.
First try starting the panel with
xfce4-panel &
Anyway, your panel settings are safe in ~/.config
You can also clear the session cache: logout, ctrl+alt+f2, login in the text console and
rm -rf .cache/sessions
then ctrl+alt+f7 and try and login again.

Elseif: One can get even more drastic and remove all the config files and start over from defaults. 

It is amazing how complex this wonderful operating system is;
[INDENT][INDENT]there are solutions
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-01-10
Okay, I purged the login/display managers I'd tried and that seemed to do the trick. Then this got rid of the sessions selection at boot:

```
rm -rf .cache/sessions
```

Thanks for that. ;) Now I am still getting asked for password at logout and here is more detail:

> Authorisation is required for rebooting the system. An application is attempting to perform an action that requires privileges.

Then under the 'details' arrow:

> Action: org.freedesktop.login1.reboot
Vendor: the systemd project

Getting a bit tricky now as for some reason Network Manager is suddenly unavailable in 14.04. I could get online via a cable at least, but now nothing. Already started a thread about the dodgy Network Manager here:

[http://ubuntuforums.org/showthread.php?t=2198703](http://ubuntuforums.org/showthread.php?t=2198703)

So, we got rid of the sessions window after login but the original issues remain:
- No login manager will take me to a desktop (does it need to be told 'startxfce4'?);
- Need to input password to log out (which takes me back to CLI where I need to issue 'sudo reboot').

lightdm, gdm, xdm, lxdm all drag in so much junk I don't need, and being a minimal install, I'm reluctant to go there. Slim seemed passable, despite the fact it is so ugly. Apparently it has a few configuration options.

---

### Post by Bucky Ball on 2014-01-11
Bit the bullet and installed gdm. Problem solved. Boots to a handsome login screen and when I choose xfce session I'm in. Log out, not asked for password.

Thanks for the help. gdm does drag in a whole lot of stuff I just don't need. Is there a better way?

So, thread resolved by dragging in a heap of stuff I didn't really want and don't need. I might fiddle with SLiM somemore and see where that gets me. ;)

---

### Post by Bashing-om on 2014-01-11
Bucky Ball; Ouch on the dragging in unwanted stuff !

Look, why do you even want a login manager ? As far as I am concerned it is more "cruft" !

I have set up ~/.xinitrc to start my Xserver:
---------
The ~/.xinitrc file is a shell script read by xinit and startx. It is mainly used to execute desktop environments, window managers and other programs when starting the X server.

It workie great, and last long time but, as they say -> YMMV.

[INDENT][INDENT]cheerfully, as on we go
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2014-01-11
Would that work okay with xfce4? I purged gdm and am currently trying lightdm which also works okay, but again, drags in a ton.

PS: Just found this:

[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

I'm getting the idea. Will delve deeper when I wake up a bit. ;)

---

### Post by Bucky Ball on 2014-01-18
> **Bucky Ball said:**
> Hi all,

But now it has started giving me a choice of 'default' 'logout' or 'new session'. If I hit 'new session' I'm asked to input a name for the new session.

For those who are interested, this was an easy fix in the end. Apps>Settings>Sessions and Startup>General>untick 'Display chooser on login'. 

That's it. Discovered it by accident when I was doing something else. 

I am using Lightdm for the moment, but can't say I love it. It's working. I will get around to trying some other (hopefully more lightweight) options shortly. ;)

---

### Post by Bashing-om on 2014-01-18
Bucky Ball; hey !

You are practicing to be an expert in xfce4 !

[INDENT][INDENT]who ya gonna call
[INDENT][INDENT][INDENT]Bucky Ball ![/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

