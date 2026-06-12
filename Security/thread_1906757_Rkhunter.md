---
title: "Rkhunter"
date: 2012-01-09
forum: Security
---

### Post by jpdeaton on 2012-01-09
I am almost positive my computer is being messed with by someone. I won't go into it but its been going on a while.    When I try to open /var/log/rkhunter.log after running rkhunter it says permission denied. What's up with that? When it was scanning in the terminal I got a warning next to:

[I]"checking for password file changes"
"checking for group file changes"
"checking for hidden files and directories"
[/I] 
 When i run tiger and try to open the folder /var/log/tiger it says:
* "the folder contents could not be displayed you do not have permission to view the contents of tiger" *

    This is all immediately after doing a clean install and installing the software I use. There is only one user, which is me. 

Can someone please give me some insight on what all this means and how to fix it? Also, how would I go about finding a hidden user, if there is one ?  Thanks

---

### Post by MadsRC on 2012-01-10
This is a long shot, but have you tried to open /var/log with root priviliges?

---

### Post by jpdeaton on 2012-01-10
I'm not sure how to do that. I'm pretty new to ubuntu.

Another problem I am having is setting up UFW. I run netstat -atlpvn to view the ports used. Theres only a handful of ports when firefox is closed, but when It's open theres like 10 for firefox and they change every time I load a page. How should I go about figuring out which ports to open?

Reloading firefox twice gave me ports 5493, 53866, 54433, 43226,
43229, 43227, 52856, 43231, 52856, 43231, 43230, 52855, 43235, 4323

---

### Post by Dangertux on 2012-01-10
> **jpdeaton said:**
> I'm not sure how to do that. I'm pretty new to ubuntu.

Another problem I am having is setting up UFW. I run netstat -atlpvn to view the ports used. Theres only a handful of ports when firefox is closed, but when It's open theres like 10 for firefox and they change every time I load a page. How should I go about figuring out which ports to open?

Reloading firefox twice gave me ports 5493, 53866, 54433, 43226,
43229, 43227, 52856, 43231, 52856, 43231, 43230, 52855, 43235, 4323


Alrighty, let's start at the beginning. I'm not sure why you think someone is messing with you, but I absolutely guarantee the two things you're observing here have nothing to do with that.

The first as someone else already stated is a normal behavior and you need to open those files with root privileges. An example would be.

```

sudo view /var/log/rkhunter.log

```

will open it with vi's view mode.  Alternatively for a more graphically intuitive way of viewing the file you can do

```

gksudo gedit /var/log/rkhunter.log

```

