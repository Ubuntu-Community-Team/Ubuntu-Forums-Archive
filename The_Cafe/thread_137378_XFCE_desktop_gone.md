---
title: "XFCE desktop gone"
date: 2006-02-27
forum: The Cafe
---

### Post by nalmeth on 2006-02-27
For the second time on my laptop, the xfce-desktop has decided to take a holiday, and can't be reached for comment.... Last time this happened I just left it and used gnome. I've done reinstall since, so I don't have a solution.

Anyone know the command for launching it? 

I wonder if there will ever be a xubuntu forum..

---

### Post by aysiu on 2006-02-27
Can you be more specific about what *exactly* happens?

You boot up your computer, and then...?

---

### Post by nalmeth on 2006-02-27
> more specific
sorry

I just mean the desktop, which is basically only the wallpaper and desktop-menu (right click) does not launch, and my problem is I don't know how to get it to launch, or what could be wrong with it. The rest of XFCE is fine.

For example, sometimes in xfce, the panel will crash, and won't reopen. So I just alt-F2 xfce4-panel, and I get it back.

I'm looking for a similar command to relaunch the desktop.

(I think what caused this, is that the desktop crashed, and I tried to log in again, but on my way out asked to save desktop settings)

---

### Post by aysiu on 2006-02-27
Perhaps Alt-F2 ```
xfdesktop
``` might help?

These are all the XFCE commands I could find: ```
xfapps                  xfdiff4                 xfs_copy
xfapps4                 xffm                    xfs_db
xfbook                  xffrecuent4             xfs_freeze
xfbook4                 xffrequent              xfs_growfs
xfce4-about             xffstab                 xfs_info
xfce4-appfinder         xffstab4                xfs_io
xfce4-kiosk-query       xfglob4                 xfs_logprint
xfce4-menueditor        xfhelp4                 xfs_mkfile
xfce4-panel             xflock4                 xfsm-shutdown-helper
xfce4-session           xfmime-edit             xfs_ncheck
xfce4-session-logout    xfmountdev4             xfs_repair
xfce4_setup             xfontsel                xfs_rtcp
xfce4-taskmanager       xfrecent                xftaskbar4
xfce4-terminal          xfrecent4               xfterm4
xfce4-terminal.wrapper  xfrun4                  xftrash4
xfce-mcs-manager        xfs_admin               xftree4
xfce-setting-show       xfsamba4                xfwm4
xfd                     xfs_bmap
xfdesktop               xfs_check
```

---

### Post by nalmeth on 2006-02-27
you got it asiyu

much appreciated

---

### Post by fuscia on 2006-02-27
[QUOTE=nalmeth]
I wonder if there will ever be a xubuntu forum..[/QUOTE]

there was, but it's gone too.

but seriously, folks...i used to have a hard time with stuff (like firefox) vanishing for no reason when i used xfce. the solution had something to do with an option to 'wrap workspaces'. maybe that's what's going on with you.

---

### Post by nalmeth on 2006-02-28
I've never had problems with firefox..
People give xfce a lot of crap, but its been pretty stable for me. There not a whole lot running, so less to go wrong the way I see it. 
Not to start another war, but of the major DE's, KDE hands down least stable in my personal experience. Not that I don't use and like it.
I just use xfce so that my laptop will run a little faster.

---

### Post by bonzodog on 2006-02-28
yeah, I had this problem. Solution:

log into xfce and hit Alt+F2: In the run dialog, type:
```

xfce-setting-show

```
click on the 'desktop' option. You will notice that at the top the option 'allow xfce to manage the desktop' is unticked. just tick this in. you will get your menus and desktop background back. DO NOT use nautilus in xfce, as it somehow unticks this option. Remember to 'save session' on logout.

---

### Post by nalmeth on 2006-02-28
thats cool thanks bonzodog
I think I'll add it to my panel

does using nautilus with xfce do any damage? Or does it just disable the xfdesktop? 
I thought it was kind of cool that the gnome desktop opened up in xfce.

---

### Post by bonzodog on 2006-02-28
It just disables the desktop, but I suppose you could disable getting nautilus to draw the desktop from gconf-editor.

---

### Post by fuscia on 2006-02-28
[QUOTE=nalmeth]thats cool thanks bonzodog
I think I'll add it to my panel

does using nautilus with xfce do any damage? Or does it just disable the xfdesktop? 
I thought it was kind of cool that the gnome desktop opened up in xfce.[/QUOTE]

if you do *nautilus --no-desktop* you shouldn't have any problem at all, in any wm.

---

