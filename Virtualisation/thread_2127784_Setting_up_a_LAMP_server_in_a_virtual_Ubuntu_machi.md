---
title: "Setting up a LAMP server in a virtual Ubuntu machine."
date: 2013-03-21
forum: Virtualisation
---

### Post by yay101 on 2013-03-21
Hey all! I am trying to set up a lamp server on a vanilla 12.04 desktop installation. I can access the webserver from any machine on my local network but as soon as i try and access it by its external IP i just get a page not found error. What am i doing wrong, if anything? Is it a router issue or are there other settings i need to change on the host or virtual ubuntu itself?

If it helps i am running ubuntu as the host as well.

---

### Post by SeijiSensei on 2013-03-21
I presume you are forwarding port 80 (and 443 if you're using SSL) back to the VM's address.  Are you sure your ISP allows inbound traffic on port 80?  Many ISPs have terms of service that prohibit servers on residential connections and block 80 to enforce the rule.

---

### Post by Kalibur on 2013-03-21
Who is you internet provider and what is the make and model of you router?  You will need to log in and open port 80 then direct inbound traffic for that port or all traffic depend what your router supports to you VMs IP address. Also what do you mean by its external IP address?  How many networks is it connected to, not that its matters.

---

### Post by yay101 on 2013-03-22
Hey guys thanks for the reply's i am not forwarding the ports no... I assume you mean from the host to the VM? 

My isp is iinet in Australia, so they were blocking for security reasons. One click and unblocked.

By External IP address i mean its internet ip.

The router is a Netgear DGND3700 v2, what settings would i need to change on it to enable webhosting?

---

### Post by yay101 on 2013-03-22
Nevermind. Between forwarding ports to its local address and a bit of luck i it is all working. Now to set up a mail server.

Thanks guys!

---

