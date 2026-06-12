---
title: "Ubuntu home folders -&gt; NAS"
date: 2010-08-17
forum: Server Platforms
---

### Post by dreamie on 2010-08-17
Hi!

I want to set up a configuration similar to this [thread]("http://ubuntuforums.org/showthread.php?t=1551765")

But I want to go a step further. I am currently using my ubuntu-server as a file server. But now I want to add a NAS "server", which will take care of the file server part. 

The ubuntu server will serve as Web, SubVersion, VPN and portal server only. Would it be possible to link the home folders (both shared and user specific) to the NAS server? 

I mean if I access my home directory (through VPN or LAN) on the ubuntu server, I actually read/write from the NAS but I still connect through Ubuntu server? 

The idea is to:
1. Preserver network mappings from all clients to the ubuntu server home directories, that are already in place.
2. Authentication is made through the ubuntu server only

It's kinda like the NAS is behind the ubuntu and acts as a external harddrive (but with raid capabilities).

Thanks for any reply.

 / Peter

---

### Post by koenn on 2010-08-17
Assuming your NAS knows NFS : moutybn a volume from the NAS on your ubuntu server (eg on /home) -> whatever you put in home will end up on the NAS volume, but you can work with it as if it was on the server.

You may need to work out some permission and ownership stuff for this to work, and work securely.

---

### Post by dreamie on 2010-08-17
Hi, and thanks for your reply.

What would you recommend, doing this way or adding the NAS as a separate unit?

 Regards,
 Peter

---

### Post by koenn on 2010-08-17
what do you mean "as a separate unit" ?

---

### Post by dreamie on 2010-08-18
Well as a "server" which user log on to just as they do on the ubuntu server. This would mean I have 2 servers instead of 1.

---

### Post by koenn on 2010-08-18
yeah, I'd do it that way - I usually try to avoid unnecessary complexity

so unless there are compelling reasons to take a different approach, ...

---

### Post by dreamie on 2010-08-19
Ok, thanks.

---

