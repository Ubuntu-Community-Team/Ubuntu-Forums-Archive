---
title: "Make virtual test server available to other pc's in lan as simple as possible"
date: 2009-08-13
forum: Server Platforms
---

### Post by whatdoesitwant on 2009-08-13
I've set up a bridged virtualbox connecting to my router with its own ip running ubuntu 9.04 desktop (jaunty).
I use it as a development and testing platform for my websites. It's working wonderfully.
I haven't configured dns yet. Everything on apache is referring to localhost.

I next want to access my sites from another pc within my local network. 
Is there an easy way to set this up, but not having the ubuntu server be accessible from the scary outside world beyond the router? Or should I just follow along with howtoforge and set up a full fledged server.

I must add that I'm a complete nitwit, I don't have a clue about a-records or configuring Bind .

**Update: **
I edited the hosts file and changed all localhost aliases to the server's ip. I can now reach the apache server on its ip from the external pc. I still seem to have to say something somewhere about dns to get the websites to work, though.

---

### Post by phillw on 2009-08-13
If you leave your router firewall set to deny the outside world contacting you (the usual default), you will just have your local computers able to chat to each-other.

Set the network up as normal - just leave out the bit about configuring your router firewall 

Regards,

Phill.

---

### Post by whatdoesitwant on 2009-08-13
Thanks Phill,

However, > Set the network up as normal is the part that i don't know anything about. 
I've seen [this]("http://www.howtoforge.com/perfect-server-ubuntu-9.04-ispconfig-2") tutorial, but that's a bit of overkill for my purposes. 

Luckily, I found an extremely easy solution in copying entries from the ubuntu server hosts file to the windows 7 client hosts file. 

For now this is good enough. Now I can look into stuff like [split dns]("http://www.miek.nl/blog/archives/2008/02/23/split_dns_done_right_2_servers_nsd_and_bind9/index.html") later.

Both hosts-files (server and client) now look like this:

```
127.0.0.1 localhost
192.168.0.5 webserver-lamp

192.168.0.5	mysite.ubu
192.168.0.5	www.mysite.ubu
192.168.0.5	othersite.ubu
192.168.0.5	www.othersite.ubu
192.168.0.5	subsite.othersite.ubu
```

Cheers, Willem

---

