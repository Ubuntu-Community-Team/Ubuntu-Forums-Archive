---
title: "Dapper Drake 6.06 questions"
date: 2007-07-08
forum: Server Platforms
---

### Post by Deros on 2007-07-08
Hi, I am building my webserver using The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

It has been smooth and painless so far but I have a few questions.  

At the top of page 4 you have a huge list of apt-get install to do but I can't seem to get the ncftp package to work.  Here is the list from the website:

apt-get install binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev g++

I deleted ncftp and the rest installed easily.  I then tried to install ncftp separately and this is what I am getting:

root@dlbwebserver1:/home/david# apt-get install ncftp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ncftp

Any ideas?  How important is this to building a webserver?  

Also a few of the other programs I am not sure if I need.  
**Quota** (it's just me so do I need to limit the amount of memory users take?) 
**DNS server **(I might register a domain name so will that be my DNS server I think please correct me if I am wrong.  Also I can just remember my IP address and type that into the browser right?)
**Postfix With SMTP-AUTH And TLS **( I don't want a mail server so I don't think I need this right?)
**Courier-IMAP/Courier-POP3** (same with this, no mail server so no need right?)

How do I decide if I want to install **ISPConfig**?

Thanks,
Deros

---

### Post by etcpool on 2007-07-08
maybe you don't have to follow the whole of those tutorial


just at the installation prompt choose to install lamp server


that's adequate for stand alone web server and then install additional service you need after that.


howtos for those aren't difficult to find around this forum and another ubuntu help page.



those kind of tutorial is about to setup the server to be the isp server which's way toooo much... imo  :P

EDIT:

for the list

Quota (it's just me so do I need to limit the amount of memory users take?) 
* if you intend to setup the server of you own and not gonna let any user log in , then this is not neccessary and it limits the storage for user not memory.
DNS server (I might register a domain name so will that be my DNS server I think please correct me if I am wrong. Also I can just remember my IP address and type that into the browser right?)
* if you don't plan to setup something complex with you domain like subdomain, mx , etc, then use dynamic dns service you can find around the internet dyndns.org is a good start and make a little more google search about that :)
Postfix With SMTP-AUTH And TLS ( I don't want a mail server so I don't think I need this right?)
Courier-IMAP/Courier-POP3 (same with this, no mail server so no need right?)
* you don't need these two for simple web server.

ispconfig is the core of what intend to make your machine a isp server it's combinded of peaces of server software available in ubuntu's repository and user interface to make your life easier to manage the complex isp system.

which i don't think you gonna need that much..

imo , i think this peace of software should be called hostingconfig instead since it doesn't has any ability to provide internet connection or such kind of data link service, it just one part of services isp offer to their customer like web, mail, ftp ,quota, billing system, etc.


correct me if i'm wrong ,and sorry for my english. :P

etc,

:)

---

### Post by Deros on 2007-07-09
etcpool, thanks for the information, it helps me make some choices.  Any idea on what "ncftp" is and if I really need it?
Thanks again and I think your english is great.
Deros

---

### Post by andrew.46 on 2007-07-31
Hi,

 Read your comment about ncftp:

> **Deros said:**
> etcpool, thanks for the information, it helps me make some choices.  Any idea on what "ncftp" is and if I really need it?
Thanks again and I think your english is great.
Deros

 I am also using Dapper Drake and just happened to also use ncftp :-) It is a command line file transfer program that aims to replace the standard Linux ftp. If you are after command line ftp this is a great choice.

 Definitely in the repositories, have you updated your lists first:

```
sudo apt-get update && sudo apt-get upgrade
```

before trying:

```
sudo apt-get install ncftp
```

This should do the trick.

             Andrew

---

