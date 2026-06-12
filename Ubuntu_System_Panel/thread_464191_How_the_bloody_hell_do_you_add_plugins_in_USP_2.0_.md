---
title: "How the bloody hell do you add plugins in USP 2.0 Aplha SVN?"
date: 2007-06-04
forum: Ubuntu System Panel
---

### Post by mthakur2006 on 2007-06-04
Tell me please. :D

---

### Post by Malac on 2007-06-04
> **mthakur2006 said:**
> Tell me please. :D
Right-click USP button,
Choose "_P_references".
On the right hand side of the window that appears is a list of plugins.
Click [_A_dd] button and then type in the name of the plugin you want .
Click [_O_K] Button.
You can move it up or down using the buttons marked accordingly.
Then click [_S_ave] button.

Hope this helps.

---

### Post by mthakur2006 on 2007-06-05
woah it works :D
cheers malac

---

### Post by DjBones on 2007-06-05
haha, i dont mean to hijack the thread, but im having problems changing my preferences because its not listed on the right click.. only about, remove, move, and lock.
is there a way to add packages to usp in the command line or somethin or other?

---

### Post by DjBones on 2007-06-05
oh yeah, if it makes any difference, the whole right click problem probably is also part of the fact that the control-center thing doesn't open either..

---

### Post by mthakur2006 on 2007-06-06
are you sure you have got USP Alpha 2.0 SVN?

---

### Post by Malac on 2007-06-06
> **DjBones said:**
> haha, i dont mean to hijack the thread, but im having problems changing my preferences because its not listed on the right click.. only about, remove, move, and lock.
is there a way to add packages to usp in the command line or somethin or other?
If you are running USP 2.0 alpha from the SVN or 1.9x from the .deb's you should be able to get to preferences by typing uspconfig at a terminal.
If you are running the 0.41 or earlier then you can use gconf-editor or download USPconfig from this post :
[http://ubuntuforums.org/showpost.php?p=1586888&postcount=2](http://ubuntuforums.org/showpost.php?p=1586888&postcount=2)

Hope this helps.hrea

---

### Post by DjBones on 2007-06-06
this is the error i get when i try to run control-center from the terminal, probably the reason i can't run it through USP?
(im sure a future version of USP will probably fix this prob.. but never hurts lol)
code:
> brian@KillAllHumans:~$ gnome-control-center

** (GNOME Control Center:7342): WARNING **: 
error raised: [libslab_get_gconf_value: error getting /desktop/gnome/applications/main-menu/lock-down/user_modifiable_apps]


(GNOME Control Center:7342): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed

** (GNOME Control Center:7342): WARNING **: 
error raised: [load_xbel_store: couldn't load bookmark file [(null)]
]

Its not that big of a deal though, because i just mapped the menu to the flag-button so i dont actually use the menu very much anyway haha

---

### Post by petehalatsis on 2008-06-27
for the gnome-control-panel, i edited the command for it in the preferences menu to "gnome-control-panel" because the previous command "gcontrol" didnt work.

---

### Post by Malac on 2008-07-03
> **petehalatsis said:**
> for the gnome-control-panel, i edited the command for it in the preferences menu to "gnome-control-panel" because the previous command "gcontrol" didnt work.
I have now set the default to "gnome-control-center" in computer.py and system_management.py as this is standard in Ubuntu, so far. :)

---

