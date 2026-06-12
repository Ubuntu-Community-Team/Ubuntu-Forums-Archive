---
title: "remove xubuntu from ubuntu server install"
date: 2010-04-13
forum: Server Platforms
---

### Post by knowram on 2010-04-13
I have set up an ubuntu install to run as a router/firewall and just about everything was working. The only thing I was having problems with was getting vpnc to stay connected to a remote site. I was told that kvpnc works much better so I installed xubuntu to give it a try. Once xubuntu was install everything started running really slow. not knowing the real differences between the normal ubuntu desktop, xubuntu, and kubuntu I just guessed that xubuntu was the best option for a light weight gui that i could use to install kvpnc. However it seems i am wrong. I would like to uninstall xubuntu and install the normal ubuntu desktop without some of the desktop addons like Evolution and OpenOffice, but continue to use the server flavor kernel use the following command ```
sudo aptitude install --no-install-recommends ubuntu-desktop
```
Can anyone help me out or even tell me that this is the wrong idea?

Thanks for the help.

---

### Post by dudumomo on 2010-04-14
If you want Ubuntu without any software as Evolution, firefox, openoffice, etc.. you have to install gnome-core
sudo apt-get install gnome-core

---

### Post by knowram on 2010-04-14
Will that let me add things as i want or need them like kvpnc, file sharing, etc. ?

Also do i need to remove xubuntu before doing this? if so how?

---

