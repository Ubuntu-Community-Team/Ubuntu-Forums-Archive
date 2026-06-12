---
title: "is connecting to a mysql db secure?"
date: 2008-12-27
forum: Server Platforms
---

### Post by enzo12345 on 2008-12-27
I am running PHP and Apache on a linux machine.

I am using it to connect to a mysql database located somewhere eon the Internet.

Is this secure? are the password and username sent unencryted?

How can I make it secure?

---

### Post by quad3d@work on 2008-12-27
I'm afraid your current setup is not secure at all.

Your MySQL connection user have to have SSL set as mandatory. Means created with "REQUIRE SSL" (encrypted) or "REQUIRE x509" (encrypted and secured) privileges.

```
GRANT .... IDENTIFIED BY 'password' REQUIRE x509;
```Create your CA cert on server. Create both server and client keys and sign it with your own CA cert. Tell the server to use the CA cert and server cert/key. Export your CA cert and client cert/key to all your clients. Issue the proper MySQL connection call using all three.

Also set your firewall (assuming both ends have static IP) only allow MySQL port (default 3306) access between the two.


EDIT
Disable AppArmor or modify it not to include mysqld. Otherwise you won't get MySQL server with SSL to work. I was frustrated for a day over this.... :)

---

### Post by enzo12345 on 2008-12-28
Hi,

Where am i meant to type

```
GRANT .... IDENTIFIED BY 'password' REQUIRE x509;
```

?

I using a shared mysql database, and I do not have access to a shell on the computer it is running.

All i have is the IP address to which I connect using PHP, I just want to make sure the data is encrypted. Is it possible on my shared mysql server?

---

### Post by ikonia on 2008-12-29
1.) use ssl on the mysql listening port
2.) lock down the users to hosts.

eg: Grant all privilages on database.* to $user@host identified by password

this will only allow the "user" to connect from that specific host, so if someone does have your password it won't matter as much unless they are on your host.

3.) make it even more secure and don't connect remotley, login to the machien via ssh and use the localhost to connect to mysql.

---

### Post by enzo12345 on 2008-12-29
hey thanks for your suggestions, but im still unsure.

1) how can I use ssl on the mysql listening port? 
I have set up tunnels before but that was on my own linux machine. I have rented a mysql database from a company, all I have is an IP to which I can connect to my database. It is also on microsofts IIS server.

2) If I lock down my own user to a host, when my IP changes will I get locked out? (im using a cable broadband)

3) I cannot connect with ssh because I dont think its set up on the mysql server, and its not linux which makes it more awkward.

Thanks any ideas suggestions welcome.

---

### Post by vpsville on 2008-12-29
Take a look at Navicat, its wonderful.  You can also connect over an ssh tunnel with just a shell account on the server.  That way you can completely isolate the Mysql server from the internet, with local access only.

Its also the best graphical database tool out there for MySQL (IMHO). Worth every penny.

---

### Post by quad3d@work on 2008-12-29
> **enzo12345 said:**
> hey thanks for your suggestions, but im still unsure.

1) how can I use ssl on the mysql listening port? 
I have set up tunnels before but that was on my own linux machine. I have rented a mysql database from a company, all I have is an IP to which I can connect to my database. It is also on microsofts IIS server.


I am not sure how MySQL is installed on this Windows host. You might want to check with your host see if it supports SSL. In Linux, MySQL server have to be compiled with SSL option, otherwise it won't support it.

> **enzo12345 said:**
> 
2) If I lock down my own user to a host, when my IP changes will I get locked out? (im using a cable broadband)


Yes, you will get locked out.

> **enzo12345 said:**
> 
3) I cannot connect with ssh because I dont think its set up on the mysql server, and its not linux which makes it more awkward.

Thanks any ideas suggestions welcome.

Talk to your host and express your concerns to them, see what they can do for you. At least try to get some type of encryption going...

You can also just rent a VPS slice with enough RAM to support MySQL server. You can probably PM vpsville see what kind of deal they can cut you. vpsville is advertising on WHT right now. :)

---

