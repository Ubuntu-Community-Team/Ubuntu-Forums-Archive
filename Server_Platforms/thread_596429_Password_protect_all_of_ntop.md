---
title: "Password protect all of ntop"
date: 2007-10-29
forum: Server Platforms
---

### Post by Sgurd on 2007-10-29
I'm working on setting up an ntop box to monitor a segment of my network.  

It will be on a public IP and I'd like to make sure I'm the only one accessing the information.

Can some one point me towards accomplishing this? 

Much thanks in advance - JD

---

### Post by deuce868 on 2007-10-29
What I did was to not open the ntop port for the web interface through the firewall. That way it only listens on localhost and you can access the web interface with an ssh tunnel. In the case of my server ssh access is via key only so the only way to get to ntop was to create a tunnel with the ssh key and it works out pretty well. 

You can also go in and setup http auth in the apache config and use that.

---

### Post by Sgurd on 2007-10-30
Thanks for the reply.  I read up a bit on Ubuntu firewall options.  Looks like a firewall is my answer.

If didn't use the ssh tunnel route but wanted to make the ntop box, on a public IP, available to myself via a browser on port 3000, behind a hardware firewall on a private IP, I would have to tell the ntop firewall to accept request on that port from the public IP of our firewall, not my private IP, right?

Pardon the compounded sentence.

   Thanks again - JD

---

### Post by jimmah6786 on 2007-12-18
when you log into the nTop site. Under Restricted URLs.

Create a new one that is blank, this will make you log in everytime you hit the nTOp page.

To make it more secure make a ssl certificate and enable ssl.

Dont forget after you get ssl working  with you nTop web, to disable regular HTTP. Do this by changing the port number to 0 in the config page.

Hope this helps

--Jimmah

---

