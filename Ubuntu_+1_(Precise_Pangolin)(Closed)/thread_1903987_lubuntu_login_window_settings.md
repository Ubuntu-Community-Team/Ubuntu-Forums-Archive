---
title: "lubuntu login window settings"
date: 2012-01-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ronacc on 2012-01-03
I want to set my desktop to login automaticly after a 10 second delay , I cannot find any settings for the login window .

---

### Post by effenberg0x0 on 2012-01-04
> **ronacc said:**
> I want to set my desktop to login automaticly after a 10 second delay , I cannot find any settings for the login window .

Ronacc, have a look at /etc/lightdm/lightdm.conf . I haven't tried it recently, but back when we started testing PP, I had a HTPC machine set to autologin and start XBMC. It was set like this:

$ cat /etc/lightdm/lightdm.conf.backup.xbmc
```
[SeatDefaults]
autologin-guest=false
autologin-user=USERNAME 
autologin-user-timeout=0 #not sure if seconds or ms, can't remember
user-session=ubuntu #self explanatory
greeter-session=unity-greeter #self explanatory
```

---

### Post by ronacc on 2012-01-04
thanks effenberg0x0  , That wasn't it but it jogged my memory and I found the right one . its /etc/lxdm/lxdm.conf   you uncomment the autolgin line and change dgod to your user name and then uncomment the timeout=10 line .

and the 10 is seconds , you can change it to another value if you want .

---

### Post by effenberg0x0 on 2012-01-04
> **ronacc said:**
> thanks effenberg0x0  , That wasn't it but it jogged my memory and I found the right one . its /etc/lxdm/lxdm.conf   you uncomment the autolgin line and change dgod to your user name and then uncomment the timeout=10 line .

and the 10 is seconds , you can change it to another value if you want .

Ah, sorry, forgot you're on lubuntu... That's for default Ubuntu/lightdm, not lxdm... But glad it helped somehow :)

---

### Post by ronacc on 2012-01-04
I actually have 3 different testing installs Ubuntu with gnome-shell Lubuntu and Kubuntu + 3 non Ubuntu install , bouncing around between all 6 keeps me permanently confused :lolflag:

---

