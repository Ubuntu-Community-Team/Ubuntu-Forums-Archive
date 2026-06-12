---
title: "apache:localhost access but not from LAN"
date: 2008-11-10
forum: Server Platforms
---

### Post by butteryak on 2008-11-10
Ok, 
  so I'm perplexed.  I"m switching over from windows apache to a linux server.  Installed LAMP.  Can access the index page from localhost.  but from anywhere else on the network, it's a no go.   I can ping port 80 on the linux/apache, but it simply refuses to serve up a page, except from localhost.   I've chmod  777 permissions on the www and var, and index, still I get nada.   There is no firewall, and I know the local LAN is ok, as I had a XP apache setup yesterday on that same IP.  Hmmmmm, any ideas as to what I should be looking at?  

Thanks guys

---

### Post by rustutzman on 2008-11-10
How are you trying to access the page? By IP? hostname?

Russ

---

### Post by butteryak on 2008-11-10
I'm trying to access it by IP, but I also tried hostname.
I can access it on the machine, with localhost  127.0.0.1 and by it's own IP address.  but from nowhere else on the LAN,  it's bizarre, as I can ping port 80 on it's IP (192.168.1.17) from another machine.

---

### Post by rustutzman on 2008-11-10
Hmmm.... by IP should work out of the box. Host name won't work without local dns or having your hosts file setup right. Can you ping that IP from the machine itself? If you put that IP in your browser on that machine does it bring up your It Works! page?

Russ

---

### Post by butteryak on 2008-11-11
yeah, I can ping from the machine itself, as well as from another machine. (192.168.1.17 port 80)  a port scan to Localhost shows port 80 open.   
also if I put the IP in the browser on the machine itself, it will bring up the index page.      I would assume. that it should simply just work OofTB.  It's really quite odd.

mysql, php, phpmyadmin, all work properly(from localhost) but from nowhere else on the LAN.    :confused:

---

### Post by Philio on 2008-11-11
By default Apache listens on all IPs, you can check /etc/apache2/ports.conf to make sure.

---

### Post by butteryak on 2008-11-11
It's listening on 0.0.0.0 80, so I assume that means all IP's

---

### Post by rustutzman on 2008-11-11
Are /etc/hosts.allow and /etc/hosts.deny basically empty? They should be but just checking.

---

### Post by Philio on 2008-11-11
> **butteryak said:**
> It's listening on 0.0.0.0 80, so I assume that means all IP's
Yep that should be fine, I just have Listen 80 in mine but 0.0.0.0 means exactly the same thing.

---

### Post by butteryak on 2008-11-11
I"m acctually away from the machine right now.  but interestingly enough, my ping to that machine from other machines on the network doesnt respond. turns out my ping to port 80 on that machine actually returns some address in the 208.x.x.x range?  huh, hadnt noticed that earlier. running a port scan to the ubuntu machine also comes back with nill.  Now, being a noob and all when it comes to ubuntu,  As far as I know, and have read, ubuntu doesnt install a firewall by default.  unless I'm mistaken?  And I assume that since apache is listening on 80, that any requests on 80, should "open" and allow traffic.   Unless I'm completely mistaken on all this.   Is there anywhere else I should be looking on ubuntu itself that is blocking ports?:confused:  

I'm done for tonight, thanks for the help so far guys, I'm sure it's somthing silly and well, you know, somthing that I'll say, "oh duh". about later.

---

### Post by butteryak on 2008-11-11
So as I lie awake in the wee hours.  It occurred to me that this machine has two NIC adapters installed.  What if apache was only serving up on one, and not the other.   which apparently that was the case.   makes no sense to me.  but I'm gonna look into it further.   Anyway, it works.   

Thanks for the support and input guys, much appreciated.

---

