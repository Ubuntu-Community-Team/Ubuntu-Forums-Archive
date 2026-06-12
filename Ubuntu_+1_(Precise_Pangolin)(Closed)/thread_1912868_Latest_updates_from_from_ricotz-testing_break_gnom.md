---
title: "Latest updates from from ricotz-testing break gnome-shell"
date: 2012-01-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2012-01-21
You may find that gnome-shell won't load any more. The culprits (for me anyway) are the latest updates of **gjs** and **libgjs0c** from ricotz-testing.

---

### Post by bmbaker on 2012-01-21
hmmm ya this just happened to me i reverted to an ealier version and disabled ricotz/testing for the moment!

---

### Post by ashishsvit on 2012-01-21
can anyone help me for the making the ubuntu server 10.04 to start the gui and internt

---

### Post by paul_in_london on 2012-01-21
> **ashishsvit said:**
> can anyone help me for the making the ubuntu server 10.04 to start the gui and internt

Are you sure you're posting in the right thread/sub-forum? Do you mean **10.04** or **12.04**?

We would need some more details to be able to try and help you.

---

### Post by paul_in_london on 2012-01-21
To compound the problem, precise isn't really usable for me at the moment because I can't choose another type of session like gome-classic or fallback (the only other option lightdm seems to give me is a guest login). I hadn't noticed until now that the session chooser thingy isn't there any more. I can do this in oneiric, but not in precise.

---

### Post by paul_in_london on 2012-01-21
Fixed now with another couple of updates in oneiric anyway.

Will just check precise again.

EDIT: Nope. Was also broken in oneiric and is now working again, but no more precise updates yet.

---

### Post by bmbaker on 2012-01-21
add a new user and log out and toggle between the users and the little cog should re-appear :-)

---

### Post by paul_in_london on 2012-01-21
> **bmbaker said:**
> add a new user and log out and toggle between the users and the little cog should re-appear :-)

Thanks. That's exactly it - in precise I have no cog on the lightdm login any more! Do I really have to add another user though? I'm not saying that's difficult, but is there no other way of fixing it at the moment?

---

### Post by zika on 2012-01-21
> **paul_in_london said:**
> Thanks. That's exactly it - in precise I have no cog on the lightdm login any more! Do I really have to add another user though? I'm not saying that's difficult, but is there no other way of fixing it at the moment?
Do You have in /etc/lightdm/lightdm.conf

```
[SeatDefaults]
...
allow-guest=false
...
```?

(Disclaimer: If I understood Your problem properly...)

---

### Post by paul_in_london on 2012-01-21
> **zika said:**
> Do You have in /etc/lightdm/lightdm.conf

```
[SeatDefaults]
...
allow-guest=false
...
```?

(Disclaimer: If I understood Your problem properly...)

Thanks zika. The guest login option still seems to be there for me in precise (although I haven't tried using it because it wouldn't solve my problem).

Because gnome-shell is still broken in precise at the moment I wanted to be able to choose another type of session (e.g. gnome classic or gnome fallback) before logging in [using my existing account] but there is no longer any way of doing that from the login screen. I hadn't noticed this until now - when I really wanted to do it!

---

### Post by paul_in_london on 2012-01-21
GS is now working again after more updates. :)

---

### Post by paul_in_london on 2012-01-24
GS has gone again for me:

```
paul@precise-64:~$ gnome-shell --replace &
[1] 15227
paul@precise-64:~$ 
Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Window manager error: Unable to initialize Clutter.
```

Apparently caused by one or more of these updates (details from /var/log/aptitude):

