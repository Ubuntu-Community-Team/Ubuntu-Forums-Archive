---
title: "Set outgoing connections and DynDns"
date: 2011-09-29
forum: Server Platforms
---

### Post by kyriacosn on 2011-09-29
Hello guys,
Ive got a HP Proliant ML 110 and I installed on it Ubuntu Server 11.04 with GUI with the recommended only applications cause I need to run JDonwloader.
I have also installed these services:
-WebMin
-phpMyAdmin
-MySQL
-PHP 5.3.5
-Apache2
-Samba

Everything seems to be just fine when i connect to the server locally, but the problem is that I can't connect on the Server when I use the external IP or Domain. The only service that seems to work with external IP is apache.
Im really sure that Ports are open and Firewall its disable(from webmin).
What can I do to make it work when Im out of my network?
Also I bought a .com domain and the Services for Dynamic IP from DynDns, i connect my server through the ddclient but I think its just redirection.(apache2 seems to work fine if i browse domain.com, so maybe domain its fine, I just ask to be sure).Anybody can help me out to set the domain with a dynamic IP and find out why I can't connect to my server out of my local network?
Thank you guys

---

### Post by Bucky Ball on 2011-09-29
Welcome.

Just a comment off topic: LTS (long-term support) releases are recommended for servers and have a five year support cycle (*MUCH* longer than 11.04 - 10.04 LTS server edition supported until April 2015). Good luck with it ... ;)

---

### Post by kyriacosn on 2011-09-29
So you suggest me to reinstall my server with 10.04 LTS so can have a long period updates, right?
Any idea about the problem that Im facing with my Server and ports?
Just to add that i have webmin on port 10002, Trasnmission to 10001 and Jdownloader 10003 (not true ports to be more secure, but just to understand my setup)

---

### Post by papibe on 2011-09-29
Are you trying to access your server using its public IP from inside your LAN?

In most cases that won't work. The ability to connect to a machine from your local network using its public name, or IP, is called NAT loopback (read about it [here]("http://www.dyndns.com/support/kb/loopback_connections.html")). Unfortunately most routers don't support it.

The easiest way to test your setup is to go to a Internet cafe, public library, or even better, a friend's house. Another alternative is to use your pnone/tablet 3G connection (not WiFi).

Regards.

---

### Post by kyriacosn on 2011-09-30
I sent a link to my friends and the can read the messing It Works from Apache 2.
But something block the ports that I have set cause from a scan I get just these ports :
[IMG]http://www.filesonic.com/file/2257621684/port4.jpg[/IMG]
How can I open them on my machine cause on my router are opened and I'm sure about that!

---

### Post by kyriacosn on 2011-09-30
Guys All set!
DMZ is the answer on my router:popcorn:

---

### Post by Bucky Ball on 2011-10-01
Good work. Please mark thread as solved from Thread Tools to help others. ;)

Good luck with it all.

---

