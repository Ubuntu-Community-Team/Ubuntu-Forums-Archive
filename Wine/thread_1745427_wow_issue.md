---
title: "wow issue"
date: 2011-05-01
forum: Wine
---

### Post by antiblizzard on 2011-05-01
I get the launcher to launch right I cannot however see the news and when it tries to swap to the game client the wine program is running I get sound and see the hand for the ingame cursor but I get no video for the game. Any helps with this problem please post any ideas thanks. Also I checked my graphics drivers and they are working correctly.

---

### Post by MollyWop on 2011-05-01
Have you checked if it is compatible with your version at [http://winehq.org](http://winehq.org)

---

### Post by antiblizzard on 2011-05-01
it seems to be compadible I am thinking it has something to do with the game overlay after you click play on the launcher.

---

### Post by MollyWop on 2011-05-01
> **antiblizzard said:**
> it seems to be compadible I am thinking it has something to do with the game overlay after you click play on the launcher. I don't know, I don't play wow.. Try looking through the appDB and see if you can find a bug fix.

---

### Post by themainliner on 2011-05-01
This is a Unity issue. WoW runs absolutely fine in Wine, with Gnome 2.x.

---

### Post by antiblizzard on 2011-05-01
I am new to using linux and wine what is a unity issue ?

---

### Post by Tweak42 on 2011-05-01
> **antiblizzard said:**
> I am new to using linux and wine what is a unity issue ?

The new default desktop environment for 11.04 is called "Unity".  Unlike Gnome 2.x, Unity uses a large launch bar along the entire left side of the screen.  Previous releases used Gnome 2.x environment, and is still available in 11.04, but you need to select it at the login screen.


Have you tried skipping using the launcher and launch the game at the command line?  Are you using opengl or d3d?

---

### Post by antiblizzard on 2011-05-01
Yes I have and it gives the same problem I can see the hand for in game cursor and hear the music but I cannot see the game image.

---

### Post by Dimarchi on 2011-05-02
More info needed - namely, your hardware setup. Tweak42's response has enough info about Tweak's hardware to draw some conclusions in case it is needed. I suggest you provide at least that much.

For what it is worth, WoW under 11.04 works for me. Copied from Windows 7 side, WTF folder trashed, followed some age old guide to download WoW svg icon and made a .desktop file (with appropriate corrections) with a pointer to the (Wow) Launcher, and finally stickied it to the (Unity) Launcher.

At startup it does the annoying Unity thing of absorbing the window bar to the menu bar, but it can be broken out of by using the maximize button (I'm playing in windowed mode). Default settings in everything except volume, windowed mode, and resolution (1650 x 1080). Wine has default settings, too.

Intel Core 2 Quad Q9650, 4 GB of DDR3 RAM, ASUS 6870 with 1 GB of GDDR5 RAM,  2 X 640 GB Samsung hard drive (one for Windows 7 Pro, one for Ubuntu), Benq 24" LCD at 1920x1200. ATI's proprietary driver from the Additional Drivers control panel installed.

---

