---
title: "Gnome3 Staging PPA is broken ATM"
date: 2013-02-24
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-02-24
I just upgraded my 64-bit setup (nvidia 285GTS graphics card) with the latest packages in the Gnome3 Staging PPA.
There are a number of gnome (3.7.90) packages available now.

However, after upgrading, the GDM (3.7.90) is not working anymore, no login window.
Also (from tty1) startx is not working either, X is broken.

So please do not upgrade until this is solved.

If you choose to test, however, you may upgrade all other packages, but not gnome-contol-center (3.7.90) and gnome-settings-daemon (3.7.90). Leave them to 3.7.5.
It seems they will break the X.

By doing the above, GDM (3.7.90) may still not work, but you can login from tty! and use the "startx" command there. X will now work.

I found that gnome-shell (3.7.90), mutter (3.7.90), gjs (1.35.8), clutter-1.0 (1.13.6), gnome-desktop3 (3.7.90) and gtksourceview3 (3.7.90) are all OK.
Also cogl (1.13.4) do work (this will remove old cogl packages libcogl11 and libcogl-pango0 and libmx-1.0-2, because of the soname bumb).

GDM is not OK.
If you install that one, you may need to login from tty1 like I wrote above.

So, do not upgrade gnome-control-center nor gnome settings-daemon ATM.

---

### Post by zika on 2013-02-24
> **Harry33 said:**
> I just upgraded my 64-bit setup (nvidia 285GTS graphics card) with the latest packages in the Gnome3 Staging PPA.
There are a number of gnome (3.7.90) packages available now.

However, after upgrading, the GDM (3.7.90) is not working anymore, no login window.
Also (from tty1) startx is not working either, X is broken.

So please do not upgrade until this is solved.

If you choose to test, however, you may upgrade all other packages, but not gnome-contol-center (3.7.90) and gnome-settings-daemon (3.7.90). Leave them to 3.7.5.
It seems they will break the X.

By doing the above, GDM (3.7.90) may still not work, but you can login from tty! and use the "startx" command there. X will now work.

I found that gnome-shell (3.7.90), mutter (3.7.90), gjs (1.35.8), clutter-1.0 (1.13.6), gnome-desktop3 (3.7.90) and gtksourceview3 (3.7.90) are all OK.
Also cogl (1.13.4) do work (this will remove old cogl packages libcogl11 and libcogl-pango0 and libmx-1.0-2, because of the soname bumb).

GDM is not OK.
If you install that one, you may need to login from tty1 like I wrote above.

So, do not upgrade gnome-control-center nor gnome settings-daemon ATM.
Too late, already stepped into that...
But I'm working from fallback from startx... ;)
[http://ubuntuforums.org/showpost.php?p=12526981&postcount=234](http://ubuntuforums.org/showpost.php?p=12526981&postcount=234)
Fingers crossed...

Question:
I know how to start almost all sessions from .xinitrc (.Xsession) but what is the line for fallback **with** compiz...?
For fallback without affects I have /usr/bin/gnome-session-fallback ...
Update&#8321;: Got it... ;)
```
/usr/bin/gnome-session --session=gnome-fallback-compiz
```...
That is a hidden bonus of all troubles: they make You read stuff You were reluctant to read otherwise...

---

### Post by dino99 on 2013-02-24
is it with all these ppas activated ?

ricotz now says:
 if you want to use ppa:ricotz/testing you are suppose to add ppa:gnome3-team/gnome3 and ppa:gnome3-team/gnome3-staging too.

):P

---

### Post by zika on 2013-02-24
> **dino99 said:**
> is it with all these ppas activated ?

ricotz **now** says:
 if you want to use ppa:ricotz/testing you are suppose to add ppa:gnome3-team/gnome3 and ppa:gnome3-team/gnome3-staging too.

):PHe was saying that even before this...
Adding either ricotz-staging or ricotz-testing or both does not solve the problem since there is no (as far as could see) newer gdm there...
That was, of course, the first thing that I've tried...

---

### Post by Harry33 on 2013-02-24
> **zika said:**
> He was saying that even before this...
Adding either ricotz-staging or ricotz-testing or both does not solve the problem since there is no (as far as could see) newer gdm there...
That was, of course, the first thing that I've tried...

This is correct.
I have not enabled Gnome Testing PPA, so I use only Gnome3 Staging PPA and from Gnome3 PPA I have installed gnome-control-center-signon (0.1.2bzr12.12.05-0ubuntu2~raring1.
That is because gnome-control-center (3.7.5) depends on that too.

---

### Post by Harry33 on 2013-02-24
> **zika said:**
> Too late, already stepped into that...
But I'm working from fallback from startx... ;)
[http://ubuntuforums.org/showpost.php?p=12526981&postcount=234](http://ubuntuforums.org/showpost.php?p=12526981&postcount=234)
Fingers crossed...

Question:
I know how to start almost all sessions from .xinitrc (.Xsession) but what is the line for fallback **with** compiz...?
For fallback without affects I have /usr/bin/gnome-session-fallback ...
Update&#8321;: Got it... ;)
```
/usr/bin/gnome-session --session=gnome-fallback-compiz
```...
That is a hidden bonus of all troubles: they make You read stuff You were reluctant to read otherwise...

If you have fully upgraded your setup with Gnome3 Staging PPA, you can always download the gnome-control-center (3.7.5) and gnome-settings-daemon (3.7.5.1) and then downgrade your set up manually with dpkg.
For download you may use wget from tty1.

Those packages are still available from the pool of the Gnome3 Staging PPA.

Here (gnome-control-center 3.7.5 and gnome-control-center-data 3.7.5):
[http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-control-center/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-control-center/)

and here (gnome-settings-daemon 3.7.5.1):
[http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-settings-daemon/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-settings-daemon/)

---

### Post by zika on 2013-02-24
> **Harry33 said:**
> If you have fully upgraded your setup with Gnome3 Staging PPA, you can always download the gnome-control-center (3.7.5) and gnome-settings-daemon (3.7.5.1) and then downgrade your set up manually with dpkg.
For download you may use wget from tty1.

Those packages are still available from the pool of the Gnome3 Staging PPA.

Here (gnome-control-center 3.7.5 and gnome-control-center-data 3.7.5):
[http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-control-center/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-control-center/)

and here (gnome-settings-daemon 3.7.5.1):
[http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-settings-daemon/](http://ppa.launchpad.net/gnome3-team/gnome3-staging/ubuntu/pool/main/g/gnome-settings-daemon/)
Thank You for a hint. I'm (still) OK with startx and I'll take this only in dire case that it breaks even more...
Simply put, not enough quality time to fiddle with all that especially since all stuff that I need still work...
Update&#8321;: You made me test: LightDM still works OK with GSF so... That could be easy makeshift solution.
Update&#8322;: GDM upgrade solved this issue, thank You all!

---

### Post by Harry33 on 2013-02-24
Confirming, the Gnome3 Staging PPA is working now.
GDM login screen looks a bit different with the opening on-screen keyboard.

Also the Desktop opens (growing from the center point) somehow over the background image.

However, this is solved for now.

---

