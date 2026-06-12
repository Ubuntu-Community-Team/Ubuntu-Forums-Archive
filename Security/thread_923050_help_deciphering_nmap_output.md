---
title: "help deciphering nmap output"
date: 2008-09-17
forum: Security
---

### Post by engineer85 on 2008-09-17
Hey guys,

I am pretty new to linux, and just discovered a new utility that seems pretty useful-nmap.  I ran nmap on my 2 computer home network, and realized I have 4 ports open: 22-ssh, 111-rpcbind, 631-ipp, 2049-nfs.

I have used ssh and nfs, but I always close the app after im done, by typing exit.  How do I actually close the ports after Im done, and open them again if I need them?  Specifically, with these 4 ports, do they even need to be closed?

Steve

by the way, what exactly is a "port"?

---

### Post by kevdog on 2008-09-18
If you are using the default installation of ubuntu -- all inbound ports are technically open, its just that nothing is listening on the port.  It sounds like you have installed some servers on your machine.  To technically close the port, you would use a firewall, however if you just stop the application listening on the port, it would accomplish the same effect.

Hmm, sorry to jump to conclusions, however we are talking about inbound ports with this example, and not outbound ports correct?

---

### Post by eentonig on 2008-09-18
> **kevdog said:**
> If you are using the default installation of ubuntu -- all inbound ports are technically open, its just that nothing is listening on the port.  It sounds like you have installed some servers on your machine.  To technically close the port, you would use a firewall, however if you just stop the application listening on the port, it would accomplish the same effect.

Hmm, sorry to jump to conclusions, however we are talking about inbound ports with this example, and not outbound ports correct?

They wouldn't show up in nmap if they weren't being used.

Some questions:

- Did you ssh from or to those host?
- How did you stop the application? Actually, in case of listening ports, we speak of servers or services.

A 'port' is a local address on your computer

---

### Post by panhandle on 2008-09-18
> Hmm, sorry to jump to conclusions, however we are talking about inbound ports with this example, and not outbound ports correct?

Exactly.

Compare the results from this link: [https://www.grc.com](https://www.grc.com) to your nmap output for informational purposes.

---

### Post by cariboo on 2008-09-18
The only way to close the ports is to shutdown the service, which defeats the purpose of having them running. If you are behind a router with an internal firewall and you don't have any ports forwarded then you have nothing to worry about. If you don't have a router, you should be running a firewall blocking ports 111 and 2049, port 631 is only accessable from the localhost, unless you changed the default configuration.

For a howto on the default firewall have a look here:

[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

Ufw is the command line interface to the default firewall, iptables. I just saw that is is a gui that will be available for ufw in the next release of Ubuntu, that is due for release at the end of October.

---

### Post by engineer85 on 2008-09-18
Thanks for the responses guys.  I am not sure if the output means that they are listening or incoming or outgoing, whatever nmap defaults to should be what is being displayed, since I haven't changed any of those config files.

As far as using ssh and nfs, yes I have used it on both machines, but I always close the service after Im done (by typing exit).  So I would have thought that would close those ports.

How do I stop and start services? Also, is is a problem that those ports are open, if they are only listening ports?

Thanks again,

Steve

---

### Post by cariboo on 2008-09-18
There two ways to stop a service. 

1. Go to System-->Adminisration-->Services and stop the service there

2. From terminal eg:

```
sudo /etc/init.d/<service> stop
```

where <service> is the service you want to form example ssh.

Jim

---

### Post by caljohnsmith on 2008-09-18
"nmap" is great for finding open ports of computers on the same LAN as you, but if you simply want to see what ports are open on your Ubuntu computer, you can just do:
```
sudo netstat -tlpu  
```
That's a lot quicker than a full nmap scan, but the nmap scan will give you more detailed results.

---

### Post by engineer85 on 2008-09-18
Interesting about how to stop those svcs. I didnt know that, thank you.  Also, is there anything wrong with stopping RPC portmapper?  Will stopping this cause my internet to stop working?

What is ssh doing using a port, if I'm not currently using it to remote login, or share files etc.?

---

### Post by kevdog on 2008-09-18
Are you sure you dont have a ssh server listening on port 22 for incoming connections?  The use of exit is only for the client based programs.  Ie ssh (the client) vs sshd (ssh daemon = server)

---

### Post by engineer85 on 2008-09-18
No, I am not entirely sure of that.  I didn't even know there was a difference.  

So if I use compy and type "ssh compx@hostname" to log into compx on hostname.  Then the client is compx, and the server compy?  

Oh boy, I guess Im just really confused about all this.  Is there a howto (basic) somewhere?

I guess youre saying that "listening" is not a bad thing, and should be allowed?

Thanks,
Steve

---

