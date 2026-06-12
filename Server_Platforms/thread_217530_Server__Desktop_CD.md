---
title: "Server / Desktop CD"
date: 2006-07-17
forum: Server Platforms
---

### Post by Flavian on 2006-07-17
Hi.
I got a question concerning ubuntu Server.
I want to set up ubuntu on my file / printer server.
The question now is, for a file / printer server could I use the normal desktop install cd as well. Or are there more differences in like samba etc... ?
The reason why I ask this is because I want a graphical desktop for my server, which does not come with the server installation cd!
And if there is no major difference in desktop / server concerning file and printer servers I was thinking about using the desktop cd.

What do the pros say? Is this dumb?

Thanks in advance.
Flo

---

### Post by az on 2006-07-17
> **Flavian said:**
> Hi.
I got a question concerning ubuntu Server.
I want to set up ubuntu on my file / printer server.
The question now is, for a file / printer server could I use the normal desktop install cd as well. 

Yes.

> **Flavian said:**
> 
Or are there more differences in like samba etc... ?

None whatsoever.
> **Flavian said:**
> 
The reason why I ask this is because I want a graphical desktop for my server, which does not come with the server installation cd!
And if there is no major difference in desktop / server concerning file and printer servers I was thinking about using the desktop cd.

What do the pros say? Is this dumb?

Thanks in advance.
Flo

It's not a dumb question.  Depending on your needs, you will adhere to a stricter best security practices.  

Running a Desktop on server is not what you would do on a mission-critical setup.

---

### Post by Flavian on 2006-07-17
Thank you very much, azz for your reply :)
I am interested now. Why is it more insecure to run a desktop environment on a Linux Server?

Did you just mean that using a desktop environment is more insecure OR that the desktop install itself compared to the server install CD is more insecure?
Sorry for my newbie questions :D but since I am sort of like a newbie I can't help but ask :)

For me, using gnome on my server would just ease up some maintenance things. Especially because my brother is not a linux pro and he needs access to the server as well :)

Thanks
Flo

---

### Post by az on 2006-07-17
> **Flavian said:**
> Thank you very much, azz for your reply :)
I am interested now. Why is it more insecure to run a desktop environment on a Linux Server?

Because vulnerabilities exist in any software.  The fewer things on your box, the ferwer things that can be potential vulnerabilities.


> **Flavian said:**
> 
Did you just mean that using a desktop environment is more insecure OR that the desktop install itself compared to the server install CD is more insecure?

Neither.  Just that less is more.

> **Flavian said:**
> 
Sorry for my newbie questions :D but since I am sort of like a newbie I can't help but ask :)

For me, using gnome on my server would just ease up some maintenance things. Especially because my brother is not a linux pro and he needs access to the server as well :)

Thanks
Flo
You can just install ssh and access your box graphically using nautlius.  Connect to server as your user on that box. You don't need to be running X on the server for that.

Just be aware that everything you do can have consequences.  If you add the server's user to the www-data group so that you can upload files to /var/wwww using ssh, be aware that you may want to remove those proviledges when your are done (and remove ssh so that no one can log into you box remotely).  

If you just want to play around, you can probably not worry so much about it and have fun.

---

### Post by DiamondX on 2006-07-17
Im going to make a home server, and I just found out about Webmin. It lets you access your *nix server with your browser, similar to how you would access a commercial router. Im planing on using it. It looks very user friendly.

---

### Post by az on 2006-07-18
Does webmin handle apache2?

Because if it doesn't, what's the point?

---

### Post by DiamondX on 2006-07-18
"Apache Webserver" is supported. Here is a list of standard modules:
[http://www.webmin.com/standard.html](http://www.webmin.com/standard.html)

I assume apache2 has the same directories as apache. Webmin also has Ubuntu on the supported OS list.

---

### Post by az on 2006-07-18
> **DiamondX said:**
> "Apache Webserver" is supported. Here is a list of standard modules:
[http://www.webmin.com/standard.html](http://www.webmin.com/standard.html)

I assume apache2 has the same directories as apache. Webmin also has Ubuntu on the supported OS list.

Apache2 has a vastly different way of being managed than apache.  And Apache is in universe, but it (apache 1.3) is on it's last legs.

---

