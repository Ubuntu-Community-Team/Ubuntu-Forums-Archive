---
title: "ssh connection from client to server very slow"
date: 2007-05-17
forum: Server Platforms
---

### Post by jerseyman on 2007-05-17
Hi!
I am new to Ubuntu server. I have installed 6.06. LTS server and OpenSSHServer and it's working fine.

I have installed ssh server to my desktop and i'm connecting to server from my laptop. I have Internet Cable connection with two computers which are connected with stupid five port swich, so i cannot configure it.

The question is why is the connection is so slow when i copy some files from server? (1 Gb takes about 3 hours). I think that the connection is going over network which i dont understand? I think that the route should be direct trough the swich, not over network and routers over there?

Is there something that i can do? Maybe the problem is the swich? It doesnt know how to manage the traffic?

Thank for your help!
jersey

---

### Post by Knowles on 2007-05-17
Are you transfering the files over sftp?

---

### Post by jerseyman on 2007-05-17
I have just installed SSH server and made a connection with gnome nautilus.

---

### Post by Knowles on 2007-05-17
Looks like it uses sftp (I may be wrong) from a bit of browsing on the net, I too have the same problem. I had to transfer 300 gig from one *nix system to another, I haven't figured why my max speed is about 400k yet but if I need something significant I use SCP (secure copy) and it is recursive too. Using SCP sped up my tranfers to the maximum.

---

### Post by jerseyman on 2007-05-17
Is there a way to use SCP with nautilus or do i have to use command line? thanks for your help!

---

### Post by Knowles on 2007-05-17
I have no clue I am no real expert, but scp I think is purely terminal (i could be wrong), I guess another alternative is to install samba and mount the shares on your system, that is what I have at the moment for general stuff like music and video.

---

### Post by jerseyman on 2007-05-17
Hi!
I just dont get it! I have tried also scp, but my speed is still only about 115 Kbps, it should be more? Is there someone who knows what limits the download speed?

Thanks!

---

### Post by Knowles on 2007-05-18
well I am clueless then, maybe someone can shine a light on the subject.

---

