---
title: "IP confusion (dumbo alert!)"
date: 2011-08-02
forum: Server Platforms
---

### Post by coldraven on 2011-08-02
OK I have set up a virtual server running Ubuntu 10.04 with apache2 and PHP5 and it is all working fine. Except when I have just visited my friend to show what a genius I am!
As usual, if you want to show off, it will all go wrong :)
So, my home setup is a laptop connected by wi-fi to my router.
I have a vague knowledge of DHCP.
At home if I want to connect to my virtual server I just open Firefox and go to [http://192.168.2.101/](http://192.168.2.101/)
Of course, at my friends house this didn't work. I presume that his router gave out a different IP address. For the life of me, I could not work out what this was..... 
As an experiment I tried this: With no network connection, go to [http://localhost/](http://localhost/) and still nothing.
I obviously need some guidance, please help :)

---

### Post by SoFl W on 2011-08-02
From the terminal on the server type "ifconfig" and it will tell you what IP address was assigned to the server.

---

### Post by gleemer on 2011-08-02
Or, most routers  will provide a list of their DHCP clients from which you should be able to figure out what address was assigned to your machine.

Regading [http://localhost](http://localhost) not working, have a look into /etc/hosts. There should be a line, probably the first line, that says "127.0.0.1   localhost". If not add it.

---

### Post by elliotbeken on 2011-08-02
This might not be a problem but have you forwarded the ports of the services such as port 80 to the IP of the virtual machine ?

---

### Post by coldraven on 2011-08-03
> **SoFl W said:**
> From the terminal on the server type "ifconfig" and it will tell you what IP address was assigned to the server.
After wasting ages try to get my friend to remember the wi-fi key I eventually just plugged into his router with a cable.
I tried typing "ifconfig" but it only seemed to return a MAC address and 127.0.0.1
> Or, most routers  will provide a list of their DHCP clients from which  you should be able to figure out what address was assigned to your  machine.
That was what I thought of afterwards!
> Regading [http://localhost]("http://localhost/")  not working, have a look into /etc/hosts. There should be a line,  probably the first line, that says "127.0.0.1   localhost". If not add  it. 	
I will check that later.
> This might not be a problem but have you forwarded the ports of the services such as port 80 to the IP of the virtual machine ? 	
I'm not to sure what you mean, I only know that it works perfectly when I am connected to my home router.

Thanks everybody for your ideas, I will do some experiments and let you know the results later. Cheers!

---

### Post by blind2314 on 2011-08-03
> **coldraven said:**
> After wasting ages try to get my friend to remember the wi-fi key I eventually just plugged into his router with a cable.
I tried typing "ifconfig" but it only seemed to return a MAC address and 127.0.0.1
 
That was what I thought of afterwards!
 
I will check that later.
 
I'm not to sure what you mean, I only know that it works perfectly when I am connected to my home router.
 
Thanks everybody for your ideas, I will do some experiments and let you know the results later. Cheers!
 
If you're not sure, that probably means no (in this case :D). You need to look into port forwarding, and forward the appropriate ports to your local IP at home.
 
Then, when at your friends house, you can connect using your home IP (not your local 192 IP that the router assigns, but the actual IP that your ISP gives you) and the request will be forwarded to your machine at home. Google is your friend here, there are a lot of good documents/resources on setting this up.

---

