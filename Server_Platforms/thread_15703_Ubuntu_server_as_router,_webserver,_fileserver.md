---
title: "Ubuntu server as: router, webserver, fileserver"
date: 2005-02-16
forum: Server Platforms
---

### Post by Limber on 2005-02-16
Just ordered parts for my new server, and ubuntu seems like a good choice for OS. What i want to do is to set up the server to act as router, webserver and fileserver (both ftp and with shared space).

How do I set it up as a router? Will I be able to use my usb wlan-adapter to connect my laptop to the server?

I think i can manage the web/fileserver part, but I have no clue on the router functions and I really want it to work so any help is greatly appreciated!  :grin: 

Another thing: I have a 300 GB usb 2.0 external harddrive (Maxtor OneTouch), any problems using that under ubuntu?

Thanks in advance! 

PS. The hardware list is on [my website](http://www.cyd.liu.se/~andli826)

---

### Post by az on 2005-02-16
"How do I set it up as a router?"
There are many options.  You need to do masquerading.  I have used shorewall for this and it is easy to set up.  You can easily add firewall rules.

sudo apt-get install shorewall shorewall-doc
With the shorewall-doc package you get example setups.  Move the two-interface example to /etc/shorewall, change a few settings and you are off!

You will also need to do dns
sudo apt-get istall dnsmasq

Edit the config and you have dns masqerading.  It also gives you a dhcp server.  Perfect as a router!


"Will I be able to use my usb wlan-adapter to connect my laptop to the server"

It depends on the driver.  You may need to use the hostap driver for prism devices, but I do not think it works for usb devices (yet).  I do not know about other types.
You would always be able to just make an ad-hoc connection.

---

### Post by Limber on 2005-02-16
Thanks for the info and the quick reply!

If anyone has any additional info you are welcome to add it.

---

### Post by st0ic on 2005-02-16
Keep us updated, I plan on attacking a server with ubuntu this weekend...FS/DC, mabye a mail server as well.

---

### Post by Rottweiler on 2005-02-16
This is good:
[http://obsidianrook.com/devnotes/2face.html](http://obsidianrook.com/devnotes/2face.html)

More links:
[http://ubuntuguide.org/](http://ubuntuguide.org/) (search for "firestarter")
[http://software.newsforge.com/article.pl?sid=04/12/20/1737201&from=rss](http://software.newsforge.com/article.pl?sid=04/12/20/1737201&from=rss)
[http://www.fs-security.com/](http://www.fs-security.com/) (they have good docs)
[http://www.shorewall.net/](http://www.shorewall.net/)

---

### Post by Limber on 2005-02-24
[QUOTE=azz]change a few settings and you are off![/QUOTE]

Optimist...  :grin: 
This is proving to be a bit of a challenge, if it doesn't work out I'll whine about it here, but I think I can work it out!

---

