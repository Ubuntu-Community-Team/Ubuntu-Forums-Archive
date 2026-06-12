---
title: "Where are the preferences in gedit?"
date: 2013-08-26
forum: Ubuntu Development Version
---

### Post by JRV on 2013-08-26
Gedit is missing the Edit=>Preferences menu item in Ubuntu 13.10 64 bit.
How do I turn the word wrap off/on?

[IMG]scc.net/~jrv/FTRANS/Screenshot-gedit.png[/IMG]

---

### Post by mc4man on 2013-08-26
Nothings changed here - it's in the app menu > edit > preferences.
Can also be accessed in dconf-editor (no longer default installed), org.gnome.gedit.preferences.editor wrap-mode

---

### Post by JRV on 2013-08-26
The menu > edit > preferences shows if you are using global menus.
If you are not using global menus it does not show.

---

### Post by mc4man on 2013-08-26
> **JRV said:**
> The menu > edit > preferences shows if you are using global menus.
If you are not using global menus it does not show.

Not really - 
If using gnome-shell then no 'global menus' but you have 'app menus' & it's in there
If using unity without global menus then it's in gedit as seen  in screen
If using gnome-flashback don't know, you should say so if using..

---

### Post by JRV on 2013-08-26
I am using Unity, Ubuntu 13.10, 64 bit.
Menu > Edit does not show preferences.

I tried to post an image but it's been years and I don't remember how.

---

### Post by vasa1 on 2013-08-27
> **JRV said:**
> I am using Unity, Ubuntu 13.10, 64 bit.
Menu > Edit does not show preferences.

[IMG]scc.net/usr/home/jrv/WWW/Screenshot-gedit.png[/IMG]

The requested URL /home/jrv/WWW/Screenshot-gedit.png was not found on this server.

Try imgur.com. That's pretty decent.

---

### Post by JRV on 2013-08-27
I am using Unity, Ubuntu 13.10, 64 bit.
Menu > Edit does not show preferences.

Global menus removed by:
```

sudo apt-get remove indicator-appmenu

```

[IMG]http://scc.net/~jrv/Screenshot-gedit.png[/IMG]

Ok I got it, how would i attach it as a thumbnail?

---

### Post by mc4man on 2013-08-27
> **JRV said:**
> I am using Unity, Ubuntu 13.10, 64 bit.
Menu > Edit does not show preferences.

Global menus removed by:
```

sudo apt-get remove indicator-appmenu

```


Well if you choose to remove that then yes, you will not get preferences for gedit & there will be other "app menus" missing here & there in an ubuntu (unity) session.
So in that case just use dconf-editor or re-install indicator-appmenu & adjust where app menus are on an individual app basis which will retain all app menu selections.

---

### Post by VinDSL on 2013-08-27
Sometimes a pic >= 1000 words...  :)

[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-27-aug-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-27-aug-2013-1.png")[/INDENT]

* Gnome-shell 3.9.90 

The gedit app prefs are now located in the app-indicator, not the gedit window.

---

### Post by VinDSL on 2013-08-27
BTW, one thing I might mention here...

I'm running GS Staging et al.  

The latest ricotz version of gedit didn't include the plugin component, which I cannot live without. :)

Soooo, I had to downgrade/pin gedit:

```
vindsl@Zuul:~$ apt-cache policy gedit
gedit:
  Installed: 3.8.3-0ubuntu3
  Candidate: 3.8.3-0ubuntu3
  Version table:
 *** 3.8.3-0ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ saucy/main i386 Packages
        100 /var/lib/dpkg/status
vindsl@Zuul:~$
```

Is this the version you're running?

---

### Post by JRV on 2013-08-27
> **VinDSL said:**
> 
Is this the version you're running?

Yes

---

### Post by VinDSL on 2013-08-28
In that case, I concur with mc4man.

You'll need to 'hack' your prefs using the dconf interface, as suggested in [Post #2]("http://ubuntuforums.org/showthread.php?t=2170457&p=12769702&viewfull=1#post12769702").  ;)

---

### Post by JRV on 2013-08-28
Thank you, thread marked solved.

---

### Post by mahiarmody on 2014-05-12
I ran into the same issue with Ubuntu 14.04 and after a bit of googling found the solution (It is suppose to work with Ubuntu 13.10 as well):

"If you've removed indicator-appmenu to remove global menus then:

Run the following command from any directory, (one long line):
gsettings set org.gnome.settings-daemon.plugins.xsettings overrides '@a{sv} {"Gtk/ShellShowsAppMenu": <int32 0>}'  

If you've edited gedit.desktop to add an env to keep menu's in it's window then remove the env, typically env UBUNTU_MENUPROXY=

As an aside: if one wanted the app menu present in a root nautilus browser then removing indicator-appmenu & running the above from a root prompt will achieve that."


The above information is more or less a direct quote from: [http://askubuntu.com/questions/364117/enable-line-numbers-in-gedit](http://askubuntu.com/questions/364117/enable-line-numbers-in-gedit)
Also see: [http://ubuntuforums.org/showthread.php?t=2173226&p=12821184&viewfull=1#post12821184](http://ubuntuforums.org/showthread.php?t=2173226&p=12821184&viewfull=1#post12821184)

This worked for me on Ubuntu 14.04, however, according to the website above, it also worked for people using Ubuntu 13.10. Furthermore, for me, the above-mentioned command also restored the missing "Help" menu in gedit.

I know that my reply comes rather late in the discussion, but I thought it might be helpful none-the-less.

---

### Post by oldos2er on 2014-05-12
Since the question was originally about 13.10, closed.

---

