---
title: "Setting up home server with backup imaging for clients"
date: 2010-01-31
forum: Server Platforms
---

### Post by Tdonohue on 2010-01-31
I'm trying to setup a server at home, it has some practical implications, but largely it is just to take a stab at it ;)

But I need the help of someone with more experience than I in defining exactly what I'm looking to do.  

Here's what I have: 
old PC running Gutsy server connected to router.  Several laptops at home connected via wifi to router. All laptops running either Windows or Ubuntu.  

Here's what I'm looking for: 
The server centralizes file storage for all clients.  I would likely incorporate a RAID  and some synchronised imaging of the files.  I also want the server to create disk images of the clients hdd, regardless of client OS. There would also be some shares that would be publicly accessible (myself and friends accross the country would be able to access the same drive).  


So I was thinking something like what corporate environment would be nice, you log into a profile that exists on the server.  Like a dumb client...all data would be stored on the server.  But I'm thinking that's more like a network boot and wouldn't work via wifi (or would it?). Also that wouldn't lend itself well to laptops used on the road in areas without net access.

now I'm thinking each client would have its own locally installed OS, and they would just access networked shares.  I could store sensitive files on the shares, but that wouldn't provide complete backup solution for each client.

Without rambling on anymore, anyone care to throw out some ideas?  I'm really just looking to see if I can do what I want.  The focus is on centrallizing files, securley backing up data and client OS's and ability to restore said images quickly.

I appreciate your ideas

---

### Post by CharlesA on 2010-01-31
You can try using Clonezilla to create the images. Set the server up as samba/whatnever and go from there.

---

### Post by Tdonohue on 2010-01-31
> **CharlesA said:**
> You can try using Clonezilla to create the images. Set the server up as samba/whatnever and go from there.

I use Clonezilla as a live CD and I'm quite happy with it, but I'm not sure how I would use it on the server side to image a client HDD. Now that I think about it, I can't think of anyway to image a disk while its in use, so I don't know how I would accomplish what I want from the server side.

---

### Post by BkkBonanza on 2010-02-01
Network boot (home on server) is ok for local network, and wifi shouldn't be a problem but speed is going to prevent you from wanting to use that anywhere you don't have a fast network, ie. internet, remote access. You're probably best off to maintain independent booting as long as the client computers are capable. No problem with shares on server though and if you keep important data on the shares then that reduces the need for complex client backups. 

Clonezilla is good but I recall there is another package out there that has more complete management of images so that you can quickly snapshot/restore any client PC and keep tabs on the various machines. I just can't recall the name but will post back if I think of it.

---

