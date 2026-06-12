---
title: "dconf-editor will not shutdown on log off or reboot"
date: 2017-07-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2017-07-28
Noticed that dconf-editor will not auto-close (wayland) on log-out or reboot . intel/nvidia both.

Is this common behaviour or should I file a bug against it?

after restart it will come up like it has been in suspend mode.

Regards..

---

### Post by #&amp;thj^% on 2017-07-28
Working good here.

---

### Post by ventrical on 2017-07-28
> **1fallen said:**
> Working good here.

Does it close when you log off or reboot?

---

### Post by #&amp;thj^% on 2017-07-28
It closes by window buttons, and a re-login nothing there. Seems to be just fine on my end.:confused:
And After a reboot:
```
top                          ./+o+-       me@me-750-417c
                  yyyyy- -yyyyyy+      OS: Ubuntu 17.10 artful
               ://+//////-yyyyyyo      Kernel: x86_64 Linux 4.12.0-041200rc7-lowlatency
           .++ .:/++++++/-.+sss/`      Uptime: 2m
         .:++o:  /++++++++/:--:/-      Packages: 2464
        o:+o+:++.`..```.-/oo+++++/     Shell: bash 4.4.12
       .:+o:+o/.          `+sssoo+/    Resolution: 1920x1080
  .++/+:+oo+o:`             /sssooo.   DE: GNOME 
 /+++//+:`oo+o               /::--:.   WM: GNOME Shell
 \+/+o+++`o++o               ++////.   WM Theme: 
  .++.o+++oo+:`             /dddhhh.   GTK Theme: Adwaita-dark [GTK2/3]
       .+.o+oo:.          `oddhhhh+    Icon Theme: Windows
        \+.++o+o``-````.:ohdhhhhh+     Font: Cantarell 11
         `:o+++ `ohhhhhhhhyo++os:      CPU: Intel Core i5-6400 @ 4x 3.3GHz [33.0°C]
           .o:`.syhhhhhhh/.oo++o`      GPU: intel
               /osyyyyyyo++ooo+++/     RAM: 952MiB / 11922MiB
                   ````` +oo+++o\:    
                          `oo++.      
me@me-750-417c:~$ top

top - 10:56:20 up 4 min,  1 user,  load average: 1.60, 1.76, 0.85
Tasks: 290 total,   1 running, 289 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.4 us,  0.5 sy,  0.0 ni, 97.7 id,  0.3 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem : 12208320 total, 10241872 free,  1043632 used,   922816 buff/cache
KiB Swap:  7337980 total,  7337980 free,        0 used. 10697240 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND              
 2398 me        20   0 2929052 172076  77080 S   3.6  1.4   0:08.67 gnome-shell          
 3142 me        20   0 1228128  16460  10792 S   1.3  0.1   0:00.99 conky                
 3042 me        20   0 2290804  18884  12556 S   1.0  0.2   0:00.69 conky                
 2403 me        20   0  306244  55808  36004 S   0.7  0.5   0:00.95 Xwayland             
 3024 me        20   0   44320   3760   3064 R   0.7  0.0   0:00.38 top                  
    8 root      20   0       0      0      0 S   0.3  0.0   0:00.33 rcu_preempt          
 1029 mongodb   20   0  321452  62224  28368 S   0.3  0.5   0:01.09 mongod               
 1112 root      20   0  469024  15716  12760 S   0.3  0.1   0:00.49 NetworkManager       
 2780 me        20   0  648428  42632  30552 S   0.3  0.3   0:00.63 gnome-terminal-      
    1 root      20   0  213268   8108   5756 S   0.0  0.1   0:01.88 systemd              
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd             
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0          
    4 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H         
    5 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u8:0         
    6 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 mm_percpu_wq         
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ksoftirqd/0          
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_sched            

```
```
echo $DESKTOP_SESSION
gnome-wayland

```

---

### Post by ventrical on 2017-07-28
:)

Ok..

Uh .. I mean when you leave the editor OPEN on the gnome-wayland desktop and then log-off or re-boot the computer .. does dconf.editor close automatically without hitting windows buttons.?

---

### Post by #&amp;thj^% on 2017-07-28
Yep just tried again... it will close automatically upon re-loging in.
Leaving it open.
Is this the box with Unity installed also?

---

### Post by ventrical on 2017-07-28
I just logged on to unity session and got:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1707259](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1707259)

However  dconf-editor will close when I log-out.

