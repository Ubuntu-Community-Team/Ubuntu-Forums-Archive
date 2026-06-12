---
title: "Server Networking Issues"
date: 2009-07-30
forum: Server Platforms
---

### Post by East82 on 2009-07-30
I have a Windows background in networking and after using Ubuntu desktop for a while and Ubuntu Server recently am confident in their stability, compatability and usability. That being said I have some concerns with a Linux environment and I'm hoping someone will point me in the right direction. This is not a Windows versus Linux deal ...I just have a myopic point of reference at this point :) 

So, here goes:


[LIST]
[*]With Apache, can I configure alternate physical locations for sites other than /var/www? For example, another drive or even another server. Also, any good GUI tools for administering LAMP?
[*]I really like Active Directory. Anything similar with Ubuntu? Tools to enforce policies, run scripts, install software, designate OU's ...Those sorts of things.
[*] What's a good email server for Ubuntu? I'm looking for something that has good archiving and search on the server side and web access and mobile device integration on the client side.
[*]DNS and NetBios - With Windows I can find any Windows machine on a network easily. I'm thinking using BIND9 on the server and SMB Client on workstations would be the solution here. Correct?? Most likely will be running in a mixed MS and Linux environment.
[*]In Windows networking you have the concept of the Forest / Domain / Domain Controller (Running AD) and can control access to resources based on membership. You also have member servers that provide any number of services. What does this look like in a Linux environment.
[/LIST]
Any other server pointers appreciated.

---

### Post by Loosewheel on 2009-07-30
Hi East82,

