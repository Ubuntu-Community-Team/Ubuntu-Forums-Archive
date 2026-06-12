---
title: "Has it really worked - home server? Have I cracked it?"
date: 2007-04-13
forum: Server Platforms
---

### Post by ade234uk on 2007-04-13
Ok I installed Apache etc, set up port forwarding to the IP Address on this machine. I made sure that Port 80 was open and it was.

I then got my main IP Address by going to [http://www.findmyip.com/](http://www.findmyip.com/)

I then entered this IP Address in my browser Router Page came up. Is this correct? Does this mean I can accept connections from the outside world?

I then decided to login in to my 123reg account and point one of my old domain names directly to the ipaddress that I got from findmyip. I entered the webaddress in the browser and my router page came up. Again does this mean it is working?

I presume that I now have to change my Apache conf file so that all requests that come from the domain name take the user to the directory of where my public_html directory is?

Your help is appreciated.

---

### Post by Frosty Cold Drink on 2007-04-13
Maybe. Your router chould be allowing administration from ther outside, which would be a problem. The only way to know for sure is to connect from an IP address outside of your network and see what happens.

---

### Post by PilotJLR on 2007-04-13
Exactly - many home routers will redirect you to their local interface if you hit your own public IP internally. The feature that prevents this from happening is called loopback, and is only occasionally present in the less expensive home routers.

So you have to test this external to your own network..

---

### Post by pjbgravely on 2007-04-13
You can't get to your IP from your IP. If you want to see your server on your own network then simply add this to the /etc/hosts in the  computer you are browsing with.

your_servers_ local_IP_address    your_domain_name.

For example it might look like this 

192.168.0.200 server.domain.com

Then when ever you use you domain name that computer will point to your severs IP address. I found this will not work with non standard ports, so you can open up port 80 for your LAN  in apache and leave any other port set up if you are using non standard ports.

The only way I know of seeing you server from the WAN is using a proxy like tor to hide your true IP address.

Paul

---

