---
title: "[SOLVED] use apache without internet access"
date: 2008-10-18
forum: Server Platforms
---

### Post by gishaust on 2008-10-18
Hi everyone 

I have a desktop machine that has apache2 installed. I want to be able to use the server when it is not plug into  the network, as stand alone machine. But it will not let me do it. If I type 127.0.0.1 into the browser I can get the machine to work but if I type 127.0.0.1/able (which does exist)  it will not open it.  But as soon as I put the network cable in it works fine.

I have tried putting ServerName localhost in the /etc/apache2/httpd.conf thinking that was the issue. but after restarting apache2 it will not make a difference.

I tried posting this issue on the desktop forum but I think it is in the wrong spot

Does anyone have any ideas??

---

### Post by Drezard on 2008-10-19
Try typing [http://localhost](http://localhost) into the the top of the browser when network cable unplugged.

Daniel

---

### Post by gishaust on 2008-10-19
I tried it and it didn't work. I know that this is a good thing but I don't know why.

---

### Post by gishaust on 2008-10-19
Apache is not the issue  it is a box in firefox 3 you have to press file then work offline and it works great.

---

### Post by az on 2008-10-19
> **gishaust said:**
> Apache is not the issue  it is a box in firefox 3 you have to press file then work offline and it works great.

Actually, you're not using apache to serve the pages at all in that case.  You're telling firefox to look at the filesystem for the pages.  Anything but straight HTML won't work.

You need to configure apache to serve pages locally.  For example, what is the ServerName set to?

---

