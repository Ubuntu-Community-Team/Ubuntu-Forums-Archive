---
title: "Global menu concept improvement"
date: 2011-10-27
forum: The Cafe
---

### Post by lovinglinux on 2011-10-27
I am really enjoying Unity, but after week using it I have realized the global menu needs some urgent improvement. I like the concept of global menu, but in my opinion, when a window is not maximized, the menu should be displayed in the window title bar and not the Unity panel. It is really confusing and more complicated to reach the global menu in this scenario. Sometimes for example the window loses focus, so the global menu doesn't show until you click the window again, then go to the top panel to access the menu. 

This problem is particularly noticeable when working with Firefox dialogs or Gimp.

I don't know if this has been posted already and if the developers are working to do that or not, but I think this should be implemented. What do you think?

---

### Post by BigSilly on 2011-10-27
I really like it as it is to be honest. I think the only thing I'd like to see is it getting polished up so it's consistent across all programs, and also have it fixed so it properly addresses which window you have in focus. For example, I still use Synaptic, but often when I download something and then click to close when it's done, I suddenly get a popup from Firefox telling me I'm about to close two tabs or whatever as if it's Firefox that's in focus and not Synaptic. At first I thought it was just me, but I could clearly see the Synaptic controls in the panel so I was very confused as to why Firefox should suddenly be affected.

But otherwise I'm enjoying the new. I think the global menus are a good idea and (other than my above concern) work well.

---

### Post by koleoptero on 2011-10-27
> **lovinglinux said:**
> I am really enjoying Unity, but after week using it I have realized the global menu needs some urgent improvement. I like the concept of global menu, but in my opinion, when a window is not maximized, the menu should be displayed in the window title bar and not the Unity panel. It is really confusing and more complicated to reach the global menu in this scenario. Sometimes for example the window loses focus, so the global menu doesn't show until you click the window again, then go to the top panel to access the menu. 

This problem is particularly noticeable when working with Firefox dialogs or Gimp.

I don't know if this has been posted already and if the developers are working to do that or not, but I think this should be implemented. What do you think?

I agree with you on the unmaximized window thing.

---

### Post by arzali on 2011-10-27
I totally agree with you and thats the reason I disable the global menu for FF and Gimp, when I use Unity

---

### Post by kaldor on 2011-10-27
> **lovinglinux said:**
> I am really enjoying Unity, but after week using it I have realized the global menu needs some urgent improvement. I like the concept of global menu, but in my opinion, when a window is not maximized, the menu should be displayed in the window title bar and not the Unity panel. It is really confusing and more complicated to reach the global menu in this scenario. Sometimes for example the window loses focus, so the global menu doesn't show until you click the window again, then go to the top panel to access the menu. 

This problem is particularly noticeable when working with Firefox dialogs or Gimp.

I don't know if this has been posted already and if the developers are working to do that or not, but I think this should be implemented. What do you think?

I've been saying this exact same thing since its inception. Really want Ayatana to realize this needs urgent attention.

---

### Post by BrokenKingpin on 2011-10-27
I think they should just remove it entirely. I really don't see what the value add is at all. Sure if the window is maximized you save a few pixels, but you could just as well auto-hide the top panel (assuming Unity lets you do that). In my opinion the Window Manager should NEVER mess with how an application is displayed. As an application developer I designed applications to have the menu inside the application form, and I don't want something messing with that. I don't even like how applications like Chrome don't use the default window boarders... if you are that concerned about vertical space use the full screen option.

For people who do like the concept of a global menu, I do agree the idea suggested by LovingLinux is a must have. There should also be a simple config option to disable it all together for people who do not like it (such as myself).

---

### Post by kaldor on 2011-10-27
> **BrokenKingpin said:**
> I think they should just remove it entirely. I really don't see what the value add is at all.

I don't need to aim my mouse. I can simple throw it to the top of my screen no matter what application I am running because it will always be in the same place. Originally I thought this would be annoying on large screens, but it's quite convenient because I don't have to keep darting my cursor all over the screen when working on multiple programs.

---

