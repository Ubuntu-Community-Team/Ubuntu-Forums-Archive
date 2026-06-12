---
title: "cogl-1.9.3 may break gnome-shell and gdm-greeter?! :/"
date: 2011-12-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tista on 2011-12-05
Guys,

Just now I've updated pp with Ricotz PPA, then I've seen ugly, rapidly flickering display!! :S

These were updated packages especially cogl-1.9.3:

> Commit Log for Mon Dec  5 17:03:57 2011


Upgraded the following packages:
balsa (2.4.11-1+git20111122.fddfb5f~tista2) to 2.4.11-1+git20111128.bd95e68~tista2
gir1.2-clutter-1.0 (1.8.2-2) to 1.9.3+git20111201.8d234d27-0ubuntu1~12.04~ricotz0
gir1.2-clutter-gst-1.0 (1.4.4-0ubuntu1~12.04~ricotz0) to 1.5.1+git20111108.23f7c03a-0ubuntu1~12.04~ricotz2
gir1.2-cogl-1.0 (1.8.3+git20111024.b76fb45d-0ubuntu1~12.04~ricotz0) to 1.9.3+git20111130.7f2a8963-0ubuntu1~12.04~ricotz0
gir1.2-coglpango-1.0 (1.8.3+git20111024.b76fb45d-0ubuntu1~12.04~ricotz0) to 1.9.3+git20111130.7f2a8963-0ubuntu1~12.04~ricotz0
libavc1394-0 (0.5.3-1build4) to 0.5.3-1ubuntu1
libcaca0 (0.99.beta17-2.1) to 0.99.beta17-2.1ubuntu1
libclutter-1.0-0 (1.8.2-2) to 1.9.3+git20111201.8d234d27-0ubuntu1~12.04~ricotz0
libclutter-1.0-common (1.8.2-2) to 1.9.3+git20111201.8d234d27-0ubuntu1~12.04~ricotz0
libclutter-1.0-dev (1.8.2-2) to 1.9.3+git20111201.8d234d27-0ubuntu1~12.04~ricotz0
libclutter-gst-1.0-0 (1.4.4-0ubuntu1~12.04~ricotz0) to 1.5.1+git20111108.23f7c03a-0ubuntu1~12.04~ricotz2
libcogl-common (1.8.3+git20111024.b76fb45d-0ubuntu1~12.04~ricotz0) to 1.9.3+git20111130.7f2a8963-0ubuntu1~12.04~ricotz0
libcogl-dev (1.8.3+git20111024.b76fb45d-0ubuntu1~12.04~ricotz0) to 1.9.3+git20111130.7f2a8963-0ubuntu1~12.04~ricotz0
libcogl-pango-dev (1.8.3+git20111024.b76fb45d-0ubuntu1~12.04~ricotz0) to 1.9.3+git20111130.7f2a8963-0ubuntu1~12.04~ricotz0
libcogl-pango0 (1.8.3+git20111024.b76fb45d-0ubuntu1~12.04~ricotz0) to 1.9.3+git20111130.7f2a8963-0ubuntu1~12.04~ricotz0
libgranite-dev (0.1.4-0~140~oneiric1) to 0.1.4-0~141~oneiric1
libgranite0 (0.1.4-0~140~oneiric1) to 0.1.4-0~141~oneiric1
liborc-0.4-0 (1:0.4.16-1) to 1:0.4.16-1ubuntu2

Installed the following packages:
libcogl6 (1.9.3+git20111130.7f2a8963-0ubuntu1~12.04~ricotz0)

and my gnome-shell was:
> 3.3.2+git20111201.2c243b67-0ubuntu1~12.04~ricotz0

Can anyone confirm this issue?

Cheers,
Tista

---

### Post by tista on 2011-12-05
And here was the message remained in term when I run "gnome-shell --replace" from classic session:

