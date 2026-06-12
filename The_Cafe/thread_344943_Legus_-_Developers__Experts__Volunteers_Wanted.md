---
title: "Legus - Developers / Experts / Volunteers Wanted"
date: 2007-01-23
forum: The Cafe
---

### Post by darrenm on 2007-01-23
What is Legus?

Legus stands for Linux Enterprise Gateway Ubuntu Server. It is an attempt to unify everything that can go into a gateway server into an easy to manage package which can be administered via a web interface by non-technical users.

Currently when a small to medium business or power home user (SOHO) wants to use remote applications, mail from anywhere, spam blocking, content filtering etc. there is no set solution. If they go down the Linux / OSS route they have lots of already excellent packages providing some great features such as:

[LIST]
[*]Postfix mail server
[*]Dovecot POP/IMAP server
[*]Spamassassin Spam blocking
[*]BIND local DNS
[*]DCC / Razor / Pyzor realtime blacklists
[*]ClamAV Antivirus
[*]Dansguardian web content filtering
[*]OpenVPN VPN solution
[*]Roundcube Webmail
[*]Squid Proxy
[*]IPTables firewall
[/LIST]

For the advanced user setting these up is not a problem but perhaps time consuming and unnecessary. Administering them is also not a problem but again time consuming and limited to advanced users.

I have started Legus ([www.legus-project.org](www.legus-project.org)) to provide a way to get all of these packages installed quickly and easily onto a Ubuntu server then have them all configured to the correct domains, users, settings etc via a PHP installer and admin interface.

I would eventually like it so if a small business has an old PC they can put another network card in, download a Legus ISO which runs the PHP setup wizard, asks them a few questions and is then ready to roll as a secure, powerful gateway server. This will provide a great product to a large demographic and show the power of Open-Source and free software.

Currently Legus is vaporware. I have a few install scripts and lots of ideas on how to accomplish everything but I need help. If you would like to help in any way then please PM me or email me at darren(at)legus-project.org. Anyone can help but if you have any experience in PHP, MySQL, iptables, Linux TCP/IP networking, Mail, DNS or any of the above software then obviously this would be of great help.

Thanks for reading. Please post any comments or ideas below or visit [www.legus-project.org](www.legus-project.org) and improve the wiki.

Cheers
Darren

---

### Post by Randomskk on 2007-01-23
Might I suggest SquirrelMail for web-mail? I'm using it happily, and there are lots of fun plugins.

---

### Post by darrenm on 2007-01-23
Squirrelmail is great but Roundcube is really nicely AJAXy

We should be able to include both and give the user the choice. When an option is selected in the web interface it will have the ability to use a sudo apt-get command in the background presenting the user with a root password prompt using Apache-PAM

---

### Post by mips on 2007-01-23
> **darrenm said:**
>  Anyone can help but if you have any experience in PHP, MySQL, iptables, Linux TCP/IP networking, Mail, DNS or any of the above software then obviously this would be of great help.


I went to the website but did not see any specifics. I might be able to assist with iptables, tcp/ip & dns but am not promising anything.

---

### Post by darrenm on 2007-01-23
> **mips said:**
> I went to the website but did not see any specifics. I might be able to assist with iptables, tcp/ip & dns but am not promising anything.

Its all very early at the moment. I hope to outline more on the website when I have some input from other people as my ideas may not be the best way of doing things.

Thanks, any help will be appreciated.

---

### Post by Randomskk on 2007-01-23
I could probably help out with some PHP and MySQL stuff, I'll keep an eye on the thread!

---

### Post by Macchi on 2007-01-25
Hello Darren and other Ubuntu Fellows!

Your suggestion is a nice initiative since I believe that Ubuntu is a base for a very good server for Small and Medium Enterprises. I will write some comments here to improve visibility for the Ubuntu comunity but later we could proceed with discussions at your LEGUS project site.

I am an independent consultant working with small business enterprises and tend to offer open source software solutions since they improve security and reliability, also reducing maintenance efforts and costs. I have a server solution based on Ubuntu but centered at a different functionality that you are suggesting.

My present solution for a SOHO server is to manually configure functions in incremental steps according to customer needs. I would like to be able to offer everything but my customers prioritize the following:

Basic Functions
[LIST=1]
[*]Multiplatform File sharing 
[*]Printer sharing, 
[*]Automated backups to USB or FireWire drives
[*]SSH server for remote adminstration
[*]Optional RAID storage
[/LIST]

