---
title: "RDP into ubuntu default desktop change"
date: 2013-01-11
forum: Virtualisation
---

### Post by d347hm4n on 2013-01-11
Hello folks,

I have an ubuntu VM running on a vsphere, I've installed xrdp on it and can rdp to it just fine.

When I login I an presented with unity as my desktop manager, I would like to use kde as the desktop manager instead, but I only want to change it on my user, I want to leave the other users using unity. How do I do this?

Thanks,

d3

---

### Post by zombifier25 on 2013-01-11
From your Ubuntu comp, log out, choose KDE, and log in. It will be set as default for your user until you change it again.

---

### Post by d347hm4n on 2013-01-11
I have done this and when I rdp it still logs me into unity. When I remote onto the vm instance in the vsphere client, I have kde selected next to my user.

---

### Post by d347hm4n on 2013-01-11
I modified /etc/xrdp/startwm.sh to the following. Now when I login with my account I get KDE and when someone else logs in they get unity. Working perfectly.

```
#!/bin/sh

if [ -r /etc/default/locale ]; then
  . /etc/default/locale
  export LANG LANGUAGE
fi

#. /etc/X11/Xsession

USER = "$(whoami)"

if [ $USER = "myName" ]; then
   startkde
else
   . /etc/X11/Xsession
fi

```

---

### Post by steeldriver on 2013-01-11
you could also have put it in ~/.xrdp/.xsession I think (I haven't tried it with startkde because I don't have kde desktop packages installed, but it works for setting a plain xterm)

a bit tidier imho

---

