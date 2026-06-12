---
title: "Webmin installed but not working"
date: 2009-06-01
forum: Server Platforms
---

### Post by svivian on 2009-06-01
I have a dedicated server running Ubuntu 8.10. I recently installed Webmin to assist with various admin. The install went fine, at the end it said "webmin is available at **[https://localhost.mydomain.co.uk:10000](https://localhost.mydomain.co.uk:10000)**" (with the actual domain where mydomain is - it was detected automatically since I didn't tell it my domain).

However, this URL doesn't work. I set up an A Record for locahost just in case. I also set up SSL in our other control panel and it seems to be working. I've tried using my site's IP address with :10000 on the end but still no luck.

Help!!

---

### Post by albinootje on 2009-06-01
> **svivian said:**
>  I've tried using my site's IP address with :10000 on the end but still no luck.


What happens when you do :
```

telnet your_server_ip 10000

```

And do you have port 10000 open on your server ?

---

### Post by svivian on 2009-06-01
With telnet I'm just getting a "Trying..." message and nothing else. I'm also getting timeouts with "ping [ip]".

I logged into the server with the SSH and if I do "wget https://localhost:10000" then I get the right login page, so Webmin must be installed correctly and working.

The domain itself is working and the main site is up and online...

---

### Post by albinootje on 2009-06-01
> **svivian said:**
> With telnet I'm just getting a "Trying..." message and nothing else. I'm also getting timeouts with "ping [ip]".

I logged into the server with the SSH and if I do "wget https://localhost:10000" then I get the right login page.

The domain itself is working and the main site is up and online...

Okay, But that still doesn't answer whether you or your ISP have firewalled port 10000. Are you using a firewall there ?

On a machine itself a firewall usually allows connections from and to localhost.

Here's a definition of "localhost" on computers :
[http://en.wikipedia.org/wiki/Localhost](http://en.wikipedia.org/wiki/Localhost)

---

### Post by svivian on 2009-06-01
I don't know if there is a firewall. However I just found this page on the webmin site: [http://www.webmin.com/firewall.html](http://www.webmin.com/firewall.html)

Unfortunately there is no file "/var/lib/iptables" on my server.

---

### Post by ghen on 2009-06-01
Alright, so you can SSH to the server so the connection is good. And you can run webmin locally to the server so webmin is installed correctly. The only thing that could be a problem is your browser, local security products (firewall, AV) not accepting the certificate, or the network blocking port 10000 somewhere between you and the server.

So what is the computer you are accessing from, what OS?

Are you on the same subnet as the server?

---

### Post by albinootje on 2009-06-01
> **svivian said:**
> I don't know if there is a firewall. 

Can you post the output of the following from your server :
```

sudo iptables -L -n

```

It should also be possible to run webmin on another port than port 10000.

---

### Post by svivian on 2009-06-01
No, the server is remote. I am trying both a Windows Vista laptop (using putty for SSH) and my home PC which is Ubuntu 9. My computers aren't blocking anything, and I can access webmin and port 10000 on another server fine (of the company I used to work for).

[This page]("http://www.debianadmin.com/webmin-installation-and-configuration-in-debian-and-ubuntu-linux.html") mentions editing a config file to allow access from the local network... the line mentioned isn't in my config file, what would I need to put to allow access from any computer?

---

### Post by svivian on 2009-06-01
Output of sudo iptables -L -n:

```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:22 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:443 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:53 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:53 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:69 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:69 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:25 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:110 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:143 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:123 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:20 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:21 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:3306 state NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:3306 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:5555 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:8002 state NEW
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:9001 state NEW
DROP       all  --  0.0.0.0/0            0.0.0.0/0

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state NEW,RELATED,ESTABLISHED
```

---

### Post by albinootje on 2009-06-01
> **svivian said:**
> 
[This page]("http://www.debianadmin.com/webmin-installation-and-configuration-in-debian-and-ubuntu-linux.html") mentions editing a config file to allow access from the local network... 

That would not give a time-out, but instead "block" you after trying to log into the webmin interface.

---

### Post by albinootje on 2009-06-01
Thanks for the iptables output.

Is this the default firewall that comes with that server ? I'm a bit surprised to see port 3306 open (Although Debian and Ubuntu run mysql on 127.0.0.1 only be default).

Can you find out where the iptables configuration is located ?
It would be handy to have iptables open up port 10000 too.

---

### Post by svivian on 2009-06-01
according to 'find', these are the only things matching iptgables:
/sbin/iptables   [binary file]
/lib/iptables   [folder]
/usr/share/doc/iptables   [folder]
/usr/share/webmin/blue-theme/iptables   [folder]

I just ran:
```
iptables -A INPUT -p tcp -m tcp --dport 10000 -j ACCEPT
```

and it seems to have opened the port (it's listed in the iptables command). Still no luck accessing from the web though.

---

### Post by albinootje on 2009-06-01
> **svivian said:**
> according to 'find', these are the only things matching iptgables:

Try : 
```

sudo grep -r -i iptables /etc/

```

And this is a Debian or Ubuntu server ?

---

### Post by svivian on 2009-06-02
It's a Ubuntu server. Here's the output from that command. Maybe I should be adding a line for port 10000 to /etc/rc.local ?

```
/etc/webmin/module.infos.cache:firewall longdesc=Configure a Linux firewall using iptables. Allows the editing of all tables, chains, rules and options.
grep: /etc/nologin: No such file or directory
/etc/apparmor/severity.db:/usr/lib/iptables/*   2 8 2
grep: /etc/fonts/conf.d/30-defoma.conf: No such file or directory
/etc/rc.local:/sbin/iptables --flush
/etc/rc.local:/sbin/iptables -A INPUT  -i lo -j ACCEPT
/etc/rc.local:/sbin/iptables -A OUTPUT -o lo -j ACCEPT
/etc/rc.local:/sbin/iptables --policy INPUT   DROP
/etc/rc.local:#/sbin/iptables --policy OUTPUT  DROP
/etc/rc.local:/sbin/iptables --policy FORWARD DROP
/etc/rc.local:/sbin/iptables -A INPUT  -m state --state ESTABLISHED,RELATED     -j ACCEPT
/etc/rc.local:/sbin/iptables -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 22 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 80  -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p udp --dport 69 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 69 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 25 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 110 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 143 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p udp --dport 123 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 20 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 21 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 3306 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p udp --dport 3306 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 5555 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 8002 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -p tcp --dport 9001 -m state --state NEW -j ACCEPT
/etc/rc.local:/sbin/iptables -A INPUT -j DROP
```

---

### Post by albinootje on 2009-06-02
> **svivian said:**
> It's a Ubuntu server. Here's the output from that command. Maybe I should be adding a line for port 10000 to /etc/rc.local ?


Yes, good idea.

---

### Post by svivian on 2009-06-02
Success!! I added a line to /etc/rc.local to open port 10000, rebooted and voila! Webmin is working.

Thanks for all your help, much appreciated. :)

---

