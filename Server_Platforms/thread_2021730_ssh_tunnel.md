---
title: "ssh tunnel"
date: 2012-07-09
forum: Server Platforms
---

### Post by lolium on 2012-07-09
Hi guys, trying to broaden my knowledge here a bit and im getting stuck with ssh tunnels.

Host A - windows box.

Host B - windows box with freesshd installed.

Host C - Linux box

I have set up Host B to allow ssh tunnels for the user i created aswell as shell access. Host C is locked down to only allow connections from Host B

I can ssh to Host B no problem but when i set up tunneling via putty i just get logged into Host B. 

Tried searching for guides online but most of them show it using ssh from the command line which i dont have the ability to do at the moment.

Can someone show me what im configuring wrong or point me in the right direction :)

Thanks in advance

Sam

---

### Post by papibe on 2012-07-09
Hi lolium.

I would gladly give you some pointers, but after reading your post a couple of times, I still don't understand what you are trying to do.

If C is locked, why mention it?
What is the role of A?

Regards.

---

### Post by kennethconn on 2012-07-09
>  
Can someone show me what im configuring wrong or point me in the right direction

You need to provide more details - when you "set up tunneling via putty", what 
exactly are you doing? It sounds like you might be doing a local rather than a remote forward, but really, the more details you can provide the more people can help.

---

### Post by hawkmage on 2012-07-09
There are 2 ssh tunnels.  Remote and local.  

OK with a remote tunnel you have something like this:
```
ssh -R 8080:localserver:443 remoteserver
```
This will forward any connections on remoteserver port 8080 through the tunnel to the localserver port 443.

With a local tunnel you have something like this:
```
ssh -L 8080:otherremoteserver:443 remoteserver
```
This will forward any connections on the local system port 8080 thorugh the tunnel to the otherremoteserver port 443.

---

