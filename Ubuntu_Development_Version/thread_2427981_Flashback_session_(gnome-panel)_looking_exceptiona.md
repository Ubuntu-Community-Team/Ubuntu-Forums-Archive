---
title: "Flashback session (gnome-panel) looking exceptionally good."
date: 2019-09-28
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2019-09-28
I haven't tried it since Bionic and I must say it looks really good. I think the issues with Nautilus have been fixed. The only thing I noticed was that the "Main Menu" applet (once added to the panel) looks a bit small compared to the other applets but that's really nit picking.

I need to see if battery/charge "time" is displayed properly in a default session when I do the next fresh install because I didn't notice it wasn't displayed until I'd switched to gnome-panel. Again a very minor issue because "time to charge" and "time remaining" is a poor estimate anyway because it varies so greatly depending on load.

---

### Post by P-I H on 2019-09-28
This is a screenshot of a fully updated Eoan, with "Dash to panel" on an Asus X202E.
Display 11.6" 16:9 HD (1366*768) LED.
The estimated battery time is very optimistic.

Edit: The battery estimate is quite OK. Just before the picture was taken the battery estimate was 9 hours.

---

### Post by KBD47 on 2019-09-28
Just curious, how much ram are you using with Classic compared to regular Gnome?

---

### Post by cruzer001 on 2019-09-28
I have a gnome session installed
[https://packages.ubuntu.com/bionic/gnome](https://packages.ubuntu.com/bionic/gnome)
that is now fully loaded with everything I wanted and upon startup shows:
```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:          7927        1580        5459          88         886        6017
Swap:         2047           0        2047

```

---

### Post by kansasnoob on 2019-09-28
Battery time remaining/time to charge is working perfectly today. Maybe I just needed a reboot?

---

### Post by kansasnoob on 2019-09-28
> **P-I H said:**
> This is a screenshot of a fully updated Eoan, with "Dash to panel" on an Asus X202E.
Display 11.6" 16:9 HD (1366*768) LED.
The estimated battery time is very optimistic.

Edit: The battery estimate is quite OK. Just before the picture was taken the battery estimate was 9 hours.

Yes, I just meant the word "estimate" should be taken as exactly that - an estimate! Like if the screensaver has been running and I then "wake it up" the initial estimate will look quite impressive but if I wait just a few minutes for that to "refresh" it will drop dramatically. I just added time and percentage because I'm testing a new battery. Usually just the "widget/icon" will suffice.

---

### Post by Hreinsi on 2019-10-01
Gnome session

```
              total        used        free      shared  buff/cache   available
Mem:           7961        1326        5556          85        1078        6300
Swap:          1907           0        1907
```

---

### Post by KBD47 on 2019-10-01
That's not bad memory use, though I thought it might be a bit less in flashback. I usually check from a fresh boot, launch neofetch in terminal to get a reading with nothing else open on the desktop. If a browser is open it will skew your result badly.

---

### Post by KBD47 on 2019-10-04
I'm using Ubuntu 18.04 with Plex server. Decided I try Flashback to see if it would save on ram use. Ubuntu default is about 1200 mb ram at boot launching neofetch. With Flashback it is 652 mb ram at boot launching neofetch to get the number. So definitely a ram saving. Not sure if compositor can be turned off to save even more ram on Fallback, but that's pretty good.

---

### Post by Claus7 on 2019-10-08
Hello,

I recently upgraded from 19.04 to 19.10 beta. Some comments to your points.

> **kansasnoob said:**
> I haven't tried it since Bionic and I must say it looks really good. I think the issues with Nautilus have been fixed.  

I saw one thread of yours about opening File System from Places. I cannot see that fixed in Eoan beta. Is it working in your installation?
Under the same context: do you have Desktop icons with 19.10 and nautilus? 

> **kansasnoob said:**
> 
The only thing I noticed was that the "Main Menu" applet (once added to the panel) looks a bit small compared to the other applets but that's really nit picking. ...

I have problems switching from one DE to the other messing the icons completely. I have to restart in order to see proper flashback gnome panel compiz icons as they are supposed to be.

Regards!

---

### Post by kansasnoob on 2019-10-10
> **Claus7 said:**
> Hello,

I recently upgraded from 19.04 to 19.10 beta. Some comments to your points.

 

I saw one thread of yours about opening File System from Places. I cannot see that fixed in Eoan beta. Is it working in your installation?
Under the same context: do you have Desktop icons with 19.10 and nautilus? 



I have problems switching from one DE to the other messing the icons completely. I have to restart in order to see proper flashback gnome panel compiz icons as they are supposed to be.

Regards!

Yep, upon closer look the places menu > Computer button is kind of useless:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1743686](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1743686)

