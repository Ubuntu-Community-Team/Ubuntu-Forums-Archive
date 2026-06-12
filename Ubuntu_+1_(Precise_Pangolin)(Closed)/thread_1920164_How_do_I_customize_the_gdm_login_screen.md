---
title: "How do I customize the gdm login screen?"
date: 2012-02-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by JRV on 2012-02-04
I am using gdm, not lightdm, in Precise.

Ubuntu-tweak still looks at lightdm.

Renaming my wallpaper file warty-final-ubuntu.png and putting it in /usr/share/backgrounds still displays the original purple background.

I don't know where to begin to try to change the icon.

---

### Post by dino99 on 2012-02-04
from Harry post:

Then copy (replacing the original one) it to this folder:
/usr/share/backgrounds/

---

### Post by JRV on 2012-02-04
> **dino99 said:**
> from Harry post:

Then copy (replacing the original one) it to this folder:
/usr/share/backgrounds/

I already tried that.

---

### Post by grahammechanical on 2012-02-04
I am not using GDM. I do not have it installed because LightDM is installed so I may not be of much help but I can tell you this:

In /etc/ there is a LightDM folder. It contains configuration scripts. You may find a GDM folder in /etc with similar scripts.

So, there is lightDM.conf which has the line:

> greeter-session=unity-greeter

And a unity-greeter.conf which has the line:

> background=/usr/share/backgrounds/warty-final-ubuntu.png

You need to find the configuration script for GDM and see where it is pointing to for the background wallpaper.

With LightDM the logo is a separate file called logo.png and it is in /usr/share/unity-greeter/

So, we can create our own version of logo.png.

I hope that some of this helps you.

Regards.

---

### Post by Harry33 on 2012-02-04
> **JRV said:**
> I already tried that.

It may very well be that Gdm is using another source for its background,
than /usr/share/backgrounds.
I do not know, I only use LightDM nowadays.
Anyways, try to find the file Gdm is using. Then replace it with your personal image, and with the same name as the original background image.

---

### Post by dino99 on 2012-02-04
some times ago i've reported this issue:

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/904622](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/904622)

maybe you can find some idea reading the comments and find the source used.

---

### Post by JRV on 2012-02-04
> **Harry33 said:**
> 
Anyways, try to find the file Gdm is using. Then replace it with your personal image, and with the same name as the original background image.

That is my plan, but so far I can't find it.

---

### Post by tista on 2012-02-04
Hi JRV ;)

Well, which version of gdm did you run?
If you'd alrady tried my ppa's gdm 3.2.x, then you should customize gdm-greeter via "dconf".

tricks are below:

1. login as gdm in terminal to customize basic appearances of gdm:
```
sudo su - gdm -s /bin/bash
```

2. run dbus-launch to show environments to be needed to run dconf-service:
```
dbus-lauch
```

3. export above 2 envs to register. for example:
```
export DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-tYAlqwhTkN,guid=129ecba86bcd68f851110f920000a6b5
export DBUS_SESSION_BUS_PID=8323
```

4. run dconf-service:
```
/usr/lib/dconf/dconf-service &
```

5. check your gdm's settings values via gsettings:
```
GSETTINGS_BACKEND=dconf gsettings gsettings get org.gnome.desktop.background picture-uri
```

6. re-set this value as what you want. for example:
```
GSETTINGS_BACKEND=dconf gsettings gsettings [color=red]set[/color] org.gnome.desktop.background picture-uri [color=red]"file:///usr/share/backgrounds/WildWheat_by_Brian_Burt.jpg"[/color]
```

But as far as I know in gdm 3.0.x or lower version, anyway we'd better to customize that via "dconf" instead of "hack the file name and places directly"... ;)

cheers.
tista.

---

### Post by JRV on 2012-02-05
I am using gdm from the precise repositories.

I could not change it with dconf-editor.

When I tried the command line method all appeared to work, no error messages, but when I restarted I had the same ugly purple screen.

---

### Post by dino99 on 2012-02-05
if you search "gdm" via the nautilus quicksearch field then you will get a list of related folders/files where you might find the config which drive the wallpaper to blame. Wonder if the plymouth theme is used with gdm.

---

### Post by JRV on 2012-02-06
I just want to thank all for the suggestions.  
I have not solved the problem, but I need to move on to other things.
Now that XDMCP is possible in lightdm I will not need gdm.

---

### Post by hugmenot on 2012-02-06
The solution lies in these files:

/usr/share/gconf/defaults/16_ubuntu-artwork
/usr/share/glib-2.0/schemas/ubuntu-artwork.gschema.override

---