```
Log complete.
Aptitude 0.6.4: log report
Tue, Jan 24 2012 18:59:58 +0000

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 24 packages, and remove 0 packages.
946 kB of disk space will be used
===============================================================================
[HOLD] nvidia-current
[UPGRADE] firefox-trunk 12.0~a1~hg20120120r84955-0ubuntu1~umd1 -> 12.0~a1~hg20120123r85111-0ubuntu1~umd1
[UPGRADE] firefox-trunk-globalmenu 12.0~a1~hg20120120r84955-0ubuntu1~umd1 -> 12.0~a1~hg20120123r85111-0ubuntu1~umd1
[UPGRADE] firefox-trunk-gnome-support 12.0~a1~hg20120120r84955-0ubuntu1~umd1 -> 12.0~a1~hg20120123r85111-0ubuntu1~umd1
[UPGRADE] gnome-control-center 1:3.2.2-2ubuntu2 -> 1:3.2.2-2ubuntu3
[UPGRADE] gnome-control-center-data 1:3.2.2-2ubuntu2 -> 1:3.2.2-2ubuntu3
[UPGRADE] language-pack-en 1:12.04+20111229 -> 1:12.04+20120123
[UPGRADE] libavcodec53 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libavformat53 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libavutil51 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libgnome-control-center1 1:3.2.2-2ubuntu2 -> 1:3.2.2-2ubuntu3
[UPGRADE] libgpg-error0 1.10-1ubuntu1 -> 1.10-2ubuntu1
[UPGRADE] libnautilus-extension1a 1:3.2.1-2ubuntu11 -> 1:3.2.1-2ubuntu12
[UPGRADE] libpostproc52 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libswscale2 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libwayland0 0.1.0~git20120120.f66aa1d0-0ubuntu0ricotz -> 0.1.0~git20120124.10eefa49-0ubuntu0ricotz
[UPGRADE] libwnck-3-0 3.2.1-1 -> 3.2.1-1ubuntu1
[UPGRADE] libwnck-3-common 3.2.1-1 -> 3.2.1-1ubuntu1
[UPGRADE] midori 0.4.3+r4456-0~precise1 -> 0.4.3+r4457-0~precise1
[UPGRADE] nautilus 1:3.2.1-2ubuntu11 -> 1:3.2.1-2ubuntu12
[UPGRADE] nautilus-data 1:3.2.1-2ubuntu11 -> 1:3.2.1-2ubuntu12
[UPGRADE] notify-osd 0.9.32-0ubuntu4 -> 0.9.32-0ubuntu5
[UPGRADE] opera 11.61.1222 -> 11.61.1250
[UPGRADE] xserver-common 2:1.11.99.901+git20120120.954bb994-0ubuntu0ricotz -> 2:1.11.99.901+git20120124.e1085a0d-0ubuntu0ricotz
[UPGRADE] xserver-xorg-core 2:1.11.99.901+git20120120.954bb994-0ubuntu0ricotz -> 2:1.11.99.901+git20120124.e1085a0d-0ubuntu0ricotz
===============================================================================

Log complete.
```

```
paul@precise-64:~$ uname -a
Linux precise-64 3.3.0-030300rc1-generic #201201191835 SMP Thu Jan 19 23:36:54 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$
```

This is with X Server 1.11.99.901 (1.12.0 RC1) and nvidia 295.09.

Anyone else?

---

### Post by Harry33 on 2012-01-24
> **paul_in_london said:**
> GS has gone again for me:

```
paul@precise-64:~$ gnome-shell --replace &
[1] 15227
paul@precise-64:~$ 
Clutter-CRITICAL **: Unable to initialize Clutter: Unable to select the newly created GLX context
Window manager error: Unable to initialize Clutter.
```Apparently caused by one or more of these updates (details from /var/log/aptitude):

