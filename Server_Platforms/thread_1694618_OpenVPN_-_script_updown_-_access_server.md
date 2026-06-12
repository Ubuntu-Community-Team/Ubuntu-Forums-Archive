---
title: "OpenVPN - script up/down - access server"
date: 2011-02-24
forum: Server Platforms
---

### Post by irish-link on 2011-02-24
Hi Everyone. I have a few issues after setting up Openvpn. I was wondering if anyone can help. 

At work i just setup a new Ubuntu Server 10.4. The server itself is working Great. I ended up getting Openvpn installed and working to a point.
I have searched online and done as much reading as i could find but i keep running into the problem of not understanding. So here is the problem. - NOTE: Im new to Ubuntu and not advanced in Linux in general so please be gentle haha. 

The server is set on a static IP address. At first i tried to have the config file listen on a virtual ip address i setup up in /etc/network/interface but that ended up not working so i set it to its specific ip address. I kept running into the error about script security while trying to start Openvpn. I tried to add into the config file "script-security 2" that way the up.sh and down.sh scripts were allowed to be run. That didn't help and then i kept trying to run Openvpn manually running the command 

> "sudo openvpn /etc/openvpn/server.conf --script-security 2" and i kept getting a message 

> "Options error: I'm trying to parse "/etc/openvpn/server.conf" as an --option parameter but I don't see a leading '--'"

So what i did was just comment out the "up" and "down" scripts in the config file. This allowed me to actually get Openvpn started on the server. So once this was done i connected form a client machine and was given an ip address like i should. The only issue is that i was not able to actually comunicate with the server. I have a samba share on there to allow me to copy files back and forth but an not able to actually communicate with the server at all. 
I should note that this is a web server that i can view from the outside. (actually get to the webpage) but i tried to access the website and share via the Openvpn gateway. I also tried to access the website portion using the hostname with no luck.

If anyone has any suggestions please let me know. Thanks in advance. 

By the way, prior to putting the server on its separate network i was able to access the webpage and the samba share using both the ip address and the hostname.

---

### Post by irish-link on 2011-02-28
So it turns out that i had multiple things that were happening that i needed to change. 
Im not sure if this really mattered or not but once i change the up and down scripts it worked. It turns out i had copied the scripts content from the online guide. This included about 2-3 indents before the "shabang" and once i removed that it worked. The script-security was actually working in the server.conf file but i didnt know this because i was getting the same errors while the scripts themselves were incorrect. 
Also this was a stand alone server. (not behind a router) i know this is unsafe and all but i didn't wan to do a lot more setup. Well i needed to assign ip address and the server was on a static. This wasn't going to work because i didn't have those ip address to give out. So i setup a router and gave out the right ip address' and now im all good. If anyone has any issue similar to this and my little rant right here didn't help let me know and i will see what i can do to explain better what happend to me.

---

