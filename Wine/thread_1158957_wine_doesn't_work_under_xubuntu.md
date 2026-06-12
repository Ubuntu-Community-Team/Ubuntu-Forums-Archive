---
title: "wine doesn't work under xubuntu"
date: 2009-05-14
forum: Wine
---

### Post by Electron on 2009-05-14
I got Jaunty installed on my laptop, last night I want to try Xfce desktop so I  installed Xubuntu desktop. Now I have both (Gnome and Xcfe) and everything is running good :) 
My only problem is with Wine, I got three application that runs good under Wine Gnome desktop, but when I switch to Xubuntu only one of them works. I don't know what the problem is. Is something related with wine? Where should I start looking?
The two application that don't work under Xubuntu need microsoft fonts to open. Is that could be the problem? The work fine under Gnome (I installed the fonts).
If this help this is how I update:

sudo aptitude install xubuntu-desktop
 
and no problem during installation. That's all.

---

### Post by asdfoo on 2009-05-14
> **Electron said:**
> I got Jaunty installed on my laptop, last night I want to try Xfce desktop so I  installed Xubuntu desktop. Now I have both (Gnome and Xcfe) and everything is running good :) 
My only problem is with Wine, I got three application that runs good under Wine Gnome desktop, but when I switch to Xubuntu only one of them works. I don't know what the problem is. Is something related with wine? Where should I start looking?
The two application that don't work under Xubuntu need microsoft fonts to open. Is that could be the problem? The work fine under Gnome (I installed the fonts).
If this help this is how I update:

sudo aptitude install xubuntu-desktop
 
and no problem during installation. That's all.

terminal output, Wine version?

---

### Post by Electron on 2009-05-15
Thanks for respond to this post!

The wine version is wine 1.0.1, and for terminal output what do you mean? It doen't give me any feedback it simply does not start the application.

Anyway I found a post on the Wine website related to this problem with this application. So far I have work around the problem doing the following.. I'll keep this post update is the final solution is found. Once again thank you.
From the Wine website

Problems with XFCE
XFCE ignores path parameter for desktop and menu launchers ... The simple solution is to change "Command" parameter in launcher to

    wine start wtlibrary.exe

---

