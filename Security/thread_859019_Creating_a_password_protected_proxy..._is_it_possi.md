---
title: "Creating a password protected proxy... is it possible?"
date: 2008-07-14
forum: Security
---

### Post by techknow on 2008-07-14
Hey guys. 

I have a friend living overseas at the moment who's having trouble with geoblocking and I was considering setting up a proxy server on my home server for him to use, but before I go about doing that I was wondering if there was any way that I could make it password protected so that only he can use it?

I don't know if it's possible but have any of you guys ever done something similar?

Cheers

Tech

---

### Post by hyper_ch on 2008-07-14
it is possible... squid can do it...

---

### Post by moonpup on 2008-07-14
Here's something I posted a while back...

First off this is a multi step process...I'll give you a brief overview but you'll need to learn about configuring squid if you don't know how. Here's a good link to follow and includes how to setup squid to use a username and password before it allows you access to it. It's written based on rpm (redhat) commands. You'll need to know the ubuntu equivalents. You can most likely stop at the point where it tells you about forcing users to use the proxy section.

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid)

1) The remote server must be running a proxy server... in this case most likely squid. Squid should be setup to only accept connections from the local network only. Do not open this up to the outside world. Also, using the default port 3128 is fine.

2) Follow the above how-to which will give you a basic, but good enough install to make this work. Again, you can most likely stop at the point where it tells you about forcing users to use the proxy section.

3) You won't (and don't) open a port on the firewall for squid as you'll be connecting through ssh

4) On your workstation, set firefox to use localhost on port 3128 for proxy settings.

5) Make your ssh connection to the server with ssh -L 3128:localhost:3128 username@server

Remember to change port #'s if necessary. If you remote server accepts ssh connection on a different port from 22, then add a -p port# to the above ssh command. As long as you are not blocked by a firewall, you should be good to go. Just open the ssh connection first and then firefox.

Hope this helps!

---

### Post by daleus on 2008-07-14
> **moonpup said:**
> 
1) The remote server must be running a proxy server... in this case most likely squid. Squid should be setup to only accept connections from the local network only. Do not open this up to the outside world. Also, using the default port 3128 is fine.


misconception, if you're using SSH you can just do what I wrote in this article [http://www.ubuntuhq.com/content/private-internet-browsing-ssh.]("http://www.ubuntuhq.com/content/private-internet-browsing-ssh.")

Or if you cba to read, "ssh -p sshserverport -D 7070 username@server" set the client machine to look at a socks 5 proxy "127.0.0.1" port 7070.


No squid required.

---

### Post by moonpup on 2008-07-14
In the solution I am providing, squid is required so I am correct. With the solution you are providing, it is correct as well. Just two different solutions to a similar problem.

---

