---
title: "Boot hangs after last night's update"
date: 2014-04-04
forum: Ubuntu Development Version
---

### Post by drfox on 2014-04-04
Boot is hanging. I tried installing cgmanager (as per another reported bug), but that didn't help. This is what I'm seeing the last few lines of the boot:

*Stopping Light DM Display Manager  [OK] 
lightdm
startpar-bridge
startpar-bridge
rc
*Stopping System V runlevel compatibility  [OK]
tty1
ureadahead
*Stopping Read required files in advance  [OK]
startpar bridge
startpar bridge

Thanks for any help

---

### Post by 23dornot23d on 2014-04-04
I can confirm that too ..... getting the very same thing ......

in fact after it ......... 

I have to now run kdm to get a login screen to appear

**sudo apt-get install kdm**

then

**kdm**

at least you get a login screen and choices of desktop then

if I just try to run lightdm it fails .....

---

### Post by zika on 2014-04-04
> **drfox said:**
> Boot is hanging. I tried installing cgmanager (as per another reported bug), but that didn't help. This is what I'm seeing the last few lines of the boot:

*Stopping Light DM Display Manager  [OK] 
lightdm
startpar-bridge
startpar-bridge
rc
*Stopping System V runlevel compatibility  [OK]
tty1
ureadahead
*Stopping Read required files in advance  [OK]
startpar bridge
startpar bridge

Thanks for any help
Try booting with &#8222;text&#8220; in kernel-boot-line and then investigate (in tty) what is happening with LightDM...
I would say that ih has to do with: [http://ubuntuforums.org/showthread.php?t=2214867](http://ubuntuforums.org/showthread.php?t=2214867)
In that case You should upgrade once You get into tty...
It looks that there is thread with same/similar problem: [http://ubuntuforums.org/showthread.php?t=2214960](http://ubuntuforums.org/showthread.php?t=2214960) or there might be two separate truobles lurking these days...

---

### Post by drfox on 2014-04-04
Not sure how or if this "solves" the problem, but I issued the command "sudo dpkg-reconfigure lightdm" (make sure the system is read/write) and it now boots OK.
I'll wait for comments before marking this thread "solved"

---

### Post by 23dornot23d on 2014-04-04
I just tried that command too ...... sudo dpkg-reconfigure lightdm

Although I can get into Unity now ..... the lightdm does not show up at all ....... 

Here is the unity shot with the top bar blank of icons or choices ..... but it is working now but lightdm is being bypassed or so it seems

[IMG]http://i.minus.com/ibmODFSaOpPjki.png[/IMG]

I just get a black screen then it seems to go straight into unity with no screen to see or choose from
with no lightdm splash appearing - or login ........ odd as I also cannot logout to see if it will show up

Seems autogin is setup on this - but I cannot remember setting it up - unless it was on the initial install - but kdm does not autolog me in

> 
Apr  4 13:39:28 keith-K53SV lightdm: pam_unix(lightdm-autologin:session): session opened for user keith by (uid=0)
Apr  4 13:39:28 keith-K53SV systemd-logind[913]: New session c2 of user keith.
Apr  4 13:39:28 keith-K53SV systemd-logind[913]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Apr  4 13:39:28 keith-K53SV lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0


having to do ctrl+alt+f1 and then start kdm to get to a login screen ........

I did find another way  ctrl+alt+del brings up the process screen now ...... and kill off the session it actually logs out
and restarts lightdm ........ handy when the top bar is missing and no other way exists to just logout.

---

### Post by sammiev on 2014-04-04
I used ctrl+alt+f1 and signed in.

```
sudo apt-get update && sudo apt-get upgrade
```

Everything back to normal.

---

### Post by david98 on 2014-04-04
+1 for sammiev same thing resolved after [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update && sudo apt-get upgrade[/FONT][/COLOR]

---

### Post by drfox on 2014-04-09
Thanks everyone. Marked as solved!

---

