---
title: "Please explain FQDN for me."
date: 2017-12-27
forum: Server Platforms
---

### Post by eddie19 on 2017-12-27
I am setting up Ubuntu server 17.04 so I can host my websites. I have about seven right now.  I am going to be using webmin and virtualmin as well. I need some basic explanation about FQDN. Does it have to be registered with a registrar?
Can I use any name in the domain piece?  If the Ubuntu servers host name is Bob what might be the domain name part. I understand that I must connect my Ubuntu servers host name with a domain name. Does that domain have to be one that is registered?

 Thanks for any help
eduardo

---

### Post by darkod on 2017-12-27
1. People mostly use LTS releases only. The current one is 16.04 LTS and the next one will be 18.04 LTS in April 2018. I wouldn't use a non-LTS release like 17.04 for a server.
2. In short, the FQDN consists of machine name part and the domain part put together. But in this case it doesn't have to be a registered domain or even a real one. If you have websites then you probably have registered domains. If you do, you can select one and use it in the FQDN you assign to the server but that does not mean it can't serve websites for other domains too. For example it can be bob.mydomain1.com and you can have all 7 websites [www.mydeomain1.com](www.mydeomain1.com) to [www.mydomain7.com](www.mydomain7.com) hosted on that same server.

---

### Post by LHammonds on 2017-12-27
darkod is correct.

The FQDN (Fully Qualified Domain Name) in terms of web sites is the externally-registered name that points to an IP address via DNS servers.

Example:  You buy foobar.com domain.

You can then edit the DNS records to redirect all traffic to that domain to a specific IP address (8.8.8.8 being whatever your static external IP is):

@foobar.com -> 8.8.8.8

You can then edit your external DNS records to include sub-domain so you can host different websites and break them out by FQDN:

@foobar.com -> 8.8.8.8
[www.foobar.com](www.foobar.com) -> 8.8.8.8
forum.foobar.com -> 8.8.8.8
ftp.foobar.com -> 8.8.8.8

You then modify your external hardware firewall to redirect incoming traffic on 8.8.8.8 based on the ports you will be using to your internal server (192.168.0.2 being whatever your internal IP is):

8.8.8.8:80 -> 192.168.0.2:80
8.8.8.8:443 -> 192.168.0.2:443
8.8.8.8:21 -> 192.168.0.2:21
8.8.8.8:990 -> 192.168.0.2:990

On your web server, you then have your configuration files setup to redirect incoming traffic based on FQDN such as anything coming from forum.foobar.com goes to /var/www/forum and anything from [www.foobar.com](www.foobar.com) goes to /var/www/main, etc.

The name inside /etc/hosts and /etc/hostname are completely irrelevant to websites.  You can have any amount of various FQDN coming into a single server and later start breaking them out if the server load becomes too much.  Such as making a dedicated server for FTP, www and forum as such:

@foobar.com -> 8.8.8.8
[www.foobar.com](www.foobar.com) -> 8.8.8.8
forum.foobar.com -> 8.8.8.9
ftp.foobar.com -> 8.8.8.10

8.8.8.8:80 -> 192.168.0.3:80
8.8.8.8:443 -> 192.168.0.2:443
8.8.8.9:80 -> 192.168.0.3:80
8.8.8.9:443 -> 192.168.0.2:443
8.8.8.10:21 -> 192.168.0.2:21
8.8.8.10:990 -> 192.168.0.2:990

LHammonds

---

### Post by eddie19 on 2017-12-27
Thanks for the quick replies! I think I have it now. Thanks for the additional info as well.
Have a great day):P
eduardo

---

