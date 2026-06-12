---
title: "Freeradius authentication problem."
date: 2016-05-17
forum: Server Platforms
---

### Post by Kikikikikik on 2016-05-17
I have set up a Freeradius server on Ubuntu 14.04 following this guide: [http://andrewpakpahan.blogspot.com.ee/2012/08/installing-and-configuring-freeradius.html](http://andrewpakpahan.blogspot.com.ee/2012/08/installing-and-configuring-freeradius.html)
Servers have freeradius, mysql, apache2 and daloradius.

I have made a clone from that server. Now I have 2 servers, Server 1 belongs to realm1 and Server2 belongs to realm2. On both servers I made an user which belongs to certain group through Daloradius. Server1 user: [EMAIL="guest@realm1.com"]guest@realm1.com[/EMAIL] and Server2 user: [EMAIL="guest@realm2.com"]guest@realm2.com[/EMAIL] . In /etc/freeradius/proxy.conf file I defined realms for both servers:
 
Server1 /etc/freeradius/proxy.conf:
```

realm realm2.com {
        type = radius
        authost = IP of Server2
        acchost = IP of Server2
        secret = password
}


realm realm1.com {
        type = radius
        authhost = LOCAL
        accthost = LOCAL
        secret = password
}

```

Server2 /etc/freeradius/proxy.conf:
```


realm realm2.com {
        type = radius
        authost = LOCAL
        acchost = LOCAL
        secret = password
}


realm realm1.com {
        type = radius
        authhost = Server1 IP
        accthost = Server 1 IP
        secret = password
}

```

To test authentication with users I use program called NTRadPing.
If I send authentication request to the server which has those users locally in their database I get Accept-Accept and freeradius -X log reads the authentication with no errors.
Main problem is that if I want to send the authentication request through Server1 with realm2 user to Server2 which has that user locally in database I get Accept-Reject result from NTRadPing and I get this error in Server1 Freeradius -X where the request was initially sent: 
[pap] WARNING! No "known good" password found for the user.  Authentication may        fail because of this.++[pap] returns noop

And I get no freeradius -X log on server2 while I'm doing that, where the authentication should have been sent.

For some reason the authentication request is not sent from Server1 to Server2 and otherwise. I have those servers hosted in Digitalocean could there be some firewall issue or what?

Sorry, English is not my first language.

---

### Post by Kikikikikik on 2016-05-17
bump

---

### Post by QDR06VV9 on 2016-05-17
Hi I have moved your thread to a more suitable section.
Kind Regards && Good luck

---

### Post by Kikikikikik on 2016-05-18
Bump, I need help with this.

---

