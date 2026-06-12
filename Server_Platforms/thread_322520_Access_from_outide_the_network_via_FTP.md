---
title: "Access from outide the network via FTP"
date: 2006-12-20
forum: Server Platforms
---

### Post by Tipo on 2006-12-20
Okay, I want to be able to connect to my Ubuntu box from school via FTP....

I've configured FTP so I can access from all the computers on my home network, however, once outside my network, I can't seem to get to it.

FTP is not blocked at my school, I have all the appropriate FTP ports open on the Ubuntu box, and as far as I can tell, proftpd is configured correctly.

Any ideas or help?

---

### Post by Mithrilhall on 2006-12-20
If you run a portscan (nmap -P0 <ip_address>) from school on your ubuntu server what ports do you see open?

---

### Post by tturrisi on 2006-12-20
Do you have a router?  If so, port forward port 21 to the lan ip of the server.  However, ftp is not really secure, passwords and usernames are transmitted in plain text, thus another student at your school running wireshark or another network sniffer will be able to read your username & password in plain text.  Use ssh or sftp instead of ftp.

---

### Post by Tipo on 2006-12-21
> **tturrisi said:**
> Do you have a router?  If so, port forward port 21 to the lan ip of the server.  However, ftp is not really secure, passwords and usernames are transmitted in plain text, thus another student at your school running wireshark or another network sniffer will be able to read your username & password in plain text.  Use ssh or sftp instead of ftp.

Okay, I'll look into using SFTP, my school blocks the SSH protocol...

---

### Post by tturrisi on 2006-12-21
> **Tipo said:**
> Okay, I'll look into using SFTP, my school blocks the SSH protocol...
That doesn't mean you can't necessisarily ssh OUT from the school.  What to do is install openssh on your server and config it to use port 3022 instead of 22 via /etc/openssh/sshd.conf!  Then use port forwarding in router to forward ssh port 3022 to the server ip. :-) 

Networks such as at your schoool filter by blocking use of known ports.  Thus one cannot ssh TO a port 22 of a school comp.  But you likely can connect to a port 22 on a comp OUTSIDE the school net because an ssh CLIENT does not use port 22.  Just like a web browser ( a client) does not use port 80 and an ftp client does not use port 21.  Clients send and receive on free unassigned ports above port 1024, while servers use standard designated ports such as 21,22 & 80.

If you can't ssh OUT from the school to your server then do as I described, change the port your ssh server uses.  If the school comps use windows then install WinSCP, it's a client that can use ssh or sftp.

---

### Post by chrisfay on 2006-12-21
> Okay, I'll look into using SFTP, my school blocks the SSH protocol...

Be aware that SFTP (mostly)utilizes the SSH protocol so, if you meant by your comment that your shool has actively stated you can't use SSH on their network, then you probably shouldn't. 

Alaternatively, if you have 'assumed' that SSH is not allowed based on network firewalling, you should do as tturrisi has described, though it would probably be a good idea to check anyways.

---

### Post by punx45 on 2006-12-21
are your connection problems because the home server can't be found?
does the server at home have either a domain name or a static ip visible to the world?

---

### Post by tturrisi on 2006-12-22
I should add that you should NOT violate any school policies.  For example, a school net filters ports for:
1. security reasons
2. to legally protect themselves: prevent students from doing illegal things such as share copyrighted media.
3. prevent students from doing what may be considered non-educational or non-edu related (chats, messenger apps, etc)

Be honest & ethical in such matters, you are in school for the purpose of learing so you can then aply in Life what you have studied.  There's little value in learning how to break rules or "get around" the policies, unless your goal is to pursue a life of crime!

---

### Post by MrHorus on 2006-12-22
> **tturrisi said:**
> Clients send and receive on free unassigned ports above port 1024, while servers use standard designated ports such as 21,22 & 80.


Erm, that's not true.

If you are connecting to a server that accepts connections on port 80 then of course you are going to open an outgoing connection using port 80 - do you think the port number magically changes once it leaves your network?

Of course for the return path your machine will open an arbitary high port above 1024.

---

### Post by dannyboy79 on 2006-12-22
> **MrHorus said:**
> Erm, that's not true.

If you are connecting to a server that accepts connections on port 80 then of course you are going to open an outgoing connection using port 80 - do you think the port number magically changes once it leaves your network?

Of course for the return path your machine will open an arbitary high port above 1024.

I don't think you understand what he said. Just because the destination port is 80 doesn't mean that the source port has to be 80. that's what he is saying! for example, when using torrents, people connect to my box using port 49193 but the port on their computer is say 24279. they don't match. the same goes for ssh, i am connected to my home comp using ssh, i am using source port 48942 from work and am connected to port 22 on my home server. get it now?!?!?!

---

### Post by chrisfay on 2006-12-22
MrHorus is right. 

The client 'does' initiate the connection on the port which the server is listening on. The returning connection is then established with the client on the random port. In the OP's case, unless the school only firewalls the ssh port on the downstream, he won't be able to connect to anything on the standard ssh port outside the network.

---

### Post by tturrisi on 2006-12-22
> **chrisfay said:**
> MrHorus is right. 

The client 'does' initiate the connection on the port which the server is listening on. The returning connection is then established with the client on the random port. In the OP's case, unless the school only firewalls the ssh port on the downstream, he won't be able to connect to anything on the standard ssh port outside the network.
That's why I said what I said, because most net filters only filter inbound ports.
Also, even though the client "initiates" a request for the server port, the "initiating request" is NOT done on the client's port 21, port 22, or port 80, for ftp, ssh & www.  The client will still send this "initial request" on a free unassigned port.  If you don't believe that then run a sniffer while connecting to a service on a remote server.  Here's an example section of the very first request sent by an ftp client:
```
Transmission Control Protocol, Src Port: 53485 (53485), Dst Port: ftp (21), Seq: 0, Len: 0
Source port: 53485 (53485)
Destination port: ftp (21)
Window size: 5840
```
Actually, the first request is a dns request and once the target address has been resolved, the first ftp request is as above.  The point being this:  a client must access a service on a remote server's port for said service, but the client NEVER uses the hosts own service ports to connect to remote services.

---

### Post by Tipo on 2006-12-27
Okay, I am pretty sure that my school blocks the entire SSH protocol, I have tried switching which ports that ssh uses in the past, and my attempts have been blocked outright.

FTP, however, is *not* blocked. I pay for webhosting, and can access that via FTP without a problem...

Ahh, and to answer an earlier question, yes, my machine is visible to the outside world, it has a static IP address. I can see the machine if I type the address into my web browser...

Anyway, thanks for the suggestions, I'll give them a shot :)

EDIT: Forwarding ports 20 and 21 to my server has worked! Thank you tturrisi! You have helped a linux deprived college student get back in touch! :)

---

### Post by tturrisi on 2006-12-27
> **Tipo said:**
> EDIT: Forwarding ports 20 and 21 to my server has worked! Thank you tturrisi! You have helped a linux deprived college student get back in touch! :)
You're welcome!
Now, just don't use ftp regularly to access data that you don't want others to see or have access to.  FTP sends the username & password in plain text and can be seen by anyone else on the school lan who is running a network sniffer like Wireshark.  You can easily use apache htaccess-htpasswd to secure a www dir & its sub-dirs, then use an index.php with code for file uploads.  This is all done via a web browser & form.

---

### Post by Tipo on 2006-12-28
Okay, I'll look into that.

It shouldn't be too much of a problem. I go to art school, not exactly surrounded by techies and hackers ;)

Thanks again!

---

