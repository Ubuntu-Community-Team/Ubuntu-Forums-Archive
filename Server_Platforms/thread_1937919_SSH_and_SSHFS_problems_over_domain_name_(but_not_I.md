---
title: "SSH and SSHFS problems over domain name (but not IP address)"
date: 2012-03-08
forum: Server Platforms
---

### Post by paulbdavis on 2012-03-08
Here is my situation..

I have my domain name through godaddy, and I am using zoneedit.com for my dynamic dns server

Whenever I use ssh and I connect using the domain name, it works for a while, but will inevitably I will get a "Write failed, broken pipe" message from ssh, or the file system mounted with sshfs will no longer respond (from the command line, even tab completion of the mounted directory name locks up) and I have to use fusermount -uz to unmount them

However, whenever I connect using my IP address (local or public) the connection is rock solid.

Anybody have any insight as to why this is happening? Is it something I can fix on my server or is it because I am using the dynamic dns?

Thanks in advance

---

### Post by papibe on 2012-03-08
I'm not very familiar with sshfs, but I use a lot of ssh using a dynamic DNS (dynnds).

AFAIK, when you ssh to a domain name, the dynamic DNS is just used once to translate the name into the current IP. Then all is done using the IP. In my opinion it should be that different than using nslookup to get the IP, and then using the IP to connect.

Have you tried to ssh without using sshfs to insulate the problem?

Just some thoughts.
Regards.

---

### Post by kevdog on 2012-03-08
If the connection works perfectly from your LAN but drops remotely, I'd speculate its a network/router issue.  Dynamic DNS is not the problem.  The DNS lookup for the dynamic IP address occurs at the beginning of the authentication.  Once the connection is established, I don't think its involved.  

As far as SSHFS -- I never really had much luck with a reliable connection.  I'm not a big fan of the fuse module -- I find it buggy but YMMV.

---

### Post by pavi_elex on 2012-03-09
I have used lots of ssh to connected different linux servers but I did not connect any with domain name. I have always connected with ip address.But I think it should work fine because if you try to connect your own machine through ssh, it will be connected. If you use your system's IP or if you use word "localhost". but if you are in a LAN and you want to connect other's system then there should be IP because, you can not use word "Localhost".

---

### Post by paulbdavis on 2012-03-09
> **kevdog said:**
> If the connection works perfectly from your LAN but drops remotely, I'd speculate its a network/router issue.  Dynamic DNS is not the problem.  The DNS lookup for the dynamic IP address occurs at the beginning of the authentication.  Once the connection is established, I don't think its involved.  

As far as SSHFS -- I never really had much luck with a reliable connection.  I'm not a big fan of the fuse module -- I find it buggy but YMMV.

As I mentioned, I can connect externally through my public IP address just fine (I have the router set up to do so). The problem only occurs when I connect through my domain name.

What are my alternatives to sshfs that I can use locally and over the web?

---

