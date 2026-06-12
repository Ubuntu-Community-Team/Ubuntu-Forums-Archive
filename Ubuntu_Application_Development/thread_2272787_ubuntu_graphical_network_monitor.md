---
title: "ubuntu graphical network monitor"
date: 2015-04-08
forum: Ubuntu Application Development
---

### Post by ashtum on 2015-04-08
hi friends .
I began a open source network monitoring project for linux , program  written in c   language and use xlib to have a transparent gui for  Charting network   traffic usage , it can run without any special library .

[IMG]https://cloud.githubusercontent.com/assets/11743154/6994226/55522172-db26-11e4-9648-7f3d6f932142.png[/IMG]

**Download and Usage**

  [SIZE=2]Download [Latest Release]("https://github.com/ashtum/ashmon/releases/latest") extract files , go to path and install ashmon by : *[COLOR=#800080]sudo sh install.sh[/COLOR]*
run ashmon by : [COLOR=#800080]*ashmon "network-interface"*[/COLOR] replace "network-interface" with that network interface you want monitored , like : *[COLOR=#800080]ashmon eth0[/COLOR]* or *[COLOR=#800080]ashmon wlan0[/COLOR]* or [COLOR=#800080]*ashmon ppp0*[/COLOR]
if you want ashmon start automatically on system startup just run autostart.sh script by : [COLOR=#800080]*sudo sh autostart.sh*[/COLOR]

  [B]gui operations :
[/B]
[/SIZE]
[LIST]
[*][SIZE=2] [COLOR=#800080]**click** [/COLOR]fade out window for 5 seconds .
[/SIZE] 
[*][SIZE=2]   [COLOR=#800080]**click and drag**[/COLOR] move window everywhere you want .
[/SIZE] 
[*][SIZE=2]   [COLOR=#800080]**mouse whele up/down**[/COLOR] change window opacity .
[/SIZE] 
[*][SIZE=2]   [COLOR=#800080]**right click**[/COLOR] exit application .

[/SIZE] 
[/LIST]
[SIZE=2]There are usage and compile tips on the github page :
github link : [URL="https://github.com/ashtum/ashmon"]https://github.com/ashtum/ashmon

[/URL][/SIZE][SIZE=2]i need help for make a pakage of this program for ubuntu .
and how i can proposal it to ubuntu repositorie .     [/SIZE]

---

### Post by mkamenjak on 2015-04-16
Looks awesome,I am installing it!

---

### Post by ashtum on 2015-04-29
> **mkamenjak said:**
> Looks awesome,I am installing it!

Thanks .
Please report likely problems .

---

### Post by GnudeNoob on 2015-06-04
> **ashtum said:**
> hi friends .
I began a open source network monitoring project for linux , program  written in c   language and use xlib to have a transparent gui for  Charting network   traffic usage , it can run without any special library .


Nice one...both 'make' and run works fine for me (14.04 64bit)

---

