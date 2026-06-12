---
title: "No ping, no ssh, no sftp, yes web access"
date: 2008-08-08
forum: Server Platforms
---

### Post by tekno1001 on 2008-08-08
I can access my apache server

[www.tylervitti.endofinternet.org](www.tylervitti.endofinternet.org)

but cannot ping (Request timed out), ssh (Network error: Connection timed out), or filezilla (Error: Connection timed out) remotely. However, I can ping, ssh, and sftp from the local network, using either tylervitti.endofinternet.org or the local ip.

My router is set to forward port 80 and 42 (re-configured ssh port) to the machines static ip. No firewall (server install).

What's going on, eh?

---

### Post by windependence on 2008-08-08
You probably have the router set to quench ping requests.

To check your port 42, from inside your network open up a browser and go to [www.canyouseeme.org](www.canyouseeme.org) and check if port 42 is open. Also make sure your ssh daemon is running on 42 (sudo /usr/sbin/sshd -p 42).

For filezilla, you will also have to forward whatever port it uses.

-Tim

---

### Post by a.thomas on 2008-08-08
I tried pinging you from my Windows server:
```
>ping www.tylervitti.endofinternet.org

Pinging tylervitti.endofinternet.org [64.160.116.29] with 32 bytes of data:

Reply from 64.160.116.29: bytes=32 time=102ms TTL=51
Reply from 64.160.116.29: bytes=32 time=116ms TTL=51
Reply from 64.160.116.29: bytes=32 time=104ms TTL=51
Reply from 64.160.116.29: bytes=32 time=105ms TTL=51

Ping statistics for 64.160.116.29:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 102ms, Maximum = 116ms, Average = 106ms
```

---

### Post by tekno1001 on 2008-08-08
@thomas:

How did you do that?! Is it possible that my work is blocking something? I doubt it... they don't even filter internet usage.

@windependence:

Thanks, I'll give that a try when I get home. Filezilla is set for sftp mode, so it should use port 42 as well. My router WAS set to quench ping by default, but I disabled it when an outside diagnostic site failed to ping me. It worked, and it seems that thomas is able to do it as well. Why can't I?

How do you like this? I tried pinging myself from a remote site, and I get:
```
PING tylervitti.endofinternet.org (64.160.116.29) from 208.65.90.64 : 56(84) bytes of data.
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=1 ttl=43 time=104 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=2 ttl=43 time=104 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=3 ttl=43 time=105 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=4 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=5 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=6 ttl=43 time=104 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=7 ttl=43 time=105 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=8 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=9 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=10 ttl=43 time=104 ms

--- tylervitti.endofinternet.org ping statistics ---
10 packets transmitted, 10 received, 0% loss, time 9016ms
rtt min/avg/max/mdev = 103.176/104.177/105.226/0.692 ms
Ping completed. 100%
```

---

### Post by MJN on 2008-08-08
Ping and SSH work from here too.

Mathew

---

### Post by tekno1001 on 2008-08-08
Alright, I've come to the conclusion that something must be blocking these activities from the side of my client. My work must have their network configured to only allow a few ports or something. 

How do I bypass this? I'm developing from work, and I need to access my file server from school. I'm sure school will have the same protection in place. I haven't gotten there yet, so I don't know for sure... :)

Is it possible to set ssh/sftp to port 80?

[EDIT]:Okay, so obviously its possible. Revise: Is it advisable, and will it solve the problem?

---

### Post by MJN on 2008-08-08
> **tekno1001 said:**
> Revise: Is it advisable, and will it solve the problem?

That depends.

You really need to discuss it with work as, chances are, their filtering is not done to merely annoy you but as a result of their security policy which presumably you've signed up to.

Should you still wish to bypass it then your success will depend on how they filtering. If it is nothing more than bog-standard port filtering then, yes, you could move SSH to a port they allow through. If they perform anything more advanced like deep packet inspection or proxying then you will unlikely have any joy.

Mathew

---

### Post by windependence on 2008-08-08
> **tekno1001 said:**
> @thomas:

How did you do that?! Is it possible that my work is blocking something? I doubt it... they don't even filter internet usage.

@windependence:

Thanks, I'll give that a try when I get home. Filezilla is set for sftp mode, so it should use port 42 as well. My router WAS set to quench ping by default, but I disabled it when an outside diagnostic site failed to ping me. It worked, and it seems that thomas is able to do it as well. Why can't I?

How do you like this? I tried pinging myself from a remote site, and I get:
```
PING tylervitti.endofinternet.org (64.160.116.29) from 208.65.90.64 : 56(84) bytes of data.
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=1 ttl=43 time=104 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=2 ttl=43 time=104 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=3 ttl=43 time=105 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=4 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=5 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=6 ttl=43 time=104 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=7 ttl=43 time=105 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=8 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=9 ttl=43 time=103 ms
64 bytes from adsl-64-160-116-29.dsl.scrm01.pacbell.net (64.160.116.29): icmp_seq=10 ttl=43 time=104 ms

--- tylervitti.endofinternet.org ping statistics ---
10 packets transmitted, 10 received, 0% loss, time 9016ms
rtt min/avg/max/mdev = 103.176/104.177/105.226/0.692 ms
Ping completed. 100%
```

That looks like a good ping to me. So it's working for you?

Like MJN said you may be violating company policy but when I ssh from work I have a daemon running on port 443 and that is the only way I can get through their firewall, but it works fine. Most companies won't block that port because it's pretty much essential.

-Tim

---

### Post by tekno1001 on 2008-08-12
Ah! I figured it out. My company does in fact block all traffic except for web browsing. However, they provide proxies (so no, it's not a violation :) ). All I had to do was find the address and configure putty.

So now I'm in. But now I have a new question.

I can't seem to get RSA keys to work, no matter how hard I try. Here's what I've done:

1) Run puttygen to produce a public and private 1024 RSA key
2) Passphrase the private key and save it to my hard drive
3) SSH onto my server and append the public key to: /home/user/.ssh/id_rsa.pub and /home/user/.ssh/authorized_keys
4) Chmod .ssh to 700 and authorized_keys to 600
5) Enable RSA key login in /etc/ssh/sshd_config
6) Instruct putty to use the private key to authorize
7) Logon

But I keep getting "Server refused our key" from both work and home. I have repeated this process several times per several online manuals, and to no avail. I've even tried generating the keys on the server. What's the deal? ](*,)

---