### Post by koleoptero on 2011-10-27
> **kaldor said:**
> I don't need to aim my mouse. I can simple throw it to the top of my screen no matter what application I am running because it will always be in the same place. Originally I thought this would be annoying on large screens, but it's quite convenient because I don't have to keep darting my cursor all over the screen when working on multiple programs.

How do you bring those programs to focus? By force of will?

---

### Post by kaldor on 2011-10-27
> **koleoptero said:**
> How do you bring those programs to focus? By force of will?

Alt tab + throw mouse to top of screen :)

---

### Post by koleoptero on 2011-10-27
:) You know I remember the globalmenu was enabled for both the windows and the bar when unity was still in development before 11.04. Isn't there an option in dconf or whateverconf?

---

### Post by dniMretsaM on 2011-10-27
Sounds like a great idea to me. Although GIMP users could find some relief in single window mode or another program like Krita.

---

### Post by koleoptero on 2011-10-27
> **dniMretsaM said:**
> Sounds like a great idea to me. Although GIMP users could find some relief in single window mode or another program like Krita.

Krita takes some getting used to. I tried it yesterday and nearly got a panic attack lol

---

### Post by dniMretsaM on 2011-10-27
> **koleoptero said:**
> Krita takes some getting used to. I tried it yesterday and nearly got a panic attack lol

:lolflag: True. I haven't used it much, but it seems pretty nice. Try GIMP in single window mode, you'll probably be more comfortable.

---

### Post by kaldor on 2011-10-27
Krita and GIMP aren't meant for the same purposes. Krita is a drawing/art application.

---

### Post by arzali on 2011-10-27
> **koleoptero said:**
> :) You know I remember the globalmenu was enabled for both the windows and the bar when unity was still in development before 11.04. Isn't there an option in dconf or whateverconf?

