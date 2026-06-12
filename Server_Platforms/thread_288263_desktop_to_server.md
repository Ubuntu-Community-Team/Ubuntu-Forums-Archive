---
title: "desktop to server"
date: 2006-10-29
forum: Server Platforms
---

### Post by shashi123 on 2006-10-29
i have installed ubuntu 6.06 lts on a P4 system

i think its a desktop version 

now i want to run this ubuntu system as a server and i have connected windows  98 systems 


though on ubuntu system i am ablt to surf the net but i am not able to access internet from windows client 

how can i use ubuntu as a internet server

---

### Post by jd65pl on 2006-10-29
Sounds like you want to enable your ubuntu machine to act as a router if I have understood you correctly. You could run a DHCP server on your ubuntu machine and share the internet connection.

See this page on DHCP server - [http://ubuntuguide.org/wiki/Dapper#DHCP_Server](http://ubuntuguide.org/wiki/Dapper#DHCP_Server)

---

### Post by shashi123 on 2006-10-29
i did install dhcp server

now i have a win98 as client 
my ubuntu server ip is 192.168.0.1

and cilent win98 is 192.168.0.2

in my win98 i have a mozilla browser can u tell me whats the setiing for mozilla broweser

is it direct internet connection]

or 

shall i write proxy setting as 192.168.0.1 if yes then whats the port no

let me know

---

### Post by jd65pl on 2006-10-29
You want to set your network card to aquire the ip address via dhcp. This should be configured through the network config in the control panel.

---

### Post by Iowan on 2006-10-29
> ,,,is it direct internet connection or shall i write proxy setting as 192.168.0.1 if yes then whats the port no,,,
My clients all believe they are directly connected to the internet. Proxy programs are available (Squid comes to mind - though I haven't used it) but you should be able to get connected without one.

---

### Post by unless on 2006-10-30
You have two options:

1) The Win98 clients connect directly to the Internet (as Iowan suggested);

2) The Win98 clients connect to a proxy server installed on the Ubuntu server (also as Iowan suggested).

> **shashi123 said:**
> i did install dhcp server

now i have a win98 as client 
my ubuntu server ip is 192.168.0.1

and cilent win98 is 192.168.0.2



How does your Ubuntu machine connect to the Internet? Does it have a modem installed on it, or does it use a router (adsl, for example) that is found on the network?

If the Ubuntu machine uses a modem, the easiest option to share its connection would be variant 2: Installing a proxy server. Personally, I like Squid. 

If there is a router on the network, you should be able to access it directly from all machines. On a Win98 machine, when you open a DOS prompt and type IPCONFIG, what is the Default Gateway that is listed?

---

### Post by shashi123 on 2006-10-30
i have got a cable connection

the ubuntu machine is connected to a cable modem through eth0 and the internal network is on eth1

---

### Post by az on 2006-10-30
You need to share your internet connection?

I think you can do this with firestarter.  Be sure to install the recommended packages as well (for dhcp server).

Internet connection sharing is known as Network Address Translation or "Masquerading".  If you are doing it from the command line, there are a number of tools available to you, but it get's complicated (because nothing is assumed).

Guidedog is also a GUI tool for that.


Edit:

Yep.  Install the firestart and dhcp packages.  The configuration wizard will set up NAT for you.

---

### Post by shashi123 on 2006-10-31
i installed firestarter

initially it was all right 

and i dont know what i did  but now it is giving me this message

failed to start firewall
an unknown error has occured
plz check your network device setting and make sure your internet connection is active  

i tried 

apt-get remove --purge firestarter

and reinstalled it 

bt it still gives me the same message

and once i install it blocks the internet connection to system

earlier i was not able to install firestarter but after ur msg i tried again and it worked but now the above proble 

can u help me once again

---

### Post by fakie_flip on 2007-05-07
Have you tried IPCop and/or SmoothWall? They are easy to setup for a firewall/router.

---

### Post by jiminycricket on 2007-05-08
Another option is this: [http://kde-apps.org/content/show.php?content=53675](http://kde-apps.org/content/show.php?content=53675)

---

### Post by fakie_flip on 2007-05-15
> **jiminycricket said:**
> Another option is this: [http://kde-apps.org/content/show.php?content=53675](http://kde-apps.org/content/show.php?content=53675)

What is the package name for that software in Ubuntu?

---

