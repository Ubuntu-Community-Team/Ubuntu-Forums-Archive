---
title: "Set up Edgy server as public and private..."
date: 2007-03-30
forum: Server Platforms
---

### Post by tiger.woods on 2007-03-30
Hopefully this will be an easy question for the Server wizards...

I want to run a webserver and a localserver on the same machine, so first off I know I need 2 NIC's in the box but one private and one public but I'm a little confused on how to setup /etc/hosts, /etc/hostname, DNS and the firewall, I think that's all I'd need to modify...

Currently - 

/etc/hostname is: server1.mydomain.local

/etc/hosts: 192.168.1.100 server1.mydomain.local server1
                192.168.2.100 server1.mydomain.com server1

Does anyone have any guidelines I could follow or suggestions that would help get this going?

Thanks,

---

### Post by Frosty Cold Drink on 2007-03-30
You don't need 2 NICs. You cah have HTTPD listen on all, one, or more IP addresses. You can run two instances of different IP addresses or use VHosts. Your hosts file is fine if you drop the final server1 from the 192.168.2.100 line.

---

### Post by tiger.woods on 2007-03-30
Any readings/how to's you could recommend that would be directly related to setting this up?

Thanks.

TW,

---

### Post by Frosty Cold Drink on 2007-03-30
> **tiger.woods said:**
> Any readings/how to's you could recommend that would be directly related to setting this up?

Thanks.

TW,

[http://httpd.apache.org/docs/2.0/vhosts/ip-based.html](http://httpd.apache.org/docs/2.0/vhosts/ip-based.html)

If you add the domain names to your hosts file, this doc should will help you with the virtual host route. I wouldn't advise running 2 seperate instances of httpd unless you had some specific requirements.

---

### Post by tiger.woods on 2007-03-31
So, maybe I didn't ask my question correctly...

If I want a .local and a .com on the same server it seems to me for security reasons I should not use a single NIC...? shouldn't they be totally seperate subnets?

Isn't HTTPD for web only, why would I want it to also handle my .local?

TW,

---

### Post by Frosty Cold Drink on 2007-03-31
> **tiger.woods said:**
> So, maybe I didn't ask my question correctly...

If I want a .local and a .com on the same server it seems to me for security reasons I should not use a single NIC...? shouldn't they be totally seperate subnets?

Isn't HTTPD for web only, why would I want it to also handle my .local?

TW,

What exactly are you serving?

---

### Post by tiger.woods on 2007-03-31
Virtual hosts for sure as well as possibly my local network. 

Sorry, for my "greeness", I'm used to a windows environment so I assumed that to keep my local network seperate from the public newtork I would need 2 different subnets???

TW,

---

### Post by rsermilik on 2007-04-01
local vs public has nothing to do with .local vs .com

For security reasons the best would be to have a firewall with an DMZ interface. Place a host with a httpd server for the public access on the DMZ and then keep your internal servers on the internal (secure) network. You must configure the FW to only allow http (port 80) traffic from public to DMZ. From internal to DMZ http and ssh shall be possible. You can the apply new web pages to the public server with scp. Scp is "Secure CoPy" which is based on ssh. Or you can use Secure FTP if you prefer that.

httpd is just an service that can be used on both public and non-public networks.

Using a single host for both doesn't work. Most (if not all) virtual  server software dosen't allow you to bind a specific virtual client to a dedicated interface card.

All the above, 1 or 2 nic's, has nothing to do with running Windows or not:-)

regards

---

