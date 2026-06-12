---
title: "Gnome-shell"
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cecilpierce on 2012-09-28
HELP!
When I logout of ubuntu (unity) and try to login to gnome (shell) it wont select it and gnome classic does not highlight sometimes either ???
I think its been like this since 3.6.

Thanks for any info...):P

---

### Post by dino99 on 2012-09-28
are both gdm & lightdm installed ? No problem here with lightdm  active for logging.

---

### Post by mc4man on 2012-09-28
There is a current issue with the unity greeter that makes clicking on the top or top 2 choices not possible.
see post 12 for tab trick highlighting

---

### Post by cecilpierce on 2012-09-28
@dino99
Yes both are installed, should I remove gdm ?

@mc4man
I tried tab and it highlighted gnome and logged in but was very slow and could not get firefox to run, but when I tried to start it again it said it was already running, NOT!

---

### Post by mc4man on 2012-09-28
> **cecilpierce said:**
> 

@mc4man
I tried tab and it highlighted gnome and logged in but was very slow and could not get firefox to run, but when I tried to start it again it said it was already running, NOT!
Probably not related to the greeter

There is a current issue I see with FF, have for quite some time. Not sure what brings it on but what happens is when the FF window is closed the firefox process is still running. In that case you have to stop/kill the process before FF can be opened again.

Happens here at least once a day.

---

### Post by Harry33 on 2012-09-28
> **cecilpierce said:**
> @dino99
Yes both are installed, should I remove gdm ?

@mc4man
I tried tab and it highlighted gnome and logged in but was very slow and could not get firefox to run, but when I tried to start it again it said it was already running, NOT!

You cannot remove GDM without removing Gnome-shell at the same time.
Gnome-shell depends on GDM.

---

### Post by cecilpierce on 2012-09-28
What a mess, thought everything was back to normal, logged out, chose gnome, tty8 popped up with a dead window "running in low graphics mode", logged in tty1 and typed startx, now im in tty9 with gnome-shell...and slow as dirt.

---

### Post by Frogs Hair on 2012-09-28
Thank you ! I finally logged into the shell using tab.

---

### Post by SheamusPatt on 2012-09-29
The <TAB> trick didn't work for me (just upgraded, so running Beta 2 code). However, this did:

    [FONT=Courier New]sudo dpkg-reconfigure lightdm

[FONT=Arial]and then choose gdm instead of lightdm. After that you can reboot into gdm and change your session - gdm doesn't have this rather suspicious bug in lightdm (are they trying to coerce people to use Unity)? Sorry, but Unity has not worked well for me, and I watch too many conspiracy shows :P

[/FONT][/FONT]

---

### Post by kurt18947 on 2012-09-29
> **SheamusPatt said:**
> The <TAB> trick didn't work for me (just upgraded, so running Beta 2 code). However, this did:

    [FONT=Courier New]sudo dpkg-reconfigure lightdm

[FONT=Arial]and then choose gdm instead of lightdm. After that you can reboot into gdm and change your session - gdm doesn't have this rather suspicious bug in lightdm (are they trying to coerce people to use Unity)? Sorry, but Unity has not worked well for me, and I watch too many conspiracy shows :P

[/FONT][/FONT]

Same problem.  First two choices in lightdm were not selectable.  gdm works fine, it seems.

---

### Post by Frogs Hair on 2012-09-29
Just received Light GDM updates moments ago , so I will test it out soon.

---

### Post by Bazon on 2012-09-29
If you try the tab trick, you really have to look very very precisly to your monitor: hitting tab will only make the border of the button a bit brighter, nothing else! 
I recommend hitting tab and then enter and so on to see the movement of the selection at all....

---

### Post by cecilpierce on 2012-10-01
Firefox won't start from icon but starts in a terminal with error:

(firefox:4361): WARNING **: Failed to open webapp application path dir /usr/local/share/unity-webapps/userscripts: Error opening directory '/usr/local/share/unity-webapps/userscripts': No such file or directory

Checked that location and it is there ???

---

### Post by Harry33 on 2012-10-02
> **cecilpierce said:**
> Firefox won't start from icon but starts in a terminal with error:

(firefox:4361): WARNING **: Failed to open webapp application path dir /usr/local/share/unity-webapps/userscripts: Error opening directory '/usr/local/share/unity-webapps/userscripts': No such file or directory

Checked that location and it is there ???

Is this only with the Gnome-shell DE?
How about Gnome Classic DE?

---

### Post by mc4man on 2012-10-02
> **Harry33 said:**
> Is this only with the Gnome-shell DE?
How about Gnome Classic DE?
I would guess that if the "Unity Websites integration" ext. is enabled that those WARNINGs would happen. Don't mean much.
(it would seem FF/ext goes thru a list of possible locations, each fail to find produces a WARNING. They stop if '/userscripts' is found or when all the locations are checked.
Why it doesn't start at the known default location is the only curious thing. ( /usr/share/unity-webapps/userscripts/

---

### Post by serdotlinecho on 2012-10-02
After doing apt-get update and apt-get dist-upgrade today, the lightdm bug has been fixed. :)

---

### Post by cecilpierce on 2012-10-02
> **Harry33 said:**
> Is this only with the Gnome-shell DE?
How about Gnome Classic DE?

Same thing in Gnome Classic, only runs in a terminal and no min, max or close icons in terminal, have to either type exit or right mouse button and select close.
And... it takes forever to logout, about a minute...:mad:

---

### Post by cecilpierce on 2012-10-02
> **serdotlinecho said:**
> After doing apt-get update and apt-get dist-upgrade today, the lightdm bug has been fixed. :)

Yea I noticed that, I hated gdm logout screen -:p

---

