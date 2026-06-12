---
title: "gnome-terminal menus is not viewable"
date: 2013-11-19
forum: Server Platforms
---

### Post by bksyssathish on 2013-11-19
Hi All,

I am building LTSP server and client in Ubuntu 12.04. When the client boots from LTSP, It had some display problem (Like: blur display after logged in ) due to the unavailability of graphics in thin client. So, I checked in internet. Then, I added the below configuration in lts.conf.
```

LDM_SESSION="gnome-session --session=ubuntu-2d"
CONFIGURE_FSTAB=false
HOSTNAME="client4"
FSTAB_1="192.168.11.25:/home    /home   nfs    defaults,rw,nolock 0       0"
```

Then, I am able to logged in and it works fine.

Now the problem is, after I opened **gnome-terminal**, I am not able to tab(** Alt + Tab** ) to some other application which is running. Terminal is always in front. I mean, when I press tab the next application should be visible and terminal should go back. But, It is not working. After I closed the terminal, then tab( **Alt + Tab** )  is working fine to switch over to other applications.

Another problems is, If I click the file menus in terminal menubar, It is not viewable. But, Still it is accessible. If I blindly click any menu items( Like. opening new tab ), it is opening.

How can I fix those issues?

Whether is it graphics/gnome related issue?

Guide me on this..

---

