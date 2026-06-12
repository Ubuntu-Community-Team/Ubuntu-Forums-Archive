---
title: "Help with server location in home"
date: 2008-07-30
forum: The Cafe
---

### Post by herbster on 2008-07-30
I have a box I use as a server and have a monitor for it, but I'm going to get remote (freenx/vnc) going so I'd like to put it in the basement or even another room on the same floor. However, I'd really like it if possible to keep the keyboard and mouse in my room, heck maybe even the monitor? I'm wondering if cables for these-- keyboard, mouse and monitor-- or even "extension" cables are available, I'm thinking perhaps in the range of ~15-30 feet? Or a more viable solution I'm unaware of, any help would be appreciated, thanks.

---

### Post by hessiess on 2008-07-30
carnt you use ssh/ remote desktop

---

### Post by herbster on 2008-07-30
Yes, I have that working, I'd simple like a physical means of controlling the box while it sits in the basement/another room on the floor :)

---

### Post by markp1989 on 2008-07-30
my torrent slave/nfs server is in a fitted wardrobe

runns with out a monitor, mouse or keyboard, everything done by ssh

is there any reason that you want to keep the monitor, keyboad, mouse pluged it?

---

### Post by herbster on 2008-07-30
Which torrent client do you use mark?

Now that I think of it, I don't have any reason but for the fact I could not get FreeNX to work properly (I'm going to give VNC a go). Via SSH, I couldn't get an X interface to use ktorrent, right--or could I? (I do use the built-in ktorrent web interface, but it doesn't provide enough options, it's just a simple one). I really like ktorrent but am more than willing to check out another option. My box is a myth/torrent/nfs server. Could you elaborate a bit on how you have yours set up? TIA :)

---

### Post by markp1989 on 2008-07-30
> **herbster said:**
> Which torrent client do you use mark?

Now that I think of it, I don't have any reason but for the fact I could not get FreeNX to work properly (I'm going to give VNC a go). Via SSH, I couldn't get an X interface to use ktorrent, right--or could I? (I do use the built-in ktorrent web interface, but it doesn't provide enough options, it's just a simple one). I really like ktorrent but am more than willing to check out another option. My box is a myth/torrent/nfs server. Could you elaborate a bit on how you have yours set up? TIA :)


I use ubuntu CLI install with torrentflux, nfs-common installed

i add torrents using the web interface

---

### Post by Lostincyberspace on 2008-07-30
> **herbster said:**
> Which torrent client do you use mark?

Now that I think of it, I don't have any reason but for the fact I could not get FreeNX to work properly (I'm going to give VNC a go). Via SSH, I couldn't get an X interface to use ktorrent, right--or could I? (I do use the built-in ktorrent web interface, but it doesn't provide enough options, it's just a simple one). I really like ktorrent but am more than willing to check out another option. My box is a myth/torrent/nfs server. Could you elaborate a bit on how you have yours set up? TIA :)
You could use deluge 0.6 (still in beta but nice and stable as of yet) It has a daemon and a fronted that you can access remotely.

---

### Post by tom66 on 2008-07-30
I would just telnet in through a local intranet. Easier.

---

### Post by herbster on 2008-07-30
Okay, I'm trying to install torrentflux now on the server (both my boxes run Arch). I'm getting an error, posted to the torrentflux forums [here](http://www.torrentflux.com/forum/index.php/topic,3800.0.html). Hopefully can get it to go and free up space in the room ;)

---

### Post by herbster on 2008-07-31
Well, I dunno if I'll wind up needing torrentflux (though I'll still get around to setting it up) as I just got VNC via SSH tunnel working perfectly. Tossing the server in the basement today :D Thanks to all for the help.

---

