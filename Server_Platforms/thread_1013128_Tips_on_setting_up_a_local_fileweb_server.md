---
title: "Tips on setting up a local file/web server"
date: 2008-12-16
forum: Server Platforms
---

### Post by ingeva on 2008-12-16
First: I'm using Ubuntu 8.04.1 because I had trouble getting some "important" stuff working in 8.10.

I'm in the process of setting up a server for my internal network.
I have 2-3 computers and a printer on the network. One wireless connection.
The server will be connected via the wireless.

I've set up Apache and samba, and will probably also set up ssh, ftp and a mail server (send only, since I won't have inbound internet access).

I want a windows based version of the OS, because it makes it easier to make changes.
The trouble is that Apache or Samba don't connect until I log in, possibly because the wireless isn't connected yet.
I do not plan to log in on the computer. Just switch it on and let it run. There will normally not be a keyboard or display connected. However, if it's possible to do an automatic login, that might help.

Any tips to get me in the right direction?

Thanks!

---

### Post by CrucifiedEgo on 2008-12-16
You'll probably have to add something to /etc/rc.local.  Depending on how your network is configured something as simple as: 
```
dhclient wlan0
```
will probably work fine.  If not, login using one of the consoles (ctrl+alt+f1) and paste in the output of ifconfig and iwconfig for starters.

---

### Post by ingeva on 2008-12-17
> **CrucifiedEgo said:**
> You'll probably have to add something to /etc/rc.local.  Depending on how your network is configured something as simple as: 
```
dhclient wlan0
```will probably work fine.  If not, login using one of the consoles (ctrl+alt+f1) and paste in the output of ifconfig and iwconfig for starters.

Thanks, I'll try that but I think the best would be to not have to log in at all.
As far as I can understand this requires a user to be logged in, so either I must make sure that this happens before logging in, or it would be necessary to log in automatically.

I can do the setup work with a keyboard connected, but for "production" there shouldn't be one. The server will be located somewhere that's not easily accessible. It will have to be moved to set it up or do maintenance, so the more I can do remotely, the better.

I'm still fairly new to linux so I don't know how to set up the startup scripts -- or even where they are and what they do.

---

### Post by CrucifiedEgo on 2008-12-17
/etc/rc.local is the last script executed during boot -- so by putting the dhcp command there, you're going to be running it automatically.

---

### Post by ingeva on 2008-12-18
> **CrucifiedEgo said:**
> /etc/rc.local is the last script executed during boot -- so by putting the dhcp command there, you're going to be running it automatically.

Well -- after I did that it takes VERY long to get to the login page, and gnome-session-deamon has a problem because the wireless needs much longer to start.

So I don't think this was a good solution,
but there's an eth0 interface in the same computer. If I disabled that, would it start the wlan0 faster?

And if I could, how to do that?

---

