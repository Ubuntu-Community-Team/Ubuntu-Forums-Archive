---
title: "USP menu draws behind window"
date: 2007-08-19
forum: Ubuntu System Panel
---

### Post by crazyhunk on 2007-08-19
hello...

first of all i realy liked the new USSP....and I installed hte latest SVN version form the google code... and I pretty much liked it a lot... it is working great .. excep that i have a small problem... if i do have a window open and i click on the USP menu the menu does not draw on top of the window but below it.... this has been a little problem for me as I have to minimize or close the window in order to use the menu... I was wondering if there is a fix for this... i am pretty much wasted for now to think so i am putting it up here for help.   :D hehehe

---

### Post by delfick on 2007-08-20
I assume you're using compiz and compiz-fusion?? :D

if so, then that problem is caused by focus stealing prevention.

just go into the ccsm -> Focus & raise behaviour

and type

(any & ! type=gnome-panel)

into the area for Focus prevention windows.....
(if you are still using beryl, then there is a similar option in the bsm somewhere)

what that does is tells it to prevent every type of window, except for the gnome-panel from stealing focus from another window

hope that helps :D

---

### Post by SlugO on 2007-08-20
Thanks for the solution delfick but unfortunately it works only for a little while for me.

After I've changed the settings like that I have to do a killall gnome-panel to get USP to show on top of windows. Unfortunately it doesn't work for very long and after a short while USP shows up behind windows at times or constantly.

Any idea how I could get it to stay on top? :P

---

### Post by crazyhunk on 2007-08-20
thanx for the solution..... but even for me it only works for a little while.... :(

---

### Post by delfick on 2007-08-20
hmmmm I'd have to agree,  that solution doesn't last for me either ....

and i don't know a solution :(

---

### Post by crazyhunk on 2007-08-20
ok I just uninstalled it completely and istalled it again... and it is good now/.... i dont know y.... :confused:

---

### Post by Hexydes on 2007-08-20
My menus draw behind windows as well. It seems like everything is working fine until I press "F9" to bring up my widget view. Once I do that, and system or application menus appear behind windows, making it impossible to see or interact with the menus.

If I kill X and log back in, the problem goes away.

This is obviously a bug with Compiz-Fusion, or one of the plug-ins for it anyway. Any thoughts on how to fix this permanently?

---

### Post by Hexydes on 2007-08-20
Oh, and I just killed both instances of the "compiz" process (there were two), as well as "compiz.real", which obviously killed Compiz. I then did Alt + F2 to bring up the run thing, pasted in the line to start Compiz-Fusion (which started up), and now the menus are working properly again.

This is probably the 20th time this has happened; getting pretty tired of it at this point. :(

---

### Post by animacide on 2007-08-28
Try using:
any & !(type=Dock)
instead.  That worked for me.

---

### Post by sneax on 2007-08-28
I have the same problem. In compiz config I now have this line:

any & !(type=Dock) & ! type=gnome-panel)

But that didn't help anything. Just to note: when restarting compiz the menu focus is allright half the time for the first 5 tries then it's back to being bad.

---

### Post by delfick on 2007-08-30
I was talking on #compiz-fusion-dev on irc to maniac103 about this issue, and after sending xprop and xwininfo for usp to him, he said this

(18:26:32) maniac103: 
he should make it override_redirect and set the window type to MENU IMO

......any possibility of that ?? :D

EDIT : i changed line 9 of /usr/share/usp/usp2.glade to

```
    <property name="type_hint">GDK_WINDOW_TYPE_HINT_MENU</property>
```

and the problem seems fixed :D

---

### Post by spockrock on 2007-09-15
thanks for this fix delfick

---

### Post by delfick on 2007-09-16
> **spockrock said:**
> thanks for this fix delfick

no probs :D

---

### Post by sweetthdevil on 2007-09-19
Many many thanks!!!

Work like a charm!!

---

### Post by mjpoetic on 2007-09-19
Confirm that works here too!!  Good find!

---

### Post by Malac on 2007-09-20
I think this was done to address a similar issue with USP under beryl where the type needed to be _DOCK.
Typical that the window type is treated differently in each of the window managers. I will do some digging and see if something can be done.

---

### Post by delfick on 2007-09-20
> **Malac said:**
>  I will do some digging and see if something can be done.

cool :D

thnx

---

### Post by munmon on 2007-09-20
many many thanks. you're the man!!!

---

### Post by Teneul on 2007-10-10
The only problem with that is that now usp shows up in the taskbar (window list) and compiz-fusion window rules won't pick up on it. I had to use devilspie's windows rules in order to hide it. Any fix for that?

*EDIT* Just added  <property name="skip_taskbar_hint">True</property> under the change above in the glade file ^^

---

### Post by mjpoetic on 2007-10-14
Good stuff...I was going to play around with it but you saved me some time with that

---

