---
title: "ufw doesn't appear to be working"
date: 2009-07-10
forum: Security
---

### Post by timzak on 2009-07-10
I set up ufw through gufw for Enabled/Deny Incoming traffic.  No specific rules or exceptions, so I assume it should deny ALL incoming traffic.  However, I'm able to receive email, download from Transmission, download rss feeds and podcasts (Liferea and Gpodder).  Everything seems to be working.  Shouldn't none of these work if I have ufw set to deny all?

Here's the output of status:
```
tim@tim-desktop:~$ sudo ufw status
[sudo] password for tim: 
Status: active

```

---

### Post by lovinglinux on 2009-07-10
No. They work as expected, because the connection request is originated on your machine. Denying incoming traffic means blocking unsolicited incoming connection requests. When you browse a web site or check your mail box, the program you are using is sending connection requests to the remote server, so they are allowed, since they are outgoing connections. Once the connection is established, you can then receive data from the remote server and the firewall won't block them, because they were solicited by you.

Transmission also works because it tries to connect to remote peers all the time, so generating outgoing requests. What doesn't work is the incoming requests from remote users. This might slow your connection due to less peers successfully connecting to you, but you will still be able to connect to peers on your request.

GUFW does not provide a method (without editing files manually) of blocking outgoing connections.

---

### Post by timzak on 2009-07-10
Thanks, I guess I just wasn't thinking about the connection request originating on my machine.  So how can I verify that ufw is doing its job?  And why are there canned configurations in gufw for pop, imap and smtp if all of these are requests that originate from the host machine?  I guess you could use these to *block* such request from going out?

---

### Post by lovinglinux on 2009-07-11
> **timzak said:**
> So how can I verify that ufw is doing its job?  And why are there canned configurations in gufw for pop, imap and smtp if all of these are requests that originate from the host machine?  I guess you could use these to *block* such request from going out?

Open a port on your router, by forwarding it to your machine, then visit [http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm) to scan that port. If you receive a report saying that the port is "Stealth", then the firewall is working.

Please notice that if you don't forward the port on the router, the firewall scanner won't be able to pass through the router and won't reach your firewall. So the result will be also "Stealth", but it represent the status of the router, not your machine.

> **timzak said:**
> And why are there canned configurations in gufw for pop, imap and smtp if all of these are requests that originate from the host machine?

These configurations are for blocking incoming ports used by servers. For example, I have two computers on my network. My desktop and a notebook, which I need to maintain. So I have installed a ssh server on the notebook, so I can connect to it and perform administrative tasks remotely. The ssh server  accepts connections on port 22, but I don't want to let other people on the Internet trying to connect to it. So the firewall on the notebook has a rule to block incoming ssh connections (port 22) and allow only those coming from my IP. The connection leaves my computer using any port available, but it enters the notebook through port 22, which is basically the port blocked by the ssh canned configuration in the firewall.

Please notice that, if you don't run a server of any kind, then you actually don't even need a firewall, because all connections reaching your machine through any port will be ignored and there is no security risk. Nevertheless, Transmission for example is a server, since it accept remote connections. But that doesn't mean you should block incoming connections on the Transmission port, otherwise other peers won't be able to connect to you. So again, the firewall won't help you.

Firewall is useful when you want to allow limited access to a server port. For example the case I explained about the ssh, where I want to be able to connect to the notebook, but also to block all computers outside my local network.

> **timzak said:**
> I guess you could use these to *block* such request from going out?

No. Just incoming. There is no reason to block outgoing connections, which is something Windows users do to avoid all the ad-aware to phone home.

---

### Post by timzak on 2009-07-11
Thanks for the clear explanation.  I really appreciate it.

Would Samba be an example of a server setup?

If so, would setting a rule such as allow 192.168.1.0/24 be sufficient?

---

### Post by lovinglinux on 2009-07-11
> **timzak said:**
> Thanks for the clear explanation.  I really appreciate it.

You are welcome.

> **timzak said:**
> Would Samba be an example of a server setup?

Yes, exactly. Samba is an example of server. It accept connections from other machines so they can download and upload files.

> **timzak said:**
> If so, would setting a rule such as allow 192.168.1.0/24 be sufficient?

Yes. it should be sufficient.

---

### Post by SamikMTBSI on 2011-04-16
I know it is very, very unkosher to bump a thread this old, but I just wanted to give a =D> to Lovinglinux for by far the most understandable, succinct breakdown of the usefulness of a firewall on Ubuntu I have yet read (assuming it's accurate / up-to-date, anyway!).

Since the title of this thread isn't exactly what people would search for when asking the questions that ended up getting answered within, here's one little bump for posterity.  If one person gets their confusion settled more quickly than I did about this subject, it will have been worth it.

---

### Post by lovinglinux on 2011-04-16
> **SamikMTBSI said:**
> I know it is very, very unkosher to bump a thread this old, but I just wanted to give a =D> to Lovinglinux for by far the most understandable, succinct breakdown of the usefulness of a firewall on Ubuntu I have yet read (assuming it's accurate / up-to-date, anyway!).

Since the title of this thread isn't exactly what people would search for when asking the questions that ended up getting answered within, here's one little bump for posterity.  If one person gets their confusion settled more quickly than I did about this subject, it will have been worth it.

Kosher or not, I appreciate your comment. :-)

---

