---
title: "ISPConfig DDNS Configuration help"
date: 2009-01-02
forum: Server Platforms
---

### Post by bikerjeg on 2009-01-02
After finally solving my initial interface problem which I fixed with new hardware I am now good to go and have installed Ubuntu 8.04 according to the perfect server setup on howtoforge found here [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I went ahead and installed ISPconfig and have a working server configuration. I know my connection does not have a static IP address so I am looking for help on setting up DDNS the easiest way possible. Back when I first started looking into configuring my server a few months ago I looked into this but I am still confused which direction to take.

I have a wrtg54 series router which I have already flashed with dd-wrt since it was suggested on a site to have more DDNS configuration options. I have signed up with various DDNS services such as no-ip and dyndns as well as afraidDNS but I am not sure how to configure the router's DDNS client settings properly with any of these services. Should I instead install a DDNS client on my actual server?

Basically my server is already working from my current IP address(dynamic ofcourse) but I would like to have my own domain which I already registered with namecheap.

Any help would be appreciated since I have looked throughout the web and various forums but none were specific to a configuration on Ubuntu with ISPconfig and DDNS.

Thanks

---

### Post by geforce123 on 2009-01-03
> **bikerjeg said:**
> After finally solving my initial interface problem which I fixed with new hardware I am now good to go and have installed Ubuntu 8.04 according to the perfect server setup on howtoforge found here [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I went ahead and installed ISPconfig and have a working server configuration. I know my connection does not have a static IP address so I am looking for help on setting up DDNS the easiest way possible. Back when I first started looking into configuring my server a few months ago I looked into this but I am still confused which direction to take.

I have a wrtg54 series router which I have already flashed with dd-wrt since it was suggested on a site to have more DDNS configuration options. I have signed up with various DDNS services such as no-ip and dyndns as well as afraidDNS but I am not sure how to configure the router's DDNS client settings properly with any of these services. Should I instead install a DDNS client on my actual server?


Yes, I personally use NO-IP, and I'm quite happy with the no-ip daemon.

> **bikerjeg said:**
> 
Basically my server is already working from my current IP address(dynamic ofcourse) but I would like to have my own domain which I already registered with namecheap.

Any help would be appreciated since I have looked throughout the web and various forums but none were specific to a configuration on Ubuntu with ISPconfig and DDNS.

Thanks
Ok, so your server is running behind you home (or office) firewall (WRT54 series).
You could do this:

- Use a static IP address for your server inside the network (i.e: 192.168.0.10)

- Setup "port forwarding" for the needed services (i.e: 80 for web, 81 for ISPCONFIG, etc, etc) so the incomming connections (from the outside) go to your server.

- Configure your domain on ISPConfig.

- Configure NO-IP so your domain name DNS server is no-ip.

- Configure the NO-IP daemon (apt-get install no-ip), the follow the instructions.  I think it asks for configuration at first start.

That's it.

---

### Post by bikerjeg on 2009-01-17
Well I ended up configuring this before checking your reply but it turns out I did exactly what you said. I ended up using afraid.org for my DDNS since I think they have better pricing for a budget setup like mine.

So I have it all setup but when I access ISPconfig from my domain I get a warning regarding my ssl certificate. I added an exception on my browser but I would still like to resolve this issue if anyone here knows how.

Another point is how do I manage multiple domains? I have other domains I would like to create accounts for on my ISPConfig server setup but I do not know how I would go about this and configuring DNS for these domains.

---

