---
title: "Added new HDD to server; Can't access through NFS"
date: 2009-05-13
forum: Server Platforms
---

### Post by OverlordManny on 2009-05-13
All computers are running Ubuntu in this scenario. The server and desktop are running 8.10 desktop. Laptop is running 9.04 desktop.

    I have a small file server that I use to stream movies to my modded xbox, among other things. Well I was running out of space so I added a new hard drive and modified my fstab to automount it. All works fine on the server; (ie I can access the new drive, r & w to it.) I can get on my xbox and access the new mount and stream from it. BUT I cannot access this new HDD from my Desktop or laptop. I can however still access the rest of the server (the older drive). When I try to manual mount the new drive through NFS onto my laptop I get.

```
damion@damion-laptop:~$ sudo mount -t nfs home-server:/home/home-server/movies ~/new
mount.nfs: access denied by server while mounting home-server:/home/home-server/movies

```

    The permissions on the files and folder are set to allow anyone access to them. I don't understand why the server is not allowing access to this mount while it allows access to another mount.

    Also... Why does this not work?:

/home/home-server/shared_files    <--- NFS mount on server to client

/home/home-server/shared_files/movies    <--- second HDD mounted on server

    Seems like if I mounted the NFS to my client, I should have access to the second HDD on the server since it is mounted under the NFS mount. Or is this just not working because I'm unable to mount the server's 2nd HDD through NFS period?

    Lol that's as clear as mud right? I don't know how to clarify it more, sorry.

---

### Post by OverlordManny on 2009-05-13
Gosh, I'm a pinhead. I didn't add the path to /etc/exports on my server. Everything's great now.

---

