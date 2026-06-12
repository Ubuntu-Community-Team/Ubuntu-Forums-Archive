---
title: "How to auto-login on xubuntu 14.04"
date: 2014-02-17
forum: Ubuntu Development Version
---

### Post by mmf2 on 2014-02-17
Hey.

I'm using Xubuntu 14.04 and I'm interested in logging in directly to the desktop. I've, in my user settings, my account configured not to ask for a password on login. However, I still need to press "enter", which kind of annoyes me.

Is there a way to boot directly to the desktop? 

PS: My title is kind of bad, perhaps you (an admin) should change it to something more descriptive.

---

### Post by zika on 2014-02-17
> **mmf2 said:**
> PS: My title is kind of bad, perhaps you (an admin) should change it to something more descriptive.You can change title for Yourself (advanced editor)...

---

### Post by mmf2 on 2014-02-17
> **zika said:**
> You can change title for Yourself (advanced editor)...

I don't know what to write...

---

### Post by steeldriver on 2014-02-17
I'm not on 14.04 yet, but it sounds like you set up *nopasswdlogin *rather than *autologin *(they are different things)

If things haven't changed too much then you should be able to configure lightdm (which I *think* is used by Xubuntu) for autologin either by editing the lightdm.conf file or by using the lightdm-set-defaults utility

```
sudo /usr/lib/lightdm/lightdm-set-defaults --autologin *username*
```

See [https://wiki.ubuntu.com/LightDM#Autologin](https://wiki.ubuntu.com/LightDM#Autologin)

---

### Post by mmf2 on 2014-02-18
> **steeldriver said:**
> I'm not on 14.04 yet, but it sounds like you set up *nopasswdlogin *rather than *autologin *(they are different things)

If things haven't changed too much then you should be able to configure lightdm (which I *think* is used by Xubuntu) for autologin either by editing the lightdm.conf file or by using the lightdm-set-defaults utility

```
sudo /usr/lib/lightdm/lightdm-set-defaults --autologin *username*
```

See [https://wiki.ubuntu.com/LightDM#Autologin](https://wiki.ubuntu.com/LightDM#Autologin)

Hey steeldriver. Thank's for the help but unfortunately, it did not work. When I try that, it says "command not found".

---

### Post by Elfy on 2014-02-18
Quick check found 

[https://launchpad.net/ubuntu/+source/lightdm/+changelog](https://launchpad.net/ubuntu/+source/lightdm/+changelog)

>  - Remove lightdm-set-defaults and gdmflexiserver.

I did have a quick play last night with this - setting in users and groups to not want password at login, adding autologin to the lightdm.conf - just ended up with no authentication and no way seemingly at the login to do so.

---

### Post by mmf2 on 2014-02-18
> **Elfy said:**
> Quick check found 

[https://launchpad.net/ubuntu/+source/lightdm/+changelog](https://launchpad.net/ubuntu/+source/lightdm/+changelog)



I did have a quick play last night with this - setting in users and groups to not want password at login, adding autologin to the lightdm.conf - just ended up with no authentication and no way seemingly at the login to do so.

So, if I understand correctly, by deleting lightdm-set-defaults and gdmflexiserver I'll accomplish what I want?

---

### Post by Elfy on 2014-02-19
No idea, I didn't try it. If you break it you get to keep both bits at least. Try it in a vm :)

---

### Post by mmf2 on 2014-02-20
I don't feel very comfortable trying something like that.. I hate to break my OS! 

Btw, does your trash icon also bug when not empty?

---

### Post by AndyGaskell on 2014-05-14
I was reading this thread and got auto-login working ok in Xubuntu 14.04

I think in older version of Xubuntu, 11.10, for example, the lightdm conf files was at "/etc/lightdm/lightdm.conf" (as per soloution at [http://ubuntuforums.org/showthread.php?t=1864527](http://ubuntuforums.org/showthread.php?t=1864527)) but now it is at "/etc/lightdm/lightdm.conf.d/10-xubuntu.conf".

So, I just changed this from...

> [SeatDefaults]
user-session=xubuntu
 
...to...

> [SeatDefaults]
user-session=xubuntu
autologin-user=cfi-user

...and now it is logging in fine.  My username is "cfi-user", so change that to yours.  "cfi-user" might seem an odd name, but this is an embedded customer service kiosk thing.

---

### Post by coffeecat on 2014-05-14
14.04 is now released. 

Thread closed.

---

