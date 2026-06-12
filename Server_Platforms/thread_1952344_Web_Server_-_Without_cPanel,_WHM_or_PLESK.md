---
title: "Web Server - Without cPanel, WHM or PLESK"
date: 2012-04-04
forum: Server Platforms
---

### Post by maverickaddicted on 2012-04-04
Hello Guys,

I want to set up a web server without using any software like cPanel, WHM or PLESK. Currently I am using Ubuntu 10.04. Is there any good guide available on the web?

---

### Post by Cheesemill on 2012-04-04
I've always found the Linode guides to be excellent:

[http://library.linode.com/lamp-guides/ubuntu-10.04-lucid](http://library.linode.com/lamp-guides/ubuntu-10.04-lucid)

---

### Post by maverickaddicted on 2012-04-04
> **Cheesemill said:**
> I've always found the Linode guides to be excellent:

[http://library.linode.com/lamp-guides/ubuntu-10.04-lucid](http://library.linode.com/lamp-guides/ubuntu-10.04-lucid)

Thank You Very Much, the guide was very useful;solved my maximum queries.

Do you have any such good guide for bind and ftp(vsftp)?

---

### Post by Cheesemill on 2012-04-04
Check out the Linode library again for DNS using NSD:
[http://library.linode.com/dns-guides/nsd-authoritative-dns-ubuntu-10.04-lucid](http://library.linode.com/dns-guides/nsd-authoritative-dns-ubuntu-10.04-lucid)

If you want to use BIND then see here:
[https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html)

I would strongly recommend against using FTP, it is inherently insecure. Use SCP or SFTP instead if you can.

---

### Post by maverickaddicted on 2012-04-05
> **Cheesemill said:**
> Check out the Linode library again for DNS using NSD:
[http://library.linode.com/dns-guides/nsd-authoritative-dns-ubuntu-10.04-lucid](http://library.linode.com/dns-guides/nsd-authoritative-dns-ubuntu-10.04-lucid)

If you want to use BIND then see here:
[https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/dns-configuration.html)

I would strongly recommend against using FTP, it is inherently insecure. Use SCP or SFTP instead if you can.

I am not able to understand Ubuntu Help Guide. They have configured Primary and Secondary DNS Server, but I have only one server. 
I have already installed vsftp, which is for internal development purpose. It is not used outside the local network. I am facing problem regarding the permissions.

1) I created a user using webmin and configured it home directory to a directory under my apache web directory.

2) Primary group of that user is www-data.

3) chown that web directory to the user and group to www-data.

4) When I log in to my wordpress backend and try install some theme via backend, it ask me FTP username and password.

5) If I upload the theme manually via FTP client(like filezilla). The theme does not work perfectly. I have to SSH to the server using admin account and change the permission of theme to 0755 manually. The user which is created for that web directory, does not have rights to modify the permission of the file. Everytime, ssh and chmod using admin account to get it working.

---

### Post by webservervideos on 2012-04-05
you can use only one server for dns... 
 at your registrar register ns1.yourdomain.com and ns2.yourdomain.com
 try to use the same ip address for both. T
his may not work and you need a second ip address to be allowed to do this.  

alias your eth0 (not sure how to do this in ubuntu, sorry) and add the second ip address... this way eth0 and eth0:1 or however ubuntu names them each have a separate ip address. 

your bind will listen to both...no problems.

 add both ipaddresses to your eth as DNS1 and DNS2.. 
You should not have to do anything with resolv.conf, but if you do, add both ips as nameservers.   

the nameserver website checkers will not like that both nameservers point at the same box, but so what.

 /etc/named.conf set up as normal (if you can figure it out)

 /var/named/ as normal, but add records in both zone and addr files for ns1 and ns2 with their ipaddresses.  

don't forget to allow recursion in named.conf so you can use it for resolving outgoing packets.  

with just one server, I would say it is perfectly fine to do it with just one nameserver, the one on the machine. Done it many times myself, works fine.

---

### Post by maverickaddicted on 2012-04-10
> 
I am not able to understand Ubuntu Help Guide. They have configured  Primary and Secondary DNS Server, but I have only one server. 
I have already installed vsftp, which is for internal development  purpose. It is not used outside the local network. I am facing problem  regarding the permissions.

1) I created a user using webmin and configured it home directory to a directory under my apache web directory.

2) Primary group of that user is www-data.

3) chown that web directory to the user and group to www-data.

4) When I log in to my wordpress backend and try install some theme via backend, it ask me FTP username and password.

5) If I upload the theme manually via FTP client(like filezilla). The  theme does not work perfectly. I have to SSH to the server using admin  account and change the permission of theme to 0755 manually. The user  which is created for that web directory, does not have rights to modify  the permission of the file. Everytime, ssh and chmod using admin account  to get it working. 	

Any idea about FTP problem?

---

### Post by SeijiSensei on 2012-04-10
You **can** use one server as both your primary and secondary DNS server, but it's definitely not considered good practice.  You might see whether you can set up your server as the primary and the registrar's server as your secondary.

The DNS RFCs even discourage having the primary and secondary within the same network topology.  I violate that rule because both my servers are in Linode's New Jersey facility, but I doubt there would be a system-wide collapse.  If I were really concerned, I'd put one of the virtuals at Linode's London facility.

---

### Post by maverickaddicted on 2012-04-11
> **SeijiSensei said:**
> You **can** use one server as both your primary and secondary DNS server, but it's definitely not considered good practice.  You might see whether you can set up your server as the primary and the registrar's server as your secondary.

The DNS RFCs even discourage having the primary and secondary within the same network topology.  I violate that rule because both my servers are in Linode's New Jersey facility, but I doubt there would be a system-wide collapse.  If I were really concerned, I'd put one of the virtuals at Linode's London facility.

Thanks for the idea. I have understood the basic about DNS. I am reading more guide about it. As there is a time to for taking it into an action. But till then, what is the problem with my FTP Connection, can you help me there?

---

