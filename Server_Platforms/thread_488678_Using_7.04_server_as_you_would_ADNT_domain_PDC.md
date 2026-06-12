---
title: "Using 7.04 server as you would AD/NT domain PDC"
date: 2007-06-30
forum: Server Platforms
---

### Post by kevindontenville on 2007-06-30
Hi All

Just trying to set up a home network to play with some central authentication for network users similar in concept to a windows domain or AD model but without a Windows Server in the mix.  

I presume a mix of Kerberos and LDAP should handle the authentication and account information but most of the Howtos I have found are based on joining an existing windows AD or NT domain not creating the server environment completely on Linux.  There may be various windows clients in the mix along with the various linux flavour clients so I think it will also include samba CIFs shares and print servers rather than NFS.

Seems that a lot more was done on the older Ubuntu flavours but not recent ones so many of the Howtos I have seen are somewhat out of date.  I know of SME and Clarke et al but I want to learn a little more about the process and perhaps twist things to fit the ideas I have for the network rather than rigid fixed mechanisms.

Any recommendations? Will be happy to feed the end results back in some documentation!

Thanks.

Kevin

---

### Post by crazyjx23 on 2007-06-30
Working with SAMBA was easiest for me on OpenSUSE using YAST. It enabled you to act as pdc with just a few clicks. I'm sure you can do it in Ubuntu, I'm just a little lazy. Sorry I can't help with Ubuntu too much.

---

### Post by kevindontenville on 2007-07-02
Thanks, I will look again at Suse for serving. Thats the beauty of Linux based OS, Choice! ;-)

---

