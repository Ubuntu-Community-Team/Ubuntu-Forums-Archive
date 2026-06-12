---
title: "Server FTP Networking issue"
date: 2010-09-26
forum: Server Platforms
---

### Post by guessswh0 on 2010-09-26
Hello everyone,

This is a networking issue I am having, and didn't know if there is a specific type of hardware I need (specific router), or if there is a way to configure the server to fix this.

I am running the server on my local network, so it is receiving a private IP address (192.168.1.x).  However, I want people to be able to hit the server from the outside.  I already have a domain, and I have a static IP address.  I've already set it all up for the domain to resolve to my IP address.  I have all the port forwarding setup on my router already.

When accessing the server from the outside using a browser, it'll display everything perfectly.  My issue is when FTPing into the server.  When I ftp, it resolves to the servers public IP, gets passed to my router through port forwarding.  However, when the server responds during the handshake, it responds with its private IP address (since that is what is connected to and gets [responds with its 192.168.1.x address]).  When that is sent back to the client, the whole handshake fails since it sends the client its private IP versus its public.

How can this be fixed?  I wouldn't think I can set my public IP address as its static IP address, and then set the gateway as the internal private IP of the router.  How do I do this so it would work?

---

### Post by windependence on 2010-09-26
Try putting an entry in your hosts file with your public address listed instead of your internal one. Tghe file should be /etc/hosts and you entry should look like this:
 
```
 
111.222.111.222 server.yourdomain.tld

``` 
where 111.222.111.222 is your public IP address.
 
 
A better solution would be not to use FTP at all and use something like WinSCP to transfer your files. Much safer and secure.
 
-Tim

---

### Post by guessswh0 on 2010-09-26
ok, that makes sense.  I can give that a shot.  Question though, if my domain is ets say, sportstalk.com  what would that look like in the hosts entry?

111.222.111.222  sportstalk.com

Would that be it?

And other question, why would the server still respond with that public IP?  It wouldn't know to check the hosts file to see if there is an IP that matches a domain, because wouldn't the server just respond with its own IP address, and not lookup a domain?

---

### Post by windependence on 2010-09-26
What is the output of the hostname command?
 
-Tim

---

### Post by guessswh0 on 2010-09-26
EMS


That is the output.

So would it be...

111.222.111.222 EMS

that in the hosts file?

---

### Post by Fafler on 2010-09-26
Port forwarding using FTP is a bit more complicated, because it uses two connections. One for control, initiated by the client and one for data, initiated by the server afterwards.

There are several ways to overcome this. Some routers take care of this transparently, some does not. Some clients use passive mode to transfer data over the control connection.

Try looking in your routers setup for a option to take care of FTP connections. Or set your client to use passive mode.

---

### Post by guessswh0 on 2010-09-26
I've tried both active and passive transfer modes.  I am using filezilla.

Also, I have a FIOS router that I have to use.  But specifically within the port forwarding section, it lets me choose protocols to forward, and I do have FTP specified.

This is what I am getting (the last part is the only part really needed).

Response:    200 OK, UTF-8 enabled
Status:    Connected
Status:    Retrieving directory listing...
Command:    PWD
Response:    257 "/" is your current location
Command:    TYPE I
Response:    200 TYPE is now 8-bit binary
Command:    PASV
Response:    227 Entering Passive Mode (192,168,1,180,235,111)
Status:    Server sent passive reply with unroutable address. Passive mode failed.
Error:    Failed to retrieve directory listing


So, I want to think it is more of a server issue.  It is sending its private IP back during the handshake, not its public IP.  I went into the hosts file, and I updated localhost and the other one listed to the public IP, even rebooted the server, but still no change.  It continues to send its private address.

---

### Post by guessswh0 on 2010-09-26
As an update

I am able to SFTP into the server no problem.  But that obviously uses SSH.  I am wanting FTP as if I host for friends/family/others, ftp would be easier for them to use.  Also, just because I want to solve this issue.

So SFTP works, but ftp is a no go...

---

### Post by windependence on 2010-09-26
You (and they) should be able to use sftp on most ftp clients out there including FileZilla, and it's much better to do that anyway.
 
-Tim

---

### Post by guessswh0 on 2010-09-26
true, and I do plan on using sftp, but the concept bothers me.  Plus sftp has a lot of overhead for slow transfers (for many files/large files).  If need be, I would like to be able to use ftp...

---

### Post by windependence on 2010-09-26
There should be little if any difference in speed for sftp vs ftp. I would be more concerned with the security (or lack of) in ftp rather than the perceived overhead (you won't notice the difference).
 
-Tim

---

### Post by SeijiSensei on 2010-09-26
It sounds to me like your router doesn't know how to handle FTP sessions.  In the iptables firewall that runs on Linux there are special helpers that fix problems like sending back the wrong IP address in passive mode.  I'd take a look at your router settings again and see if there's something special you can configure to handle FTP correctly.

[http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html#PASVNATProblems](http://www.ncftp.com/ncftpd/doc/misc/ftp_and_firewalls.html#PASVNATProblems)

---