```
Log complete.
Aptitude 0.6.4: log report
Tue, Jan 24 2012 18:59:58 +0000

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 24 packages, and remove 0 packages.
946 kB of disk space will be used
===============================================================================
[HOLD] nvidia-current
[UPGRADE] firefox-trunk 12.0~a1~hg20120120r84955-0ubuntu1~umd1 -> 12.0~a1~hg20120123r85111-0ubuntu1~umd1
[UPGRADE] firefox-trunk-globalmenu 12.0~a1~hg20120120r84955-0ubuntu1~umd1 -> 12.0~a1~hg20120123r85111-0ubuntu1~umd1
[UPGRADE] firefox-trunk-gnome-support 12.0~a1~hg20120120r84955-0ubuntu1~umd1 -> 12.0~a1~hg20120123r85111-0ubuntu1~umd1
[UPGRADE] gnome-control-center 1:3.2.2-2ubuntu2 -> 1:3.2.2-2ubuntu3
[UPGRADE] gnome-control-center-data 1:3.2.2-2ubuntu2 -> 1:3.2.2-2ubuntu3
[UPGRADE] language-pack-en 1:12.04+20111229 -> 1:12.04+20120123
[UPGRADE] libavcodec53 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libavformat53 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libavutil51 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libgnome-control-center1 1:3.2.2-2ubuntu2 -> 1:3.2.2-2ubuntu3
[UPGRADE] libgpg-error0 1.10-1ubuntu1 -> 1.10-2ubuntu1
[UPGRADE] libnautilus-extension1a 1:3.2.1-2ubuntu11 -> 1:3.2.1-2ubuntu12
[UPGRADE] libpostproc52 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libswscale2 4:0.8~beta2-3ubuntu1 -> 4:0.8-1ubuntu1
[UPGRADE] libwayland0 0.1.0~git20120120.f66aa1d0-0ubuntu0ricotz -> 0.1.0~git20120124.10eefa49-0ubuntu0ricotz
[UPGRADE] libwnck-3-0 3.2.1-1 -> 3.2.1-1ubuntu1
[UPGRADE] libwnck-3-common 3.2.1-1 -> 3.2.1-1ubuntu1
[UPGRADE] midori 0.4.3+r4456-0~precise1 -> 0.4.3+r4457-0~precise1
[UPGRADE] nautilus 1:3.2.1-2ubuntu11 -> 1:3.2.1-2ubuntu12
[UPGRADE] nautilus-data 1:3.2.1-2ubuntu11 -> 1:3.2.1-2ubuntu12
[UPGRADE] notify-osd 0.9.32-0ubuntu4 -> 0.9.32-0ubuntu5
[UPGRADE] opera 11.61.1222 -> 11.61.1250
[UPGRADE] xserver-common 2:1.11.99.901+git20120120.954bb994-0ubuntu0ricotz -> 2:1.11.99.901+git20120124.e1085a0d-0ubuntu0ricotz
[UPGRADE] xserver-xorg-core 2:1.11.99.901+git20120120.954bb994-0ubuntu0ricotz -> 2:1.11.99.901+git20120124.e1085a0d-0ubuntu0ricotz
===============================================================================

Log complete.
``````
paul@precise-64:~$ uname -a
Linux precise-64 3.3.0-030300rc1-generic #201201191835 SMP Thu Jan 19 23:36:54 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$
```This is with X Server 1.11.99.901 (1.12.0 RC1) and nvidia 295.09.

Anyone else?

Hmm, I have done the same updates on all my 3 setups without any issues. However not those browsers, but I think that is not the problem.

There are differencies, though. I use the kernel from Precise repos and nvidia-current from xorg-edgers with the xserver 1.12 rc1.
Where did you get nvidia_295.09 driver?
Do you use Gnome-shell Testing PPA?

---

### Post by paul_in_london on 2012-01-24
> **Harry33 said:**
> Hmm, I have done the same updates on all my 3 setups without any issues. However not those browsers, but I think that is not the problem.

There are differencies, though. I use the kernel from Precise repos and nvidia-current from xorg-edgers with the xserver 1.12 rc1.
Where did you get nvidia_295.09 driver?
Do you use Gnome-shell Testing PPA?

Hi Harry. Yes, it wasn't obvious why this should have happened after those updates.

Got 295.09 from here:

[http://www.nvnews.net/vbulletin/showthread.php?p=2514702](http://www.nvnews.net/vbulletin/showthread.php?p=2514702)

To install this driver, I needed a work-around based on the suggestion in this thread:

[http://ubuntuforums.org/showthread.php?t=1911985](http://ubuntuforums.org/showthread.php?t=1911985)

See my post there for more details.

When you say the GS Testing ppa do you mean ricotz-testing? I'm using xorg-edgers again instead of ricotz-unstable by the way.

---

### Post by Harry33 on 2012-01-25
> **paul_in_london said:**
> Hi Harry. Yes, it wasn't obvious why this should have happened after those updates.

Got 295.09 from here:

[http://www.nvnews.net/vbulletin/showthread.php?p=2514702](http://www.nvnews.net/vbulletin/showthread.php?p=2514702)

To install this driver, I needed a work-around based on the suggestion in this thread:

[http://ubuntuforums.org/showthread.php?t=1911985](http://ubuntuforums.org/showthread.php?t=1911985)

See my post there for more details.

When you say the GS Testing ppa do you mean ricotz-testing? I'm using xorg-edgers again instead of ricotz-unstable by the way.

Yes Gnome-shell Testing PPA is owned by Ricotz.
However, the Unstable PPA (Ricotz) has no xserver packages any longer and xorg-edgers is the right place to play with and test xserver 1.12 rc's.

---

### Post by paul_in_london on 2012-01-25
> **Harry33 said:**
> Yes Gnome-shell Testing PPA is owned by Ricotz.
However, the Unstable PPA (Ricotz) has no xserver packages any longer and xorg-edgers is the right place to play with and test xserver 1.12 rc's.

Thanks Harry. I'm apparently using the appropriate ppas so I'm still not sure why GS stopped working for me after yesterday's updates. We'll see what today brings...

---

