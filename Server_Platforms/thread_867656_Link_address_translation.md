---
title: "Link address translation"
date: 2008-07-23
forum: Server Platforms
---

### Post by sh1ny on 2008-07-23
Hello there. I am brand new here, but i have somewhat good experience with debian/ubuntu etc. Today i got a challenge, and i want to ask if anyone knows how this is doable. So here goes :

Basicly i need to redirect connections from a router to boxes in the internal network all coming in on the same port ( 443 ). The only thing that can distinguish them is the SSL certificates. One of the redirects is for apache running over ssl, the other is for a windows machine inside that  Terminal Services Gateway ( vpn i think T.T ).I've been told you can do that under windows using ISAserver configuring this - [http://technet.microsoft.com/en-us/library/bb794742(TechNet.10).aspx](http://technet.microsoft.com/en-us/library/bb794742(TechNet.10).aspx)

Is there any such alternative to do that under ubuntu/debian ?

---

### Post by windependence on 2008-07-23
Why would you not want to run your VPN on some oether port. The traffic is encrypted anyway.

At any rate, it's possible using OpenVPN:

[http://christophe.vandeplas.com/2008/06/01/portsharing-with-openvpn](http://christophe.vandeplas.com/2008/06/01/portsharing-with-openvpn)

-Tim

---

### Post by sh1ny on 2008-07-23
Because i have to work on how my windows part requires it. Basicly it's like that

Router IP - 111.111.111.111

All connections must be made to port 443.

So opening the web site at [https://111.111.111.111](https://111.111.111.111) should redirect to :

192.168.1.1:443

Trying to open 111.111.111.111 with a TSG client should go to :

192.168.1.2:443

The problem is i am not using OpenVPN, but there is a TSG running on 192.168.1.2 that will then handle the connecting client. As far as i understood, the client that they're using doesnt support Port switching ( i.e. i can't make them connect to port 445 and redirect it to 192.168.1.2:443 ).

The only other thing that comes to mind is acquiring 1 more public IP and redirecting based on that >.<

P.S. I am not sure that adding another public IP will be accepted as a solution tho :(

---

### Post by windependence on 2008-07-23
What is a TSG?

-Tim

---

### Post by sh1ny on 2008-07-23
[http://technet2.microsoft.com/windowsserver2008/en/library/9da3742f-699d-4476-b050-c50aa14aaf081033.mspx?mfr=true](http://technet2.microsoft.com/windowsserver2008/en/library/9da3742f-699d-4476-b050-c50aa14aaf081033.mspx?mfr=true)

M$....

---

### Post by MJN on 2008-07-23
> **sh1ny said:**
> Basicly i need to redirect connections from a router to boxes in the internal network all coming in on the same port ( 443 ). The only thing that can distinguish them is the SSL certificates.
 
It all depends on what sort of device your 'router' actually is.
 
If it is a standard layer 3 router then it will not have visibility of SSL certificates (layer 7) and hence can only make decisions based solely on the layer 3 info (IP addresses) and potentially layer 4 (ports).
 
The easiest solution would likely be adding an additional IP address as you've mentioned - this can then be used to distinguish between the common port using DNS or explicitly specifying the appropriate IP address.
 
Adding a proxy between the router and servers would also work although it is not going to be the easiest thing to set up given the requirement for it to act in a dual proxying role for HTTP and TSG data.
 
You could of course switch one of the ports away from 443 (or, less elegantly, use DNS combined with an application layer redirect) but I assume you've already considerd/discounted this as a feasible option.
 
Incidentally, all this advice could be inappropriate as your title (link address translation) does not equate with your description of what you want to achieve.
 
Mathew

---

