---
title: "Need Some Guidance with LAMP Server Setup"
date: 2006-11-01
forum: Server Platforms
---

### Post by laceiba on 2006-11-01
Howdy Folks,

I recently installed the LAMP server option of 6.10 onto an old computer in my office. Since this thing is old and underpowered, I'd like to stick to the command line. I have a few basic questions and I am wondering where to start. My Googling has not been very effective so far.

This LAMP box lives on an Active Directory Windows network that I do not completely control. It will only be used within my office and will never see the Internet. I hope to run a Drupal-powered site on it eventually. 

I can go to a Windows computer, open a browser, type in the IP address of my LAMP server, and I will see the default Apache install. How can I make it so that I can access my LAMP server by its hostname? Do I need Samba? At present, I can ping my LAMP server by IP, but not by name.

My second question is, how do you recommend uploading files to the server? Since I will always be accessing it on the same network, is creating a Samba share for var/www the way to go, or should I do something else like SSH?

Thank you in advance for any help.

---

### Post by wpwood3 on 2006-11-01
Personally, I would go the SSH route. I've managed Linux servers for years using SSH and that works fine.
Install the SSH server on your Ubuntu box and install an SSH client on your Windows box.
There are several guides here for getting Apache, MySQL and PHP configured.

---

### Post by bmathis on 2006-11-02
> **laceiba said:**
> How can I make it so that I can access my LAMP server by its hostname? Do I need Samba? At present, I can ping my LAMP server by IP, but not by name.

You dont need to have samba installed to update dns. As far as I know, there is 2 different ways, but someone else might have another way.

1. If you have access to DNS on the domain server you can manually add a host file for the specific IP address.

2. Edit the dhclient.conf file located at /etc/dhcp3/dhclient.conf and add or uncomment the following lines:

```
send fqdn.fqdn "myhostname";
send fqdn.encoded off;
send fqdn.server-update on;
do-forward-updates on;
```

Update us if this works or you find out a different way... have fun! ;)

---

### Post by laceiba on 2006-11-02
Thank you both for your suggestions. I will look into implementing them. 

> There are several guides here for getting Apache, MySQL and PHP configured.

I found several of them, but none of them seemed to address the problem of domain name resolution on a private, Windows-based, Active Directory network. Many of the guides focus on Internet-facing servers, where DNS is taken care of through non-Windows means. Thank you again. I will get back to you on how I am progressing.

---

### Post by laceiba on 2006-11-02
OpenSSH is installed and running nicely. Samba is also installed since making a DNS change was not really an option. Now I can access my server by the host name. Many thanks.

---