Lemme try gnome-shell without wayland before we mark unity7 as the culprit.

regards

---

### Post by ventrical on 2017-07-28
works just fine on gnome-shell.

This is a wayland issue.  Unless you can provide a theory that unity7 is affecting it (wayland)? I sure am willing to listen. If unity7 is affecting wayland in any way then it should be pulled from the repos. I am on the Mark Shuttleworth/Will Cooke bandwagon that if unity7 affects GNOME in any way then it's gotta go, no ifs ands or buts.

Regards..

---

### Post by ventrical on 2017-07-28
In the meantime I'm filing this bug.

[https://bugs.launchpad.net/ubuntu/+source/dconf-editor/+bug/1707261](https://bugs.launchpad.net/ubuntu/+source/dconf-editor/+bug/1707261)

---

### Post by #&amp;thj^% on 2017-07-28
Well that's all it would be is a theory.:) This dose not show on just a plain Gnome/wayland/X11 for me.
The way I'm going to do it.. is keep Unity on a separate install, to avoid any possible confusion between the two as far as bug triaging.

---

### Post by ventrical on 2017-07-28
> **1fallen said:**
> Well that's all it would be is a theory.:)
The way I'm going to do it.. is keep Unity on a separate install, to avoid any possible confusion between the two as far as bug triaging.

Well .. put it this way then ... can you give me a three point list with documentation at how unity7 (currently) is affecting GNOME on wayland?

If you or jbicha can share with me in a three point form how maintaining unity7 can cause a strenuous and added burden on GNOME-WAYLAND developers (current) and into the 18.04 cycle then I would recommend that unity7 be pulled so that we can move on from it. Just a point before you answer. I am currently trying to get support for unity7 maintainers from the community so if it is a waste of time I sure would like some brief context on this subject.

Regards..

---

### Post by ventrical on 2017-07-28
> **1fallen said:**
> Well that's all it would be is a theory.:) This dose not show on just a plain Gnome/wayland/X11 for me.
The way I'm going to do it.. is keep Unity on a separate install, to avoid any possible confusion between the two as far as bug triaging.



I tired it  on bare metal with GNOME only. Had a raw install going for quite some time. dconf-editor closes normally in wayland. so .. yes . it is game on. unity7  install could be interfecting GNOME wayland.

---

### Post by mc4man on 2017-07-28
> **ventrical said:**
> . so .. yes . it is game on. unity7  install could be interfecting GNOME wayland.

What does that have to do with anything? 
If someone was going to **install unity 7** then they would have no use or care about gnome sessions, on wayland or X11.
There mere presence of unity in the repos could not possibly have any affect on whatever it is that Ubuntu is releasing so  - 

"I am on the Mark Shuttleworth/Will Cooke bandwagon that if unity7 affects GNOME in any way then it's gotta go, no ifs ands or buts" = pure nonsense..

---

### Post by #&amp;thj^% on 2017-07-28
> **ventrical said:**
> I tired it  on bare metal with GNOME only. Had a raw install going for quite some time. dconf-editor closes normally in wayland. so .. yes . it is game on. unity7  install could be interfecting GNOME wayland.
And a little in XFCE logouts etc etc. (and this is just so far what we have discovered)
So far just a Unity session only install is working satisfactory for an Alpha release.

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> What does that have to do with anything? 
If someone was going to **install unity 7** then they would have no use or care about gnome sessions, on wayland or X11.
There mere presence of unity in the repos could not possibly have any affect on whatever it is that Ubuntu is releasing so  - 

"I am on the Mark Shuttleworth/Will Cooke bandwagon that if unity7 affects GNOME in any way then it's gotta go, no ifs ands or buts" = pure nonsense..

There are currently no developers or maintainers stepping forward and if unity7 causes a bad experience it will be pulled.

edit: And so it is my understanding that if persons want to have unity7 alongside GNOME and unity7 causes a bad experience standalone (or alongside) then it will be pulled.

Regards..

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> What does that have to do with anything? 
If someone was going to **install unity 7** then they would have no use or care about gnome sessions, on wayland or X11.
There mere presence of unity in the repos could not possibly have any affect on whatever it is that Ubuntu is releasing so  - 

"I am on the Mark Shuttleworth/Will Cooke bandwagon that if unity7 affects GNOME in any way then it's gotta go, no ifs ands or buts" = pure nonsense..

Perhaps I misquoted;

> 
from Will Cooke:

subject: unity7 maintainers and developers
    [SIZE=1][SIZE=1]Hi Dale, Mark,[/SIZE]
 [/SIZE]
 [SIZE=1] 
 
 Just to add a little more background here:
 
 
 
 Unity 7 in 16.04 LTS will naturally be supported until 2021 by the  Desktop team with security updates and critical bug fixes.  These would  very likely be forward-portable to Unity 7 in 17.04, 17.10 etc.
 
 
 The problems for U7 arise in 17.10 and beyond because of the way we  have patched the Gtk libraries & apps to get them to integrate well  with Unity 7.  For example, we patch out header bars and client side  decorations & patch in support for the global menus.  This are fundamentally incompatible with GNOME Shell, and so we need to  make a decision about whether to add more patches to make these apps  work well in both Unity 7 and GNOME Shell or drop the patches and focus  on the GNOME Shell experience.  The current preference is drop the patches.
 
 
 There are some other incompatibilities in the desktop session  between GNOME Settings Daemon & Unity Settings Daemon, or GNOME  Online Accounts & Ubuntu Online Accounts.  We need to use the GNOME  version in the GNOME session, so these would be prime candidates for a community team to maintain in the future for the U7 session.
 
 
 Where does this leave Unity 7 in 17.10 then?  At the moment we are  testing Unity 7 alongside GNOME Shell to spot when something we land  causes Unity 7 to break.  While we can probably work around some of  these issues, the overall experience will be hampered by the incompatibility between our U7 patches & services and GNOME  Shell, and this will, unfortunately, degrade the U7 experience on  17.10.  We're still looking at what changes could be made to keep U7  working in the archive so I can't make any promises of functionality yet.  I'd like to make that call before Beta 1 so people  know what to expect.
 
 
 Any community teams who'd be interested in helping out with that  would be very welcome and I'd be very happy to help get them set up with  the access they need and support from the Desktop Team.
 
 
 Cheers, Will
 [/SIZE]
 
 
 
 
                           
     

So, mac4man, would you like to help with the unity7 maintainers team when the time comes?

Regards..

---

### Post by mc4man on 2017-07-28
> **ventrical said:**
> Perhaps I misquoted;



So, mac4man, would you like to help with the unity7 maintainers team when the time comes?

Regards..
Personally I think it's a dead dog & MS and company know that.
That being said if it survives 17.10 release I can see means to keep it going under the banner of 18.04 which gains 2 years over 16.04. (- which has some value.
/as far as fixing gtk/glib/gnome-desktop issues would not be able to help at all..

As far as this thread - 
tried on an install of yesterday
Installed unity7, rebooted
Can not see dconf-editor surviving a log out in a wayland session, it closes just like in X11, both gnome-shell & unity

Also switched to lightdm & still don't see

Now I'm sure one could create issues with the differences between lightdm & gdm3 but that's neither here or there, if wanting to use unity 7 I'd switch to lightdm & remove gdm3, ect.

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> 

As far as this thread - 
tried on an install of yesterday
Installed unity7, rebooted
Can not see dconf-editor surviving a log out in a wayland session, it closes just like in X11, both gnome-shell & unity

Also switched to lightdm & still don't see

Now I'm sure one could create issues with the differences between lightdm & gdm3 but that's neither here or there, if wanting to use unity 7 I'd switch to lightdm & remove gdm3, ect.

Thanks for your input and help as always.

Regards..

---

### Post by mc4man on 2017-07-28
> **ventrical said:**
> I just logged on to unity session and got:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1707259](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1707259)

However  dconf-editor will close when I log-out.

Lemme try gnome-shell without wayland before we mark unity7 as the culprit.

regards
I've seen that in 17.10 and in the past, seems not uncommon
( [https://www.bountysource.com/issues/3836681-xorg-crashed-with-sigabrt-in-osabort](https://www.bountysource.com/issues/3836681-xorg-crashed-with-sigabrt-in-osabort)

Anyway I wouldn't be surprised if mixing Dm's & De's causes occasional hiccup, that's why I only view the state of Ubuntu as seen running gdm3 & unity as seen running lightdm. (- just look at difference between tty2 & tty7 in either..

So can't see why MS & Will Cooke were alluding to, are you sure you got their intent correct?

---

### Post by ventrical on 2017-07-28
> **mc4man said:**
> I've seen that in 17.10 and in the past, seems not uncommon
( [https://www.bountysource.com/issues/3836681-xorg-crashed-with-sigabrt-in-osabort](https://www.bountysource.com/issues/3836681-xorg-crashed-with-sigabrt-in-osabort)

Anyway I wouldn't be surprised if mixing Dm's & De's causes occasional hiccup, that's why I only view the state of Ubuntu as seen running gdm3 & unity as seen running lightdm. (- just look at difference between tty2 & tty7 in either..

So can't see why MS & Will Cooke were alluding to, are you sure you got their intent correct?

Yes I am sure. 

> 
Hi Dale,
 
 I would like to keep Unity7 in the archives, but if as Jeremy says it will result in a bad experience then we should pull it. <........>

Mark


Regards..

---

### Post by mc4man on 2017-07-29
> **ventrical said:**
> Yes I am sure. 
I would like to keep Unity7 in the archives, but if as Jeremy says it will result in a bad experience then we should pull it. <........>

Mark 


Regards..
I take that as a bad unity7 experience, not a bad gnome-shell exp due to unity source presence.. 
From that perspective it's pretty much guaranteed to be bad come 18.04, probably should be almost ok in 17.10

---

### Post by ventrical on 2017-07-30
> **mc4man said:**
> I take that as a bad unity7 experience, not a bad gnome-shell exp due to unity source presence.. 


I think you misunderstood me. It is common sense that a package just being in the repos would not affect a DE in particular but if persons  install unity side by side with GNOME then it could be a bad experience for both. So , in whichever scenario, it would be pulled. End_users would naturally want to try a unity7 install during 18.04. Thats one of the reasons Will Cooke and Mark are directing the team to test them together side by side during this cycle, (as I understand it)  and yes , mostly to test unity7 behaviour. I have been through all this in another thread. ie; [https://ubuntuforums.org/showthread.php?t=2363847&page=3&p=13658210#post13658210](https://ubuntuforums.org/showthread.php?t=2363847&page=3&p=13658210#post13658210)  so , yes . there can be weird behaviour if they are installed together , one interfecting the other, in which case it should be pulled from the repos so people are not tempted to install it come the time when unity7 is very unstable.

Just a side note: when I was asked to take admin positon of U+1  I took on added task of staying in contact with Canonical developers so I could present current  activities that are going on in some areas of development to U+1 and ubuntuforums.  

  regards..

---

### Post by ventrical on 2017-07-30
> **mc4man said:**
> I take that as a bad unity7 experience, not a bad gnome-shell exp due to unity source presence.. 
From that perspective it's pretty much guaranteed to be bad come 18.04, probably should be almost ok in 17.10

I am doing my best to build a maintainers team. [https://launchpad.net/~unity7maintainers](https://launchpad.net/~unity7maintainers)  It will depend on the contributions from the community in general whether or not unity7 stays in the repos and then ... who knows .. there is always a dynamic at Canonical which is hard to predict because of their innovative spirit.

Regards..

---

### Post by mc4man on 2017-07-30
Not sure why Ubuntu (Canonical) would care about that, for the most part they never did & recent history suggest mixing sessions was/is a poor idea..
Most users just use whatever is presented so again mixed is not relevant

As far as those wanting one or the other, once in place they'd never want or use the other. Up until now those wishing best gnome(shell) experience would use Ubuntu-Gnome. Those happy with unity would install Ubuntu. Those who don't like either would use some other buntu or something else entirely.

As far as users currently installing unity in Ubuntu well that not possible thru gnome/ubuntu software app so again having both would be a rare case of no importance to Canonical (other than maybe PR?

---

### Post by ventrical on 2017-07-30
> **mc4man said:**
> Not sure why Ubuntu (Canonical) would care about that, for the most part they never did & recent history suggest mixing sessions was/is a poor idea..
Most users just use whatever is presented so again mixed is not relevant

As far as those wanting one or the other, once in place they'd never want or use the other. Up until now those wishing best gnome(shell) experience would use Ubuntu-Gnome. Those happy with unity would install Ubuntu. Those who don't like either would use some other buntu or something else entirely.

As far as users currently installing unity in Ubuntu well that not possible thru gnome/ubuntu software app so again having both would be a rare case of no importance to Canonical (other than maybe PR?

Or unless you are a conservative tester. I know I like to test multiple DEs on the same install. But there are several other reasons why unity-session would break as this cycle and the next moves on especially  not having any Canonical interest. So I guess it is for those in the community who are interested in keeping unity7 viable in 18.04. Unity has been good to me and good to my clients but I can live with GNOME if I can't get community support.

regards..

---

