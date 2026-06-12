---
title: "Help with server anyone?"
date: 2012-09-25
forum: Server Platforms
---

### Post by archieburden9 on 2012-09-25
hey, i JUST got ubuntu server to try hosting some things as a learning curve, maybe a website or anything, i don't know. but i have some questions because of the things that have gone wrong >.<
:lolflag:

anyways, the 1st question sounds really stupid, and i might know it but im making sure here, but is DNS a choice of the types they offer you in installation? you get a list of all the things to see what type you want and i definitely chose a 3 letter one, it might be NAT and DNS but im not sure >.<


now that i know what i installed for sure not i am asking what to do, what CAN i do with this? what can i host? i don't want to do anything with FTP file sharing or IRC chats, i want to host a website or have a server. help anyone?

i know im being vague here but i really do want general help of what i can and should do (preferably a website ;))


i have logged in and everything, im looking at the terminal looking screen... :TeachmE:

---

### Post by lykwydchykyn on 2012-09-25
Typing "sudo tasksel" at the terminal should give you the menu you get at installation.  I believe one of the choices is DNS; web server (maybe called LAMP?) is also one.  That should get you started.

---

### Post by darkod on 2012-09-25
It doesn't really work like that. You can't simply ask "what can I do?". You can do million things with linux servers, and then some more. :)

First YOU need to decide what do YOU want to do. Hosting test (local) website as a learning step? Fine, then focus on a webserver installation and configuration.

And when talking about websites, the very first thing you should probably know is that you don't really need to host your own DNS. It might be too complicated for a start.
The registrar where you bought the domain (if you do have a real domain name bought) has their own DNS servers and you will need to simply create a host A record there, pointing to where ever your webserver is (your home public IP?).

As for the actual webserver, the basic starting point is the LAMP package/role. When it installs, you already have a basic webserver running.

As mentioned above, if you didn't select LAMP during installation you can always invoke the same menu by running:
sudo tasksel

---

### Post by archieburden9 on 2012-09-25
i want to host a website, i have google around and i know all about hosting on windows but i want to do it on a server for better performance, now just tell me how to get my site online, i don't care if its technical because i have to learn anyway. COME AT ME

---

### Post by darkod on 2012-09-26
I don't know apache in details so I can't help much, but just to remind you that by default the installation might have set up the server with dhcp. If you don't cancel it during install, that's what it does.

You need to configure static IP on your server so that you know which IP it has always. Look into /etc/network/interfaces. If the eth0 interface is something like:
```
auto eth0
iface eth0 inet dhcp
```

you need to edit it to something like:
```
auto eth0
iface eth0 inet static
   address 192.168.x.x
   netmask 255.255.255.0
   gateway 192.168.x.x
   dns-nameservers x.x.x.x y.y.y.y
```

Of course, use the IP address you want and it needs to be outside of the routers dhcp range. And for gateway use the routers IP. For nameservers you can use which ever you want, either some global ones or your ISP nameservers.

After changing the settings restart networking with:
```
sudo /etc/init.d/networking restart
```

After that you know which static IP your server has.

---

### Post by lykwydchykyn on 2012-09-26
In a nutshell:

- You need a http server installed.  Apache2 is the usual suspect, but you could choose lighttpd if you're interested in using fewer resources.

- You need a static IP on your server, as described above.

- You need a static public IP from your ISP

- You need to have your domain registrar direct your domain to the static public IP

- You need to make sure port 80 on your router is forwarded to port 80 on your web server.

- You need to chuck files in /var/www to build your website.

If you want more specific help, just ask a more specific questions.

---

### Post by Lars Noodén on 2012-09-26
> **lykwydchykyn said:**
> 
- You need to make sure port 80 on your router is forwarded to port 80 on your web server.

Port 443 would be good to have forwarded too, in case HTTPS is used.

---

### Post by SeijiSensei on 2012-09-26
As always, start by reading the [Ubuntu Server Guide](https://help.ubuntu.com/12.04/serverguide/).

---

### Post by drdos2006 on 2012-09-26
Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings on your network.


> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.590_all.deb

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to your server to edit files, create shares, startup daemons etc..

regards

---

### Post by archieburden9 on 2012-09-27
thanks, ill keep you posted tomorrow when i call my ISP to make sure they are OK with me hosting and to give me a static IP etc. 

where do i go to find the directories? this is in a virtual machine by the way and i installed it off a file instead of disk.

---

### Post by DaveyG on 2012-09-28
> **archieburden9 said:**
> i want to host a website, i have google around and i know all about hosting on windows but i want to do it on a server for better performance, now just tell me how to get my site online, i don't care if its technical because i have to learn anyway. COME AT ME

As for DNS, I would recommend taking a look at this thread: [ubuntuforums.org/showthread.php?t=236093]("http://ubuntuforums.org/showthread.php?t=236093")

---

