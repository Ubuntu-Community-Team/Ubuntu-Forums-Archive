---
title: "Help setting up 2 redundant servers."
date: 2009-08-23
forum: Server Platforms
---

### Post by munchi3s on 2009-08-23
Well here is what I want to happen, and I know its possible, but I need some help finding information about it. I am trying to set up 1 server as a primary DNS/Apache/FTP/DHCP/Squidcache/ server but because its going to be so invaluable to the network I wanted to set up a second piece of identical hardware that is redundant to the main server. I tried looking for HOWTOs online but I dident come up with much. I dont really want to do a ghost backup every week as that could not work out in my benefit. I know that having so many servers on a single machine is a bad idea and I will probably split it up some but I still want to figure out how to create a redundant piece of hardware that constantly refreshes itself with the primary server. This way if the server goes down I can just through the new server in and be back up and online in 30 - 60 minutes.
 
 If anyone can help I would appreciate it very much.

---

### Post by Adina on 2009-08-24
Ihave not tried this myself but maybe you find it helpful: [Linux-HA (high availability)]("http://en.wikipedia.org/wiki/Linux-HA")

---

### Post by fishy6969 on 2009-08-24
Virtualisation might be the way to go - [openvz]("https://wiki.ubuntu.com/OpenVZ") or [kvm]("https://help.ubuntu.com/community/KVM") would be suitable. You could then keep backup images of the main server (and you could also use it to 'break up' the multiple services you've got running on one machine)

---

### Post by windependence on 2009-08-24
If you're going to run two physical boxes, just rsync one to the other. This is old but still applies:

[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

-Tim

---

### Post by munchi3s on 2009-08-24
> **clarejoy said:**
> I think the best approach is one machine at  a time for one is best Why not you can enhance capacity of your server.

[website hosting]("http://www.sharphosts.com")

Well I'm only a student in high school although I'm a senior we have limited hardware in our lab.(I'm heading the server team.) Right now for use in my home network I'm using GX270 which works for now. Were getting some nicer servers donated to us in a few weeks, but I'm going to look up setting up virtual servers and I will also try rsync and mabey a combination of them both. Thanks everyone who has posted.

---

