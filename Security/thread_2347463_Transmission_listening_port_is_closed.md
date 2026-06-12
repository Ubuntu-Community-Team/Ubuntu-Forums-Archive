---
title: "Transmission listening port is closed"
date: 2016-12-25
forum: Security
---

### Post by garvind25 on 2016-12-25
Hi,

  I am trying to download torrent file via transmission. I speed is very slow. I checked the status of listening port 51413 at Edit --> Preferences --> Network. It is showing 'Port Closed'. I opened the port with ```
sudo ufw allow in 51413/tcp
```. On checking ufw status via ```
sudo ufw status verbose
``` I got the following output :

```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
64000                      DENY IN     Anywhere                  
64000/tcp                  DENY IN     Anywhere                  
51413/tcp                  ALLOW IN    Anywhere                  
64000 (v6)                 DENY IN     Anywhere (v6)             
64000/tcp (v6)             DENY IN     Anywhere (v6)             
51413/tcp (v6)             ALLOW IN    Anywhere (v6) 
```

So, basically 51413 is open. So why is transmission showing it as closed (and maybe thereby the downloading speed is slow).


Thanks,

Arvind Gupta

---

### Post by ian-weisser on 2016-12-25
Is the port open in your upstream router?
Is the port blocked by your ISP?

---

### Post by papibe on 2016-12-26
> **ian-weisser said:**
> Is the port open in your upstream router?
+1

The purpose of port 51413 is so that other peers can connect to you. This is the 'sharing' part of the bittorrent protocol. In other words, it is for requests from 'the Internet' to your computer.

Unless you are running a VPS on the real Internet, you need to forward the port from your router to your machine.

Note that this won't stop you from downloading. You can still download without forwarding the port. You just won't be sharing.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sudodus on 2016-12-26
I am trying to use torrents for my own software, and I am confused. I don't think I understand correctly, what happened yesterday:

Transmission in Lubuntu 16.04.1 LTS (persistent live) was reporting, that it was uploading and later that it had uploaded (and how much). Would that be after a request via the 'listening' port, which is reported as closed, when tested?

**Edit - Preferences - tab:Network - button:'Test Port'**

Either this is a bug, or I don't understand, or both :-P

---

### Post by ian-weisser on 2016-12-26
A very good answer to this very question is at [http://askubuntu.com/questions/405487/transmission-says-port-is-closed-but-seeding-is-happening](http://askubuntu.com/questions/405487/transmission-says-port-is-closed-but-seeding-is-happening)

The short version of the answer is: Transmission does more than just listen. It goes out and seeks, too. If the listening port is closed, then all your activity is from going out and seeking. This means your torrents may download (and uploads) bit slower than if both methods were active.

---

### Post by sudodus on 2016-12-26
Thanks *ian-weisser*, now I am starting to understand what is happening:-)

After reading

> If the torrent has few peers then it is likely that with active mode you would get much better speed.

I realize that I would be better off with an open port so I opened a port to the computer, that is a temporary(?) torrent server.

---

### Post by DuckHook on 2016-12-26
@sudodus

Does your router have UPnP enabled? My understanding may be wrong, but I've read that Transmission makes use of this service to automatically open (and forward) the listening port (and auto-closes it when not in use). Some people have security concerns about UPnP, so caution is in order. I've not heard anything about holes in Transmission's implementation of UPnP, but must admit to not having delved into it much either.

*EDIT*

Just read ian-weisser's link which discusses exactly the UPnP settings I alluded to. Apologies for redundancy.

---

