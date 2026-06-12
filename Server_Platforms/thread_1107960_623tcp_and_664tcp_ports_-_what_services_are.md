---
title: "623/tcp and 664/tcp ports - what services are?"
date: 2009-03-27
forum: Server Platforms
---

### Post by Windows_ on 2009-03-27
Hello!

I've scaned my server by nmap and get this incident:

623/tcp filtered unknown
664/tcp filtered unknown

Coud anybody tell me - what services are on the ports 623 and 664?

---

### Post by Akita on 2009-03-27
From the horse's mouth @ [http://www.iana.org/assignments/port-numbers:](http://www.iana.org/assignments/port-numbers:)

oob-ws-http	623/tcp    DMTF out-of-band web services management protocol

oob-ws-https	664/tcp    DMTF out-of-band secure web services management protocol

---

### Post by Windows_ on 2009-03-27
> **Akita said:**
> From the horse's mouth @ [http://www.iana.org/assignments/port-numbers:](http://www.iana.org/assignments/port-numbers:)

oob-ws-http	623/tcp    DMTF out-of-band web services management protocol

oob-ws-https	664/tcp    DMTF out-of-band secure web services management protocol

OK, thank you! 

Hmm, are these services necessary? Can I uninstall it?

---

### Post by Windows_ on 2009-03-27
If anybody it is interesting, look here - [http://www.auditmypc.com/port/tcp-port-623.asp](http://www.auditmypc.com/port/tcp-port-623.asp)

But I don't understand - is this necesary service?

---

### Post by cdenley on 2009-03-27
Are you scanning your ubuntu computer, or your router? Post this output to see what TCP listeners you have on your computer.
```

sudo netstat -tlnp

```
However, I believe "filtered" means there was no server that responded, but some device rejected the connection instead of simply ignoring it. This is the default response for any connection attempt which actually reaches an ubuntu system. Typically, users are behind NAT routers, so connection attempts don't reach their system unless it is "port forwarded" in the router.
```

man nmap

```

---

### Post by Windows_ on 2009-03-27
> **cdenley said:**
> Are you scanning your ubuntu computer, or your router? Post this output to see what TCP listeners you have on your computer.
```

sudo netstat -tlnp

```


Thank you for your reply. This is output

```
root@server:~# netstat -tlnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      2033/sshd       
tcp6       0      0 :::22                   :::*                    LISTEN      2033/sshd   
```

And nothing else...

---

### Post by cdenley on 2009-03-27
The only listening process you have running is ssh. You have no service listening on either of the ports you have mentioned.

---

### Post by Windows_ on 2009-03-27
> **cdenley said:**
> The only listening process you have running is ssh. You have no service listening on either of the ports you have mentioned.
I know it, but I want to disalbe 623/tcp and 664/tcp services because I don't know about it at all. And I don't know how can I make it and will be it safely for working server...

---

### Post by cdenley on 2009-03-27
> **Windows_ said:**
> I know it, but I want to disalbe 623/tcp and 664/tcp services because I don't know about it at all. And I don't know how can I make it and will be it safely for working server...

As I already said, you have no such services.

---

### Post by Windows_ on 2009-03-27
> **cdenley said:**
> As I already said, you have no such services.
Ok, it seems I understand you. Thanks :)

---

### Post by Windows_ on 2009-03-29
**cdenley**, read this:

[INDENT]I have a friend that had a really weird problem with a program that used RPC. Every once and a while the program that used RPC would open a port and tell the client to contact on the port it just opened. The client would try to do that and fail. Problem was this only happened randomly. Random problems are a pain to track down. The problem was eventually tracked down. The following is a description of what it was and the fix for it.

RPC uses a range of ports on Linux to allow clients to contact the server. By default these are 650-1023. RPC will pick a port at random from the range of ports. That is as long as port in the range is not already being used. Their servers have built in Baseband Management Controllers (BMC). BMC communicates with a BMC management utility (BMU) on a remote client using IPMI protocols. The BMC for the servers are in band and use the network controller on the motherboard to send and recieve data. **The ports the BMC uses are 623 and 664**. The thing is the controllers don't run any software in Linux to do this. So how do they work you ask? Well, they intercept the traffic on those ports before it gets into the OS's network stack. That means any data you send to those ports on those machines the OS will never see. You won't see it on any network sniffer on that machine at all. So any machine that RPC told to connect to it on 664 was failing. But it was random because that port would only come up from the pool of ports randomly. [url]("http://www.pantz.org/hardware/ipmi/ipmiconflictwithrpc.html")[/INDENT]

**Are there any ideas**? May be it is BMC?

---

### Post by cdenley on 2009-03-29
> **Windows_ said:**
> **Are there any ideas**? May be it is BMC?

Sounds like that is what the ports are related to, but you never indicated whether you are scanning your router or your computer. Also, what is the problem? Why are you concerned with ports which are "filtered"?

---

### Post by Windows_ on 2009-03-29
> **cdenley said:**
> Sounds like that is what the ports are related to, but you never indicated whether you are scanning your router or your computer. Also, what is the problem? Why are you concerned with ports which are "filtered"?
I'm afraid to get breach in the server via these ports. And I don't know is there BMC or smb installed backdoor.

---

### Post by cdenley on 2009-03-29
> **Windows_ said:**
> I'm afraid to get breach in the server via these ports. And I don't know is there BMC or smb installed backdoor.

If the ports are filtered, then how is a breach or backdoor possible?

---

