---
title: "Nameserver question"
date: 2010-04-05
forum: Server Platforms
---

### Post by dtommy79 on 2010-04-05
Hi,

I ordered my VPS but my domain name that I registered my VPS with is with another host. So obviously I have to update the nameserver options there.

How can i find out what my nameserver settings on my vps?
I'm using webmin

Thanks

---

### Post by koenn on 2010-04-05
what you should update is the name server that hosts the records for your domain name.

---

### Post by mbehamin on 2010-04-06
Hi 
i read your post two times but im not underestand what exactly your problem but 
if your problem is that your vpn name is localhost.yourdomain.com and you want to change it into myname.yourdomain.com just you can edit the /etc/hosts file. 
but if you wanna to check what exactly your name server on your linux you can cat /etc/resolve.conf file or type nslookup and then in nslookup type server to show you what is your name server ! 

regards

---

### Post by capscrew on 2010-04-06
> **mbehamin said:**
> Hi 
i read your post two times but im not underestand what exactly your problem but 
if your problem is that your vpn name is localhost.yourdomain.com and you want to change it into myname.yourdomain.com just you can edit the /etc/hosts file. 
but if you wanna to check what exactly your name server on your linux you can cat /etc/resolve.conf file or type nslookup and then in nslookup type server to show you what is your name server ! 

regards

You have look at this from a different perspective.  **koenn** has answered the question appropriately.

The OP is asking how to have the others requesting his *myname.yourdomain.com* resolve to his VPS.  This requires him to ask the DNS hosting service to configure the entry in their DNS servers to point (resolve) to the OP's new IP address.

The etc/hosts file is only for the localhost to resolve names to IP addresses.  The file /etc/resolv.conf (no e on the end of resolv) is to point the local host to the DNS server of choice.  This also is not what the OP was asking about.

The different perspective is that *[COLOR="DarkSlateGray"]**others also need to look for your host**[/COLOR]*.  You are looking at the problem as on of the localhost looking for DNS resolution.

---

