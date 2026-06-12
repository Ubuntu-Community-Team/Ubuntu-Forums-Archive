---
title: "Centrally authenticated network"
date: 2008-05-06
forum: Server Platforms
---

### Post by darkadept on 2008-05-06
What technologies work well together for a centrally authenticated network?

I want to set up a small network that allows users to be centrally authenticated and store files on the server. I want them to be able to log in on any workstation and still have access to their profile. I also want the laptop users to be able to log in when they are on-site but still be able to use their "offline" profile when they leave the network. Mostly I'd use linunx desktops but it would be nice to be able to have a windows client connect as well, although that is not a requirement.

I've played a bit with LDAP, Samba, NFS, NIS, etc but have never been able get this scenario working properly.

I would like to get this working using standard open-source Ubuntu server packages with out having to compile a lot of extra packages from source with special customizations.

I have done this sort of set up on Windows with active directory and roaming-profiles but don't want to use windows servers anymore.

I'm not afraid of the command line and don't really need a gui interface like active directory although a web interface for setting up users would be a nice feature.

Any help or examples of what server technologies you use or how to's would be greatly appreciated.

Thanks

---

### Post by rickyjones on 2008-05-06
> **darkadept said:**
> What technologies work well together for a centrally authenticated network?

I want to set up a small network that allows users to be centrally authenticated and store files on the server. I want them to be able to log in on any workstation and still have access to their profile. I also want the laptop users to be able to log in when they are on-site but still be able to use their "offline" profile when they leave the network. Mostly I'd use linunx desktops but it would be nice to be able to have a windows client connect as well, although that is not a requirement.

I've played a bit with LDAP, Samba, NFS, NIS, etc but have never been able get this scenario working properly.

I would like to get this working using standard open-source Ubuntu server packages with out having to compile a lot of extra packages from source with special customizations.

I have done this sort of set up on Windows with active directory and roaming-profiles but don't want to use windows servers anymore.

I'm not afraid of the command line and don't really need a gui interface like active directory although a web interface for setting up users would be a nice feature.

Any help or examples of what server technologies you use or how to's would be greatly appreciated.

Thanks

I highly recommend my guide. I'm currently working on the next version (still based on Server 7.10) and it is slowly becoming a much more mature product. It sounds like it could work in the environment that you are looking at.

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Sincerely,
Richard

---

### Post by darkadept on 2008-05-06
Thanks!

Yeah I have actually done a setup that is pretty much the same as your guide before but I want to work on streamlining the linux client side of it. Especially in regards to laptops. I've been reading the pages on your post but i'm only up to page 23 of 63. Since I played around with this a year or so ago things have changed a bit. I've already picked up some good tidbits from your guide and from the comments!

One thing I haven't seen mentioned in your post (at least not up to page 23 :) ) is dynamic dhcp + bind. I managed to get this working on my ubuntu server at home. The dhcp serves out ip's to clients and then updates the dns server with their hostname. This means you don't have to worry syncing up /etc/hosts files all over the place. :)

I'll have to get back into setting up a good ldap server again once I finish my large Qt project I'm working on.

Thanks for the reply! At least it shows me I'm on the right path  using the right technologies!

-mike

---

