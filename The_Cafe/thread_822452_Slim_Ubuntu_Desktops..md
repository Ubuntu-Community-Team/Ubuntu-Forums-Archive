---
title: "Slim Ubuntu Desktops."
date: 2008-06-08
forum: The Cafe
---

### Post by kagashe on 2008-06-08
I am Ubuntu user since version 5.04 and it use to run on Gnome Desktop on 128 MB RAM comfortably. When Dapper Drake arrived I could install it but I had to add RAM to use it. I added 256 MB. Then the Laptop Display was broken and I converted the Laptop into Desktop by connecting an external monitor. This reduced available RAM to 312 MB.

I installed Gutsy and could use enhanced Desktop effects but it was very slow. I added KDE 4 also just to see what is coming but it was slow. For daily tasks I added Fluxbox. Then I saw LXDE thread and added LXDE. Since then I was using LXDE and liked it very much.

For Hardy Heron I decided to do Cli install and add Window Managers one by one. Initially I added openbox and fbpanel. Then I tried to install lxde meta package but it failed to install due to unmet dependencies. I checked the dependencies and could not find 3 packages in Ubuntu repositories. I downloaded these packages from Debian and installed through dpkg. Finally I could install LXDE Desktop.

Initially, I did not install any Login Manager and was using startx command after console login.

Today I discovered slim login manager and installed it. On Login Screen I could select the session by pressing F1 key. The first option was XFCE which I had not installed. After pressing F1 again the second option was openbox and I could login to openbox. Third option was IceWM, so I installed IceWM and could login to IceWM session.

I searched for "slim" files and got /etc/slim.conf file. In the section "Available sessions" I changed "xfce4-session" to "lxsession" which also became the default session.

Now I could login to LXDE Desktop. Then I thought that I should add all light weight WMs to the sessions and downloaded Fluxbox and JWM and replaced "wmaker" and "blackbox" with "jwm" and "fluxbox".

I really like these "Slim Ubuntu Desktops" and slim login manager.
LXDE
openbox
IceWM
Fluxbox
JWM

kagashe

---

### Post by mkendall on 2008-06-08
I really like this post. Thank you for sharing.

---

### Post by zmjjmz on 2008-06-08
Don't forget PekWM and...
well, vtwm is like from the 90s but you can still use it.

---

### Post by chucky chuckaluck on 2008-06-08
i've been a big fan of lightweight wm's since early on (first out of necessity and then, just because i like them better). if you haven't tried a tiling wm yet, you might give dwm a shot. it's wicked light and you could probably save some memory by using it. also, you might want to check out evilwm. both dwm and evilwm are a slightly different cup of tea from what you've been using and you might find them entertaining, at least.

---

### Post by zmjjmz on 2008-06-08
I've found e16 (the old one that is way more stable) to be very light.
Can't say the same about e17.

---

### Post by slackthumbz on 2008-11-14
I'd have to go with e16, the fact is that it's much easier to configure than many of the light wm's such as the *box family and it remains capable of being very graphically pretty :) my one little bugbear with ubuntu at the moment is that although the latest version of e16 is available in the the repositories there is no package for the epplets (like little desktop applets, very cute) in intrepid. I'm currently using an acer aspire one (it's tiny) and initially installed xubuntu on it. My model of the 'one' has 512mb ram and 120GB hdd. I figured xubuntu would be ideal and so far it more or less has been but I have noticed some performance slowdowns and minor annoyances when watching video etc. 

So I switched the desktop to e16. screenshot -> 
[http://omploader.org/veGFz/2008-11-14-132727_1024x600_scrot.png](http://omploader.org/veGFz/2008-11-14-132727_1024x600_scrot.png)

e16 can take a little getting used to but once you do it's extremely rewarding. Using apps such as e16keyedit you can easily configure key bindings and the menu format is very, very simple. A little tip, screen backgrounds are supposed to stored in ~/.e16/backgrounds/ but I tend to just symlink that path to my wallpapers folder ~/Pictures/wallpapers :)

I reckon it's got to be the best lightweight wm around.

---

### Post by K.Mandla on 2008-11-14
Closed for necromancy.

---

