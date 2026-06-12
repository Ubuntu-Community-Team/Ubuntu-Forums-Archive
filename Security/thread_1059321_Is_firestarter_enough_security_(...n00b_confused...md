---
title: "Is firestarter enough security? (...n00b confused...)"
date: 2009-02-03
forum: Security
---

### Post by listerdl on 2009-02-03
hi - as far as i understand - linux is basically safe from viruses, or am i wrong? I have installed the firestarter firewall from the add/remove programs - will that suffice or should i be doing something else to protect my laptop?

Thanks - Lister

---

### Post by listerdl on 2009-02-03
In fact, i basically answered myself...the question i asked cant be answered v simply. I will do more research!!

---

### Post by ikt on 2009-02-03
There's never enough security until one is able to browse the web without running random unchecked binaries.

This is something a majority of windows users cannot do, and there's nothing to suggest it won't affect linux users.

---

### Post by amauk on 2009-02-03
No wild viruses exist for linux
the only viruses that do exist are "proof of concept" viruses

Linux has a firewall built-in, it's called IPtables
firestarter, ufw, etc. are just front-ends to IPtables

Firewalls are designed to allow selective incoming communication
If you run any servers (apache web server, ssh server, ftp, etc.) then without a "firewall", it's all or nothing
either everybody can connect, or nobody
a firewall allows you to be more selective
accept /reject incoming connections from certain IPs, etc.

If you don't run any daemons, you do not need to worry about firewalls, Linux blocks all incoming ports by default

---

### Post by ikt on 2009-02-03
> **amauk said:**
> No wild viruses exist for linux
the only viruses that do exist are "proof of concept" viruses

There are no viruses except there are plenty of trojans.

Still need to be careful of random downloads.

---

### Post by cariboo on 2009-02-03
Please provide links to these trojans in the wild. The biggest security problem is the user. Nothing can run system wide unless the user installs it as root.

Jim

---

### Post by hyper_ch on 2009-02-04
generally not messing around with iptables is the best thing to do.

---

### Post by handydan918 on 2009-02-04
> **ikt said:**
> There are no viruses except there are plenty of trojans.

Still need to be careful of random downloads.

For that matter, how about a link to ANYTHING dangerous to a Linux system. 

Not holding my breath....

:p

---

### Post by ikt on 2009-02-05
> **cariboo907 said:**
> The biggest security problem is the user.

...

that's exactly what I said.


> Still need to be careful of random downloads. 

Here's a list of some malware:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by handydan918 on 2009-02-05
Thanks for the list. It shows that the only people concerned about this are trying to sell linux AV programs. 
Still no links to the actual "malware"?

---

### Post by listerdl on 2009-02-05
amauk mentioned that you are safe as long as you "don't run any daemons"

Can you expand on this?

---

### Post by amauk on 2009-02-05
You're pretty damn safe no matter what you do

In order for someone to connect to your machine from the outside, you need 2 things
1) a program running on your machine to accept any communication on a specific port
2) the port needs to be opened

If both of these are true, then communication can happen

- Ubuntu, by default, doesn't have any programs listening to incoming communications
- Ubuntu, by default, doesn't have any ports open


examples of programs that accept incoming communication are:
Apache web server
proftp FTP server
OpenSSH server
etc.

Server software that runs in the background
(often called daemons)

If you install any daemons, then these programs will listen for connections on their default port numbers.
Also, during installation, the specific ports will also be opened

This is not a bad thing
but it does mean anyone can connect to your machine

example:
- Install Apache
- port 80 is opened
- Apache listens on port 80
- anyone who cares to try will be able to connect to your machine via a browser and view any pages your web server is hosting

This is exactly what you want if you are wanting to host a website from your local machine
But you probably want a little more control over who can FTP or SSH into your machine

a firewall allows finer tuning of who can connect to your machine

---

### Post by jerome1232 on 2009-02-05
> **handydan918 said:**
> Thanks for the list. It shows that the only people concerned about this are trying to sell linux AV programs. 
Still no links to the actual "malware"?

by trojan I mean any program disguised as a beneficial or wanted program but actually does something else malicious. Hopefully I have my definition right.

I'm sure even I can pick enough python up to code a trojan that delete's a user's home directory or something else similar, then package at as a .deb, the problem will be to trick more than 2 people into downloading and "installing" it.

I don't think any system can protect against trojans due to social engineering. That's where the user part comes in.

---

### Post by Koori23 on 2009-02-05
I ran netstat -tunlp to show what's running on my system at the present time.


-CUPS (Linux Print Server) is the only thing that's listening.. And that's not even connecting to the outside world.

-avahi-daemon is multicast-DNS which I can probably get rid of. Avahi is a daemon whose rights are "nobody". 

-dhclient I'm assuming is running because I need to fetch DHCP info from my router.

Ufw (Similar to Firestarter) is running and as you can see, I'm online.

That's the servers that are running locally on my system.

The second photo is of my nmap scan. I'm still online but no ports are open to the outside world. My firewall has rejected all requests.

---

### Post by ikt on 2009-02-09
> **jerome1232 said:**
> I don't think any system can protect against trojans due to social engineering. That's where the user part comes in.

Exactly.

---

