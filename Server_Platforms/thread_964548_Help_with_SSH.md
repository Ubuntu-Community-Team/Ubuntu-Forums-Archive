---
title: "Help with SSH"
date: 2008-10-31
forum: Server Platforms
---

### Post by y3llow on 2008-10-31
Hi Everyone, im trying to setup ssh on my desktop at home so that i can connect to it from work.  So far I have the port forwarding setup on port 22 and ssh works when I am at home connecting to the private IP.  I searched the forum and most people get it to work at this point but mine doesnt =\ any suggestions???

---

### Post by manpaz on 2008-10-31
You need to install the openssh server on your desktop, and then enable it.

```

# apt-get install openssh-server
# /etc/init.d/ssh start

```

   Thanks,

---

### Post by y3llow on 2008-10-31
Oh wow... well I just tried it and I got this error. "ssh: connect to host start port 22: connection timed out"  I then used nmap to check the ports and it shows 22 being open.  Are there any other reasons why it may of timed out?

---

### Post by manpaz on 2008-10-31
Please, ensure you have enabled your network, to make sure you are connected
```
/etc/init.d/networking restart
```
You will see the OK messages on each interface.

Then check if you are going out to the internet 
```
host ubuntuforums.org
```
You will see the ip associated.

If all is running good, check your router at home, since you are telling that you want to connect from work to home, you need to make sure that your router is forwarding port 22 to your desktop.

   Thanks

---

### Post by y3llow on 2008-10-31
OK I figured it out.... turns out I had installed a program long ago which automatically made some changes on the firewall one of which was port forwarding of port 22 to a different IP.  I am still a little surprised the router didnt prevent me from adding the server.  Thanks for all your help!

---

### Post by pogztimz on 2008-10-31
i have the same problem.. i want to connect my computer at work when i am at home here is the result when i used nmap to view the ports open.
```
Not shown: 1695 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
110/tcp  open  pop3
137/tcp  open  netbios-ns
138/tcp  open  netbios-dgm
139/tcp  open  netbios-ssn
143/tcp  open  imap
389/tcp  open  ldap
443/tcp  open  https
445/tcp  open  microsoft-ds
631/tcp  open  ipp
953/tcp  open  rndc
993/tcp  open  imaps
995/tcp  open  pop3s
3128/tcp open  squid-http
3306/tcp open  mysql
5432/tcp open  postgres

Nmap done: 1 IP address (1 host up) scanned in 0.750 seconds

```

now i want help how to configure my router to point at port 22 so i can ssh at home.?? ty in advance!

---

### Post by y3llow on 2008-10-31
Your going to need to do some port forwarding for 22 or any other port you plan on using.  Since each router is different I recommend [http://portforward.com/routers.htm](http://portforward.com/routers.htm)  hope this helps

---

### Post by Titan8990 on 2008-10-31
Also, many ISPs block port 22 so that you can't have a ssh server.

---

### Post by y3llow on 2008-10-31
Even if the isp blocks 22 cant you change the ip your connecting to?  For instance port forward 55 to the server and connect with port 55 as well.

---

