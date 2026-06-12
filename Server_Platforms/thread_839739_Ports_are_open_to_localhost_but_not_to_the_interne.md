---
title: "Ports are open to localhost but not to the internet; help"
date: 2008-06-24
forum: Server Platforms
---

### Post by Blackie_Chan on 2008-06-24
Hi. 

I've installed Oracle XE on ubuntu server edition 8.04 (which is on my VMWare virtual machine). 

Now, I've having problems access certain port 8080. When I run 
```
user@ubuntu:/etc/network$ nmap -P0 localhost

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-24 17:41 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1711 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
1521/tcp open  oracle
8080/tcp open  http-proxy

Nmap done: 1 IP address (1 host up) scanned in 0.114 seconds

```
Then I run nmap (so that it goes over the web:
```
user@ubuntu:/etc/network$ nmap -P0 ubuntu

Starting Nmap 4.53 ( http://insecure.org ) at 2008-06-24 17:42 EDT
Interesting ports on ubuntu (127.0.1.1):
Not shown: 1712 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
1521/tcp open  oracle

Nmap done: 1 IP address (1 host up) scanned in 0.126 seconds

```

Notice that port 8080 is not accessible over the web. After googling I tried:
```
user@ubuntu: $ sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 8080 -j ACCEPT
``` 
Which lead me to
```
user@ubuntu:/etc/network$ sudo iptables -nL
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8080

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

How can I access port 8080 from over the web? How can I open the port?  Note, I run my web application on port 9001, but I stopped it, to do my tests.

---

### Post by Nythain on 2008-06-25
are you behind a router, if so, forward the port???

---

### Post by windependence on 2008-06-25
Go to [www.canyouseeme.org](www.canyouseeme.org) and test port 8080 from there to see if it is open. 

How were you testing the port "so that it goes ver the web"? If you were trying this from inside your network that will not work because your router is not going to send packets out that are just going to come back in, that's not how it works.

-Tim

---

### Post by Blackie_Chan on 2008-06-25
To clarify, My computer has Windows XP Pro (Host OS) on it. I then installed Ubuntu Linux(Guest OS) in VMWAre . My goal is run a web application in ubuntu, and be able to access it in from my browser in Windows XP. 

My problem is that when the web application is running in linux, I have to run firefox in linux to access it. When I try to access the application from a browser in Windows XP, it seems like it doesn't exist. 

Another thing that's odd. I have two users in linux, let's call them user1 and user2. I ran an old version of a web application as user1 on the same port, and the application is accessible outside of VMWare. When I run a newer version of the web application as user2 on the same port, it is not accessible from outside VMWare.

---

### Post by windependence on 2008-06-25
OK so let's say your XP machine has an IP of 192.168.0.2 and the Linux VM has an IP of 192.168.0.5

If you go to the XP box and type in [http://192.168.0.5:8080](http://192.168.0.5:8080), you can get to Oracle?

-Tim

---

### Post by Blackie_Chan on 2008-06-25
> **windependence said:**
> OK so let's say your XP machine has an IP of 192.168.0.2 and the Linux VM has an IP of 192.168.0.5

If you go to the XP box and type in [http://192.168.0.5:8080](http://192.168.0.5:8080), you can get to Oracle?

-Tim

No, I can not get to Oracle.

---

### Post by koenn on 2008-06-25
Oracle XE 's web interface by default only listens on localhost : port 8080 
You can only log on through from a browser on the local machine (or by setting up an ssh tunnel)

If you want it listening on any other interface than localhost, you have to configure it to do so. You can do that in the web interface itself.

---

### Post by Blackie_Chan on 2008-06-25
> **koenn said:**
> Oracle XE 's web interface by default only listens on localhost : port 8080 
You can only log on through from a browser on the local machine (or by setting up an ssh tunnel)

If you want it listening on any other interface than localhost, you have to configure it to do so. You can do that in the web interface itself.

Accessing oracle from outside of the VM wasn't my main problem, there's always a way around it. My main problem is that I can't access my application server (weblogic 9.2), the server is running on port 9001. How can I access it outside of the VM?

---

### Post by koenn on 2008-06-26
> **Blackie_Chan said:**
> Accessing oracle from outside of the VM wasn't my main problem, there's always a way around it. My main problem is that I can't access my application server (weblogic 9.2), the server is running on port 9001.
Funny, seeing that your OP is 40 lines describing a problem accessing port 8080 on an Oracle XE - where Oracle Application Expres (management interface /application dev tool) is running, 
and only has a cursory mentioning of a web application at port 9001

---

### Post by Blackie_Chan on 2008-06-26
> **koenn said:**
> Funny, seeing that your OP is 40 lines describing a problem accessing port 8080 on an Oracle XE - where Oracle Application Expres (management interface /application dev tool) is running, 
and only has a cursory mentioning of a web application at port 9001

Whether it's port 9001 or 8080, I need it to be accessible from outside of VMWare. I figure, if someone has a solution for port 8080, you'll be able to apply the same fix to access 9001. 

Also, I needed oracle running before I will be able to run my web application in weblogic. Can someone still help me with the problem?

---

### Post by koenn on 2008-06-27
> **Blackie_Chan said:**
> Whether it's port 9001 or 8080, I need it to be accessible from outside of VMWare.


If you've set up VMware server with bridged networking, the guest systems have IP addresses in your real LAN and are accessible from any LAN host, including the VM host system. In other words : on the network levels, vm guests behave exactly the same as physical computers. 

If you haven't enabled bridged networking, you have to enable it, or work out a networking solution with routing between your physical LAN and VM's virtual network(s).

> **Blackie_Chan said:**
> I figure, if someone has a solution for port 8080, you'll be able to apply the same fix to access 9001. 

Not necessarily. 
I gave you a solution for your port 8080 problem. Now you see how you can apply it to port 9001.

---

### Post by Blackie_Chan on 2008-06-29
I finally fixed the problem. Weblogic 9.2.2 only listens on localhost. I had to configure it to listen to the linux IP.

so I added the following to my weblogic start domain command:

```
-Dweblogic.ListenAddress=<Linux IP>
```

---

