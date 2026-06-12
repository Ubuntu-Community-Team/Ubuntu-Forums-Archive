---
title: "Problems with beryl"
date: 2007-02-20
forum: Ubuntu Customization Guide
---

### Post by evertvr on 2007-02-20
Hi there!,

I have problems with my beryl not working properly.

If I start the beryl-manager everything goes find, but then when I try to switch to beryl as window manager (still in my gnome environment) the windows that are open flickr a few times. Then it stops, and metacity is my window manager again. What should be the cause of this problem?

Thanks in advance, evertvr

---

### Post by ytrewq on 2007-03-07
I have the same problem in my Kubuntu. I had it working fine and nice but now suddently it doesn't work at all. Only same kind of flickering windows and then back to old window manager. I may have done something with some settings but I haven't got any idea what it could be. 
My Kubuntu is 6.10 Edgy and I have the Nvidia quadro FX 560.

---

### Post by Waappu on 2007-03-07
> **evertvr said:**
> Hi there!,

I have problems with my beryl not working properly.

If I start the beryl-manager everything goes find, but then when I try to switch to beryl as window manager (still in my gnome environment) the windows that are open flickr a few times. Then it stops, and metacity is my window manager again. What should be the cause of this problem?

Thanks in advance, evertvr

Hi

Type in terminal ```
beryl
```and see if there some error message that might help to find problem

---

### Post by Gorbachev on 2007-03-10
I am almost positive I know the problem. 

Use Envy to install your graphics card drivers. Then try to enable Beryl again and explode with joy.

---

### Post by Th1eF` on 2007-03-13
i had the same problem...and when i write beryl in terminal i get the following:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by Ze`tah on 2007-03-13
exact same problem here.. :confused:  envy dosen`t sove it .. :(

---

### Post by crimesaucer on 2007-03-14
I'm not an expert, but I'm wondering if you did this part of configuration when you installed Beryl:

This is the link to the wiki that I used. Following every direction worked perfectly for me: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX)

This is the part I think that is your issue:

*************This is from the wiki for installing Beryl AiGLX for 6.10 Edgy.******************

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

Configuring Beryl

Now that Beryl and AIGLX are installed, you need a way to start them up automatically. It is best to have a separate session (in GDM or KDM) for AIGLX, as some applications don't run properly with it (such as OpenGL games or remote sessions), and because it is experimental software that may be unstable and buggy. That way you can always log out or restart the X server and log into a regular session.


We will need to create two new files: A startup script and an X session file.

To create the session shell script, open up your favourite text editor (eg gedit or kwrite) as Root and create a new script named startberyl.sh:

```

 gksudo gedit /usr/bin/startberyl.sh

```

```

 kdesu kwrite /usr/bin/startberyl.sh

```

You can also save it to /usr/local/bin or ~/bin, changing the instructions below to suit.

Note: In Gnome it is handy to set up an Application Menu entry for Gedit as Root using System > Preferences > Menu Layout, using the command gksu "gedit %U", and Nautilus as Root using gksu nautilus.

Depending on your configuration, use one of the following scripts:

GNOME

```

 #!/bin/sh
 beryl-manager
 sleep 4
 exec gnome-session

```
 

KDE

```

 #!/bin/sh
 export KDEWM="/usr/bin/beryl-manager"
 exec startkde

```
 

XFCE

```

 #!/bin/sh
 beryl-manager
 sleep 4
 exec xfce4-session

```
 

Alternatively, the last line can read

```

exec dbus-launch --exit-with-session gnome-session

```

for Gnome, and for KDE substituting gnome-session with startkde

Now you need to make the script executable; this can be done in Nautilus or Konqueror (running as Root) by right-clicking the file and choosing Properties, or in the terminal:

```

sudo chmod a+x /usr/bin/startberyl.sh

```


To create the session, create the file /usr/share/xsessions/Beryl.desktop, and give it the following contents in a text editor (again, as root or using gksudo/kdesu):

```

[Desktop Entry]
Encoding=UTF-8
Name=Beryl
Exec=/usr/bin/startberyl.sh
Icon=
Type=Application

```

Now when GDM or KDM starts, you should have a session called Beryl available for selection; if you log into this session, Beryl will run (via the startberyl.sh script) and load GNOME or KDE for you. Logging into your normal session will give you a standard, un-accelerated desktop for troubleshooting or running programs which don't play nicely with AIGLX.

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

So all of those directions are from the configuration part of the Beryl wiki. It worked for me and took about 5 minutes to follow the directions and be spinning my cube.

Beryl forums area good place to ask questions if this doesn't work for you.

---

### Post by crimesaucer on 2007-03-14
Also remember that after doing all of this, you still log in to your usual desktop environment.

When staring up, I log in as XFCE like I normally do, and then I am automatically using the Beryl Window Manager instead of xfwm4 because of those scripts. Then, if I need to use the xfwm4, I can select it in the Beryl Manager-->--Select Window Manager.

---

### Post by Mohammad_Khalid_Hussain on 2007-03-17
I have an Nvidia 5500 FX and used instructions from the Beryl Wiki to install Beryl on my PC.
Here were the results:

1.Using Nvidia: All was fine and fast but after like 10 minutes of using the PC, some windows would have like this yellow overlay and some would just get stuck and then the whole PC would hang.

2. Using AIglx: This one wasn't very pretty either and had a similar effect as above except that it was able to work properly for a longer period before going wacko.

3.Using Xgl: So far the best experience I've had. Everything works though startup takes a little longer but it doesn't bother me. I've had slight problems but I'm easily able to restart Beryl, the system doesn't hang whatsoever.

I used Xgl on my Acer Ferrari 4003 and it worked great. I decided to do the same to my PC, but before that i tried the two other ways, and Xgl turned out to be the best once again.

---

### Post by mfolnovic on 2007-06-09
I had the same problem yesterday, then I did something in /etc/X11/xorg.conf, try putting this in the xorg.conf:
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
and it worked :D

Hope I helped.

btw. sorry about my english :P

---

### Post by Madrigal77 on 2007-08-16
I'm having the same problem.Here's what I get in terminal:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by link48010 on 2007-08-16
I have a slight issue. I installed Beryl and all the effects work fine, but now my screen resolution won't change from 800 by 600 with a 50 hz refresh rate. It is far to small to work on very well. Is there any way to "force change" the resolution. BTW I'm using the Nvidia glx drivers with a Geforce FX 5500. Everything else works great.:confused:Got any thoughts. I'm new to Linux to not really intense commands please. A friend installed Beryl for me.

---

### Post by bravekorea on 2007-08-17
Sorry im new Ubuntu user. Jz start today. Starting my 3D Cube desktop work properly... but duno why after restart it wont work again. May I know what is happening?

---

