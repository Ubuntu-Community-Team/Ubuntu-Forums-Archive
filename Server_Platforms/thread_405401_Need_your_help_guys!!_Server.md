---
title: "Need your help guys!! Server"
date: 2007-04-09
forum: Server Platforms
---

### Post by ade234uk on 2007-04-09
Our dedicated server is still running.
Ftp is still running I can access view the files through my ftp client
MySQL is still running, I backed up the database 15 minutes ago through PUTTY.

When I ping [www.domainname.co.uk](www.domainname.co.uk) success SENT 4 PACKETS RECEIVED 4 PACKETS
When I ping ns1.domainame.co.uk success SENT 4 PACKETS RECEIVED 4 PACKETS

All the ip addreses are correct.

Except when I enter our domain name the site is not coming up whatsover. It just keeps loading.
Is there something up with our hosts DNS or something like that?

What pisses me off even more is that they state that they have skilled army of engineers around the clock to sort out your problems 24 hours a day. When I telephone them know one picks up.

---

### Post by mssever on 2007-04-10
Are you having trouble reaching your web site, then? (A domain name can be used for many different services.) When I'm troubleshooting such an issue, I usually use telnet so that I can see the exact traffic. Try something like this:

```
telnet www.blah.com 80
``` where 80 is the port number (80 is the default). Once a connection has been established--if the server is responding--type
```
HEAD / HTTP/1.1
Host: www.blah.com

```Add an extra blank line at the end, and the server should spit out 
the headers for the URL /. Replace HEAD with GET to see the entire output. Note that editing what you type is impossible. If you make a single typo, you have to start over from the beginning.

---

### Post by ade234uk on 2007-04-12
Strange. I rebotted the server and the site came back up. For the life of me I dont know why it ended up doing what it did.

Like I said everything was running, server was alive. 
pinged the domain name came back with the ip
pinged the nameserver came back with the ip

This told me that the domain name was OK. I then started wondering if it had something to with our hosts.

When you entered the domain name the browser would try to load the site blank page, eventually timing out.

All working now...

---

### Post by mssever on 2007-04-13
For future reference, the telnet method I mentioned is extremely useful for debugging such problems, because if you can ping the server, and resolve the domain name, but not telnet to port 80, then you know that the problem is in your web server.

---

### Post by MilesZS on 2007-04-13
> **ade234uk said:**
> Strange. I rebotted the server and the site came back up. For the life of me I dont know why it ended up doing what it did.

Like I said everything was running, server was alive. 
pinged the domain name came back with the ip
pinged the nameserver came back with the ip

This told me that the domain name was OK. I then started wondering if it had something to with our hosts.

When you entered the domain name the browser would try to load the site blank page, eventually timing out.

All working now...

It sounds like it was a problem with Apache.  Either Apache had actually stopped running, or some other such nonsense (read: or something else that I probably can't explain without sounding like an idiot).  It happens, honestly.

Next time, depending on how you installed Apache, or what version you are running, you can probably run something like 'sudo /etc/init.d/apache2 restart' and it'll come back.

---

