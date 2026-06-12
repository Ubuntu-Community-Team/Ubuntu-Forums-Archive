---
title: "PuTTY and hostname"
date: 2008-11-01
forum: Server Platforms
---

### Post by NeoGreen on 2008-11-01
Hello all, I have a question.. I recently installed and configured and Ubuntu Server to run LAMP.  I want to be able to log on to the server using PuTTY.  However...I have to type the IP address to access it instead of the host name...is there a way to configure it so I can access it jut by typing the name of the server?  Any advice will be appreciated.  

Thanks :)

---

### Post by lykwydchykyn on 2008-11-01
You need some way for your client to resolve the name to an IP.  If you have your own DNS server, you can put a record in there.  Otherwise, you can make an entry in the hosts file of the client to point it to the machine:

```

192.168.blah.blah    my_servers_name

```

Hosts file on Windows is c:\windows\system32\drivers\etc\hosts

---

### Post by NeoGreen on 2008-11-02
Great it worked.  Thanks for the advice.

---

