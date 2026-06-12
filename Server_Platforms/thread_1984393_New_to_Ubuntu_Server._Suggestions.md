---
title: "New to Ubuntu Server. Suggestions?"
date: 2012-05-21
forum: Server Platforms
---

### Post by jeremygotcher on 2012-05-21
Hi, Just to give you a little background about myself I've tinkered with Linux on and off for about 6 years.. I kept trying different distros but always kept coming back to Ubuntu because of its ease of use. Anyways.. I had this great idea because where I live I currently have My house my parents house and there office more or less under one roof. We have 4 computers at my house 4 at their house and 5 at their office not including networked printers, Tv's  etc.. so needless to say we have enough equipment for a decently sized office.. but I've been concerned with a few things for the last couple of years and one is data organization.. I would like to get one machine that holds all the information and shares out all the printers and thought I would do it with a Ubuntu server.. but to be honest I've never really jumped right into the console.. second I would like to look into something that could run monitoring software to make sure I don't have rogue things going on in my network.. I've used Spiceworks at my office but don't really know if there is something better for an Ubuntu server.. 

I guess my main thing is that I need something that will help me maintain and organize my network.. 

any suggestions would be greatly appreciated.. let me know if there is anything someone needs me to clarify.. I'll do it to the best of my ability

thanks
J

---

### Post by arrrghhh on 2012-05-21
No clue about trying to find "rogue things" in your network... If you mean virii/malware, then I would run something on the machines.

If you mean like someone trying to brute force into the box/your network, just make sure you don't open any ports you don't need (Ubuntu doesn't come with any open by default) and make sure you secure anything you do open.  IE don't use simple SSH passwords, disable SSH password auth completely (use keys), etc.

Most other "intrusion detection" systems are designed for enterprise networks.  Unless the server IS the router or internet gateway, I don't know what to tell ya.  If the server is the gateway, you have all sorts of options since all the internet traffic has to traverse the server ;).

As for file sharing, that is very simple.  Samba for Win machines, NFS for Linux.

---

### Post by volkswagner on 2012-05-21
You may be interested in researching packaged solutions like [Zentyal]("http://www.zentyal.com/"), or other non Ubuntu products like [ClearOS]("http://www.clearfoundation.com/Software/overview.html") (formerly ClarkConnect) or even[ Amahi ]("http://www.amahi.org/")Home Server.

---

### Post by jeremygotcher on 2012-05-22
yes when I was saying rogue things I was mainly referring to brute force attacks that have gotten through and people hacking my wireless.. 

thanks to both of you for the suggestions.. I check them out..

---

### Post by LHammonds on 2012-05-22
I would also suggest Zentyal.  You can quickly setup a file-sharing, print-serving and even username server with relative ease.  I am currently using their print server and it is rock solid.  I even have it setup where people on my Windows Active Directory network login and based on what security group they are in, they get printers installed to their local Windows PC...which is great for those that "float" around from PC to PC.

I have some unfinished notes about it [posted here]("http://forum.zentyal.org/index.php/topic,9472.0.html") but you can see the basics of how I setup mine.

LHammonds

---

