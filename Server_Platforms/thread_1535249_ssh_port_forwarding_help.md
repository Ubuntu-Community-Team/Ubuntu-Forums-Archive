---
title: "ssh port forwarding help:"
date: 2010-07-20
forum: Server Platforms
---

### Post by magnetpest2k7 on 2010-07-20
Hello All,

I am trying to use the ssh port forwarding. I have used the following commands but i am refused from my home computer since it is not accepting the password i give. Here is the way i connect. say the password is 1234 for my home pc.

ssh -R 2210:localhost:22 <homeuser_name>@<ip_address_of_homeuser>

then i enter the password which is 1234

now in home pc i give:

ssh -p 2210 localhost
<homeuser_name>@localhost's password: (here i enter 1234)
but the system doesn't accept the password and says:
Permission denied, please try again.
<homeuser_name>@localhost's password:

I guess I am going wrong some where. Any help is appreciated 

Thanks
Vin

---

### Post by beren.olvar on 2010-07-20
I think you cannot just forward port 22 unless you are root... even then you might have problems since port 22 will probably be in use.

in the ssh manpage:

"Privileged ports can be forwarded only when logging in as root on  the  remote
machine."

try doing it backwards. In your local computer write:
```

ssh -l remoteuser -N -L 2210:localhost:22 remoteaddress
```

then, in some other terminal doing
```

ssh -p 2210 remoteuser@localhost
```

will take you to the remoteaddress, but note that external connections to remoteaddress are still going to be handled by that server, not your local computer.

---

### Post by anon.jdh on 2010-07-20
I use SSH tunneling to get to my machine at home. 
Here are the commands:

ssh -L <local port>:<remotehost name or ip>:<remote random port> -p <actual listening ssh port> <user>@<remotehost name or ip>

ssh -L 5901:myhomedomain.net:5901 -p 2222 [email]jdh@mydomain.net[/email]

Just make sure that the port you use for SSH is forwarded at the router or you'll never get to it.

---

### Post by maclenin on 2011-07-13
Thanks, **anon.jdh**, for laying it out so clearly....

---

### Post by brighty22 on 2011-07-13
Use a service like [DynDNS]("https://www.dyndns.com/account/services/hosts/add.html") to give your IP its own domain name for free. Doubly worth it if you have a dynamic IP address; Ubuntu can be configured to update the pointer when it changes.

---

