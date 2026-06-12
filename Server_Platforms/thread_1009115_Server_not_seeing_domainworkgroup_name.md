---
title: "Server not seeing domain/workgroup name"
date: 2008-12-12
forum: Server Platforms
---

### Post by happyhacker on 2008-12-12
When I start the server 8.10 one of the lines on the screen seems to be saying that it cannot associate the server name and defaults to the IP addres 192.168.etc. I also am unable to type into a browser on XP the swerver name and have to use the actual IP address.

Can someone tell me what's missing?

---

### Post by volkswagner on 2008-12-12
You can edit your /etc/hosts file.

If you have a static ip for the server add that and the name on and additional line under the loop back entries.

---

### Post by cdenley on 2008-12-12
Are you running apache?
> 
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

Try editing /etc/hostname to change your hostname to a fully-qualified domain name (such as mydomain.com), then run
```

sudo hostname mydomain.com

```

How are you expecting windows to resolve ubuntu's hostname? I believe you can install bonjour on windows to use zeroconf, or you can install samba on ubuntu to broadcast a netbios name.

---

### Post by happyhacker on 2008-12-12
Ah,if I add 192.168.x.x (I have fixed the IP of the server in the router) and put "servername" next to it then that should resolve - good, thanks. I have Samba running on the server so I guess when it starts up it will broadcast from Hosts file and then I can type the webmin address thus \\"servername"\(webmin access string). Is this the gist of it? I will retry next time I'm in work.

---

