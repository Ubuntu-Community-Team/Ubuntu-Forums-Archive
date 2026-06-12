---
title: "Ubuntu 10.04 and Citadel"
date: 2010-06-25
forum: Server Platforms
---

### Post by egravede on 2010-06-25
Frankly, I'm a total noob when it comes to setting up servers, especially email.  Someone pointed me towards Citadel, so I downloaded and installed, the setup went fine.  Now the server can send emails, but not receive and I am totally stumped as to why.




Also, my company is wanting to migrate from godaddy(we use their webclient for mail now), how would I go about doing this using Citadel?  Do I just point something to my server and let it go from there?

---

### Post by koenn on 2010-06-25
you're gonna need MX records
[http://en.wikipedia.org/wiki/MX_record](http://en.wikipedia.org/wiki/MX_record)

also, how do you know you can't receive mails ? What happens if one is sent to you (or your citadel) ?

---

### Post by egravede on 2010-06-28
I get a timed out message from google (using gmail):

"This is an automatically generated Delivery Status Notification

THIS IS A WARNING MESSAGE ONLY.

YOU DO NOT NEED TO RESEND YOUR MESSAGE.

Delivery to the following recipient has been delayed"

And it just goes on stating email and the contents of the message.

---

### Post by koenn on 2010-06-28
how is that server connected to the internet ?

---

### Post by HermanAB on 2010-06-28
Howdy,

For email to work properly, you MUST have the following:
DNS with A, PTR and MX records
Static IP address
A Server account with your ISP (allowing port 25)

Here are a bunch of howtos:
[http://www.aeronetworks.ca/citadel-basics.html](http://www.aeronetworks.ca/citadel-basics.html)
[http://www.aeronetworks.ca/citadel-howto.html](http://www.aeronetworks.ca/citadel-howto.html)
[http://www.aeronetworks.ca/citadel-clients.html](http://www.aeronetworks.ca/citadel-clients.html)
[http://www.aeronetworks.ca/citadel-ssl-certificate.html](http://www.aeronetworks.ca/citadel-ssl-certificate.html)

---

### Post by egravede on 2010-06-30
@koenn
Its connected through a switch, which in turn is regulated through our DNS server (windows server 2003).

@Herman
Thanks!! I'll definitely be taking a look at these.

---

### Post by koenn on 2010-06-30
> **egravede said:**
> @koenn
Its connected through a switch, which in turn is regulated through our DNS server (windows server 2003).

in order to receive mail, mail servers on the internet will need to be able to connect to your server. So your server (or at least some ports) will need to be visible on the internet. Some routers, especially the residential types, will need additional configuration to achieve this.

Switches have nothing to do with it, and neither has a DNS server on your LAN.

---

