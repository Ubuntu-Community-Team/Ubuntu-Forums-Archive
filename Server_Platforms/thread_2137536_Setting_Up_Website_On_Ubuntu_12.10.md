---
title: "Setting Up Website On Ubuntu 12.10"
date: 2013-04-21
forum: Server Platforms
---

### Post by marwan83 on 2013-04-21
Hi,

I'm really new to Ubuntu. I have moved my website from a complete managed shared hosting to a complete unmanaged dedicated cloud hosting. Currently, I'm using Ubuntu 12.10 and I'm really stick. I'm looking for someone who can help. Even if his support will be paid. I have got 2 servers. One server will handle the website and the other one will handle mails for all the domains. Here's a list of what I want to do:

Move all my domains (around 5 domains) to the new Ubuntu servers.
Configure DNS for the new setup (2 servers).
Setup the http on all domains to the website.
Setup mail services and move them from the old hosting to the new server.
Setup a firewall on both servers.

I'm a computer engineer but I come from Windows environment. I have the logic. I know what I want to do but I dont know how to do it on Ubuntu.

---

### Post by darkod on 2013-04-21
First about the DNS. If your domain registrar has any type of DNS control panel, I would use that instead of your own dns servers. Since you are not experienced to run bind dns servers, it takes one thing off the table for you. As long as the registrar allows you modifying the records for web and mail, it would be the better option.
If the registrar only allows you to specify dns servers to use with the domains, you have no option but to run your own dns servers. In that case this short and prcise how-to might help you. Just modify it for your needs:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

