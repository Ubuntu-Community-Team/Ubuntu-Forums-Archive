---
title: "Pure FTPd"
date: 2009-08-28
forum: Server Platforms
---

### Post by elitium on 2009-08-28
Hi
I've been trying to setup a FTP server for a while now..I'm using Pure FTPd and I get it to run sometimes. I'm messing with the SSL/TLS function. I have followed the guide on Pure FTP's homepage but the thing is that i want the users to only be able to access the server with an SSL certificate.
I've created one self sign certificate as in the guide.
But when im trying to log on to the ftp from a windows xp machine with coreftp (FTP) it's poosible, but when I choose (FTP TLS) sometimes i get an error message or sometimes I get a warning saying that it's not secure, do I want to continue, pressing yes will log me in but i think I'm not using any typre of SSL encryption then.

Is there a way to see if I'm using SSL or not?

I've been trying to change the TLS value in the ..pure-ftpd/conf/TLS file to 3 instead of 1 but when I try to restart the server i get that's no corresponding directory, not even when I change it back to 1.
I've also tryed with "pure-ftpd --tls=3 &"
that giving me: Unable to start a standalone server: Address already in use

There are three different types of options on SSL
1 = you can log on with both SSL or not (which I seem to have when it works)
2 = SSL is enabled
3 = some harder SSL function
I don't know the diffrences between 2 and 3, does 3 work with a self sign certificate?
If i choose 2 I'm a secured then? or can someone "hack/sniff" anything?

Regards

---

### Post by hessiess on 2009-08-28
The FTPS protocol is a mess and dousen't work very well (it breaks with a lot of firewalls). Use SFTP (SSH File transfer protocol) instead. which, besides containing the letters `f' `t' and `p' in the name, has absolutely nothing in common with the outdated FTP protocol.

---

### Post by elitium on 2009-08-29
Sorry if I wasn't clear on my usage with the FTP. I'm attending to use it as a file transfer between our subsidiary and our company workers so the server should be reach from the internet. Does SSH (SFTP SCP) offer this? Isn't SSH more of "remote configure" instead of file transfering? How does the users reach the server? do they need to have some kind of SFTP/SCP client? Can they have a gui client? They are running Windows. I haven't used SSH so I don't no how it works really.

---

### Post by hessiess on 2009-08-29
> **elitium said:**
> Sorry if I wasn't clear on my usage with the FTP. I'm attending to use it as a file transfer between our subsidiary and our company workers so the server should be reach from the internet. Does SSH (SFTP SCP) offer this? Isn't SSH more of "remote configure" instead of file transfering? How does the users reach the server? do they need to have some kind of SFTP/SCP client? Can they have a gui client? They are running Windows. I haven't used SSH so I don't no how it works really.

SFTP is a perfectly good file transfer protocol (actually it works more like a remote file system), All you need to do to make it available over the net is to open port 22. To use it on windows you will need to use Winscp.

SSH is not just for remote shell connections, it is just a general encrypted data tunnel which can be used to implement other protocols, or just encrypted port forwarding (which can be used for a basic VPN), If you want to prevent user log in just set the `shell' of the user to /dev/null.

In a nutshell, this is the problem with FTP: There are more computers on the internet that IP addresses available with the 32 bit IP V4. To get around this NAT was invented, which works by creating a local network with fake IP adresses, and presents all of the mechenes on the network under a single `public' IP. When a computer on the network sends a packet to the internet the NAT router logs the target IP, `translates' the `fake' local IP into the public IP and sends the packet on, logging the target IP with the corresponding `fake' IP in its routing table. So when the server responds to the request the NAT looks at the IP of the server, checks its routing table and sends the packet to the correct `fake' IP. Becouse of this any connections cuming from outside the local network are dropped. 

Establishing a connection with the FTP protocol is done by the client connecting to the server, then the server connects back to the client again on a random port, because this isn't expected the packet gets dropped and the connection fails. The two port nature of the protocol also makes it very difficult to secure. FTP was designed in the old days of computing before NAT came to the scene and security was such a major problem. SFTP is a highly secure, protocol which works fine with modern networking technologies (only uses one port).

---

