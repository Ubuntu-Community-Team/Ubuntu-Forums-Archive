---
title: "desktop background gone and not to recover"
date: 2015-09-26
forum: Ubuntu Studio
---

### Post by dirk-l on 2015-09-26
Hi forum,

not really new to ubuntu, but also no linux-freak, I wasn't able to solve the problem:


[LIST]
[*]after login the desktop comes up wrong, with standard background-pictures. The menu only shows "change background" which is not working (nothing happens). An entry like "desktop-settings" does not exist. 
[*]I found some possible fixes in the Internet, but nothing worked. I deleted ~/.config/xfce4/ . It was built new, but the symptoms stay. Tried some other stuff, but nothing helped:
[LIST]
[*]```
sudo chown -R -v user:user /home/user ; sudo chmod -R -v u+rwX /home/BENUTZER ; sudo chmod 600 /home/user/.dmrc ; chmod 755 /home/user
```
because it was not unlikely I made a mistake with root-rights. 
[*]I reinstalled xfce4 and ubuntustudio-desktop 
[*]I made the file **~/.gtkrc-2.0** 
[*]while trying to run xfdesktop, it says: xfdesktop: another desktop manager is running. - But isn't it because of lightdm running and doing the job? 
[/LIST]
  
[*]after all of these I signed out and in again or rebooted. Or both, just to be sure (old win-habits, hard to get over it ;-) ). 
[*]IMPORTANT, I think: a fresh new-user-desktop just works fine, but copying his .config/xfce4/ - folder doesn't help. (?) adapting the ownership of course.
[*]I also copied my ~/.config/xfce4-folder to a new users account. It works fine (?!). There are still hundreds of settings in the old user-account so just using the new user is not really an option. Just like reinstall is not. 
[/LIST]

So maybe it's not a xfce4-problem at all?
Any ideas are welcome. I'm stuck :-/

System: ubuntustudio 14.04.3 LTS x86-64, up to date
possible interferences (?): pyWO installed, synergy installed though deactivated for testing.

---

### Post by Toz on 2015-09-26
> **dirk-l said:**
> after login the desktop comes up wrong, with standard background-pictures. The menu only shows "change background" which is not working (nothing happens). An entry like "desktop-settings" does not exist. 
> while trying to run xfdesktop, it says: xfdesktop: another desktop manager is running. - But isn't it because of lightdm running and doing the job?
There is another program managing your desktop. Maybe naultilus, or nemo, or pcmanfm, or something else. If you want xfdesktop to manage your desktop, you need to kill that process, restart xfdesktop and set up the offending process to not manage the desktop (usually through some sort of parameter to pass to the application or a configuration setting).

> So maybe it's not a xfce4-problem at all?
Is just an issue of conflicting desktop managers.

---

### Post by Dreamer Fithp Apprentice on 2015-09-26
> **dirk-l said:**
> while trying to run xfdesktop, it says: xfdesktop: another desktop manager is running. - But isn't it because of lightdm running and doing the job?I might be a good idea if you clarified that. I don't use a conventional desktop per se (my root window is just empty and serves only as a mouse target to click for menus), so I may be all wet here, but I think when an xfce user checks out this thread it might help if they know EXACTLY (verbatim) what error message you are getting (maybe that is what you posted - if so, you might want to make that fact explicit) and EXACTLY what circumstances you are getting it under.

Lightdm is what is called a "display manager", not a "desktop manager", nor a "desktop environment", nor a "window manager". "Display manager" is a misleading expression IMO, but we seem to be stuck with it. It is a gui ap to manage logins and select a session type, "session type" basically meaning what window manager you want to use. There shouldn't be any reason for conflict between it and xfdesktop, which is a "desktop environment", that I know of. It sounds like you have a window manager already running when you are trying to start another one. What happens when you cold boot? Do you get a gui screen to type your username and password into? If so does it have a menu (probably at the top of the screen) to select a session-type? Or do you get a text interface and use "startx"? It might help if you state the exact sequence of events that leads to this error message. Also, it couldn't hurt to post the contents of /etc/lightdm/lightdm.conf and /etc/lightdm/lightdm-gtk-greeter.conf.

If the objective is merely to change the background image, you might try opening the image you want with an image viewer. and looking for a menu or right click on the image context menu option to "set this as desktop background". A lot of the heavier image viewers have this option. I'm pretty sure Mirage and the one that used to be the default on the standard gnome desktop (I forget the name of that one) do. I don't have them installed ATM to check (I'm trying gpicview instead - it is blazing FAST).

Not sure I can help, but I'll check back. And in the meantime, if you post the info suggested, it might help some xfce user to point you toward a solution faster.

============================
Added by edit:
I see Toz posted while I was slowly typing. You're in good hands then.

---

### Post by dirk-l on 2015-09-26
Oh wow, it's already late here (germany) and I didn't really expect answers coming up so fast. thank you both. 
@ Toz: I found out, that it is nemo. I just prefer using nemo instead of thunar, so I have to find a way around. I will check my settings.
@[**[COLOR=#000000]Dreamer Fithp Apprentice: [/COLOR]**]("http://ubuntuforums.org/member.php?u=1435975") 	 thanks for the insight. I was confused by the words, so its a good thing for me to clear this up: lightdm does NOT the same thing like xfdesktop
BIG THX

---

### Post by Toz on 2015-09-26
> **dirk-l said:**
> 
@ Toz: I found out, that it is nemo. I just prefer using nemo instead of thunar, so I have to find a way around. I will check my settings.
```
gsettings set org.nemo.desktop show-desktop-icons false
```
...should stop nemo from managing the desktop.

---

### Post by dirk-l on 2015-09-26
hi again.
With your help I managed to get it back running. It seems to be always loading a session, where nemo was running. so I changed settings "session and start-behaviour" to save session automatically after logout (direct translations, maybe its slightly different). I stopped nemo and everything else. After re-login - Tataaa - everything was fine. Then I changed back to my original ~/.conf/xfce4/-folder. And again it worked. I have all original backgrounds and the panel and so on. 

:D Can't get the grin of my face now, big THANK YOU again.

---

### Post by dirk-l on 2015-11-26
It happened again! 
The solution was: 
 - I killed just nemo
 - rebooted
 - then ran xfdesktop
and *tataa* everything was fine again.

---

