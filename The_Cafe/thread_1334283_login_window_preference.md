---
title: "login window preference"
date: 2009-11-22
forum: The Cafe
---

### Post by DarinB on 2009-11-22
I heard that the login window preference is gone in karmic will it come back in lynx? I just discovered all the great things i can do inventing new login screens. it would suck if i can't use the ones i made in karmic or lynx?

---

### Post by joey-elijah on 2009-11-22
the plan is to include GDM options for xsplash in Lynx that were removed after the switchover. I doubt it'll affect any themes for xsplash much, just allow important tweaks to be done easily.

---

### Post by DarinB on 2009-11-22
the gdm options for xsplash is the login window preferences? [ATTACH]137203[/ATTACH]
What is xsplash vs what we have now in jaunty for example? 

i am trying to figure out when to upgrade,,,it includes these issues. plus so many others like will skype ever work with pulse audio? or will my logicam ever work on ubuntu so i can skype with it? so many questions. Its hard to recommend ubuntu to people when so much of the "basic" stuff doesn't work. at least that is what people consider to be basic stuff.

---

### Post by Keyper7 on 2009-11-22
Sorry to break this to you, but you won't be able to use your login screens in Karmic, Lucid or any other Ubuntu release from now on. At least not from a default install.

The theming scheme has changed and it's not backwards compatible.

---

### Post by joey-elijah on 2009-11-22
> **Keyper7 said:**
> Sorry to break this to you, but you won't be able to use your login screens in Karmic, Lucid or any other Ubuntu release from now on. At least not from a default install.

The theming scheme has changed and it's not backwards compatible.

Whoops i obliviously misunderstood the question, but my update is still true: the "missing" features of GDM will return in Lucid so users get back what they've "lost" by the switchover. So to speak.

---

### Post by DarinB on 2009-11-22
i don't really get it if the missing features of gdm will return in lucid, then will i won't be able to use the log in screens i create but will i be able to create my own log in screens again?

---

### Post by cariboo on 2009-11-23
You can already change xsplash screens, it just isn't as easy as it was pre-karmic. The author of startupmanager is apparently working hard to get the next version out in time for lucid.

For instructions to change xsplash and gdm, have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1277030").

---

### Post by Rainstride on 2009-11-23
> **DarinB said:**
> i don't really get it if the missing features of gdm will return in lucid, then will i won't be able to use the log in screens i create but will i be able to create my own log in screens again?

you will get the options to change your themes and settings and that stuff, but the themes made for say jaunty won't be compatible because the changes to gdm . so you will have to redo your gdm theme to comply with the new way it works. I have no clue how hard or easy that will be, it may be as simple as changing a a few lines in your themes files or redoing them completely from scratch.

---

### Post by blueshiftoverwatch on 2009-11-23
Seems like the new login screen is sort of a security hazard. Someone trying to get into your computer already knows your username because it's selectable instead of being typed in. They only have to guess at the password. As opposed to having to guess at both username and password.

---

### Post by Rainstride on 2009-11-23
> **blueshiftoverwatch said:**
> Seems like the new login screen is sort of a security hazard. Someone trying to get into your computer already knows your username because it's selectable instead of being typed in. They only have to guess at the password. As opposed to having to guess at both username and password.

no more so than using the browser login that we could select before. though i suspect that they used the face browser login for karmic because of the fact we can't change it until lucid gets the customizing options back (themes, autologin preferences, and all the stuff). unless you know what files to manually change buy hand in a root nautilus.

---

### Post by Keyper7 on 2009-11-23
> **blueshiftoverwatch said:**
> Seems like the new login screen is sort of a security hazard. Someone trying to get into your computer already knows your username because it's selectable instead of being typed in. They only have to guess at the password. As opposed to having to guess at both username and password.

If that's a problem, enter the command below.

```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true
```

---

### Post by DarinB on 2009-11-23
wow so much involved,,, i just thought it was cool to download a theme and copy and paste my own pictures and there you go you have a better picture for your login screen... i had no idea it was a major issue with security!!!!!!

---

### Post by Psumi on 2009-11-23
> **Keyper7 said:**
> If that's a problem, enter the command below.

```
sudo -u gdm gconftool-2 --set /apps/gdm/simple-greeter/disable_user_list --type bool true
```

VERY nice, I will be using this from now on.

---

### Post by blueshiftoverwatch on 2009-11-23
> **Keyper7 said:**
> If that's a problem, enter the command below.

...
Thank you.

---

### Post by jacobs444 on 2009-11-23
> **DarinB said:**
> wow so much involved,,, i just thought it was cool to download a theme and copy and paste my own pictures and there you go you have a better picture for your login screen... i had no idea it was a major issue with security!!!!!!

if you want to do that just edit or change the pictures in /usr/share/images/xsplash, i think you may have to use the same resolutions though.

thats how I customized mine

---

