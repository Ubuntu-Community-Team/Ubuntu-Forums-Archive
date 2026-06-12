---
title: "Setting up /etc/hosts file for a single domain"
date: 2010-05-22
forum: Server Platforms
---

### Post by ckennow on 2010-05-22
Current /etc/hosts file config


```
127.0.0.1       localhost
127.0.1.1       server.new.rr.com       server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Perfect Server 10.04 w/ISPConfig3 suggested config

```
127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

So the question is...

The howtoforge tutorial suggests this configuration but this is with the presumption that I will be hosting multiple domains using ISPConfig3. I only wish to host one domain. In the past when using the walkthrough's settings I had to send e-mail's to <username@server.example.com> I want to be able to send email to <username@example.com> instead. What are the proper settings for the hosts file for one single domain so that when email is sent to/from my server it will need only be sent to/from <username@example.com> not <username@server.example.com>?

---

### Post by bab1 on 2010-05-22
> **ckennow said:**
> Current /etc/hosts file config


```
127.0.0.1       localhost
127.0.1.1       server.new.rr.com       server

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

Perfect Server 10.04 w/ISPConfig3 suggested config

```
127.0.0.1       localhost.localdomain   localhost
192.168.0.100   server1.example.com     server1

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

So the question is...

The howtoforge tutorial suggests this configuration but this is with the presumption that I will be hosting multiple domains using ISPConfig3. I only wish to host one domain. In the past when using the walkthrough's settings I had to send e-mail's to <username@server.example.com> I want to be able to send email to <username@example.com> instead. What are the proper settings for the hosts file for one single domain so that when email is sent to/from my server it will need only be sent to/from <username@example.com> not <username@server.example.com>?

The /etc/hosts file only maps IP addresses to hostnames (and aliases)  There are no email pointers (MX) in the /etc/hosts file.

In addition it only provides the information to the host on which it resides.  If you read the information on [**_ISPConfig_**]("http://www.ispconfig.org/") you will see that it uses BIND9 for DNS and MX records.

---

### Post by ckennow on 2010-05-22
> **bab1 said:**
> The /etc/hosts file only maps IP addresses to hostnames (and aliases)  There are no email pointers (MX) in the /etc/hosts file.

In addition it only provides the information to the host on which it resides.  If you read the information on [**_ISPConfig_**]("http://www.ispconfig.org/") you will see that it uses BIND9 for DNS and MX records.

Thank you can you give me some insight as to why my issue might have been happening then. I had gotten it to work at one point but I didn't even touch the BIND9 settings. What configuration controls that and what are the settings to be concerned with?

BTW I don't care about ISPConfig. I don't need it.

---

### Post by bab1 on 2010-05-22
I wouldn't have a clue.  I was only commenting on the use of /etc/hosts.

---

### Post by ckennow on 2010-05-22
> **bab1 said:**
> I wouldn't have a clue.  I was only commenting on the use of /etc/hosts.

Last time when I did get it working it was after setting these settings. I will go through it again and see if I can get it to work again. I just wish I knew what settings it was that control this behavior.

---

### Post by bab1 on 2010-05-22
> **ckennow said:**
> Last time when I did get it working it was after setting these settings. I will go through it again and see if I can get it to work again. I just wish I knew what settings it was that control this behavior.

As I said BIND9 uses MX for email redirection.  Bind9 uses C and A records to define the hostname to IP mapping. At its most basic you place these records in a conf file.

I think that you have forgotten how to set this up using ISPCOonfig.  I browsed the guide and I see that you do have to install BIND9.  But you do not directly configure it.  When you install ISPConfig you will have a web page to configure the mail records (MX) and the FQDN (domain).  Just follow the instructions.  Try and not jump ahead.

FWIW -- I think these type of "helper programs' cripple users.  You have no idea what is going on behind the scenes.  If you want to continue to use ISPConfig, at least take notes on what you do so you can refer to them later on.

You should make am attempt to learn what is going on with the supporting tools so you can possibly solve these things on your own.  At the very least you would be able to troubleshoot the problems.

---

### Post by ckennow on 2010-05-22
> **bab1 said:**
> As I said BIND9 uses MX for email redirection.  Bind9 uses C and A records to define the hostname to IP mapping. At its most basic you place these records in a conf file.

I think that you have forgotten how to set this up using ISPCOonfig.  I browsed the guide and I see that you do have to install BIND9.  But you do not directly configure it.  When you install ISPConfig you will have a web page to configure the mail records (MX) and the FQDN (domain).  Just follow the instructions.  Try and not jump ahead.

FWIW -- I think these type of "helper programs' cripple users.  You have no idea what is going on behind the scenes.  If you want to continue to use ISPConfig, at least take notes on what you do so you can refer to them later on.

**You should make am attempt to learn what is going on with the supporting tools so you can possibly solve these things on your own.  At the very least you would be able to troubleshoot the problems.**

Gee I thought that is what I was doing. Kind of the reason I am asking these questions. Why do you feel the need to berate me when I am attempting to do exactly what you are suggesting.

---

### Post by ckennow on 2010-05-22
As I've said before I am not using ISPConfig I am only hosting 1 site. I don't need to run a hosting control panel. I am only looking for a simple LAMP server with mail. I am using the ISPConfig walkthrough as a guide to setup some of the applications needed. I am wondering why the mail seems to demand using the entire server.example.com suffix. If  it is BIND9 that controls this then please enlighten me.

---

### Post by bab1 on 2010-05-22
> **ckennow said:**
> As I've said before I am not using ISPConfig I am only hosting 1 site. I don't need to run a hosting control panel. I am only looking for a simple LAMP server with mail. I am using the ISPConfig walkthrough as a guide to setup some of the applications needed. I am wondering why the mail seems to demand using the entire server.example.com suffix. If  it is BIND9 that controls this then please enlighten me.

Ahhhh, you never said you are not going to use the control panel.  

I already told you the that BIND is the tool that you need to configure.  You will have to **[_search for tutorials_**]("http://lmgtfy.com/?q=bind9+configuration") on BIND9 and configuration of DNS C, A and MX records.

---

### Post by ckennow on 2010-05-22
> **bab1 said:**
> **Ahhhh, you never said you are not going to use the control panel.  **

I already told you the that BIND is the tool that you need to configure.  You will have to **[_search for tutorials_**]("http://lmgtfy.com/?q=bind9+configuration") on BIND9 and configuration of DNS C, A and MX records.

Read my second post (my first reply to you)

---

