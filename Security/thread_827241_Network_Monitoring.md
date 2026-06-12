---
title: "Network Monitoring"
date: 2008-06-12
forum: Security
---

### Post by TorchlightJay on 2008-06-12
Hello,
  I want to setup a solution to monitor a variety of networks from a single point. How can I accomplish this? I hear a lot about Nagios but I am sure that is only one piece of the puzzle. I want to be able to setup something to monitor a variety of firewalls, servers, desktops, and know when something crazy happens and be able to respond. Any ideas?

---

### Post by The Cog on 2008-06-12
Depends what you're looking for. It may be worth looking at OSSEC which is a server that monitors log messages from other machines. I have been impressed with what I have seen from it so far.

---

### Post by TorchlightJay on 2008-06-12
well what i want a few things. i want to be able to log into a nice gui and be able to see what I need to see. I want to know what services are running and what went down. I also want to know when something wrong happens with the network (be able to monitor the firewall or otherwise)

I am looking at OSSEC and it looks good. Nagios looks good too. I want to do it with Mac, Linux, and Windows. Do you think these can help me? Can I install OSSEC onto a central system then put an agent on all the systems needing monitoring?

---

### Post by The Cog on 2008-06-13
> **TorchlightJay said:**
> well what i want a few things. i want to be able to log into a nice gui and be able to see what I need to see. I want to know what services are running and what went down. I also want to know when something wrong happens with the network (be able to monitor the firewall or otherwise)
Nagios should be worht looking at for that. Maybe also OpenNMS.
> 
I am looking at OSSEC and it looks good. Nagios looks good too. I want to do it with Mac, Linux, and Windows. Do you think these can help me? Can I install OSSEC onto a central system then put an agent on all the systems needing monitoring?
OSSEC doesn't really have a GUI, but it does email you about things. Yes, you can install OSSEC on a central server (linux) and put the agent on lots of assorted platforms.

---

### Post by TuckLive on 2008-06-14
Take a look at OSSIM.  It combines Nagios, Snort, and several other sensors to help you monitor a network.  OSSIM also has a fairly nice web ui you can log into.  [http://www.ossim.net/](http://www.ossim.net/)

EasyIDS is a Snort/BASE combo set that is easy to setup.  I'm not sure about multiple networks, but I have it on my personal network and I like it.  You can configure everything through the web page.  [http://www.skynet-solutions.net/easyids/](http://www.skynet-solutions.net/easyids/)

---

### Post by TorchlightJay on 2008-06-16
cool, hey this is a more advanced style question. How do you add remote connection into all of this. Nagios and OSSEC and a lot of these other systems are great but they only allow for monitoring, doesn't provide much in terms of logging into the system and fixing it. Does anyone know of an already formed solution or a way to build this solution? Let me know if you have any ideas.

---

### Post by wirelessmonkey on 2008-06-16
I use Groundworkopensource [http://groundworkopensource.com/]("http://groundworkopensource.com/") for everything you're describing.  I've never had any problems.

Best of Luck

---

### Post by TorchlightJay on 2008-06-18
Hello,
  I didn't realize that groundworks allowed for remote connection into machines. That's cool. Does it allow for reports to be made and does it also have a web interface? How do you install it on client computers? Is it just a simple agent?

---

### Post by HermanAB on 2008-06-18
When all else fails, there is always Webmin.

---

### Post by TorchlightJay on 2008-06-19
True but i want to connect to windows machines as well

---

### Post by wirelessmonkey on 2008-06-19
Groundwork uses SNMP for anything other that uptime/pings, so just enable SNMP on your windows machine if necessary. A goodly portion of GWMOS is just a frontend for Nagios configuration.  Read their forums for a more thorough explanation, I post there sometimes as well ;)

---

