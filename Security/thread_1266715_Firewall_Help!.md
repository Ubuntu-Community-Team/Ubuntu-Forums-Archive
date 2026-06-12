---
title: "Firewall?? Help?!"
date: 2009-09-14
forum: Security
---

### Post by kyle787 on 2009-09-14
[SIZE=2]Hi I'm really new to Ubuntu and so far I really like it. Unfortunately I started to aimlessly mess around with iptables and ended up blocking all my connections, so I did the only thing I could think of and that was to disable iptables. So I didn't want to be insecure so I downloaded Firestarter. Tonight I was downloading a torrent and firestarter came up with something telling my how a "hit was stopped". This began to get me to wonder if I really was secure, so I checked the Events in Firestarter and it had all these things. I check /log/var/messages and /log/var/auth.log to try to see if I was being hacked, I just googled it to see what other Ubuntu users did, and well nothing in those two files made sense. So I need your help... 1) Is my computer safe 2) Do I need to reenable iptables 3) Should I be worrier about the hits. I am computer savvy but not so much in "computer language" so you will need to explain this as detailed as you can tell me exactly what I need to do step-by-step. If I need to reenable iptables I'm not sure which ports I need to open, last I know i had http, https, and ssh? ports open.
Thanks in advance, and sorry for being such a noob...[/SIZE]

---

### Post by abaden on 2009-09-14
IPTables is still running, because Firestarter is simply a frontend for configuring IPTables. It should be noted though that [gufw]("http://gufw.tuxfamily.org/index.html") is the new preferred firewall for Ubuntu, since Firestarter is no longer maintained. 

If you do some googling you can find tons of different commands for ufw, and of course gufw gives you the full graphical interface. 

If you were torrenting firestarter probably stopped somebody from connecting to your torrent. Are you sure anybody was able to connect? Also, there should be some firestarter logs somewhere (sorry I can't be more specific, I'm pretty unfamiliar with firestarter) that show what was denied and why. 

In "/var/log/auth.log" you will be able to see all the open and closed sessions on your machine. If you see something that looks suspicious, post it here and we'll let you know if you need to be concerned. You should just see a bunch of sessions for the root user and your own user. 

Based on your description that's about as much as I can provide. If you can give us some more information, we'll probably be able to provide a better guess, but it's almost impossible to know for sure unless you're sitting at a terminal (ok, or a desktop).


Alex

---

### Post by TuckLive on 2009-09-15
Hello,

As posted earlier ufw is now the preferred way to manage IPTables.  To put your mind at ease you could run

```
sudo ufw default deny
sudo ufw logging on
sudo ufw enable
```

Then open the ports you require open as needed.  It's always good to have a "deny by default" policy.

[[COLOR="Blue"]https://help.ubuntu.com/community/UFW[/COLOR]]("https://help.ubuntu.com/community/UFW")

---

### Post by lovinglinux on 2009-09-15
Read the [COLOR="DarkRed"]**Security**[/COLOR] and the [COLOR="DarkRed"]**FAQ**[/COLOR] sections of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It answers all your questions. In fact, I recommend you read the entire guide, since it explains most things you need to know about torrents.

---

### Post by kyle787 on 2009-09-15
> **TuckLive said:**
> Hello,

As posted earlier ufw is now the preferred way to manage IPTables.  To put your mind at ease you could run

```
sudo ufw default deny
sudo ufw logging on
sudo ufw enable
```Then open the ports you require open as needed.  It's always good to have a "deny by default" policy.

[[COLOR=Blue]https://help.ubuntu.com/community/UFW[/COLOR]]("https://help.ubuntu.com/community/UFW")

Can you tell me or give me a list of ports? Because all I know is last time I closed all the ports and was unable to download stuff using the terminal when I had the deny by default policy.

---

### Post by cbugsubunt on 2009-09-15
thanks that was helpfull and for me.

---

### Post by TuckLive on 2009-09-15
With default deny you can download from webpages and the like.  P2P is a different beast and I recommend reading the link lovinglinux provided [[COLOR="Blue"]HERE[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1259923").

If you are running services on your computer that others need to access like http, https, or ssh then you'll need to open those ports for others to access.

---

### Post by sh4d0w808 on 2009-09-18
If U still want to play with iptables, I recommend to give a try to [IPTables Generator]("http://easyfwgen.morizot.net/gen/"). U just need to fill out asked fields.

---

