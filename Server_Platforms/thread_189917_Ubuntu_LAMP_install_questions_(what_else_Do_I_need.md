---
title: "Ubuntu LAMP install questions (what else Do I need to do?) firewall?"
date: 2006-06-05
forum: Server Platforms
---

### Post by zerrudo on 2006-06-05
I did some searching on the forums but haven't really found great answers for what needs to be done.

I did a fresh LAMP install with Ubuntu 6.06 and everything installed fine.

I configured my router to port forward port 80 to my Ubuntu box (which has a static IP on the router as 10.1.1.111)

Using a local computer (attached to the same router), I was able to use firefox and view the apache website correct install page (basically [http://10.1.1.111](http://10.1.1.111) showed up saying that apache had been installed correctly).

Thats where the good news stopped.  I played around with my DNS control on my web-host so that [www.mywebsite.com](www.mywebsite.com) go to my IP, through the router which would  route to my Ubuntu box.

EX. Nslookup [www.mywebsite.com](www.mywebsite.com) brings up my IP as 5.5.5.5
My router has a static IP address of 5.5.5.5
So [www.mywebsite.com](www.mywebsite.com) hits up my router at port 80
and my router port forwards this request to port 80 to ubuntu box at 10.1.1.111

Now, the DNS control that my web-host service uses is in fact installed correctly, because attached to my router is another server that I use as a mail exchanger and it is setup properly 

After typing in [www.mywebsite.com](www.mywebsite.com), the page that said that apache had been  installed correctly does not show up.

The Ubuntu box itself does have an internet connection that works as I played around with some commands and it is able to ping other ips, nslookup things.

I have done some searching and everyone says that Ubuntu server is open; however, if you go to [www.ubuntu.com/server](www.ubuntu.com/server) and read the third paragraph, it states that:

A key lesson from the Debian heritage is that of security by default. *The Ubuntu Server has no open ports after the installation and contains only the essential software needed to build a secure server.*

I'm not concerned whether or not it is, I simply want to know what else do I need to do in order to get the people on the internet to connect to my Ubuntu box?

I think I've explained everything to the best of my ability, all I'm trying to get out of this Ubuntu box is a simple website to host pictures.

---

### Post by anson on 2006-06-06
I learned from another thread that ISP may have blocked all incoming port-80 requests.  I'd suggest you do a traceroute from outside of your LAN and see where it gets lost.

---