Installing apache for the web services shouldn't be an issue. The configuration is also simple, you just have to specify all domains separately and their document root. The official documentation is here, google can give you loads of other tutorials too:
[https://help.ubuntu.com/12.04/serverguide/web-servers.html](https://help.ubuntu.com/12.04/serverguide/web-servers.html)

For mail services I would use postfix as MDA and dovecot as MTA. The setup is also mainly working by default:
[https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html)

But before you even start, is there a reason you chose 12.10? Because it's the latest version? For a server most people would run only LTS versions, which have long term support. The latest LTS is 12.04 and it will be supported until April 2017. The 12.10 is supported only until April 2014.

What do you plan to do with the firewall? Close everything except the ports for web and email? And ssh for remote administration?

---

### Post by marwan83 on 2013-04-21
> **darkod said:**
> First about the DNS. If your domain registrar has any type of DNS control panel, I would use that instead of your own dns servers. Since you are not experienced to run bind dns servers, it takes one thing off the table for you. As long as the registrar allows you modifying the records for web and mail, it would be the better option.
If the registrar only allows you to specify dns servers to use with the domains, you have no option but to run your own dns servers. In that case this short and prcise how-to might help you. Just modify it for your needs:
[http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/](http://www.pressbyte.com/4581/setup-dns-ubuntu-vps-quick/)

Installing apache for the web services shouldn't be an issue. The configuration is also simple, you just have to specify all domains separately and their document root. The official documentation is here, google can give you loads of other tutorials too:
[https://help.ubuntu.com/12.04/serverguide/web-servers.html](https://help.ubuntu.com/12.04/serverguide/web-servers.html)

For mail services I would use postfix as MDA and dovecot as MTA. The setup is also mainly working by default:
[https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html)

But before you even start, is there a reason you chose 12.10? Because it's the latest version? For a server most people would run only LTS versions, which have long term support. The latest LTS is 12.04 and it will be supported until April 2017. The 12.10 is supported only until April 2014.

What do you plan to do with the firewall? Close everything except the ports for web and email? And ssh for remote administration?

Hey darkod! Thanks a lot for your reply. Here are my answers below:

DNS is not an issue. I'm using the DNS control panel of the provider I'm hosting my server on. I'm able to create CNAMEs, A records, MTXs and so on. It is a piece of cake. Right now, I have the following names redirected to my IP: auto-works.info, web.auto-works.info, mail.auto-works.info.

I will read the apache2 document you just sent me. I really feel lost. However I will give it another shot. Apache is installed on web.auto-works.info. I just need to configure it to listed and start serving.

I did choose postfix as MDA and dovecot as MTA as you highlighted. I did install them on another server and will be playing with it also. My challenge is to add different domains to postfix and dovecot so they can process inbound and outbound for all different mailboxes in those domains.

I want to enable the firewall to have more protection for both servers. I will be running ftp, mail, and web services on the servers. I'm so worried about security. Our services are purely online service. Otherwise w wouldnt be investing that much moving and configuring the new setup. We are looking for the best performance for our services.

I choose version 12.10 as it was the most recent version. When I created the server I just chose that version. I dont have any particular other reason. I also think it helps staying on the most recent version?

---

### Post by CharlesA on 2013-04-21
Check out virtual users for Dovecot/postfix.

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

If you are going to be running a server, I would suggest sticking with the LTS releases. support for 12.10 ends in April 2014, while 12.04 support ends in April of 2017.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by SeijiSensei on 2013-04-22
You've created a very large task for yourself here.  Let's start with a couple of hints on getting the websites up and running.  

First, you need to start by reading this document: [https://help.ubuntu.com/12.04/serverguide/web-servers.html](https://help.ubuntu.com/12.04/serverguide/web-servers.html).  Start by reading the Apache documentation.  I'll just concentrate on getting one virtual server up and running.

Ubuntu puts the configuration file for each virtual host in the directory /etc/apache2/sites-available/.  You then "activate" the available sites with the command "a2ensite".  In practice, it creates a "symbolic link" or "symlink" in /etc/apache2/sites-enabled/ that points to the file in /sites-available/ that defines the virtual host. (A Unix symbolic link is somewhat akin to a Windows "shortcut" though no actual file is created.)  

So what you need to do is follow that guide to create a virtual host definition that will reside in /sites-available/ and be activated.  One thing that file will define is the "DocumentRoot" for the server, the directory that corresponds to the root URL [http://example.com/](http://example.com/).  The default location on Ubuntu is /var/www, but that is a directory only root can write to.  I put my sites in users' home directories.

In your case, I would create a user called "autoworks" and create a directory in that user's home directory to house the website.  I would use /home/autoworks/web, but you can choose whatever you want.  Make that the DocumentRoot in the site's configuration file and apply any <Directory> controls you need.  This makes managing the site much easier since you just need to log in as user autoworks to access the website.

---

### Post by marwan83 on 2013-04-22
> **SeijiSensei said:**
> You've created a very large task for yourself here.  Let's start with a couple of hints on getting the websites up and running.  

First, you need to start by reading this document: [https://help.ubuntu.com/12.04/serverguide/web-servers.html](https://help.ubuntu.com/12.04/serverguide/web-servers.html).  Start by reading the Apache documentation.  I'll just concentrate on getting one virtual server up and running.

Ubuntu puts the configuration file for each virtual host in the directory /etc/apache2/sites-available/.  You then "activate" the available sites with the command "a2ensite".  In practice, it creates a "symbolic link" or "symlink" in /etc/apache2/sites-enabled/ that points to the file in /sites-available/ that defines the virtual host. (A Unix symbolic link is somewhat akin to a Windows "shortcut" though no actual file is created.)  

So what you need to do is follow that guide to create a virtual host definition that will reside in /sites-available/ and be activated.  One thing that file will define is the "DocumentRoot" for the server, the directory that corresponds to the root URL [http://example.com/](http://example.com/).  The default location on Ubuntu is /var/www, but that is a directory only root can write to.  I put my sites in users' home directories.

In your case, I would create a user called "autoworks" and create a directory in that user's home directory to house the website.  I would use /home/autoworks/web, but you can choose whatever you want.  Make that the DocumentRoot in the site's configuration file and apply any <Directory> controls you need.  This makes managing the site much easier since you just need to log in as user autoworks to access the website.

waw! That was an awesome writeup SeijiSensei. Im currently working the same way mentioned. I started reading 2 days ago and now I have a better understanding to what you are saying. Im a Microsoft boy so I know how emails and websites work but not Ubuntu environment. Im sure you guys are a good help if I will need anything.

---

### Post by marwan83 on 2013-04-22
> **CharlesA said:**
> Check out virtual users for Dovecot/postfix.

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

If you are going to be running a server, I would suggest sticking with the LTS releases. support for 12.10 ends in April 2014, while 12.04 support ends in April of 2017.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
Thats what Im doing Charles. I have moved down to LTS.

---

### Post by marwan83 on 2013-04-30
I have created a thread related to this one. Please check: [http://ubuntuforums.org/showthread.php?t=2140585](http://ubuntuforums.org/showthread.php?t=2140585)

---

### Post by tad1073 on 2013-04-30
> **SeijiSensei said:**
> In your case, I would create a user called "autoworks" and create a directory in that user's home directory to house the website.  I would use /home/autoworks/web, but you can choose whatever you want.  Make that the DocumentRoot in the site's configuration file and apply any <Directory> controls you need.  This makes managing the site much easier since you just need to log in as user autoworks to access the website.

Couldn't he just give write permisisons to himself or a group for /var/www/sitename?

---

### Post by brent1975 on 2013-05-01
> **tad1073 said:**
> Couldn't he just give write permissions to himself or a group for /var/www/sitename?
That is how I have my server set up. /var/www/site1.  Everyone has their own methods on how they want to organize the apache docroot. weather it be in var/www/site1  or /home/sites/site1. You can be creative on your organization.

---

