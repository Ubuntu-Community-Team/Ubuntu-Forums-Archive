---
title: "setting up server"
date: 2008-01-27
forum: Server Platforms
---

### Post by linux noooob on 2008-01-27
I am setting up ubuntu server and i was wondering do i use the ip address my isp gives me the one my router gives me or do i have to get a domain name. If i have to get a domain name is there any company that gives free domains like mydomain.company.com.  Last i am on a router and have 2 computers on it my one computer is the server the other computer well i don't want it to even be TOUCHED i want it blocked from EVERYTHING that has to do with my server my dad will freak if anything bad happens.

---

### Post by freebeer on 2008-01-27
It would help if you told us what you want the server to actually do.  Is it serving up web pages?  FTP? etc.

A router will act as a hardware firewall and you can set it up so that outside traffic (ie web page requests from the interwebs) is only forwarded to the server.  

You'll want to give your server a static IP address internally.  This way, when you configure your router to forward ports to the server, the traffic will always flow to the server.  

As for a domain name, you can get a free dynamic name through DynDNS.com and a few others.  You can then run a script in the background on the server to check to see if your public (outside) IP address has changed.  If it has, the script will update DynDNS's (or other's) entry for your domain name to point to the new address.  That way "www.yourdomain.org" is always pointing to your current IP address.

---

### Post by linux noooob on 2008-01-27
thanks :D and i am making a web site type thing and a place to put files on because i am tired of sending files over msn and usb key to my friends or other computers!

---

### Post by freebeer on 2008-01-27
If you want to restrict access to who can actually access the files, then something like an FTP server might be the best route.

Something to consider as you travel along the learning curve.  :D

---

### Post by linux noooob on 2008-01-27
ya i think i am going to go with ftp problem is i have no clue how to set it up or what it even is :confused:

P.S. when i try to make my server have a static ip i set it up i choose the right computer and hit the clone MAC button then i hit submit but it says the MAC address is in wrong format :confused:

i would also like to set up a user name/password so i choose who gets on and who doesn't

---

### Post by freebeer on 2008-01-27
You can start your understanding of FTP here, if you like: [HOWTO linky]("http://ubuntuforums.org/showthread.php?t=79588")

You don't need to clone your MAC address (usually).  In System -> Administration -> Networking, change your network card setting from DHCP to Static IP.  Then fill in the IP adddresses as appropriate for your LAN.

---

### Post by linux noooob on 2008-01-28
i was talking about my LAN router my ubuntu is already set to static but my router will not send it a static ip is says MAC in wrong format when i try to set on static ip on my router

---

### Post by linux noooob on 2008-01-28
also on my DI-524 i have a virtual server set up should i fill that out too?

---

