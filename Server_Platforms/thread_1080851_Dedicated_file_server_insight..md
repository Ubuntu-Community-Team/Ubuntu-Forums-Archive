---
title: "Dedicated file server insight."
date: 2009-02-25
forum: Server Platforms
---

### Post by medicineman24 on 2009-02-25
I want to set up a dedicated server that I can access from school.

I need to be able to:
1) access/copy files (1-700mb) hosted on the server on/to a remote computer
2) download torrents to the server storage from the remote computer

But, I have zero server experience.

I have an eeepc 4g (+ext hd) that might work to host the files.  If that wouldn't work would [http://www.marvell.com/featured/plugcomputing.jsp]("http://www.marvell.com/featured/plugcomputing.jsp") be a possibility?

Anyone have any suggestions and/or specific instructions? Thanks in advance.

PS.  eeepc/server would run ubuntu, and the remote computer would run vista

---

### Post by cariboo on 2009-02-25
Why not find an older unused computer and us it for a file server, you don't need a lot of horsepower just to serve files. Have a look at this [file server howto]("http://doc.ubuntu.com/ubuntu/serverguide/C/windows-networking.html"). 

You will also need to setup [Remote Administration]("http://doc.ubuntu.com/ubuntu/serverguide/C/remote-administration.html") and setup port forwarding on your router. You'll have to look at the docs for your router to setup port forwarding, as they all seem to do it a differnet way.

Jim

---

### Post by zeronothing on 2009-02-25
I agree with what cariboo907 said. I have an old machine at home with a bunch of hard drives in it. all it does is server out files. what I do to access the files remotely is use ssh. so if you were to download filezilla which is a ftp client program you can set it up to connect back to your home server to access your files..

---

### Post by medicineman24 on 2009-02-25
Thanks for the replies and links.  Yeah, I don't use my eee so I think it'll work fine to host files.  I'll see what I can figure out with ftp and ssh. Is there any advantage to running a server distro of ubuntu just to host some files?

---

