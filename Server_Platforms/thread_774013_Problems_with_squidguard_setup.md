---
title: "Problems with squidguard setup"
date: 2008-04-29
forum: Server Platforms
---

### Post by aberry5555 on 2008-04-29
Hi there everyone. Ok, so here's my set up so far: I have set up a working squid proxy server on our existing  7.10 LAMP server, with ubuntu-desktop installed. With a few regex acls, it all seems to work ok and, with the short blacklist that we've made ourselves, it does file type and site blocking perfectly fine.

The problem I'm having, though, is that I have installed squidguard so that I can add shalla's list on top of our current configuration so as to save us some work. 

I followed the following set of instructions (and I followed them to a T, I'm pretty sure, though I could be wrong) but I can't for the life of me get squid to start once I put the redirector line in to squid.conf:

[https://help.ubuntulinux.org/community/SquidGuard](https://help.ubuntulinux.org/community/SquidGuard)

After following the troubleshooting section I think I've found the reason why squid won't start, but can't get any further when I issue the following command:

```
sudo echo "http://porn.com 10.0.0.1/ - - GET" | squidGuard -d -c /etc/squid/squidGuard.conf 
```

I get the following error message:

```
loading dbfile /var/lib/squidguard/db/porn/domains.db 
Error db_open: Permission denied
```
(please excuse the reference to porn, I'm using a blacklist of one site to test)

Now I'm pretty sure I've set all the necessary permissions, I followed all of the possible permission commands in the help document, all of the necessary folders are user: proxy group: proxy and all permissions are set in the described way. Maybe it has something to do with this document being slightly dated, and a different user is now required? or perhaps I'm missing some simple step but whatever I do I can't get around this permission denied error. 

If anyone can help and needs me to show any logs and the like please let me know as this is starting to get very frustrating, heh.

Thanks in advance,

Alex

---

### Post by aberry5555 on 2008-04-29
Anyone? Even if you're not sure of the exact problem just a pointer that you could think of would be very helpful. Thanks

---

### Post by Schlandower on 2008-12-28
> **aberry5555 said:**
> Anyone? Even if you're not sure of the exact problem just a pointer that you could think of would be very helpful. Thanks

Something I have noticed running my own server with squidGuard is that when I ran a test like the one you described I also got the same error.
The problem is with permissions.
In short the permissions are correct for squid and squidGuard but not for a normal user, not even sudo.

The way I found to test the setup is create a separate test-user.
This user then is included in a group in the squidGuard configuration to be very restricted.
Now try accessing a site you know should be banned as this user.

You should be blocked, if not then there is a problem with the setup in the squidGuard.conf.

I hope this can help you in some way, info on squidGuard odities I have found to be **very** rate.

---

### Post by Schlandower on 2008-12-28
> **aberry5555 said:**
> Anyone? Even if you're not sure of the exact problem just a pointer that you could think of would be very helpful. Thanks

Something I have noticed running my own server with squidGuard is that when I ran a test like the one you described I also got the same error.
The problem is with permissions.
In short the permissions are correct for squid and squidGuard but not for a normal user, not even sudo.

The way I found to test the setup is create a separate test-user.
This user then is included in a group in the squidGuard configuration to be very restricted.
Now try accessing a site you know should be banned as this user.

You should be blocked, if not then there is a problem with the setup in the squidGuard.conf.

I hope this can help you in some way, info on squidGuard odities I have found to be **very** rare.

---

