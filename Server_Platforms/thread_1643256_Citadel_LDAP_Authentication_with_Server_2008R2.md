---
title: "Citadel LDAP Authentication with Server 2008R2"
date: 2010-12-11
forum: Server Platforms
---

### Post by rampager5000 on 2010-12-11
Little backstory... Trying to setup an exchange alternative for my small company. Huge fan of open source, would try to replace any M$ software I can using it. That being said here goes.

I have an ubuntu 10.10 server with an M$ 2008R2 Active Directory server to authenticate.

I have tried installing citadel using both the Easy Install Script as well as the citadel-suite.deb package. 

I followed the guide at: [http://www.citadel.org/doku.php/faq:installation:msadsso](http://www.citadel.org/doku.php/faq:installation:msadsso) to handle the authentication. Once done though no authentication happens whatsoever. Is there something I'm missing to make this work correctly?

I have tried googling like crazy to find something so now I lay this at the hands of the OpenSource gurus to help me get it fixed.

EDIT:
I didn't change anything on the defaults other than inputting my LDAP Server IP 192.168.10.250

---

### Post by rampager5000 on 2010-12-12
Just a bump... I really really wanna make this work. Can someone offer help?

---

### Post by Baked- on 2010-12-14
check out likewise.  Ive used it with 2k3 AD and it seems to work perfectly.

---

### Post by rampager5000 on 2010-12-16
I would have thought that I wouldn't have to have the server joined to the domain to make that work ok. I had a go at getting an OpenLDAP server set up as an alternative to M$ AD. I've had bad luck with that also. I just can't find a good server to use to authenticate in an alternative to exchange.

---

### Post by ingramproductions on 2011-09-01
check the system logs jerod:

tail -f /var/log/messages

---

