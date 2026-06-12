---
title: "Nessus install help"
date: 2009-12-25
forum: Security
---

### Post by sourcenaut on 2009-12-25
I'm a relatively new Linux user that started 4-5 months ago on and off.  Please have patience with me.  Here is some background information:

I have a computer which is running ubuntu desktop 9.10.  I download Nessus 4.2 and install it.  After it finishes I add a user admin account.  I then go and register for plugins and download/install it successfully.  I start the daemon which now is added to startup.

I am behind a dedicated firewall.  I only wish to scan the hosts behind the firewall.  I add pass rules for all ports between the Nessus server and the laptop that I wish to use as a client.  I then try to connect to the Nessus server with firefox using the following address: [https://192.168.1.10:8834]("https://192.168.1.1:8834").  There is no connection that can be made.  Nessus Daemon is running. 

What happened?  Thanks for your input.

edit: The server address  that is posted up there isn't really the server address I'm using, it is an example.  The original post had 192.168.1.1 listed which is usually the default gateway address.  I really don't feel secure enough to map out my private network on the forum to fix this problem.

---

### Post by hansdown on 2009-12-25
Welcome to the forum sourcenaut.

I can't offer any advice, but I tried to connect to that link, and got this.

A google search gives this.

What is the 8834 at the end?

---

### Post by sourcenaut on 2009-12-26
Thats the listening port of the Nessus server I'm trying to connect to.

---

### Post by hansdown on 2009-12-26
> **sourcenaut said:**
> Thats the listening port of the Nessus server I'm trying to connect to.

Doh! That's not too embarrasing.

This is why you shouldn't put much faith in my reply.

Something I did find, That may help...

[http://www.securityfocus.com/infocus/1753](http://www.securityfocus.com/infocus/1753)

Also, this may be interesting.

[https://discussions.nessus.org/message/4513;jsessionid=75E4D09B66C09C4CBA86A7146B1C92DC](https://discussions.nessus.org/message/4513;jsessionid=75E4D09B66C09C4CBA86A7146B1C92DC)

---

### Post by Lars Noodén on 2009-12-28
[Nessus](http://www.darknet.org.uk/2008/08/openvas-open-vulnerability-assessment-system-nessus-is-back/) started out as open source, but was enticed by an external interest to go closed source.  The replacement GPL-licensed Open Vulnerability Assessment System is [OpenVAS](http://www.openvas.org/) and is part of Ubuntu's universe repository.

If you are just starting out, then OpenVAS might be a much better investment.  The client and server are easy to install.

[http://www.openvas.org/openvas-client.html](http://www.openvas.org/openvas-client.html)

[http://www.openvas.org/openvas-server.html](http://www.openvas.org/openvas-server.html)

---

### Post by TammieSeo on 2010-09-19
Thank you Lars Noodén. I got OpenVAS Client installed and it looked good. Thanks for the recommendation.

---