There is a server platform forum here:
[http://ubuntuforums.org/forumdisplay.php?daysprune=-1&f=339](http://ubuntuforums.org/forumdisplay.php?daysprune=-1&f=339)

The first sticky will lead you here:
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

And this is what you will need the most:
[http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

for your first question, take a peek at 'Mapping URL's....', and 'Virtual Hosting'.

---

### Post by East82 on 2009-08-03
Many Thanks ...great starting point

---

### Post by koenn on 2009-08-03
> **East82 said:**
> I have a Windows background in networking and after using Ubuntu desktop for a while and Ubuntu Server recently am confident in their stability, compatability and usability. That being said I have some concerns with a Linux environment and I'm hoping someone will point me in the right direction. This is not a Windows versus Linux deal ...I just have a myopic point of reference at this point :) 

So, here goes:


[LIST]
[*]With Apache, can I configure alternate physical locations for sites other than /var/www? For example, another drive or even another server. Also, any good GUI tools for administering LAMP?
[*]I really like Active Directory. Anything similar with Ubuntu? Tools to enforce policies, run scripts, install software, designate OU's ...Those sorts of things.
[*] What's a good email server for Ubuntu? I'm looking for something that has good archiving and search on the server side and web access and mobile device integration on the client side.
[*]DNS and NetBios - With Windows I can find any Windows machine on a network easily. I'm thinking using BIND9 on the server and SMB Client on workstations would be the solution here. Correct?? Most likely will be running in a mixed MS and Linux environment.
[*]In Windows networking you have the concept of the Forest / Domain / Domain Controller (Running AD) and can control access to resources based on membership. You also have member servers that provide any number of services. What does this look like in a Linux environment.
[/LIST]
Any other server pointers appreciated.
You're gonna have to find a cure for that myopic view - it's going to get in your way.

0-
ubuntu has no, or very little, GUI tools for system administration. Most of the time you don't need them : If you know what you want and how you want it, all you have to do is write that down in the appropriate config file, and it'll work. If you need wizards that to tell you what it is you want to do, and then do it for you, you're better of with other distros, or Windows. 

1- 
apache, refer to the link Loosewheel gave you

2-
mail - haven't done that. I hear good things about Zimbra, Zarafa and Citadel, and I probably overlook a few.

3- DNS and NetBIOS
do you really want NetBIOS. It's loud and messy, and DNS should be all you need anyway, unless you have obsolete windows applications that still require netbios and WINS because they can't deal with DNS. 
Populating "network neighborhood' still depends on netbios, I believe.
Samba probably covers this adequately. 

Bind is the reference implementation of a dns server, so it should cover your needs. There are alternatives that may be sufficient also, depends on your plans. Read about "dnsmasq". 

4- 
Active directory (and the concepts of domains and forests that come with it) are microsoft's way of remote management of computers that were meant to be stand alone systems. There's no real Linux equivalent. There are a lot of programs / suites / solutions that offer parts of AD's functionality, but lots of AD solves problems that never existed in a Unix environment. so they have no counterparts. 

It's one thing to offer standard services in a mixed environment, it's a completely different thing to expect a linux server to configure Windows computers - would you expect Active Directory to be able to manage users, computer configurations, software deployment, and access control on a Linux desktop ? 

you might want to read this : [http://users.telenet.be/mydotcom/howto/linux/migration03.htm](http://users.telenet.be/mydotcom/howto/linux/migration03.htm)

That said, Samba will cover some of your needs, openldap some others, you may also want kerberos, or you might want to look at some directory servioces offered by other linux distro's, there are linux server solutions for remote deploying software to windows PC's  (ocsinventory is one) etc, 
but most likely, if your "mixed environment" is linux servers and Windows desktops,  you'll continue to run AD off a Windows server;

---

### Post by bear24rw on 2009-08-03
"With Apache, can I configure alternate physical locations for sites other than /var/www?"

you can change it in

/etc/apache2/sites-available/default

i think

---

### Post by jamesrfla on 2009-08-03
For Active Directory you can use OpenLDAP witch runs on Linux.

---

### Post by Iowan on 2009-08-03
> **East82 said:**
> With Apache, can I configure alternate physical locations for sites other than /var/www? For example, another drive or even another server.[Here]("https://help.ubuntu.com/community/ApacheMySQLPHP#Virtual%20Hosts") is a help page for virtual hosts which mentions changing default directory.  I suspect it could be on another mounted drive (or filesystem).

---

### Post by East82 on 2009-08-11
> **koenn said:**
> You're gonna have to find a cure for that myopic view - it's going to get in your way.

0-
ubuntu has no, or very little, GUI tools for system administration. Most of the time you don't need them : If you know what you want and how you want it, all you have to do is write that down in the appropriate config file, and it'll work. If you need wizards that to tell you what it is you want to do, and then do it for you, you're better of with other distros, or Windows. 

1- 
apache, refer to the link Loosewheel gave you

2-
mail - haven't done that. I hear good things about Zimbra, Zarafa and Citadel, and I probably overlook a few.

3- DNS and NetBIOS
do you really want NetBIOS. It's loud and messy, and DNS should be all you need anyway, unless you have obsolete windows applications that still require netbios and WINS because they can't deal with DNS. 
Populating "network neighborhood' still depends on netbios, I believe.
Samba probably covers this adequately. 

Bind is the reference implementation of a dns server, so it should cover your needs. There are alternatives that may be sufficient also, depends on your plans. Read about "dnsmasq". 

4- 
Active directory (and the concepts of domains and forests that come with it) are microsoft's way of remote management of computers that were meant to be stand alone systems. There's no real Linux equivalent. There are a lot of programs / suites / solutions that offer parts of AD's functionality, but lots of AD solves problems that never existed in a Unix environment. so they have no counterparts. 

It's one thing to offer standard services in a mixed environment, it's a completely different thing to expect a linux server to configure Windows computers - would you expect Active Directory to be able to manage users, computer configurations, software deployment, and access control on a Linux desktop ? 

you might want to read this : [http://users.telenet.be/mydotcom/howto/linux/migration03.htm](http://users.telenet.be/mydotcom/howto/linux/migration03.htm)

That said, Samba will cover some of your needs, openldap some others, you may also want kerberos, or you might want to look at some directory servioces offered by other linux distro's, there are linux server solutions for remote deploying software to windows PC's  (ocsinventory is one) etc, 
but most likely, if your "mixed environment" is linux servers and Windows desktops,  you'll continue to run AD off a Windows server;

Koenn,
Thanks for the info.
Let me clarify ...I wrote myopic point of reference, not view, meaning that I have lots of experience with the MS model and not with Linux. Not an MS advocate at all. I'm just exploring what's available in the Linux environment right now. I like Ubuntu because of the repositories, support and community. 

I agree, NetBIOS is kinda chatty, and BIND DNS should work just fine.

Not the fastest keyboarder, but not afraid of the CLI either ;-) BTW I'm a big fan of the modularity of programs and separation of threads in Linux.

I guess the long and short of it is this. If I have several hundred Linux workstations in my network, across many departments, in separate subnets, requiring baselines and security settings can I centrally manage them with Linux??

Again,
Thanks

---

### Post by koenn on 2009-08-11
> **East82 said:**
> Koenn,
Thanks for the info.
Let me clarify ...I wrote myopic point of reference, not view, meaning that I have lots of experience with the MS model and not with Linux. Not an MS advocate at all. I'm just exploring what's available in the Linux environment right now. 
Let me clarify as well ...
I understood that ; what I meant is : If you look at Linux and your view is colored by your Windows experience, most of the time you'll end up looking for the wrong solutions, eg (hypothetical example) you go looking for tools to deny users access to the systems area of the file system, as in the numerous GPO settings that deal with this kind of problem, while in Linux, this is just a matter of filesystem permisions, and users have by default no write access outside their home directories so they won(t mess up your system to begin with. 

> **East82 said:**
> Koenn,
I guess the long and short of it is this. If I have several hundred Linux workstations in my network, across many departments, in separate subnets, requiring baselines and security settings can I centrally manage them with Linux??

tough question - I have no experience with such situation. Is this for real ? I was under the impression that you would be dealing with Windows workstations (talking about  NETBIOS and all). If we're talking Linux workstations,  your first problem is gong to be migrating to Linux-compatible end-user applications. That's going to be a challenge.

Now, about central management, this were my problem, I'd probably look in to

1/ "Server Based Computing"
"terminal services" in Windows speak. Makes management a lot simpler. Google 'LTSP'. 
I'd als have a look at desktop virtualisation, but that's a long shot. 


2/ Old School : user homes on NFS
Since **all** user config is stored inside the user home dir, having them centralised on a computer (and mounted over NFS) not only gives you "roaming profiles", it also lets you centrally edit the user configs : all config files are text files, and Unix/Linux has excellent tools for bulk text processing and the scripting thereof. 

3/ remote command execution
You can simply log on to a remote workstation and execute whatever command/set of commands / programs ... you like. With a bit of work (public key authentication in stead of passwords, a couple of scripts to iterate through a list of workstations, ...) this could go a long way towards managing workstations

4/ application specific solutions
Some applications have their own mechanisms for central management/configuration eg Google 'Mozilla Mission Control'. There are probably others (I think I remember reading something about Open Office in this respect)

5/ The Big Guns 
Google 'eBox' and 'Canonical Landscape'. Novell probably has something like this as well, being such pioneers in PC networking and all. Don't know about RedHat. 
To a lesser extend : OCSInventory has a mechanism for software deployment and remote command execution, and lets you define groups of workstations for a granular approach. Even Nagios (network monitor) can do most of this based on triggers, although this feature is mostly used to initiate corretive/currative actions on the monitored systems


Other than that, I don't know. 

Ebox or Landscape are probably a good choice if you're not into building your own  solutions from standard tools, server-based computing can be an excellent solution but it's a bit of a paradigm shift.

---

### Post by East82 on 2009-08-12
Koenn,
Much appreciated. The Linux file structure definitely makes for a better out of the box OS as far as security goes. I'll take a look at some of your suggestions and play with them in a lab (P and V machines)

I know that I can deploy a Linux network easily in, say, a classroom and even use LTSP with thin clients. My goal is to be able to offer that same solution to a small business where maintenance costs will be far lower than MS licensing. I know, however, that there are going to be WIndows boxes that they cannot live without, thus the integration concerns.

Again, TYVM

---

### Post by epsolon77 on 2009-08-20
LTSP requires the clients to boot from the network.  I have set this up and tested, and it works very well.  This will probably work for the setup you are speaking of, as long as the thin clients are able to boot from the network.  An option for a traditional terminal server is freeNX.  I used the build created by George Wright found here [http://blog.gwright.org.uk/articles/category/nx](http://blog.gwright.org.uk/articles/category/nx).
This allows someone to boot into their computer normally, and then access the "terminal server" environment.

---

