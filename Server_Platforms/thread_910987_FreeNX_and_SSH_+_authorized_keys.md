---
title: "FreeNX and SSH + authorized_keys"
date: 2008-09-05
forum: Server Platforms
---

### Post by jpdk on 2008-09-05
Hi Guys,

I am trying to set up a way to connect via remote desktop to my Ubuntu 8.04 server from my Windows Macine. 

I have installed Firestarter and closed down everything so no ports are open but port 22 and no ping is replied to. I have set up my SSH demon to only accept certificate authentication. This somehow conflicts with FreeNX, that also uses port 22 or is it SSH... don't really know. FreeNX also tries to use its own certificate authentication, which conflicts with what I have set up.

I have set up my SSH like this because I need a tunnel to my MySql server, which is exposed on the internet, and I have certificates on remote sites already. 

I can get VNC to work, but I need to have the session on the server logged in, and I don't think that would be a very good solution.

I have tried to find a solution in the forum already, but I can't find anyone who provides a solution.

Thanks,
JP

---

### Post by windependence on 2008-09-05
Why run a desktop at all on your SQL server? It's not necessary to admin the server and it opens security holes. 

Also, instead of VNC try nomachine.

-Tim

---

### Post by jpdk on 2008-09-05
Hi Windependence,

Thanks for your reply. The reason is that I am not that experienced with Linux yet, and I just feel more comfortable with a desktop. 

I have the MySql access set up so I can administer it remotely already. I have tried to minimize the security risks by only opening up for SSH using certificates and no username/password authentication... and further more restrict all certificates but one to access port 3306 without any console access or X11 access.

Give me time ;) I am eager to get to know the world of Linux, but I am at this time only a novice. I promise that my next server will not have a Desktop, if I can just have this one to practice on.

I will take a look at nomachine.

/jp

---

### Post by windependence on 2008-09-05
Good deal, and good luck.

when you feel comfortable with the CLI, you should try screen. Screen allows you to disconnect a session and come back to it later while it continues to run. It's really cool. 

If you need help with the command line, just post it here and we'll help you out. ;)

-Tim

---