start an app like this: APPMENU_DISPLAY_BOTH=1 gedit
more info: [http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html](http://www.webupd8.org/2011/03/disable-appmenu-global-menu-in-ubuntu.html)

---

### Post by BrokenKingpin on 2011-10-28
> **kaldor said:**
> I don't need to aim my mouse. I can simple throw it to the top of my screen no matter what application I am running because it will always be in the same place. Originally I thought this would be annoying on large screens, but it's quite convenient because I don't have to keep darting my cursor all over the screen when working on multiple programs.
Aiming a mouse ins't that hard, unless you have a physical Impairment, in which case I apologize. You would still need to "aim" a little bit anyways to hit the correct menu. Like I said I don't care if people like it or not, I just don't see this as a compelling argument for spending the time on a feature like this.

---

### Post by lovinglinux on 2011-10-28
I have used Gimp a lot since I posted this thread an it was really inconvenient to deal with the global menu. Tried Krita and also Pinta, but nothing beats Gimp. Perhaps I am just familiar with it and won't let it go.

I also don't want to disable the global menu, Starting the applications with those commands is an interesting solution, but would kill the convenience of starting an app from Dash, which I find very easy.

---

### Post by ubu_dynamite on 2011-10-28
> **lovinglinux said:**
> I am really enjoying Unity, but after week using it I have realized the global menu needs some urgent improvement. I like the concept of global menu, but in my opinion, when a window is not maximized, the menu should be displayed in the window title bar and not the Unity panel. It is really confusing and more complicated to reach the global menu in this scenario. Sometimes for example the window loses focus, so the global menu doesn't show until you click the window again, then go to the top panel to access the menu. 

This problem is particularly noticeable when working with Firefox dialogs or Gimp.

I don't know if this has been posted already and if the developers are working to do that or not, but I think this should be implemented. What do you think?

when a window is not maximized, the menu should be displayed in the window title bar and not the Unity panel.
Also would be great if the menu was not hidden when maximized.

---

### Post by arzali on 2011-10-28
> **lovinglinux said:**
>  Starting the applications with those commands is an interesting solution, but would kill the convenience of starting an app from Dash, which I find very easy.
What i did:
 gedit  ~/.gimpy
```

UBUNTU_MENUPROXY=0 gimp-2.6

``` chmod +x ~/.gimpy

gksu gedit /usr/share/applications/gimp.desktop
```

[Desktop Entry]
Version=1.0
Type=Application
Name=GIMP Image Editor
GenericName=Image Editor
Comment=Create images and edit photographs[COLOR=Red][B]
Exec=/home/username/.gimpy[/B][/COLOR]
TryExec=gimp-2.6
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.6.11
X-GNOME-Bugzilla-OtherBinaries=gimp-2.6
StartupNotify=true
MimeType=application/postscript;application/pdf;image/bmp;image/g3fax;image/gif;image/x-fits;image/pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/tiff;image/jpeg;image/x-psp;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;image/x-wmf;
X-Ubuntu-Gettext-Domain=gimp20

```perhaps there is an better solution but this works for me

---

### Post by kaldor on 2011-10-28
> **BrokenKingpin said:**
> Aiming a mouse ins't that hard, unless you have a physical Impairment, in which case I apologize. You would still need to "aim" a little bit anyways to hit the correct menu. Like I said I don't care if people like it or not, I just don't see this as a compelling argument for spending the time on a feature like this.

It's not hard, but when moving windows around a lot it's just another thing to have to search for. It's very minor, but I do find it nicer to have one single location to find everything. It also prevents the need for me to reposition a window just to find a menu entry, or losing entries if I shrink the window.

I asked a couple of older relatives about the idea of a global menu. They think it's easier because they only have to "remember" one spot on the screen where it will always be. Another relative is a Mac user (and very tech impaired) and the global menu is one of the things that they love about the UI. Same reason as before- it's always in one place.

I guess growing up using various systems or non-OS X/Amiga Workbench environments make it seem trivial. Personally I am fine either way, but I do prefer using a global menu.

Note just to clarify what I mean by "Aim":

I'm not talking about aiming to select certain items, but instead aiming at a different part of your screen every time you access a different window or move the window around. Consistency is a good thing, so that's why I enjoy the global menu. I obviously do see reasons why others would hate this, of course.

---

### Post by lovinglinux on 2011-10-30
> **arzali said:**
> What i did:
 gedit  ~/.gimpy
```

UBUNTU_MENUPROXY=0 gimp-2.6

``` chmod +x ~/.gimpy

gksu gedit /usr/share/applications/gimp.desktop
```

[Desktop Entry]
Version=1.0
Type=Application
Name=GIMP Image Editor
GenericName=Image Editor
Comment=Create images and edit photographs[COLOR=Red][B]
Exec=/home/username/.gimpy[/B][/COLOR]
TryExec=gimp-2.6
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.6.11
X-GNOME-Bugzilla-OtherBinaries=gimp-2.6
StartupNotify=true
MimeType=application/postscript;application/pdf;image/bmp;image/g3fax;image/gif;image/x-fits;image/pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/tiff;image/jpeg;image/x-psp;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;image/x-wmf;
X-Ubuntu-Gettext-Domain=gimp20

```perhaps there is an better solution but this works for me

Thanks, that worked great.

---

### Post by Tibuda on 2011-10-30
> **arzali said:**
> What i did:
 gedit  ~/.gimpy
```

UBUNTU_MENUPROXY=0 gimp-2.6

``` chmod +x ~/.gimpy

gksu gedit /usr/share/applications/gimp.desktop
```

[Desktop Entry]
Version=1.0
Type=Application
Name=GIMP Image Editor
GenericName=Image Editor
Comment=Create images and edit photographs[COLOR=Red][B]
Exec=/home/username/.gimpy[/B][/COLOR]
TryExec=gimp-2.6
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.6.11
X-GNOME-Bugzilla-OtherBinaries=gimp-2.6
StartupNotify=true
MimeType=application/postscript;application/pdf;image/bmp;image/g3fax;image/gif;image/x-fits;image/pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/tiff;image/jpeg;image/x-psp;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;image/x-wmf;
X-Ubuntu-Gettext-Domain=gimp20

```perhaps there is an better solution but this works for me

Have someone reported a bug to make that by default?

---

### Post by gsmanners on 2011-10-30
So, something like this to configure it (this is just a mock up in glade):

---

