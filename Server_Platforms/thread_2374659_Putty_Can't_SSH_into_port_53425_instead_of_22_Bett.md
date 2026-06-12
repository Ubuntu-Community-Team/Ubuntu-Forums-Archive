---
title: "Putty: Can't SSH into port 53425 instead of 22? Better Security?"
date: 2017-10-17
forum: Server Platforms
---

### Post by peppy3 on 2017-10-17
Greetings,

**Question 1:**
I am running a virtual test server in _Ubuntu 16.04_ for learning and practice purposes. I read in a book (Mastering Ubuntu Server) that it is best to edit "/etc/ssh/sshd_config" and change the port to something other than the default "22" (I chose 53425 as a random example). I went into Putty to login and changed the port to "53425". However, it doesn't login, and I do not have a firewall set up on my server yet (as far as I know). There is no "iptables" installed, so I'm not sure why Putty is not able to login using this specific port (timeout error when I try), and no other service is using that port. Any advice on how to login to the port, or is this simply a natural Ubuntu security measure?

[B]Question 2:
[/B]After reading through various forums trying to figure out the problem above, I came across an older post from a few years ago that claimed that changing the SSH port to a number above 1024, is actually unsecure due to it not being in the privileged ports range? Is this true? Should I just leave my SSH port to 22 , or just change it something like 72?

Thanks
Kind regards

---

### Post by wildmanne39 on 2017-10-17
*Thread moved to **Server Platforms for a more appropriate fit**.*

---

### Post by HermanAB on 2017-10-17
Did you restart sshd after changing the config file?

Usually what I do is add a second port without deleting port 22.  Restart sshd, make sure everything works, then remove port 22 and check again.  The problem is that after changing the port number, netfilter rules may block the new port so you may have to adjust the firewall rules also - if you have it enabled.

---

### Post by peppy3 on 2017-10-18
I followed the steps in the book and restarted sshd after saving the changes to the config file. I have practically a fresh install of Ubuntu, so as far as I know, there is no firewall installed at all. I'm not sure if there is a default firewall or not, but UFW is not installed.

If I wanted to use port 53425 for SSH, am I supposed to add it somewhere else besides the sshd_config file?

---

### Post by TheFu on 2017-10-18
The Linux kernel is where the firewall runs.  iptables, ufw and others are just interfaces into the firewall.  Linux isn't Windows.

Changing the default port on the server isn't something that I do.  I let the router perform port translation, so it listens on 53425/tcp and forwards to an internal LAN IP:22/tcp where the ssh server is listening.  This provides 2 different ports - 1 for internal use (the default) and one for external use over the internet.  

Is using a non-default port more secure?  Not really, but it does drastically reduce all the attempted connections, thus reducing log files and stupid attempts.

How to secure ssh: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

* Don't use passwords
* Do use ssh-keys (ssh-copy-id)
* Quickly block failed attempts. Don't let them hammer at a system for days
* Monitor the log files for hacking attempts.
* Do use different identities for different server connections
* Do use the ~/.ssh/config file.

---

### Post by LHammonds on 2017-10-18
I don't change the default ports on my server.  Instead, I use [firewall rules]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p458") to limit access to them completely.  Then I use [fail2ban to monitor the logs]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p533") and temp ban any IP attempting to hack the service.

LHammonds

---

### Post by SeijiSensei on 2017-10-18
> **peppy3 said:**
> After reading through various forums trying to figure out the problem above, I came across an older post from a few years ago that claimed that changing the SSH port to a number above 1024, is actually unsecure due to it not being in the privileged ports range? Is this true? Should I just leave my SSH port to 22 , or just change it something like 72?

The distinction between privileged and unprivileged ports has nothing to do with security.  It's convention that reserves the ports below 1024 for use only by processes running as the root user.  So ordinary users cannot start a web server on the designated port 80, or a mail server on port 25.  All users can bind processes to ports above 1024.  I suggest browsing the file /etc/services if you have never done so to see which services are bound to which ports.  Many services that are usually started by root also bind to high ports, like MySQL (3306) and PostgreSQL (5432), because these are not offering services defined as an Internet protocol like HTTP or SMTP via RFCs.

---

### Post by peppy3 on 2017-10-18
Thanks for all the responses, I greatly appreciate the help and useful links.

Unfortunately, I still cannot connect to a non-standard port (53425) from Putty. I have the firewall set up to accept this port. I even checked /var/log/auth.log and can confirm that "Server listening on 0.0.0.0 port 53425". I updated the port in Putty and it's just not working. It seems like it should be really simple, but it's not working.

---

### Post by TheFu on 2017-10-18
Troubleshooting ssh connections: [http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](http://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

---

### Post by SeijiSensei on 2017-10-19
Can you connect with "ssh -p 53425 localhost" on the machine running the SSH server?  What if you replace "localhost" with the external IP of the machine?

---

### Post by peppy3 on 2017-10-19
Thanks everyone for the solutions, I figured it out based on reading your links and advice.

---

