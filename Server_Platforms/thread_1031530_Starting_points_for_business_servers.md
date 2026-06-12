---
title: "Starting points for business servers"
date: 2009-01-05
forum: Server Platforms
---

### Post by lixoman100 on 2009-01-05
Hello,

I'm currently responsible for keeping the network systems running where I work. It is a small network with about 10 client machines running Windows or MacOS X and some mobile clients that usually run Windows. We have a couple servers holding accounts and files, a printer server and some other services, everything currently on Windows Server.

We intendo to migrate to Linux on the servers to reduce costs. Some of the stuff I would need to do includes:

- Centralized logins for the Windows machines, preferably with roaming profiles;
- Centralized file sharing with an easy way to set up permissions with good granularity;
- Enable some kind of VPN so people can access all that and other services from outside.

I did some research on Samba and Samba+LDAP but I am still a little confused by all this. I didn't reach any conclusion on how to deal with file permissions efficiently, and I don't know where to start with the VPN.

What I would like to ask are some starting points... links to useful information, guides, FAQs, all that stuff so I can get started on this. I have no problem on doing everything by hand as long as I know what I am doing. I'd like to keep everything open source as well.


Any help is greatly appreciated.

---

### Post by HermanAB on 2009-01-05
Go to the Samba web site and read the "Official Howto Guide".  

There is also a guide specifically written for Ubuntu.

Cheers,

Herman

---

