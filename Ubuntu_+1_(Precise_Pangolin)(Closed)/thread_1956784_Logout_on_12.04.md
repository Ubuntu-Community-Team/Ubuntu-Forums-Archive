---
title: "Logout on 12.04"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Cpierce on 2012-04-11
I am used to having a logout icon on my cairo dock in lucid. I just installed 12.04 and found the logout program in bash and dragged it on my unity dock. Everything worked fine until I updated. Now my logout button is gone and I can't find it with bash. Seems the update deleted it.

Anyone know how to get it back ?

---

### Post by nothingspecial on 2012-04-12
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by Cpierce on 2012-04-12
Well I guess I don't know what I am doing. I guess my question should be how do I get a logout button on my Unity dock and keep it ?

---

### Post by philinux on 2012-04-12
> **Cpierce said:**
> Well I guess I don't know what I am doing. I guess my question should be how do I get a logout button on my Unity dock and keep it ?

Open Dash and type logout then drag the icon to the launcher.

---

### Post by bluenova on 2012-04-12
> **philinux said:**
> Open Dash and type logout then drag the icon to the launcher.

I think that's what he did before.

The point is the Logout, Shutdown etc have been removed from the Dash in latest update.

---

### Post by mc4man on 2012-04-12
The .desktops where removed via this bug fix
[https://bugs.launchpad.net/indicator-session/+bug/973181](https://bugs.launchpad.net/indicator-session/+bug/973181)

If you wish one or more of them back then dl the previous indicator-session package, extract the .deb, & copy the .desktop(s) to either /usr/share/applications or ~/.local/share/applications, they can be found in the usr/share/applications folder

[https://launchpad.net/ubuntu/+source/indicator-session/0.3.95-0ubuntu1](https://launchpad.net/ubuntu/+source/indicator-session/0.3.95-0ubuntu1)

Or go for instance for log out
```
gedit ~/.local/share/applications/indicator-session-logout.desktop
```

or (maybe better for cairo dock?
```
sudo gedit /usr/share/applications/indicator-session-logout.desktop
```

```
[Desktop Entry]
Name=Log Out
TryExec=/usr/lib/indicator-session/gtk-logout-helper
Exec=/usr/lib/indicator-session/gtk-logout-helper --logout
Icon=system-log-out
Terminal=false
Type=Application
OnlyShowIn=Unity;
Categories=System;
Version=1.0
X-Ubuntu-Gettext-Domain=indicator-session
```

---

### Post by jbicha on 2012-04-12
And of course, you can click the icon at the top right of your screen and click Log Out...

---

### Post by Cpierce on 2012-04-12
Bluenova, you are right, that's what I did before. jbicha, that is what I have been doing, but the big button is easier for us older farts. Mc4man, you are the only one that offered a solution and I will try that.

Still don't know why the update removed it.

---

### Post by Cpierce on 2012-04-13
Mc4man, I did that and I did get a logout. However, it was just a logout. The previous "logout" that was in bash, had the option to restart or shutdown. It was the same menu as clicking the top right icon and selecting shutdown. 

How do I get that back ?

---

### Post by jbicha on 2012-04-13
You could also just press your computer's power button.

---

### Post by mc4man on 2012-04-13
If you want that then likely this .desktop

```
[Desktop Entry]
Name=Shut Down
TryExec=/usr/lib/indicator-session/gtk-logout-helper
Exec=/usr/lib/indicator-session/gtk-logout-helper --shutdown
Icon=system-shutdown
Terminal=false
Type=Application
OnlyShowIn=Unity;
Categories=System;
Version=1.0
X-Ubuntu-Gettext-Domain=indicator-session
```

---

### Post by Cpierce on 2012-04-13
Mc4man............you are the man ! 

Thank you

---

### Post by Cpierce on 2012-04-13
Mc4man, a quick question. Where is this script pull the icon from ? Where is the icons located ? I would like to change it.

---

