---
title: "getting ubuntu server connected to the net"
date: 2009-09-02
forum: Server Platforms
---

### Post by oospill on 2009-09-02
could use a little help here:

I just got ubuntu server installed on my desktop, and ubuntu desktop on my laptop.  BOTH are connected to a netgear router which goes to a cable modem.

I really want to mess with apache server, but I can't figure out how to get the server to connect to the internet or vice-versa.

when I type: 
"/etc/init.d/apache2 start" 

mr computer says:
"could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName" then "(13)Permission denied: make_sock: could not bind to addresss 0.0.0.0:80 no listening sockets available, shutting down"


I'm guessing I need to mess with the router, as well as ubuntu server.

any help would be much appreciated!

---

### Post by cariboo on 2009-09-03
You need to add sudo to the command:

```
sudo /etc/init.d/apache2 start
```

Apache2 should start by default when you reboot.

> could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

Means that you you don't have a name aliased to your ip address in /etc/host. My /etc/hosts file look like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	alexis
192.168.1.250	willy
192.168.1.200	horsefly
192.168.1.230	likely
192.168.1.1	router
```

My servers ip address is 192.168.1.250, I access it by typing:

```
http://willy
```

in a web browser.

---

### Post by oospill on 2009-09-03
yeah, I've got the sudo part down, but other than that, I feel like a bloomin idiot..   here's why:

still get the error:

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid2384) already running

I don't remember that last line, so is it already running?  

sudo /etc/init.d/apache2 stop

^^^ appeared to make it shutdown.   SO, I think got it to start, or it started at boot..  wouldn't that be easy.  (??)

does this seem right to you?  also, please help me figure out what I need to put in the etc/hosts file

thank you for the help so far!!

---

### Post by fahadsadah on 2009-09-03
Add, to the file:
```
127.0.1.1 domain-goes-here
```
Where domain-goes-here is the fully qualified domain name of your server.
If you don't have one, it's OK to ignore the warning?

---

### Post by oospill on 2009-09-03
here's what I've got in my etc/hosts file:


127.0.0.1     localhost
127.0.1.1     ubuntu-server

#The following lines are desirable for IPv6 capable hosts
::1     localhosts ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6.mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


okay.. now that I've typed all that..  I guess my question is how do I connect to the server from my laptop (both are connected to my router) .. I tried to load 127.0.1.1 from my laptop (in firefox), and it says failed to connect, however if I run 'lynx 127.0.1.1' from the server's prompt, I get a page that says 'It works!' .. how can I connect from I different computer?

thankyou folks for the help!

---

### Post by wojox on 2009-09-03
You need to log onto the router and see what ip address it assigned your server.

Something like 192.168.1.101 or 192.168.1.102

Once you have that put it in your browser.

---

### Post by bear24rw on 2009-09-03
you can ignore that warning, also apache should start at boot, if you want to restart apache you can
```
sudo /etc/init.d/apache restart
```

---

### Post by snowman4839 on 2009-09-03
Simply put...

To find your IP... type "ifconfig" in terminal and look at what comes up
"lo" is your loopback interface in case you want to send something out to the web wanting it to come back to your machine. 127.0.0.1 is always the loopback IP address.
"eth0" is your ethernet port (assuming you have one). If you are on a wired network then look at the "inet addr: XXX.XXX.XXX.XXX" and the XXX.XXX.XXX.XXX is your IP address
"wlan0" is your wireless card (assuming you have one). If you are on a wireless network then to find your IP, do the same thing from from eth0...

Then... now that you know you're own IP address... type that IP address (or 127.0.0.1 since it will just send it back to your computer) into you're web browser's address bar and it will make an HTTP request to your computer which will then be processed by Apache and sent back to yourself in your web browser... BAM! that is your Apache Server in a nutshell.

The reason it said "httpd (pid2384) already running" is because Apache probably auto-started with your computer and httpd (http daemon (daemon = background process)) was already started when Apache started with the computer. It's no big deal.

Quick Commands
to start apache server - "sudo /etc/init.d/apache start"
to restart apache server - "sudo /etc/init.d/apache restart"
to stop apache server - "sudo /etc/init.d/apache stop"

Tips
If you are getting the "You don't have permission to access / on this server" it is because your permissions are not allowing you to view that particular directory... to fix this type "sudo chmod -R 777 DIRECTORYPATHHERE" This allows anyone to do anything to the contents of that directory.
If you want some security on your web server, look into .htacess files for Apache.

---

### Post by oospill on 2009-09-03
thank you for the post...  I got the ip for my server (192.168.1.3).. and I typed that into my laptop, and it loaded the "It works!" page..  super duper!  now, what address would I give to *you* to load the same page?

---

### Post by bear24rw on 2009-09-03
you need to foward port 80 on your router to 192.168.1.3 and hope you ISP doesnt block 80 inbound then go to 

[www.whatismyip.com](www.whatismyip.com)

and thats the ip that we should be able to see you page at

---

### Post by oospill on 2009-09-04
Abosolutely loveley!! worked like a charm..  now only if I knew whether my ip static or dynamic..  any input?

---

### Post by bear24rw on 2009-09-04
My bet would be you have a dynamic ip.. how dynamic is the question. my IP hasnt changed all summer where as my friends changes all the time, just depends on your ISP i suppose..

---

### Post by oospill on 2009-09-04
well, I reset my cable modem after leaving it unpluged for 5 minutes.  when I booted back up and went to whatismyip.com it told me that I have the same ip addy that I had last night.  does anyone know if that means I have a static ip?

also, could someone please explain to me why someone would install a DNS server, and what DHCP is??

back in the day, I had to use dyn-ip (or whatever it was called) in windows to have a static address that I could tell people.

that's kinda what I'm going for right now.

thanks to you guys for responding!!

oospill

---

### Post by bear24rw on 2009-09-04
> **oospill said:**
> well, I reset my cable modem after leaving it unpluged for 5 minutes.  when I booted back up and went to whatismyip.com it told me that I have the same ip addy that I had last night.  does anyone know if that means I have a static ip?

Doesn't mean you have a static IP i have a dynamic one but i can do the same thing and my IP doesnt change.. it all depends on your ISP

---

