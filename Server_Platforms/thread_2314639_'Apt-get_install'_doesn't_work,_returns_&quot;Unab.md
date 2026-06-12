---
title: "'Apt-get install' doesn't work, returns &quot;Unable to locate package - &quot;"
date: 2016-02-22
forum: Server Platforms
---

### Post by gectorwhitlox on 2016-02-22
I am having problems setting up an Ubuntu-server on an old PowerEdge 2850 Dell server. I've gotten many bugs worked out so far but now I'm stumped. During installation of the OS I get an error in the 
"Select and install software" stage. If I bypass that step every thing else goes fine, but when I boot into the OS and I try and run "sudo apt-get install ubuntu-desktop", I get a "Unable to locate package -" 
error. I've tried doing "sudo apt-get update" also. I'm a complete noob at this.

---

### Post by QIII on 2016-02-22
Moved to Server Platforms.

Hello!

Would you please post the entire message returned when you try to install ubuntu-desktop?

(Just as a bit of info:  very few of us put a GUI on the server version.)

---

### Post by midhun4 on 2016-02-24
I had the same prob,Try sudo apt-get upgrade ad sudo apt-get update.Hopefully this will solve ur issue!!!

---

### Post by Bucky Ball on 2016-02-24
> **midhun4 said:**
> I had the same prob,Try sudo apt-get upgrade ad sudo apt-get update.Hopefully this will solve ur issue!!!

Different problem by the looks. And just a heads up: always run the update command before the upgrade one. 

From the OP's first post:

[QUOTE=gectorwhitlox]I've tried doing "sudo apt-get update" also.[/QUOTE]

____

Welcome. Hold on. You are installing the server version and then 'sudo apt-get install ubuntu-desktop'???

Just install Ubuntu. The command you are using after installing server has pretty much the same effect and makes installing using the server install media redundant. No point. The idea of the server install is to have a server setup, no desktop environment, or a very light one, few apps and, well, a server.

If you want to build from the ground up, the minimal ISO or the server route (the mini if you are intending a regular desktop at the end) is great, but if you're intending to install '*buntu-desktop' after install, don't waste time with either. :)

* Just a thought: are you installing using the text-only server installer because you can't get the graphic installer of Ubuntu to work? Might be easier to work out why that's not working if this is the case. Also, please confirm which Ubuntu release you are attempting to install.

---

### Post by midhun4 on 2016-02-24
> **Bucky Ball said:**
> Different problem by the looks. And just a heads up: always run the update command before the upgrade one.



Thank you,I didnt knew tht,Update should be run first and then upgrade,Will keep in mind  ,Being a newbie I would like to thank you for info..

---

### Post by MAFoElffen on 2016-02-26
Did anyone ask if he had a working network connection?

Please try these commands and post back if there is any problem with them.
```

ping -c 3 8.8.8.8
ping -c 3 www.google.com
nslookup www.google.com

```
The reason I gave you those commands is that apt and sources.list uses DNS to map the domain names to ip's. You can have a network connection, but if you have a DNS problem, then apt is going to fail. When you installed, did you chose dhcp or static for your network connection?

---

