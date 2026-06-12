---
title: "How to set up a fully qualified Domain/Host name?"
date: 2009-06-17
forum: Server Platforms
---

### Post by Radio91 on 2009-06-17
Hi

ok I'm having a few issues with my VPS. I need to set up a fully qualified domain/host name for the server.

When I got the VPS, all I got was a root account and password and two IP addresses. Ubuntu was already installed and the host name was set as my user name.

So to set up a fully qualified host name for my server I will need a domain? I have several in my godaddy account that I'm not using for anything.

So the first thing I need to do is? Point this domain name to one of my IP addresses for the server?

or

Edit records in ubuntu to set the hostname?

Can somebody go through this step by step on how to sort this issues out?

cheers

---

### Post by Bachstelze on 2009-06-17
> **Radio91 said:**
> 
So the first thing I need to do is? Point this domain name to one of my IP addresses for the server?

or

Edit records in ubuntu to set the hostname?

You'll have to do both, but the order doesn't matter. To change the hostname of your machine in Ubuntu, do [font="monospace"]sudo -i[/font] to get a root shell, then edit [font="monospace"]/etc/hostname[/font] and put your new hostname in it, replacing the old one. Finally, run [font="monospace"]hostname host.domain.tld[/font] and [font="monospace"]exit[/font] your root shell.

---

### Post by ghen on 2009-06-17
Wait, what are you trying to accomplish here and what's the situation?


Are you in a lease agreement with a company controlling the hardware or something?

Are you trying to set up a web server?

Did they install server or workstation ubuntu and what version?



Your hostname cam be whatever you want... and it can include .'s to look like a FQDN if you want. If this server is going to connect via VPN to a domain controller of some sort then you don't want the hostname to be that complicated since the DNS with your domain will append the correct suffix.

If its going to be a webserver then the hostname of the machine means squat. You can name it Yoda (personal favorite) and still give it a real public-facing domain name like [www.example.com](www.example.com)

---

### Post by Radio91 on 2009-06-17
Its a Virtual private server. I'm setting up a web server. But the server will host more than one website. 

It has ubuntu 8.04 sever installed and updated. I going to be setting up DNS namesevers ect 

I know the host name itself can be anything but If i want a fully qualified host name I need an actual domain name to point to the server correct? I don't want to use this domain name for any of the actual sites just for the server. 

So if Im setting this up I could call it Yoda.mydomain.com 

and then just point mydomain.com to one or both of my servers IP addresses?

---

### Post by ghen on 2009-06-17
Unfortunately that's where my expertise gets limited. I'm thinking that whatever DNS server houses your domain name would have to have a record of your server's name if you're going to access it like that but I'm not sure. So it would have an A record labeling 

yoda.example.com. IN A 69.9.64.11

and that's where it would direct www. and other queries.

---

### Post by Malg on 2009-06-17
Do you want your server to be just a dns server or a web server running different websites?

If you would like your server to run website you need Apache server and presumable mysql and php running. You can check if your apache server is running by going to:

cd /etc/init.d/apache2 restart 

If apache is not installed you will need to install it and then add your virtual servers to apache (ie different domains ). Virtual servers in apache is not the same as the virtual server which you have ordered from a hosting company.

If you want to run dns server you will also need to add your zones in the /etc/bind/named.conf.local file.

If you have any visual interface such as Plesk it is easier to work with that . Otherwise you can install webmin which is free.

---

### Post by LepeKaname on 2009-06-17
This worked for me (as far as I remember):

Edit your /etc/hostname file and add your host name there (for example):

```
myserver
```

And run: 

```
sudo hostname myserver
sudo /etc/init.d/hostname.sh

```

Then at your /etc/hosts:
```
127.0.0.1    myserver.myexample.com  myserver localhost
```

If you have a static IP, you can set it there like:
```
127.0.0.1   myserver localhost
250.69.47.112  myserver.myexample.com  myserver 
```

That way you will have your FQN .

---

