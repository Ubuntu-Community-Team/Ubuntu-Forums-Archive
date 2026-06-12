---
title: "How to get something like remote desktop on 8.10"
date: 2009-04-10
forum: Server Platforms
---

### Post by srdjo on 2009-04-10
I created VPN connection between two servers, and i tried to get the remote desktop included in 8.10 working, tried all the settings, but I cant get it working.

I want to be able to connect from one server to another and get the logon screen where I could login as any user I want.

How can I do that ?

p.s. VPN connection is already set to connect on boot and I can ping both ways.

---

### Post by srdjo on 2009-04-10
Just to add that I am using hamachi as VPN connection, have ufw installed and the server i want to connect to is ltsp server.

---

### Post by srdjo on 2009-04-10
I got it to show desktop for logged users.

It was firewall problem.

But how can I get to login screen so I can log in to my account from remote pc ?

---

### Post by HermanAB on 2009-04-10
Install SSH server and client.

---

### Post by srdjo on 2009-04-10
Since it is a LTSP server, it already has some kind of ssh.

My only preoccupation about ssh is that it could mess something up with LTSP.

Is there any how to ore something else on that mater ?

---