As I said in that bug report I think the most sensible "fix" is to remove the Computer button altogether because it's just not needed. Just go Home > Other locations .............

I don't think the flashback team provides any support at all for Compiz?

---

### Post by kansasnoob on 2019-10-10
Oh, and NO on desktop icons. It seems like some things changed in GNOME itself making that not possible, or at least i can't find a path in dconf at all. Also right click on desktop does nothing which is not a big deal I guess.

---

### Post by deadflowr on 2019-10-10
Some references on Desktop Icons and nautilus:
[https://discourse.ubuntu.com/t/files-nautilus-v3-28-will-lose-the-desktop-icons-capability/3115/12]("https://discourse.ubuntu.com/t/files-nautilus-v3-28-will-lose-the-desktop-icons-capability/3115/12")
[https://discourse.ubuntu.com/t/no-desktop-icons-already-arrived-in-19-04/9295]("https://discourse.ubuntu.com/t/no-desktop-icons-already-arrived-in-19-04/9295")
Unity and budgie run the same problem as flashback.
Not sure about budgie, but unity just decided to have nemo handle the desktop and use nautilus solely as the Files program.

---

### Post by Claus7 on 2019-10-10
Hello,

thank you for your responses, just to add a couple of comments/ideas where I can.
 
Today with the latest updates in gnome shell it seems that Gnome Classic got rid of the login loop and switching between that and flashback things seem to be ok.

> **KBD47 said:**
> That's not bad memory use, though I thought it might be a bit less in flashback. I usually check from a fresh boot, launch neofetch in terminal to get a reading with nothing else open on the desktop. If a browser is open it will skew your result badly.

my results thus far are (gnome panel flashback):
```
free -m
              total        used        free      shared  buff/cache   available
Mem:           7880         594        5841          90        1443        6929
Swap:          2047           0        2047
```

from system monitor I get ~1GiB, whereas for classic ~1.2Gib. With Disco it was 1.1Gib for flashback, so there is an improvement.

> **kansasnoob said:**
> Yep, upon closer look the places menu > Computer button is kind of useless:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1743686](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1743686)

As I said in that bug report I think the most sensible "fix" is to remove the Computer button altogether because it's just not needed. Just go Home > Other locations .............

I don't think the flashback team provides any support at all for Compiz?

I do not know, yet the Developers themselves could shed some light:
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
I have to admit that I was not using that way to access Computer, yet I checked it while you mentioned about some bugs you had come accross.

> **kansasnoob said:**
> Oh, and NO on desktop icons. It seems like some things changed in GNOME itself making that not possible, or at least i can't find a path in dconf at all. Also right click on desktop does nothing which is not a big deal I guess.

For Desktop icons under dconf I get the following, among others, when I type 'desktop':
org.gnome.desktop.background show-desktop-icons true
 
yet it does not seem to affect anything (true or false). I have exactly the same behavior meaning no Desktop icons and no right click on Desktop.

> **deadflowr said:**
> Some references on Desktop Icons and nautilus:
[https://discourse.ubuntu.com/t/files-nautilus-v3-28-will-lose-the-desktop-icons-capability/3115/12]("https://discourse.ubuntu.com/t/files-nautilus-v3-28-will-lose-the-desktop-icons-capability/3115/12")
[https://discourse.ubuntu.com/t/no-desktop-icons-already-arrived-in-19-04/9295]("https://discourse.ubuntu.com/t/no-desktop-icons-already-arrived-in-19-04/9295")
Unity and budgie run the same problem as flashback.
Not sure about budgie, but unity just decided to have nemo handle the desktop and use nautilus solely as the Files program.

I thought that there might be something different with 19.10 since from the response I got back in 19.04 and the following link:
[https://gitlab.gnome.org/GNOME/gnome-flashback/issues/7](https://gitlab.gnome.org/GNOME/gnome-flashback/issues/7)
it seemed that sooner or later flashback might solve the issue on its own. I asked, since I had some minor issues during the upgrade and I though that this might have affected that behavior.

Concerning battery I have to say that it lasts much less than it used to and the percentage remaining seems to be out of regular order at the time being (it shows less than it used to and it lasts also less). Yet, there are more restarts at that time because of the upgrades so it needs time so as for regular use to take place and for safe comments on that matter.

My most serious problem with the upgrade is the touchpad. I was using fusuma and it seems that every time I do the upgrades touchpad is not working as it should and more restarts are required. I'm waiting for the final release so as to have a say on that.

Regards!

---