Groupware and Application Software Functions
[LIST=1]
[*]Remote desktops
[*]Optional Virtual machines
[*]WordPress server
[*]Optional Groupware server with 
[*]Optional Intranet web server
[/LIST]

Gateway Functions
[LIST=1]
[*]FireWalls (external box and software on the server)
[*]Web proxy
[*]Content Filter 
[*]Virus and Malware scanning
[/LIST]

As you see, I have a different approach but would be very interested in a cooperation since we have many common goals. My approach is based on practical experience and priority order defined by actual business customers, not by administrators and engineers. 

Specifically we have chosen to move business critical email and web servers to external providers due to improved reliability as well as lower installation, maintenance, and equipment costs. 

I have eventually used Webmin but now prefer text-based configuration scripts that are easy to set up and run through ssh. Obvioulsy it would be nice to have a web-based  interface but my priorities are on core functionality.

A key point is that actually there are not so many parameters to configure a server, provided that the functionality is fixed on certain increments. My customers start with basic functionality and later may demand more complex solutions.

---

### Post by MkfIbK7a on 2007-01-25
> **darrenm said:**
> Squirrelmail is great but Roundcube is really nicely AJAXy

We should be able to include both and give the user the choice. When an option is selected in the web interface it will have the ability to use a sudo apt-get command in the background presenting the user with a root password prompt using Apache-PAM

yes i use roundcube i like it alot

---

### Post by Lod on 2007-01-26
This is a very interesting project. I've been using [Clarkconnect ]("http://www.clarkconnect.com")for years now but am not happy with the new version and the upcoming roadmap. I've been looking into Ubuntu as a server because it is simple and apparently without too much unnecessary packages. Unfortunately I have no time (or wish) to learn about firewalls, serversettings and so on. A web based solution would be perfect (like the clarkconnect admin tool).

I know a bit about php, java and so on but probably to little to be of any help :) . I might be helpful with translating things to Dutch (if needed) and I can act as the stupid windows-noob...

I will be following your progress with the upmost interest

---

### Post by darrenm on 2007-01-26
Excellent. Good to hear that someone will find it useful too (when it comes to fruition)

---

### Post by Lod on 2007-01-26
If I may add two suggestions of services which should/could be included:
- Filesharing/Samba (already mentioned by Macchi)
- FTP-server

---

### Post by Bavo on 2007-01-26
This looks like a nice project, but as far as i have seen it doesn't include a centralized authentication system.

I'd like to suggest to include an openldap, nfs, samba and cups server.
I believe that a centralized system is something many people need. And the suggested programs will make it possible for every user to have his own files and settings on whatever computer they log on to, be it a windows or linux client.

---

### Post by darrenm on 2007-01-26
> **Lod said:**
> If I may add two suggestions of services which should/could be included:
- Filesharing/Samba (already mentioned by Macchi)
- FTP-server

I think that may be outside the scope of the initial project. Samba and FTP are very easy to set up so if anyone wants to use them on the same box they can and also it kind of goes away from what the original aim is which is to make an easily installable and configurable gateway server. You don't really want file sharing on a gateway server that will potentially be the main firewall to the internet. FTP perhaps... we can always look at that later.

---

### Post by darrenm on 2007-01-26
> **Bavo said:**
> This looks like a nice project, but as far as i have seen it doesn't include a centralized authentication system.

I'd like to suggest to include an openldap, nfs, samba and cups server.
I believe that a centralized system is something many people need. And the suggested programs will make it possible for every user to have his own files and settings on whatever computer they log on to, be it a windows or linux client.

Again perhaps outside the scope of the original aim. certainly nfs, samba and cups is.

Although a centralized auth system will be a useful part. It will need some way of passing the authentication to the user through the web browser when system changes are needed. I was looking in mod_pam for this although ldap may be another way.

---

### Post by koenn on 2007-01-28
Sounds fun. I have something similar (but not as extensive) at home, tailored to my needs and preferences,  so it would be interesting to see how one creates such a thing for others and allow cusomization to suit different circumstances. 
So, I'll keep an eye on this thread and wait till you announce some sort of kick-off. I can probably give input on general network stuff, iptables, network services (dns, dhcp), general system administration / configuration and some shell scripts when required. 

