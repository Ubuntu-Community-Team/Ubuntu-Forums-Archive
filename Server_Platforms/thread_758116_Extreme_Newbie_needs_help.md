---
title: "Extreme Newbie needs help"
date: 2008-04-17
forum: Server Platforms
---

### Post by mashtdi on 2008-04-17
Okay guys.  I just loaded gutsy server.  Me being so green to this, I didnt understand that it  is totaly command line... I have no clue of any commands.  Is there a way to get a GUI on this thing untill I putz around enough to learn some commands....  Perhaps someone has a Ubuntu server for dummies doc's out there?

---

### Post by wormser on 2008-04-17
You can install a desktop but I recommend you don't.  It will force you to learn the command line faster.  I recommend setting up ssh on the server and remote in.  This way you can have tutorials open in Firefox with the shell on the same screen.  Install Webmin to have graphical control via Firefox incase you get stuck.

```
sudo apt-get install openssh-server
```Then you can ssh in from another computer.
```
ssh username@serverIP
```Search the net and the forum for a HowTo on whatever you want to do.

---

