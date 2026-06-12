---
title: "Departmental Server Requirements/Setup"
date: 2008-04-23
forum: Server Platforms
---

### Post by westcoastlinux on 2008-04-23
I am a system administrator at a software company. I am quite new to the game and have been given the task of implementing a new network. The network is to have all mail servers, the SIP server, external DNS etc separate to the file servers, authenticating tools, internal DNS and more.

To increase security each department will be given their own server, which will give them access to only files that are needed to be accessed by them within their department (A fileserver). 

My question is do these departmental servers require Kerberos, NIS, NTP, Webserver, Wiki individually? or can there be a semi-'master' server which will host the servers for each of these services and give authentication and supply this service to each other server. 
Will this lower security?
Is this a practical and efficient way to go?
Or does each departmental server need to have its own head server for each of these services?

Please help..

---

### Post by kmyram on 2008-04-23
The services you mention are quite different by nature - think you'll get more answers if you could be much more specific.
Not to put you down but I'm surely not the only one confused as to what you wish to achieve :)

---

### Post by westcoastlinux on 2008-04-23
Well... I would like to basically have Kerberos to be able to authenticate sub-realms (our file servers) and workstations connected to these sub-realms.
Ie. workstation1.sysadmin.business.com is a workstation to the server sysadmin.business.com as a sub realm to business.com. 
Is it possible to have Kerberos do this? Is it making any sense even... haha.
Or does anyone know a way around my problem..?
thanks.

---

### Post by Dr Small on 2008-04-23
I can see secondary servers for like say, a mailserver, a dns server and have the fileserver/web server, but why a server for each department?

I think that is overly complicating things.
Of course, backup servers for each of the listed above, incase something fails on one, or you would need backups.

Dr Small

---

### Post by westcoastlinux on 2008-04-24
I didn't make the plans.. I just have to implement it. 
Basically though it is to split up the intellectual property so no one person has access to the lot.

---