> You don't really want file sharing on a gateway server that will potentially be the main firewall to the internet
My thoughts exactly. While it is perfectly possible to throw whatever on a "server" - if you're going to use it as a gateway / firewall it should concern itself with "things passing true" , not offer additional services (file sharing, printing, ...) to the network, that then consequently need to be blocked / regulated and monitored on the internet side. Bad idea. 

An additional 3th network interface might be a good idea, to provide a DMZ or a 2nd LAN. And an Enterprise version with multiple internet connections, either dedicated (on for normal use, one reserved for vpn's ?) or redundant (load balanced, or fail-over ...) :)

---

### Post by darrenm on 2007-01-28
> **koenn said:**
> Sounds fun. I have something similar (but not as extensive) at home, tailored to my needs and preferences,  so it would be interesting to see how one creates such a thing for others and allow cusomization to suit different circumstances. 
So, I'll keep an eye on this thread and wait till you announce some sort of kick-off. I can probably give input on general network stuff, iptables, network services (dns, dhcp), general system administration / configuration and some shell scripts when required. 


My thoughts exactly. While it is perfectly possible to throw whatever on a "server" - if you're going to use it as a gateway / firewall it should concern itself with "things passing true" , not offer additional services (file sharing, printing, ...) to the network, that then consequently need to be blocked / regulated and monitored on the internet side. Bad idea. 

An additional 3th network interface might be a good idea, to provide a DMZ or a 2nd LAN. And an Enterprise version with multiple internet connections, either dedicated (on for normal use, one reserved for vpn's ?) or redundant (load balanced, or fail-over ...) :)

So far there is definitely myself and one other on board. Neither of us have a great deal of PHP knowledge but we can pick that up along the way. It shouldn't need really advanced PHP stuff to just change some stuff in MySQL and a few config files then run system commands.

I will put some initial specs together in this thread as it seems pretty essential at this stage to have something concrete to aim for.

3rd interface for a DMZ / failover is a great idea and entirely possible within this project

---

### Post by seijuro on 2007-01-28
> **Lod said:**
> If I may add two suggestions of services which should/could be included:
- Filesharing/Samba (already mentioned by Macchi)
- FTP-server

Filesharing is a given need for most business set ups. I would suggest sftp or ssh over standard FTP has they are more secure. Also depending on implementation they can be used as a filesharing alternative/backup as well as allow for sharing between internal and external networks. Though I'm not sure this is entirely practical for the main gateway server. ssh fits for sure though.

---

### Post by koenn on 2007-01-28
```
Filesharing is a given need for most business set ups
```
but that doesn't necessarily mean the "gateway" needs to provide it. Let another server do the file serving. 
For those cases where a fileserver needs to be accessibla from the outside, the gateway should provide a vpn tunnel to a file server, rather that share the files.

---

### Post by seijuro on 2007-01-28
hense why I said I wasn't sold on the practicality of doing it on the gateway.

---

### Post by Choad on 2007-01-28
i have no experience in any aspect of what you are doing, but i do have a few words of encouragement:

this kind of thing is EXACTLY what linux needs, generally. the world of linux is full of amazing single purpose tools that do one job exceptionally, but in order to get full use of the system as a whole you need a lot of expertise. this kind of project, aiming to unify lots of single purpose apps in to a well structured multi-purpose app is a step in the right direction.

like i said, i dont really know what this does on any kind of technical level, but i wish you luck in getting it off the ground

---

### Post by koenn on 2007-01-28
glad we agree

---

### Post by seijuro on 2007-01-28
> **Choad said:**
> i have no experience in any aspect of what you are doing, but i do have a few words of encouragement:

this kind of thing is EXACTLY what linux needs, generally. the world of linux is full of amazing single purpose tools that do one job exceptionally, but in order to get full use of the system as a whole you need a lot of expertise. this kind of project, aiming to unify lots of single purpose apps in to a well structured multi-purpose app is a step in the right direction.

like i said, i dont really know what this does on any kind of technical level, but i wish you luck in getting it off the ground

Indeed, I think there is a lot of room for projects like this that could help out the average user quite a bit.

---

### Post by darrenm on 2007-01-29
> **seijuro said:**
> Filesharing is a given need for most business set ups. I would suggest sftp or ssh over standard FTP has they are more secure. Also depending on implementation they can be used as a filesharing alternative/backup as well as allow for sharing between internal and external networks. Though I'm not sure this is entirely practical for the main gateway server. ssh fits for sure though.

Without doubt SSH will be there. I kind of neglected to mention that as its really a given. Some kind of enforcement of a restricted set up in the ACP (admin control panel) will be a must though to ensure that when everyone sets the passwords to be the same as the usernames they don't get random dictionary attacks succeeding.

I think filesharing will be best from another internal server and accessed over the VPN as you say.

I'm thinking FTP shouldn't be a standard part of it because of the possible security implications. SFTP will be part of SSH being there though.

---

### Post by Macchi on 2007-01-29
I believe that we see here again another traditional fight-for-features of a product.

My opinion is that the end customer/user should decide wich functions are desirable or not. This decision should require no more that a clicking few check boxes, provided with a short explanation of the functions. 

Thus my suggestion is a modular system, a framework for many installation modules.
Every installation module is a wizard that fetches common data (for instance domain and host names, etc) and installs certain functions on the system. This architecture would provide for maximal flexibility.

Lets find common areas of interest and cooperate as much as possible!

Failing to do so will probably fork or kill prematurely the project since it is very difficult - if not impossible - to agree exactly on with functionality the end customer is going to demand. This dilemma between features is very common and has to be surpassed with extreme maturity. Many excellent ideas have died on that battle.

---

### Post by koenn on 2007-01-29
> **Macchi said:**
> I believe that we see here again another traditional fight-for-features of a product.

My opinion is that the end customer/user should decide wich functions are desirable or not. 
Thus my suggestion is a modular system, ...  This architecture would provide for maximal flexibility.

 This dilemma between features is very common and has to be surpassed with extreme maturity. Many excellent ideas have died on that battle.

Finding common ground will indead by somewhat of a challenge. I'm afraid that what follows is not going to make it easier.

You mention "fight-for-features. That term is new to me. I do know "feature creep" : the tendency of adding as many features as possible. It usually leads to "bloated" sollutions. 

For this particular project - i think it's main purpose was to create a **gateway** - not a "Small Business Server" (which could also be an interesting idea - hmmm ). Mixing the two in a flexible framework and let the end-user decide which features to activate sounds like a good idea, but even then we'd have to agree on which features we should offer to the end user. there are some design decisions that you don't want the end user to take - like, if you're designing cars, you don't leave it up to the customers to decide whether or not they want breaks installed. 

a gateway is by definition an exposed system : exposed to the internet and anyone on it. If someone, anyone, finds a flaw in, say, your implementation of the file sharing, he might be able to abuse that to compromise the system, possibly rendering your security measures useless.That's whay exposed systems should be "hardened". rule #1 in hardening is : don't run anything you don't need. 
That's why I'd have serious doubts about file sharing etc. on a gateway system.

---

### Post by Macchi on 2007-01-29
Thanks Koen for your answer.

Yes, you are right that it might be a challenge to harmonize the different goals and interests. Still, I believe that there is a lot in common in improving the installation, configuration and maintenance of both a small enterprise server and a gateway. 

They are not mutually exclusive, actually most people might need need both. Thus, if the Legus project is interested in collaboration I hope to see a modular framework that can be reused. Of course, it is not safe to combine certain functions in the same machine.

Later I will try to elaborate more my descriptions of the "Small Enterprise Server" and I could share them here, if there are enough people that are interested.  


The expression "fight-for-features" has (superficial) roots from my days in product management, when teams responsible for the implementation of different features of product or different subsystems would almost literally fight to get a larger share of the development budget. Given a fixed total budget, they had to prioritize what would be included or not.  In most cases there is also a tendency to introduce more and more features in a products, as you mentioned the "feature creep".

---

### Post by darrenm on 2007-01-30
Thanks for the kind words of encouragement.

Heres what I've put together as some specs and initial goals. These will be replicated on the main project website ([www.legus-project.org](www.legus-project.org)) and then the site will take the main development information.

**Mail - SMTP**

Postfix providing the MTA services. A MySQL backend will enable us to quickly add/remove domains and users via the PHP web interface. For initial setting of domains and users the PHP installation script will ask the user. This will then enter the info into the database. 

Amavisd-new will be providing the interface between Postfix and ClamAV and Spamassassin. There are quite a few helper packages for this too.

Most packages auto-configure themselves nicely from the repos. Postfix will need some extra config done by the installer to enable MySQL lookup tables and Amavis. Whether it's better to just copy some preconfigured files over or get the PHP script to call Perl to edit the files regexp-style will be tested.  

_Packages_
postfix
postfix-mysql
amavisd-new
clamav
clamav-base
clamav-daemon
clamav-freshclam
spamassassin
cpio
binutils
unrar
arj
arc
lha
cabextract

**Mail - POP/IMAP**

Dovecot providing POP3 / IMAP service. Only SSL connections available by default with the option to turn unsecured connections on in the Admin Panel. Dovecot will be referencing the same tables that Postfix will for the users therefore a heavily customised /etc/dovecot/dovecot-sql.conf will be needed.

Roundcube webmail running on Apache2 only on secured connections from outside. While it is possible for everyone to use the VPN to collect their mail, not everyone will have access to install OpenVPN(client) on a PC if they are in a web cafe etc. So webmail is a definite need. Roundcube seems the best (or perhaps just best-looking) webmail client but it should be fairly easy to add others on and give the Admin the option to choose which is running. Apache will need 2 vhosts entries, 1 for the Admin Panel and 1 for the outside facing webmail http site. On installation the script will show the user all the interfaces on the system, ask them to choose which is internal, DMZ or external then configure the IP's. From this information the vhosts entries can be set up.

_Packages_
dovecot-common
dovecot-pop3d
dovecot-imapd
roundcube-webmail

**Content Filtering / Proxying**

Dansguardian is the best application for web content filtering. Very easy to configure and a PHP front end should be straightforward. I'm not sure about the licensing which, although GPL has some restrictions about commercial use. I can't see that complies with the GPL so we may fork this software and re-release under the GPL with no restrictions. 

Squid will be the main proxy that Dansguardian talks through. We will probably find it easier to do the outbound access control using iptables rules rather than Squid ACLs. Then we can keep all iptables rules together and use that module for a lot of configuration such as redirecting port 80 outbound to port 8080 for Dansguardian or 3128 for Squid if the content filter is turned off via the Admin Panel.

Blacklists is a grey area. [http://urlblacklist.com](http://urlblacklist.com) seems to have one of the most comprehensive blacklists available so it may be a good idea to have a module in the Admin Panel to subscribe directly to this and get updates from their site. If the user does not want a commercial blacklist service then it isn't enabled by default using just the regex and filtering of Dansguardian.

_Packages_
dansguardian
squid
squid-common

**VPN**

OpenVPN is the obvious best choice for this (only choice?). We will need to have a front end for creating keys and changing the config. Also the Admin Panel needs to have access to the information about the interfaces and networks to correctly add routes to the VPN config.

_Packages_
openvpn

**Admin Interface**

Apache2 will serve the pages. Everything should be possible using PHP and Perl regex's. We will protect the directory using mod_auth_pam and set up www-data as a sudoer so apache can run system commands only in a certain directory where we keep the system admin scripts. I can't think of any other way to do this that would be more secure and it seems to be standard everywhere. Anyone?

I would very much like to make it modular with a few standard 'must-have' features such as the ones mentioned here. It will be very easy to add new features using apt-get then PHP/Perl to set up the config when installed.

_Packages_
apache2
apache2-common
apache2-mpm-prefork
php5-mysql
php5-common
php5-mysqli
mysql-server

**Firewall**

IPtables is the only firewall anyone will ever need. We will construct the rules using PHP and run them using sudo with some kind of sanity checking to ensure they don't completely lock themselves out.

_Packages_
iptables

---

### Post by koenn on 2007-01-30
> **Macchi said:**
> ...
I believe that there is a lot in common in improving the installation, configuration and maintenance of both a small enterprise server and a gateway. 
... most people might need both

... a modular framework that can be reused. 

Of course, it is not safe to combine certain functions in the same machine.

OK, I see  your point now.

---

### Post by koenn on 2007-01-30
> We will probably find it easier to do the outbound access control using iptables rules rather than Squid ACLs.
I have some doubts on this one.
iptables works at network/transport level : ipaddresses and ports, Unless I'm mistaking, at best, you could block access to given (web) servers / complete websites through IP tables. you'd require Squid for advanced access controll (days/times, matches on strings, ...); unless Dansguardian can handle all filtering you need.

---

### Post by koenn on 2007-01-30
> Firewall

IPtables is the only firewall anyone will ever need. We will construct the rules using PHP and run them using sudo with some kind of sanity checking to ensure they don't completely lock themselves out.
You'd also need to have them executed at system (re-)start

---

### Post by darrenm on 2007-01-31
> **koenn said:**
> I have some doubts on this one.
iptables works at network/transport level : ipaddresses and ports, Unless I'm mistaking, at best, you could block access to given (web) servers / complete websites through IP tables. you'd require Squid for advanced access controll (days/times, matches on strings, ...); unless Dansguardian can handle all filtering you need.

If you are forwarding traffic between 2 interfaces you are able to redirect all port 80 requests to the port you want, in this case 3128 or 8080. You can also set the rules up to only allow certain IP addresses. Yes internet access times would need to be done with Squid/Dansguardian. What do you mean with matches on strings?

---

### Post by darrenm on 2007-01-31
> **koenn said:**
> You'd also need to have them executed at system (re-)start

Yep :) The commands can be constructed using PHP and output to a file then run as sudo. That file can also be dotted into /etc/rc.local

---

### Post by koenn on 2007-01-31
> **darrenm said:**
> What do you mean with matches on strings?
match the requested url to a given string / regexp / pattern / .... eg to block certain extensions or parts of filenames (eg to prevent downloading windows exutable files) without having to block all content from that givben IP address / host. 
kind of simple 'content' filter - but as I said, Dansguardian maybe offers better ways (I don't know Dansguardian, only heard of it)

---

### Post by Omnios on 2007-01-31
Might be interesting to have a web interface to work with Ip tables. This ability would probably be apreciated by the average user.

---

### Post by mips on 2007-01-31
> **Omnios said:**
> Might be interesting to have a web interface to work with Ip tables. This ability would probably be apreciated by the average user.

There is this really great gui app called Firewall Builder but I don't think it supports a web interface. [http://www.fwbuilder.org/](http://www.fwbuilder.org/)

---

### Post by Macchi on 2007-02-15
Throwing some fuel at the firewall discussion:

Have you looked at FireHOL? ([http://firehol.sourceforge.net/](http://firehol.sourceforge.net/))

It is a high-level configuration interface for iptables, easily configured by a text file. Thus it can be easily adapted for running with scripts, php, or whatever necessary. That would speed up the design, without having to care about low level iptables on the design of the php configuration panel. Most configuration  entries for the firewall don't have to be manipulated explicitly, since they could be added or removed automatically based on the presently active functions for the gateway.  

PS: By the way, have you looked at DenyHosts? ([http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/))
It is very useful for safer remote administration through ssh. I consider both FireHOL and DenyHosts as very useful applications for servers and gateways.

---

### Post by darrenm on 2007-02-15
Nice links thanks. I'll explore them thoroughly later :)

---

### Post by Lod on 2007-04-04
So? Can we expect version 2.4 soon? :cool:

---

### Post by darrenm on 2007-04-04
He he. I've been sidetracked a little lately. I have been doing lots of groundwork though. I'm looking at a realistic beta release with the next LTS (Feisty + 1)

I'm putting a howto showing a small bit of what I've been doing here: [http://ubuntuforums.org/showthread.php?t=398866](http://ubuntuforums.org/showthread.php?t=398866)

Once the mail side is out the way the rest should be fairly easy compared.

Also I'm kinda thinking of doing it in Ruby on Rails to speed up development. This project would really benefit from the big DRY philosophy that Ruby has.

Also I'm renaming it to UbuntuGatewayServer as the benefits this product will bring will be just as important to home users, parents, small business users as enterprise users.

:)

---

### Post by solar george on 2007-04-07
Can I suggest that the installer could include 'tasks' like "install a gateway" and "install a file sharing server" with different default set-ups.

---

### Post by darrenm on 2007-04-07
Yep. Thanks for the suggestion. The installer will be the last thing I tackle before first beta but that kind of thing should be do-able. I definitely won't be putting file-sharing on a gateway server though. If the person using it wanted to put it on themselves afterwards it's up to them.

---

### Post by solar george on 2007-04-07
> I definitely won't be putting file-sharing on a gateway server though

I was thinking that you could make the two mutually exclusive. Although that wouldn't exactly fit your project description.

I may be able to help out with design based parts of the project, I don't know enough to really help out with the rest, I don't mind testing it though.

---

### Post by darrenm on 2007-04-07
> **solar george said:**
> I was thinking that you could make the two mutually exclusive. Although that wouldn't exactly fit your project description.

I may be able to help out with design based parts of the project, I don't know enough to really help out with the rest, I don't mind testing it though.

I definitely need any help I can get. I'm useless with Logos, graphics, UI design etc so if you can help with any of that I'd be grateful.

---

### Post by solar george on 2007-04-07
OK, here are some logo ideas.

Let me know if I'm thinking in the right way, and if anything else needs designing.

---

### Post by darrenm on 2007-04-07
Thanks dude, I've renamed it UbuntuGatewayServer now though. I wanted something like the Ubuntu logo as part of a key or something. Or like a keyhole in the middle of the Ubuntu logo... Thanks for the effort so far :)

---

### Post by solar george on 2007-04-08
OK, How about these.

Any of the fonts should work with any of the logos.

---

### Post by solar george on 2007-04-08
and these,

All of these logos will need permission from Canonical - see [http://www.ubuntu.com/aboutus/trademarkpolicy](http://www.ubuntu.com/aboutus/trademarkpolicy)

---

### Post by darrenm on 2007-04-08
They all look super thanks mate. I'm most in favour of the last but one. The one with the keyhole in the middle. Thanks for the time you've taken. :)

---

### Post by solar george on 2007-04-08
Here's an SVG version of the logo. You will still need to check with Canonical before using it though. Would you like to keep the ubuntu colour scheme or would you like to choose one for the project, If you choose a colour as a base I can change the other colours to fit in with it.

---

### Post by darrenm on 2007-04-08
> **solar george said:**
> Here's an SVG version of the logo. You will still need to check with Canonical before using it though. Would you like to keep the ubuntu colour scheme or would you like to choose one for the project, If you choose a colour as a base I can change the other colours to fit in with it.

The colours look fine at the moment. I would really like to stick with the Ubuntu colour scheme until I have more time to look into it. I've mailed Canonical. Damn I'd better get some more coding done then! :)

---

### Post by H.E. Pennypacker on 2007-06-26
How is this project at the moment?  I really hope it is doing well, and I keep it on my watchlist.

---

### Post by darrenm on 2007-06-26
Now called UGS :)

Doing pretty well, however as I'm writing everything from scratch I find something else I want to implement and a better way to do things.

I've written most of the mail front end which is the largest part, but now I want to change from standard MySQL connector to MySQLi and make the rest of the code OO. Its currently linear code split into functions and config include files but it really needs to be OO.

I know exactly how I'm going to do everything, I just need something approaching functional to release as 0.1 so other developers will come on board.

Not sure if I've already said this but the idea now is to make it into a package that can be in the repos but the main focus will be the installer CD which will be a customised Ubuntu server install CD so UGS can be installed on very low spec machines with 2 NIC's and everything can be configured from the web front end.

I have to be very careful with security issues though while developing so that will take a lot of time.

Thanks for the interest. I have to update the site at [www.ubuntugs.org](www.ubuntugs.org) but everything will continue from there.

---

### Post by CrucifiedEgo on 2007-07-27
For the record, I'm a PHP/MySQL monkey, and I work for a domain registrar, so DNS/networking are second nature.  I've also got experience with high-traffic mailservers.  If you need a hand, let me know.

</j>

---

### Post by darrenm on 2007-07-28
> **CrucifiedEgo said:**
> For the record, I'm a PHP/MySQL monkey, and I work for a domain registrar, so DNS/networking are second nature.  I've also got experience with high-traffic mailservers.  If you need a hand, let me know.

</j>

Super thanks. The code is a bit rubbish at the moment but I suppose we all have to start somewhere. As soon as I have something worth showing I'll get back to you.

---

### Post by CrucifiedEgo on 2007-07-30
Looking forward to it :)

</j>

---

### Post by solar george on 2007-08-06
Hey people, I've just done some updated UGS logos with the proper Ubuntu title font, here they are,

---

### Post by darrenm on 2007-08-07
Thanks dude. I'm still a little unsure on how Canonical allows use of the Ubuntu logo. I like the first one though :)

---

### Post by curuxz on 2007-08-07
Can I suggest you that you guys at least TRY to look at ubuntu server project before starting your own from scratch maybe you could just join them, they need help and pooled resources seem like a great idea! 

You should also check out, Citadel, Ebox and the mess that is deepofix :)

---

### Post by darrenm on 2007-08-07
Yeah thanks. I had a good look at ebox today and it looks fab. They are doing everything I wanted to do really well. I'm not really sure there is a need for UGS now but I would like to write an ebox module that makes it work as a 'parent' server, something that sits in between the router and the switch / wifi AP and silently picks up traffic and makes it into something parents can use to monitor their kids online activity.

---