(or if you're using kubuntu)

```

kdesudo kwrite /var/log/rkhunter.log

```

Now on to this second question about netstat I'm assuming you're referring to something that might look a little bit like this

```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:7175          0.0.0.0:*               LISTEN      1141/postgres
tcp        0      0 192.168.0.4:42948       74.125.47.84:443        ESTABLISHED 1721/firefox
tcp        0      0 192.168.0.4:44853       74.125.47.120:443       ESTABLISHED 1721/firefox
tcp        0      0 192.168.0.4:35904       74.125.47.83:443        ESTABLISHED 1721/firefox
tcp        0      0 192.168.0.4:44854       74.125.47.120:443       ESTABLISHED 1721/firefox
tcp        1      0 192.168.0.4:43586       50.7.240.26:80          CLOSE_WAIT  1823/http
tcp        0      0 192.168.0.4:44851       74.125.47.120:443       ESTABLISHED 1721/firefox
tcp        0      0 127.0.0.1:7175          127.0.0.1:45234         ESTABLISHED 2305/postgres: msf3
tcp        0      0 192.168.0.4:34389       74.125.47.83:80         ESTABLISHED 1721/firefox
tcp        0      0 192.168.0.4:43596       74.125.47.18:80         ESTABLISHED 1721/firefox
tcp        0      0 127.0.0.1:7175          127.0.0.1:45233         ESTABLISHED 2278/postgres: msf3
tcp        0      0 192.168.0.4:44852       74.125.47.120:443       ESTABLISHED 1721/firefox
tcp        0      0 127.0.0.1:45233         127.0.0.1:7175          ESTABLISHED 2229/.ruby.bin
tcp        0      0 192.168.0.4:47142       74.125.47.100:443       ESTABLISHED 1721/firefox
tcp        0      0 127.0.0.1:45234         127.0.0.1:7175          ESTABLISHED 2229/.ruby.bin
tcp        0      0 192.168.0.4:43585       50.7.240.26:80          ESTABLISHED 1822/http
tcp        0      0 192.168.0.4:43557       192.168.0.2:22          ESTABLISHED 1972/ssh
tcp        0      0 192.168.0.4:44850       74.125.47.120:443       ESTABLISHED 1721/firefox
tcp6       0      0 ::1:7175                :::*                    LISTEN      1141/postgres

```

That being said, you need to understand how connections on the internet work. For instance when you visit a web page with Firefox this is what happens.

Your computer (firefox) sends an HTTP GET request to the server (we'll say ubuntuforums running on port 80) so the server has port 80 open, however in order for Firefox to send the GET request it must also create a socket on a port randomly specified from unassigned ports (usually in the 40,000s). Each time a new connection is made (you may have many connections for a single site, due to the way the hypertext transfer protocol works) a new socket will be created.

In short, everything you're seeing is normal.

---

### Post by jpdeaton on 2012-01-10
Thanks, the command line worked for rkhunter. How would I go about restricting outgoing ports (if possible) to allow only firefox? I'm kinda confused because I don't see how it's possible seeing firefox keeps using different ports.

---

### Post by Dangertux on 2012-01-10
> **jpdeaton said:**
> Thanks, the command line worked for rkhunter. How would I go about restricting outgoing ports (if possible) to allow only firefox? I'm kinda confused because I don't see how it's possible seeing firefox keeps using different ports.

iptables/netfilter (the firewall that comes with most linux distributions) does not really have a convention for limiting by application. Also since you pointed out it's almost impossible to define preset port by port rules for firefox, however you do have an option. In terms of iptables you could create a firewall something like this.

```

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -p tcp -m state --state NEW --dport 80 -j ACCEPT
iptables -A OUTPUT -p tcp -m state --state NEW --dport 443 -j ACCEPT
iptables -A OUTPUT -p tcp -m state --state NEW --dport 53 -j ACCEPT
iptables -A OUTPUT -p udp -m state --state  NEW --dport 53 -j ACCEPT

```What this is going to do is set all of our policies for inbound/outbound/forwarded traffic to drop packets. We are then going to set two ACCEPT rules for RELATED,ESTABLISHED connections. Then we're going to accept NEW connections outbound destined for port 80 (http) 443 (https) and 53 tcp and udp (DNS). What will happen is when you visit a site the port 80 connection will be allowed the subsequent connections made by firefox will be allowed because they are "RELATED". However if say gwibber attempts to connect to something on port 31337 it will not be allowed and it will be dropped because it is not related to the initial port 80 connection. 

For more on configuring a firewall in Ubuntu check out my thread here : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

Hope this helps.

---

### Post by jpdeaton on 2012-01-10
When I try to run iptables -P INPUT DROP i get this error, 

iptables v1.4.10: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

I tried sudo too and got the same thing. My kernel is 3.0.0.14 and I ran sudo apt-get update and sudo apt-get upgrade as an attempt to upgrade iptables. What gives?

---

### Post by Dangertux on 2012-01-10
> **jpdeaton said:**
> When I try to run iptables -P INPUT DROP i get this error, 

iptables v1.4.10: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.

I tried sudo too and got the same thing. My kernel is 3.0.0.14 and I ran sudo apt-get update and sudo apt-get upgrade as an attempt to upgrade iptables. What gives?

Should work fine with sudo.

However you need to understand that if you apply those rules in without any other firewall rules it will pretty much break everything. I was giving it as an example of how to control traffic better with iptables.

You really need to do some planning before you get into that type of firewall, like what ports are you actually making requests to, likely quite a few other than 443,80 and 53.

---

### Post by jpdeaton on 2012-01-10
okay, thanks

---

### Post by jpdeaton on 2012-01-11
Well, i know what ports I want to open up, but i've ran into a roadblock.. when i try this command, it tells me command not found (or something like that ) for NEW. I take the new out and it says I need to specify state.

---

### Post by Dangertux on 2012-01-11
Oh hey because it should look like this

```


iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT

```

Sorry for the typo

---

