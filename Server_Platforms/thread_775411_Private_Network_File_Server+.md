---
title: "Private Network File Server+"
date: 2008-04-30
forum: Server Platforms
---

### Post by konradpiskorz on 2008-04-30
Hi everybody,

I just switched to lniux last week so I'm still fairly new to this but so far I am enjoying the freedom it allows immensely.

I have a spare old computer that I want to use as a network server to listen to music from or even watch movie on my laptop wirelessly from if thats even possible.

In the future I might want to add the ability to connect privately to stream music as well... Now this is in the possibly maybe in the future column but it would be nice to get some details on this as well.

What I do know is that I want
-Store Drives on server comp to hold music/movies/files available over the network.
-Be able to administer the server remotely (so I don't need to keep it connected to a monitor
-Keep the server as light as possible.  Ubuntu is a little well featured for it... or maybe not.  I really don't know.  It just doesnt need to do more than that!

I just have no idea where to start with this and any help would be appreciated.

Thank you!

---

### Post by hyper_ch on 2008-04-30
> **konradpiskorz said:**
> -Store Drives on server comp to hold music/movies/files available over the network.
with NSF/SSHFS you can simply mount partitions on a remote computer on your local linux computer... or use Samba if the local computer is running windows

> **konradpiskorz said:**
> -Be able to administer the server remotely (so I don't need to keep it connected to a monitor
Install openssh-server - that's all you need for remote administration

> **konradpiskorz said:**
> -Keep the server as light as possible.
Install a server version (I'd recommend Debian Etch Server)

And for music streaming, there are different options.

---

### Post by konradpiskorz on 2008-04-30
Thanks a lot! Thats a lot simpler than I thought it would be!

---

### Post by hyper_ch on 2008-05-01
it is not that difficult

[https://wiki.ubuntu.com](https://wiki.ubuntu.com) should have howtos for all of that.

---

