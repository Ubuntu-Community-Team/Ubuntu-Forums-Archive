---
title: "Help with routing in ubuntu server"
date: 2019-06-08
forum: Server Platforms
---

### Post by arluy288 on 2019-06-08
I've been asked to make a project with Ubuntu server for college homework.
One of the requisites is to have the Ubuntu Server VM as a router. The professor sent us a guide but it's from 2009 and I think file structure changed since then (interfaces file). 
I am using Ubuntu Server 18.04 and I think this guide is for a very old version.

Full requisites of the project
>  1. The server will be mounted with a Linux Ubuntu Server system. There should be also two clients, Windows and Ubuntu Desktop (Manager and Worker Tester).2. The server will divide the company's network into two independent networks: one of them for management (as the Manager) and another for workers. As well must allow Internet access to any of the previous networks, since it will be the Only company equipment directly connected to the ADSL router (via IP dynamic).
3. The server will work within the company as an IP address server.
 All equipment will work with dynamic IP (a total of 100 computers) except the manager who must always obtain the same IP address.
4. To control the use made of the network, it is decided that all traffic will go to internet through the server. Therefore it must be allowed to increase the speed of traffic (where possible) through a proxy as well as filter the contents that users will be able to see In the company they want to be able to filter at least domains The only team that will not leak any traffic will be the one from manager. The rest should not be able to avoid going through it. **(SQUID + DansGuardian) **
5. The server must function as a firewall of the company, so it should not allow any incoming connection except those that are necessary according to these requirements. **(IPTABLES Block incoming connections)**
6. This server will also function as an internal domain name server of the company. This domain will be mycompany.com, naming this machine "Server" within that domain. The manager's team will be named "manager".
7. The server will be physically housed in a server room enabled for this purpose, so you should be able to manage it remotely, ensuring security and privacy of the data. **(SSH)**
8. As a web server you must serve pages, supporting at least the technologies HTML, PHP and MySql databases. In addition, each user of the company must be able to host your personal pages by yourself on the server the most safe possible.** (APACHE + SSH // MODULE USER PUBLIC HTML)**
9. Since your company handles two commercial brands, the web server must be able to serve two different domains: integralsolutions.com and onlinedomains.com. (DNS)
10. You want to be able to remotely administer the server through a web interface. **(WEBMIN)** Install one and configure it so that only the administrator has access to it.
11. It should be possible to remotely copy files to the server via FTP, but as only as an anonymous user. **(FTP Anonymous Script)**
12. The server must be completely stable, and in case it needs to be restarted by part of the company's personnel, it must return to normal operation according to these requirements.
 
*I wrote the bold quotes from what I think he wants from each point.*

This is my first big project and I don't really know how to approach it. My biggest struggle is with the network part, I already have the three virtual machines but I don't really know how to do everything at once (DNS, DHCP...) 

Sorry if there are some errors, English isn't my main language.

---

### Post by Doug S on 2019-06-08
> **arluy288 said:**
> I've been asked to make a project with Ubuntu server for college homework.Under the code of conduct rules here (which I can not find the exact reference at the moment), we have to be careful helping with homework.

This is a big project.

> **arluy288 said:**
> One of the requisites is to have the Ubuntu Server VM as a router. The professor sent us a guide but it's from 2009 and I think file structure changed since then (interfaces file). 
I am using Ubuntu Server 18.04 and I think this guide is for a very old version.
If you are referring to the /etc/network/interfaces file, then yes that changed with 18.04 LTS. Using 16.04 LTS might be more in-line with the professors reference.
You can also refer to the [Ubuntu 18.04 Serverguide]("https://help.ubuntu.com/lts/serverguide/index.html") or [Ubuntu 16.04 Serverguide]("https://help.ubuntu.com/16.04/serverguide/index.html"), also available in PDF (see here: [https://help.ubuntu.com/](https://help.ubuntu.com/) )

---

### Post by SeijiSensei on 2019-06-08
That's an enormous project. From my experience learning DHCP, DNS, Apache, routing, iptables and Squid, this should take at least a person-month.

---

### Post by Doug S on 2019-06-08
> **SeijiSensei said:**
> That's an enormous project. From my experience learning DHCP, DNS, Apache, routing, iptables and Squid, this should take at least a person-month.

+1, actually I would have said even more time.

---

### Post by aljames2 on 2019-06-08
> 11. It should be possible to remotely copy files to the server via FTP, but as only as an anonymous user. **(FTP Anonymous Script)**

A scary thought from a security standpoint.

As mentioned already the server guides can be a resource to help with various aspects of setting up and using an ubuntu server.

+2 a huge project, ditto that.  There are so many advanced topics involved in this project that you won't find all your answers in one place.  Much research will be needed.

---

