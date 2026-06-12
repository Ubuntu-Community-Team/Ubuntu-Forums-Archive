---
title: "enable auto login on ubuntu 12.04 lts"
date: 2013-07-19
forum: Virtualisation
---

### Post by pegi on 2013-07-19
[COLOR=#000000][FONT=times new roman]Dear friends
[/FONT][/COLOR]
I need to enable auto login on LXC(Ubuntu 12.04 lts) 
i have  tested the some commands for 12.04 but i do not know why it does not working...

thank you so much for your attention and cooperation in advance

---

### Post by slickymaster on 2013-07-19
To enable auto login you need to edit the **/etc/lightdm/lightdm.conf** file. Just run at a terminal window the following:```
sudo geany /etc/lightdm/lightdm.conf
```and add the following lines replacing USERNAME with your own username:```
autologin-user=USERNAME
autologin-user-timeout=0
``` Save and close the file.

---

