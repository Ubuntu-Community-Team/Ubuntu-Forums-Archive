---
title: "Mumble / Murmur Server Help :: I have both installed, now what?"
date: 2009-08-08
forum: Server Platforms
---

### Post by own3mall on 2009-08-08
I've downloaded and installed both mumble and murmur, but I have no idea what to do now.  There is no web interface installed right off the bat, so how do I moderate / modify the settings of the server?  How do I even know if it's running?  What's ICE or whatever it is talking about?  

Anyone have a guide for ubuntu 9.04 that is super easy?  

I wish it would be as easy as setting up Teamspeak2 on a Windows machine.  

Let me know.
~
Thanks
OwN

---

### Post by own3mall on 2009-08-10
Anyone?

---

### Post by Kapli on 2009-08-25
Had these same questions myself, ran into this thread on google.
What I did:
sudo dpkg-reconfigure mumble-server
gksu gedit /etc/mumble-server.ini

By running those commands and configuring it then doing
sudo /etc/init.d/mumble-server restart
I had a mumble server working perfectly. 
If you installed mumble server through synaptic then it would of installed a web interface too, to access it type localhost/mumble/ into your browser, localhost/mumble/register.cgi for registering new users.
There are other web interfaces that are more advanced, check out [http://mumble.sourceforge.net/Running_Murmur#Web-Interfaces](http://mumble.sourceforge.net/Running_Murmur#Web-Interfaces)
I haven't tried any of them yet but I will do it later.

---

### Post by own3mall on 2009-08-29
> **Kapli said:**
> Had these same questions myself, ran into this thread on google.
What I did:
sudo dpkg-reconfigure mumble-server
gksu gedit /etc/mumble-server.ini

By running those commands and configuring it then doing
sudo /etc/init.d/mumble-server restart
I had a mumble server working perfectly. 
If you installed mumble server through synaptic then it would of installed a web interface too, to access it type localhost/mumble/ into your browser, localhost/mumble/register.cgi for registering new users.
There are other web interfaces that are more advanced, check out [http://mumble.sourceforge.net/Running_Murmur#Web-Interfaces](http://mumble.sourceforge.net/Running_Murmur#Web-Interfaces)
I haven't tried any of them yet but I will do it later.

How do you install it through synaptic?  It came with web administration?  How do you create admin users?

---

