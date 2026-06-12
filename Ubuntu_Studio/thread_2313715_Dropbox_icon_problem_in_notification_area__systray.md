---
title: "Dropbox icon problem in notification area / systray"
date: 2016-02-15
forum: Ubuntu Studio
---

### Post by Chris Bradley on 2016-02-15
Hello. A few days ago, the dropbox icon in the notification area of my Ubuntu Studio 14.04 (32 bit) turned into an X. Same with Studio 15.10 (32 bit.)

If I choose other themes it looks like a red "stop" sign, you know, a circle crossed out. Either way it looks like something that says "no access."

I used to click on it to access the dropbox prefs, but now no menu appears. I can't find access to the dropbox prefs menu anywhere else. Funny thing is, dropbox is actually working; things are getting synced. But, without its menu, several important configuration options don't seem possible, and you can't see what dropbox is doing.

Is anyone else seeing this? I found a workaround but it's nearly useless. Use the terminal:
```
sudo dropbox stop                             # if you've got it running this will switch it off
sudo dropbox start                            # starts it up with the correct icon
rm ~/.config/autostart/dropbox.desktop        # stops it from autostarting on future boots with the bad icon
```

Now, on each boot you have to start it yourself. But if you run it from the main applications menu you'll just get the "no access" icon. Instead, you have to use the terminal:
```
sudo dropbox start
```

It works: you get the correct icon and the menu etc. But like I said, it's pretty dumb having to go to the terminal and enter your password each time you boot. Without the sudo it'll skip the password requirement but you'll just get the "bad news" icon again.

(BTW during Ubuntu Studio installs I always tick the "encrypt my home folder" box. Is this related? And if so, how was it working fine until a few days back?)
(BTW the dropbox notification icon works fine in regular Ubuntu 15.10, 32 bit version)

What does all this mean?

---

### Post by Nosphky on 2016-02-15
Yes, I can confirm this.  I noticed it around the end of last week.  On UbuntuStudio 14.04.3 LTS.
  I should think it is a result of a kernel update from UbuntuStudio (I think there was one amongst last week's updates).  

I noticed that it had no effect on sync.  But I did drop a line to Dropbox support and got a reply saying that they would get in touch in a day or three.

The same thing happened around January 2015 and I had to live without access to the menu items behind the tray icon until one day Dropbox announced a new revision which restored everything.

I guess another revision will be forthcoming when enough people complain to Dropbox.

(My old laptop on Debian 8.3 is displaying the icon correctly - that's what made me think it must be down to some update from Ubuntu).

Your workaround is interesting.  I tried it and it works fine providing I do "sudo dropbox start" - then I get the correct icon.  If I just kill and restart using "$ dropbox start"  (ie not sudo) - then dropbox starts ok but with the 'no entry' icon.

---

### Post by Nosphky on 2016-02-18
Dropbox has made contact by email and I've supplied a screenshot.  Will update later if we get progress.

---

### Post by serfcx on 2016-02-23
> **Nosphky said:**
> Dropbox has made contact by email and I've supplied a screenshot.  Will update later if we get progress.
Any news on this as the same has happened to me on Linux Mint 17.3

---

### Post by Nosphky on 2016-02-23
After a few emails backwards and forwards with dropbox, someone at dropbox supplied me with the following link from others who had the same problem on xubuntu - following some recent ubuntu software updates :

[URL="http://askubuntu.com/questions/732967/dropbox-icon-is-not-working-xubuntu-14-04-lts-64/736205#736205"]http://askubuntu.com/questions/732967/dropbox-icon-is-not-working-xubuntu-14-04-lts-64/736205#736205
[/URL]

The suggested workaround :

$ dropbox stop && DBUS_SESSION_BUS_ADDRESS="" dropbox start

works for me and gives the correct icon in the panel from which I can access the functions with a right-click.
A further advantage is that the dropbox process still runs as my user name process rather than as a root
process (which happens if you use sudo to restart dropbox).

See the above link for further info.
hth

---

### Post by sethanath2 on 2016-02-23
Hi,

It works for me too, but once you reboot your computer, it would happen again.

---

### Post by Nosphky on 2016-02-23
Yes, to avoid a manual change each time you start up, you'll have to adopt one of the solutions given in the link in post #5 above.  

You could also just make a small script incorporating the  "$ dropbox stop && DBUS_SESSION_BUS_ADDRESS="" dropbox start" which you run after start up.

---

