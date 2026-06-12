---
title: "Mail Server Port Question"
date: 2008-06-05
forum: Server Platforms
---

### Post by Black Mage on 2008-06-05
For a mail server(postfix), should port 25 be open on the firewall?

Because couldn't anybody just login from port 25 and just start spoofing mail?

---

### Post by klange on 2008-06-05
You need to keep port 25 open in some way if you want to receive incoming mail. You need to check your SMTP server configuration for protecting it from outside access. I personally have mine set up to not accept any outgoing mail, only incoming mail headed towards an approved address. Mail sent through my server must be sent from my server (IE, via webmail).

---

### Post by Black Mage on 2008-06-05
Is there a tutorial for setting up secure telnet?

---

### Post by K.Mandla on 2008-06-05
Moved to Server Platforms.

---

### Post by windependence on 2008-06-06
> **Black Mage said:**
> Is there a tutorial for setting up secure telnet?

You only want to telnet in from the inside of your network to test the server. If you want to see if your port is open and not blocked by your ISP, go to [www.canyouseeme.org](www.canyouseeme.org) and test the port.


-Tim

---

### Post by thedevnull on 2008-06-06
> **Black Mage said:**
> Is there a tutorial for setting up secure telnet?

Do you mean SSH?  I think you do.  There are tons of them like this one...

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by thedevnull on 2008-06-06
> **Black Mage said:**
> For a mail server(postfix), should port 25 be open on the firewall?

Because couldn't anybody just login from port 25 and just start spoofing mail?

I would take a look at the documentation on postfix and it will elucidate it to the nth degree. 

[http://www.postfix.org/documentation.html](http://www.postfix.org/documentation.html)

:guitar:

---

