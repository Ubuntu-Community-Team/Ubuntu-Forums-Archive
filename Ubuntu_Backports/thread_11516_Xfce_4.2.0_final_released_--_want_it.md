---
title: "Xfce 4.2.0 final released -- want it?"
date: 2005-01-17
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-17
I just noticed XFCE 4.2.0 Final is out. Does anyone have dire need for it? It was a lot of work in the first place!

---

### Post by HiddenWolf on 2005-01-17
[QUOTE=jdong]I just noticed XFCE 4.2.0 Final is out. Does anyone have dire need for it? It was a lot of work in the first place![/QUOTE]
Wait for it to be in hoary...

---

### Post by poofyhairguy on 2005-01-18
[QUOTE=jdong]I just noticed XFCE 4.2.0 Final is out. Does anyone have dire need for it? It was a lot of work in the first place![/QUOTE]

Don't worry about it jdong, I used the Repo provided on the XFCE download page.

[http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)

Its works well. I was able to smoothly upgrade over your version. Thanks for the first debs, thats what got me hooked! This is all I'll run on my laptop now. its nice! much better than KDE IMHO!

EDIT: I went back and noticed that the only way I was able to get XFCE to install was your xnetcardconfig package in staging.

---

### Post by HiddenWolf on 2005-01-18
[QUOTE=poofyhairguy]Don't worry about it jdong, I used the Repo provided on the XFCE download page.

