---
title: "Server not working after Squid uninstall"
date: 2008-06-21
forum: Server Platforms
---

### Post by R.Bucky on 2008-06-21
Here is the deal. I host an Apache based web site using Ubuntu 7.04. I installed Squid using apt-get then decided against messing around with it. I uninstalled using apt-get purge and then autoremove/clean and then restarted Ubuntu. Now, my web site comes back with "Problem Loading Page." Using [http://localhost](http://localhost), I can access the site no problem.

Any ideas to what is amiss?

---

### Post by windependence on 2008-06-21
Check your Apache.conf file. The server is probably still listening on the proxy port.

-Tim

---

### Post by R.Bucky on 2008-06-21
The apache.conf and ports.conf are unchanged. No configuration entries are changed. The router looks fine too.

---

### Post by windependence on 2008-06-21
Have you restarted apache since you removed squid?

-Tim

---

### Post by R.Bucky on 2008-06-21
I have restarted the computer previously in addition to restarting apache just a moment ago. It truly is strange.

---

### Post by windependence on 2008-06-21
OK we'll go through some checks and get you going. You are on comcast?

Check to make sure you port is still open at [www.canyouseeme.org](www.canyouseeme.org).

Check to make sure apache is running:

sudo ps aux | grep httpd

Let me know the results. And to confirm, you can reach the site from another machine on your network or only from the machine itself?

-Tim

---

### Post by R.Bucky on 2008-06-21
The results from: sudo ps aux | grep httpd
mark      6719  0.0  0.0   5116   820 pts/0    S+   18:29   0:00 grep httpd

and

you were right. Port 80 is blocked? Weird. I cannot reach the pages from another machine, although it is on the same router as I.

Comcast indeed.

---

### Post by R.Bucky on 2008-06-21
I have checked my router and ports.conf to make sure that everything is open. I am thinking that squid messed with my iptables. Have not worked with iptables, but squid caused a similar problem in the past. I am stuck!

---

### Post by windependence on 2008-06-22
> **R.Bucky said:**
> The results from: sudo ps aux | grep httpd
mark      6719  0.0  0.0   5116   820 pts/0    S+   18:29   0:00 grep httpd

and

you were right. Port 80 is blocked? Weird. I cannot reach the pages from another machine, although it is on the same router as I.

Comcast indeed.

Apache is not started. The process you listed here is just your grep command.

-Tim

---

### Post by R.Bucky on 2008-06-22
I used terminal to start apache and it indicates that it is running. Here is the result:
* Starting web server apache2                                                  httpd (pid 6101) already running 
                                                                         [ OK ]

The results from sudo ps aux | grep httpd again:
mark      7497  0.0  0.0   5120   824 pts/0    S+   06:24   0:00 grep httpd

---

### Post by MartynA on 2008-06-22
Probably: ps aux | grep apache

Whats the output of:

sudo iptables --list

---

### Post by R.Bucky on 2008-06-22
The results from sudo iptables --list:
sudo iptables --list
[sudo] password for mark:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

Apache still shows up using ps -a as being active. I have double-checked the router without success. Everything looks fine to me. The linux gods are mad at me

---

### Post by R.Bucky on 2008-06-22
I am unfamiliar with Squid (which is why I uninstalled without using it). Does this program alter how the DNS are read? Pulling at strings here.

---

