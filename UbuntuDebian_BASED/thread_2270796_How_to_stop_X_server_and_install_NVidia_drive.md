---
title: "How to stop X server and install NVidia drive"
date: 2015-03-25
forum: Ubuntu/Debian BASED
---

### Post by talialu on 2015-03-25
Hi all,
last night I do a fresh installation of PinguyOS (64bit based on Ubuntu 14.04) in my Lenovo U410.
It's all perfect, I fix some minor bug.....life of battery approx ok....just the big issue when I attempt to install NVidia drive.

Now.....I try for first time with ubuntu "software and update ----> additional drive" I've select the NVidia drive.....I proceeded to install this, .....finish the procedure and when I shot down the system all was freeze and I have force the shot down; when I switch-on the laptop start the screen and after 5sec all system are stopped and I have blanck screen.

So, I decide to change the way of installation. I've download the NVidia drive from the site ([COLOR=#555555][FONT=Arial]NVIDIA 346.47 [/FONT][/COLOR][COLOR=#555555][FONT=Arial]GPU driver[/FONT][/COLOR])....convert the .run file in executable, in terminal I kill the [COLOR=#555555][FONT=Arial]display manager ([/FONT][/COLOR][COLOR=#555555][FONT=consolas]$ sudo /etc/init.d/lightdm stop[/FONT][/COLOR][COLOR=#555555][FONT=Arial]).....[/FONT][/COLOR] all done, but when I run command of installation the system stop the installation drive because the X server run (doesn't stop it).

Any idea to resolve this issue? 

from now I disable the grafic card from BIOS and all ok.

Thx a lot in advance for the attention and for any help.

---

### Post by howefield on 2015-03-25
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

