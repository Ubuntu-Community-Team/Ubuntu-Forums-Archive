---
title: "Rename Server???"
date: 2010-10-04
forum: Server Platforms
---

### Post by joek71 on 2010-10-04
Hello Guys

I installed ubuntu Server on a dev machine, i would like to rename from [http://ocalhost](http://ocalhost) to [www.blah.com](www.blah.com)
How would I do this?  

thanks,
joe

---

### Post by arrrghhh on 2010-10-04
You just need a domain... and then point the domain to your server.

Unless you just want to change the hostname on the server itself...?  Based on your summary, it doesn't seem like that's what you want/need.

---

### Post by joek71 on 2010-10-04
This is internal server local in office, just want to rename it from localhost to blahdev.com, just internal purpose only.  Makes it easy on the dev team.

---

### Post by Crazedpsyc on 2010-10-04
I think you can change the line in /etc/hosts that says 
127.0.1.1    [I]yourhostname
[/I]to
127.0.1.1    *your.host.name*
but the best option would be to leave it at your host name and then everyone who wants to access it can type in [http://*yourhostname](http://*yourhostname)*/ as long as the browser is set up to not add www. and .com automatically.
n firefox go to about:config and edit the appropriate lines (values are www. and .com) to be empty

---

### Post by joek71 on 2010-10-04
i cant find /etc/hosts

i looked not there, all i am trying to do is when referring to the local dev machine, instead of typing localhost, i want to type htt://blah.com

thats it, trying to setup mirror of the live machine.

---

### Post by arrrghhh on 2010-10-04
Well you have two options.

Run a DNS server.

Adjust the hosts file on the client PCs.

---

### Post by joek71 on 2010-10-04
i can do it on my DNS Server right?  Not in the ubuntu scripts

---

### Post by Crazedpsyc on 2010-10-04
Ok more detail:
open a terminal from Applications>Accessories>Terminal
enter 
```
sudo gedit /etc/hosts
```
and press enter
the text editor will open up
change 
> 127.0.1.1    *yourhostname*
to 
> 127.0.1.1    *yourhostname.com*
and save it. you may have to restart. [http://localhost/](http://localhost/) will still work, but so should the new yourhostname.com.
although: It might not work if there is already a yourhostname.com on the internet.

---

### Post by arrrghhh on 2010-10-04
> **joek71 said:**
> i can do it on my DNS Server right?  Not in the ubuntu scripts

Of course, if you already have a DNS server that the client PCs use you can just update it.

The hostname really has no bearing on how the clients access it, unless you use avahi/network discovery...

---

### Post by CharlesA on 2010-10-04
I suppose it would depend on how you want to set it up. You could use the DNS server to point [www.blah.com](www.blah.com) to the ipaddress of the test server.

I don't think you really need to change the hostname of the server.

---

### Post by Vegan on 2010-10-04
Not a good idea to use a FQDN for you local net.

Better is to just call the server blah or whatever.

Mine is called the most unimaginative name possible, Ubuntu

My WRT54G takes care of the domain, it make the Linux box, ubuntu.contract-developer.tk so its already on its own subnet

This is how I run my network, so every machine has its own URL that is addressable formally and properly

---

