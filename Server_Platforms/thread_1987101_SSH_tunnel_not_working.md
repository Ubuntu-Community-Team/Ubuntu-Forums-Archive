---
title: "SSH tunnel not working"
date: 2012-05-25
forum: Server Platforms
---

### Post by jasbur on 2012-05-25
I'm having trouble getting an SSH tunnel to work.

I have a Windows client running an ftp server on port 55555. I've tested it locally and it's working.

I'm connecting to my server using plink (command line putty) using this command:

plink [email]user@serveraddress.com[/email] -R 55555:localhost:55555
I've also tried:
plink [email]user@serveraddress.com[/email] -L 55555:localhost:55555

in either case I can run netstat -tunelp | grep 55555 to see that the port appears to be open. However when it try to connect to the windows ftp by typing in ftp localhost:55555 on the Ubuntu machine it just says something about an unrecognized service and doesn't connect.

Any ideas?

---

### Post by papibe on 2012-05-25
Hi jasbur.

I have a couple of questions:
[INDENT]Is serveraddrress the Linux machine or the Windows?

Are you running plink on the Windows machine or the server?[/INDENT]
Regards.

---

### Post by jasbur on 2012-05-26
Yes, the server is on Linux and I'm using plink as the client on Windows.

---

### Post by kennethconn on 2012-05-26
Sounds like a firewall issue to me, probably Windows firewall (I presume ftp client is installed on server). Take plink out of the mix and see if you can connect by LAN IP address to Windows client from server.
 
Also, you should probably put the FTP service on your server and connect from your client PCs (in your case the Windows PC).
 
I have had issues connecting to Windows computers to secure copy files using pscp (think it was a username issue), but I don't think that is your issue here. Try as suggested above, hopefully that will get you sorted.

---

### Post by jasbur on 2012-05-26
Actually the ftp server is just for testing purposes. Eventually I'd like the Windows computer to be running an instance of VNC. I'm trying to use tunneling to bypass a customer's firewall (for remote support). My understanding is that no ports should need to be open on the Windows computer to achieve this.

By the way I have tried local network access to the ftp server and it works fine. Again, wouldn't the tunnel bypass it anyway?

---

### Post by The Cog on 2012-05-26
I would have expected 
> plink [email]user@serveraddress.com[/email] -L 55555:localhost:55555
to be the one that works. Maybe the "localhost" is sent to the windows box which can't resolve that name. Try this:
> plink [email]user@serveraddress.com[/email] -L 55555:127.0.0.1:55555
but you sre still unlikely to get ftp to work properly because it uses other connections on other ports (that you're not tunneling) to do the data transfers. The login should succeed, but not data transfers (that includes directory listings).

---

### Post by kennethconn on 2012-05-26
>  
By the way I have tried local network access to the ftp server and it works fine

 
What command are you typing on your Linux server machine to connect successfully to FTP server running on your Windows machine, as you indicated above?
 
[https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)
 
>  
Ports numbers less than 1024 or greater than 49151 are reserved for the system, and some programs will only work with specific source ports, but otherwise you can use any source port number.

 
Might be the problem, try a lower port number - after that it's been so long since I worked with creating SSH tunnels (actually for use with VNC), I'd be probably wasting your time than helping.

---

### Post by jasbur on 2012-05-26
Actually it looks like 
```
plink -R 55555:localhost:55555
```
should be the right choice according the article posted above, because the connection would be originating from the Linux box into the Windows box. 

I'm using the command
```
ftp localhost:55555
```
To try to connect from the Linux box.

---

### Post by kennethconn on 2012-05-26
I would disagree with that and say the command should be:
 
plink -L 55555:localhost:55555
 
actually I would be trying something like:
 
plink -L 12345:localhost:55555
 
ftp localhost:12345
 
 
But what I wanted to know is what command you typed from the linux box to connect to the Windows machine when you said that "I have tried local network access to the ftp server and it works fine"?

---

### Post by papibe on 2012-05-26
I was so concern trying to understand the network layout, that I forget something very important: we are dealing with ftp.

ftp is an old, limited, and I even say *natty* protocol.

From 'SSH: The Secure Shell - The Definitive Guide':
[INDENT]> To understand the problems between FTP and SSH, you need to understand a bit about the FTP protocol. Most TCP services involve a single connection from client to server on a known, server-side port. FTP, however, involves multiple connections in both directions, mostly to unpredictable port numbers...
[/INDENT]
So, in short, it looks like a simple one-port tunnelling won't work with ftp.

Here is some useful information: [FTP Forwarding]("http://docstore.mik.ua/orelly/networking_2ndEd/ssh/ch11_02.htm").

I hope that helps,
Regards.

---

### Post by jasbur on 2012-05-28
Wow, I didn't see that coming. Anyway I was just trying to use FTP as a test service to determine whether or not the traffic was being tunneled properly. I'm actually shooting for VNC to be forwarded. 

The good news is I think I figured it out. I need the initiate the tunnel from the Windows end using:
```
ssh -R 5900:[public IP of the windows box]:5900 user@linuxserver.com
```
It appears the mistake I was making was not using the public IP of the Windows box.

---

