---
title: "Unable to access LAMP server outside of local network"
date: 2008-11-10
forum: Server Platforms
---

### Post by will492 on 2008-11-10
I'm currently running 8.10 desktop edition and have installed apache, mysql, and php. I've also installed phpmyadmin, it's working properly with "localhost and 127.0.0.1" so I know all the components are functioning properly.

The problem is whenever I try and access the website outside of my network the page doesn't load for a few minutes then says the server has timed out. 

The server is behind a router but I have port forwarded both port 80 and 433 to the correct computer. I have also tried plugging the computer straight into the modem and that still fails to work.

I'm stumped on this problem and I've reinstalled the server countless times trying to get this to work.

---

### Post by gpsmikey on 2008-11-10
I have not played that game, however, you may find your ISP is blocking traffic to port 80 - most ISP's don't want you to run a server of some sort on "home networks".  Comcast for example specifically states you can't have a server on a home internet account (well, at least one visible to the outside) in their AUP.

mikey

---

### Post by will492 on 2008-11-10
Thanks for replying, LAMP isn't a game though. It stands for linux, apache, mysql, php. But I'll still go check out if my ISP, cox, is blocking that port.

---

### Post by gpsmikey on 2008-11-10
I meant "game" in the sense of "scenario" or along those lines not "game" as in "kill the bad guys" or something.  I do know what LAMP is -- I have it running on two machines in my local network here in the house although I have not opened any ports in the router from the outside since I didn't want Comcast after me ( I believe they often scan all their IP's on a regular basis looking for servers etc based on comments I have seen from others when they look at the logfiles from their firewalls etc.)

mikey

---

### Post by Coreigh on 2008-11-10
Do you have multiple computers on your home network? You have the LAMP server, do you also have a laptop or a computer in another room, and can you access the LAMP server website from those? Before trouble shooting availability to the internet, is it available to your local network?

Next while it is true many ISPs frown on servers on the residential network you may be able to work around by using an alternate port or a dynamic DNS service.

UPDATE:
here is a link to dynamic DNS - [http://www.no-ip.com/]("http://www.no-ip.com/")

---

### Post by will492 on 2008-11-10
Oh ok, I get what you mean now. I have found out that cox does block port 80 so I guess I'll change the port the server opperates on to port 81 or purchase their $60 dollar a month connection. Right now I'm leaning toward the first option.

:)Once again thanks for your help.

---

### Post by Iowan on 2008-11-10
As Coreigh mentioned, try to access the server from another machine on your network first.  There are some Apache configurations that allow access from localhost only.

---

### Post by Philio on 2008-11-11
Are you sure your router allows you to forward on port 80? Some don't as it's the standard HTTP port for all websites.

---