```
Mesa: User error: GL_INVALID_OPERATION in glDrawArrays (fragment program not valid)
Cogl-WARNINGS **: ./cogl-attribute.c : 1087: GL error (1282): Invalid operation
```

Means/causing mesa version?
PC: Sony VAIO Z (VPCZ21AJ) sandy-bridge mobile.

Mine is:
```
7.12~git1111300845.2134d2~gd~o
```
Yep, these're contributed by Oibaf, great man of mesa.. :)

---

### Post by Harry33 on 2011-12-05
You need to have an updated version of gnome-shell too.
This is now building in Ricotz Testing PPA:
[         gnome-shell - 3.3.2+git20111204.0cbaeaef-0ubuntu1~12.04~ricotz0       ]("https://launchpad.net/%7Ericotz/+archive/testing/+sourcepub/2108192/+listing-archive-extra")

Older gnome-shell (and mutter) depends on libcogl5, while the new clutter (1.9.3) contains libcogl6.

---

### Post by tista on 2011-12-05
> **Harry33 said:**
> You need to have an updated version of gnome-shell too.
This is now building in Ricotz Testing PPA:
[         gnome-shell - 3.3.2+git20111204.0cbaeaef-0ubuntu1~12.04~ricotz0       ]("https://launchpad.net/%7Ericotz/+archive/testing/+sourcepub/2108192/+listing-archive-extra")

Older gnome-shell (and mutter) depends on libcogl5, while the new clutter (1.9.3) contains libcogl6.

Hi Harry33,

Thanks for your info... ;) ASAP I would update them to the latest.

And one thing.
I've seen some posts that you suggested Ricotz PPA for gnome-shell testing, are you friends? then if you could contact to him, please tell him that I wish you could add some dependencies/version requirements in debian/control between clutter/cogl and gs/mutter...

cheers.

**EDIT:**
OK. now this issue was fixed with that new gnome-shell. ;)

---

### Post by Harry33 on 2011-12-05
> **tista said:**
> Hi Harry33,

Thanks for your info... ;) ASAP I would update them to the latest.

And one thing.
I've seen some posts that you suggested Ricotz PPA for gnome-shell testing, are you friends? then if you could contact to him, please tell him that I wish you could add some dependencies/version requirements in debian/control between clutter/cogl and gs/mutter...

cheers.

**EDIT:**
OK. now this issue was fixed with that new gnome-shell. ;)

Hi Tista,

I can also comfirm the transition to the new clutter-1.0 (1.9.3) with gnome-shell and mutter rebuilt against it works very well.
After this transition a new libcogl6 is installed and the old libcogl5 is to be removed.

I do have Ricotz Gnome-shell Testing PPA enabled (installed) like I also have some Xorg-edgers packages installed (nvidia-current_290-10 and xserver 1.11.2).
I am grateful to Rico Tzschichholz for the Testing PPA.
However, I do not know him.

---

### Post by jbicha on 2011-12-07
Of course, ricotz' PPA is rather experimental. If you want a bit more stable, you could use the GNOME 3 PPA but of course it doesn't have GNOME Shell 3.3 or much of anything 3.3 yet.

---

### Post by tista on 2011-12-07
> **jbicha said:**
> Of course, ricotz' PPA is rather experimental. If you want a bit more stable, you could use the GNOME 3 PPA but of course it doesn't have GNOME Shell 3.3 or much of anything 3.3 yet.

Hi jbicha. ;)

Yeah I know...
IMHO, I think gnome-shell 3.3.x seems quite stable so far!! :)
even though gs 3.4 would be a stable release by fixing lots of minor issues (paper cuts?), I want ubuntu devs to update gnome-shell to 3.3.x in main repository...

I suppose now the time's come to update these stuff on main repository, isn't it? ;)
For many precise testers especially git based gs lovers, Since today precise seems to become "The best platform" in the world! If we could get it as possible as early, the theme creaters/designers could follow upstream changes quickly as well, so finally gnome-shell would be more beautiful and usable!!

cheers.

---