[http://www.os-works.com/view/debian/](http://www.os-works.com/view/debian/)

Its works well. I was able to smoothly upgrade over your version. Thanks for the first debs, thats what got me hooked! This is all I'll run on my laptop now. its nice! much better than KDE IMHO!

EDIT: I went back and noticed that the only way I was able to get XFCE to install was your xnetcardconfig package in staging.[/QUOTE]
Is XFCE actually noticably faster than gnome/kde?

---

### Post by poofyhairguy on 2005-01-18
[QUOTE=HiddenWolf]Is XFCE actually noticably faster than gnome/kde?[/QUOTE]

I have been using the new version for a day and a half and I can say that yes it is. In KDE and Gnome, the desktop environment ate up so many resources that my 400mhz celeron couldn't play divx movies without major skipage, on XFCE it fine. 

Using it on my big box (2.66 P4) shows less differences. I bet anything over 2ghz + 256mb ram will handle Gnome and Xfce about the same.

I will probably switch back from Xfce to Gnome on my big box soon because I miss my weather applet, but XFCE is nice. I especially like not seeing the weird windowlines when I minimize, maximize stuff in gnome!

---

### Post by MoveZig on 2005-01-18
I used this to install Xfce: (use sudo when you do so)
[http://www.os-cillation.com/article.php?sid=43](http://www.os-cillation.com/article.php?sid=43) 

Took less than five minutes to install.

Then create a .desktop file with this in it: (name it xfce.desktop or something similar)

[Desktop Entry]
Encoding=UTF-8
Name=Xfce 4.2 Session
Comment=Use this session to run Xfce 4.2 as your desktop environment
Exec=/usr/local/bin/startxfce4
Icon=/usr/local/share/pixmaps/xfce4_xicon1.png
Type=Application

Move it to /usr/share/xsessions, Restart gnome and Xfce will be listed under the sessions tab on the login screen. 

It runs very fast compared to gnome.  Takes less than 4 seconds to boot up, and in general, VERY fast.

---

### Post by Michael Steinberg on 2005-01-18
I too used the os-cillations installer, as "root" via sudo--very smooth after I added the missing libraries with Synaptic, which the xfce installer noticed right off when I restarted it. And I did none of the additional commands after installation; the option for xfce was right in the menu when I logged out.

Very nice environment so far. A pleasure to change the "face" of the system so easily.

---

### Post by MoveZig on 2005-01-18
[QUOTE=Michael Steinber]And I did none of the additional commands after installation; the option for xfce was right in the menu when I logged out.[/QUOTE]

Hmm... GDM didn't recognize it after I did the install, so I had to to the above in my previous post.

I forgot to say to install it using sudo.  (edited now)

---

### Post by spaceballl on 2005-02-07
So about 60% of the way through the installer, it crashes for me and the log file produces this... any thoughts??
-Kevin

libglib-2.0.so -Wl,--rpath -Wl,/usr/local/lib
xfce4_session-xfsm-properties.o(.text+0xdc8): In function `xfsm_properties_load':
: undefined reference to `compose'
xfce4_session-xfsm-properties.o(.text+0xe38): In function `xfsm_properties_load':
: undefined reference to `compose'
xfce4_session-xfsm-properties.o(.text+0xee5): In function `xfsm_properties_load':
: undefined reference to `compose'
xfce4_session-xfsm-properties.o(.text+0xf27): In function `xfsm_properties_load':
: undefined reference to `compose'
xfce4_session-xfsm-properties.o(.text+0xf69): In function `xfsm_properties_load':
: undefined reference to `compose'
xfce4_session-xfsm-properties.o(.text+0xfab): more undefined references to `compose' follow
collect2: ld returned 1 exit status
make[2]: *** [xfce4-session] Error 1
make[2]: Leaving directory `/tmp/xfce4-4.2.0-installer/xfce4-session/xfce4-session'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/xfce4-4.2.0-installer/xfce4-session'
make: *** [all] Error 2
!! Failed to build xfce4-session, see the errors above
!! for details on the problem.

---

### Post by lockenkeyster on 2005-02-08
so, for me the installer gets almost to 100%, but then flakes out and give this in the error log:

.....
checking for unsetenv... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gobject-2.0 >= 2.2.0... Requested 'gobject-2.0 >= 2.2.0' but version of GObject is 2.0.7

configure: error: Library requirements (gobject-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
!! Failed to configure libxfce4util, see the errors above
!! for details on the problem.

anyone have any ideas?

thanks in advance!

---

### Post by kori.mendocino on 2005-02-08
[QUOTE=lockenkeyster]so, for me the installer gets almost to 100%, but then flakes out and give this in the error log:

.....
checking for unsetenv... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gobject-2.0 >= 2.2.0... Requested 'gobject-2.0 >= 2.2.0' but version of GObject is 2.0.7

configure: error: Library requirements (gobject-2.0 >= 2.2.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
!! Failed to configure libxfce4util, see the errors above
!! for details on the problem.

anyone have any ideas?

thanks in advance![/QUOTE]

All you need in this case is a newer GObject (2.2.0 or up), install it with Synaptic.

---

### Post by landotter on 2005-02-08
[QUOTE=poofyhairguy]

Using it on my big box (2.66 P4) shows less differences. I bet anything over 2ghz + 256mb ram will handle Gnome and Xfce about the same.

I will probably switch back from Xfce to Gnome on my big box soon because I miss my weather applet[/QUOTE]

I don't feel a big performance boost using XFCE vs. Gnome on a 1.1ghz/256mb box when doing day to day stuff. I'm sure I'd notice on a slower box. I do find it interesting that gnome seems faster now than the 1.4x series.

BTW, XFCE has a fabulous weather applet. :P

---

### Post by lockenkeyster on 2005-02-08
[QUOTE=kori.mendocino]All you need in this case is a newer GObject (2.2.0 or up), install it with Synaptic.[/QUOTE]

tried searching for that yesterday, but it's not in my repository... I've double-checked that I have all the necessary repos linked, but no dice...

EDIT: added my sources.list (just in case...)

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041013)]/ unstable main restricted 


## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe multiverse 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 

deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports/](http://cloud9.somniumcomputing.com:81/ubuntu/backports/) warty-backports main universe multiverse restricted 

deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports/](http://cloud9.somniumcomputing.com:81/ubuntu/backports/) warty-backports-staging main universe multiverse restricted 

deb [http://cloud9.somniumcomputing.com:81/ubuntu/backports/](http://cloud9.somniumcomputing.com:81/ubuntu/backports/) warty-extras main universe multiverse restricted 

deb [http://www.os-works.com/debian/](http://www.os-works.com/debian/) testing main  

# deb [http://wine.sourceforge.net/Ubuntu/apt/](http://wine.sourceforge.net/Ubuntu/apt/) binary/ 
# deb-src [http://wine.sourceforge.net/Ubuntu/apt/](http://wine.sourceforge.net/Ubuntu/apt/) source/ 

deb-src [http://www.os-works.com/debian/](http://www.os-works.com/debian/) testing main

---

### Post by Jad on 2005-02-08
What I didn't like in XFCE, I couldn't figure out how to setup keyboard layout, I use englisg/arabic

---

### Post by foxy123 on 2005-06-19
Any chance to get 4.2.2 backported?

---

### Post by skoal on 2005-06-19
"*Xfce 4.2.0 final released -- want it*?"
This is obviously a trick question! For a second there, I almost fell for it.  I for one welcome my XFCE backporting overlords!

\\//_

---

### Post by virgule on 2005-06-19
[QUOTE=Jad]What I didn't like in XFCE, I couldn't figure out how to setup keyboard layout, I use englisg/arabic[/QUOTE]

Xfce4 use GNOME's engine (gtk?). A lot of settings from GNOME will affect Xfce4's behavior.. I would try to use **gnome-keyboard-properties** from within XFce4 and see if it work.

---

### Post by DarkSilver on 2005-06-20
edit
(is there a delete option ?)

---

