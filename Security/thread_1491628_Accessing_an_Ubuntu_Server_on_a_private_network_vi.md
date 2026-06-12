---
title: "Accessing an Ubuntu Server on a private network via the Internet"
date: 2010-05-23
forum: Security
---

### Post by zoon_unit on 2010-05-23
I am doing Drupal cms development on a local Ubuntu server on my private network. Everything works fine, but I want to access my server securely over the Internet when traveling.

I want to be able to do the following:

1) Access my server via openssh over the Internet
2) Access my server's Drupal web pages over the Internet
3) Do it all SECURELY without the dangers of hackers accessing my local server.

Here's my current setup:

I have a private network that includes Windows XP, Windows 7 and my Ubuntu server, all working properly using Samba.

My private network is behind a firewalled router. My question is this: Do I need a VPN, even though my router provides firewall capability? Can I access my Ubuntu server using SSH by providing the router's IP address? If so, how can I access the Ubuntu server's web server through the Internet?

My router allows me to "punch through" the firewall by defining which ports I can access through the router to which device, but I assume that ANYONE who uses these ports would have access to my server. (obviously, they couldn't get SSH access without the password, but what about web access?) I want to limit access to myself with some kind of functionality similar to a VPN.

Is that what I need? Or is there a simpler way? (remember, I need SSH and Web access) If so, what is a reasonably secure and easy configuration? Poptop? OpenVPN? Other?

---

### Post by drdos2006 on 2010-05-23
Check out TeamViewer, it might suit your needs. You need a server on one machine and a client on the other machine.

regards

---

### Post by jerome1232 on 2010-05-23
Couldn't you setup a ssh tunnel, and view the pages through the tunnel (that way your not opening the web server up to the world).


For ssh I would set up keyed authentication, disable password authentication, and use fail2ban or denyhosts to ensure ssh is fairly secure.

---

### Post by CharlesA on 2010-05-23
You should be fine with just SSH. You can forward X over SSH if needbe.

Outsiders wouldn't be able to access the server from any port other then the one that you forwarded. If you lock down SSH with keys and forwarded the port the web server uses. I can access my RAID config utility by forwarding port 7402 thru the SSH tunnel to my local machine, which would be accessed by going to [http://localhost:7402](http://localhost:7402).

Also, I've been running SSH using keys without using denyhosts or fail2ban, haven't had any attacks logged in the auth.log.

I am running on a non-standard port, of course. :)

---

### Post by The Cog on 2010-05-24
To access your SSH server over the internet, you need to configure your router to forward incoming connections (to the router's IP address) to your Ubuntu server. This is normally port number 22 but you can configure sshd to listen on a different port number if you want, some people do to avoid the attention of the ssh password guessing bots.

I would advise configuring the ssh server to require certificates instead of passwords for authentication - google for password-less SSH. 

You can configure SSH to tunnel other TCP connections through, and they get encrypted along the way, so they gain SSH's security. To tunnel to the webserver, use an ssh command like:
ssh -L localhost:80:localhost:80 1.2.3.4
but replace 1.2.3.4 with your router's public address. Then just point your web browser at [http://localhost](http://localhost).

---

