---
title: "change ubuntu server name &amp; domain from DHCP"
date: 2015-01-26
forum: Server Platforms
---

### Post by nicolasdiogo on 2015-01-26
Good Morning Ubuntu Experts


My small lab uses ubuntu servers that are cloned from templated 'images' - this is a copy'n'paste of Ubuntu server disks.

I would like to be able to set the names of the 'new instances' using DHCP.
so that i could have the ubuntu servers (12,14) picking up their new names from the DHCP request.

I am not certain if the best approach would be by running a BASH script or by installing a package.

Surelly, there will be a more experienced person that could provide me with some guidance on how i can best achive this objective.


thanks,

---

### Post by SeijiSensei on 2015-01-26
Are you in control of the DHCP server?  Is it running Linux and ISC dhcpd?

As I recall, it is the client that tells the DHCP server its hostname, not the other way around.  Usually IP->hostname mappings are handled in DNS.  Browsing the [man page for dhcpd.conf]("http://linux.die.net/man/5/dhcpd.conf") didn't turn up any suggestions for how to have the server give a name to the client.

---

### Post by nicolasdiogo on 2015-01-27
thanks

I guess that the option in OpenSuse that does this change is the:

> DHCLIENT_SET_HOSTNAME="yes"


see this post: 
[http://quartz-net.co.uk/quartzwiki/index.php/SuSE_DHCP_client](http://quartz-net.co.uk/quartzwiki/index.php/SuSE_DHCP_client)

where it says:
> ## Type:        yesno
## Default:     no
#
# Should the DHCP client set the hostname? (yes|no)
# 
# When it is likely that this would occur during a running X session, 
# your DISPLAY variable could be screwed up and you won't be able to open
# new windows anymore, then this should be "no". 
#
# If it happens during booting it won't be a problem and you can 
# safely say "yes" here. For a roaming notebook with X kept running, "no"
# makes more sense. 
#
DHCLIENT_SET_HOSTNAME="yes"



on a similar discussion about Ubuntu;
we can read:

> 
The DHCP client was expecting the hostname from DHCP server (by adding 

**request host-name **

in the dhclient.conf)



but i have tried that i got no where so far..

which is why i have posted here.


I will leave the question open, as others may be able to contribute to the topic.


regards,

---

### Post by SeijiSensei on 2015-01-27
Well, I found this: [http://www.ingmarverheij.com/configure-hostname-via-dhcp/](http://www.ingmarverheij.com/configure-hostname-via-dhcp/)

You can apparently add "option host-name" to the host{} declaration in dhcpd.conf for clients with reserved addresses.
```

host LAPTOP_IV {
   hardware ethernet 60:6B:BD:0B:67:3F;
   fixed-address 192.168.0.101;
   option host-name "LAPTOP_IV";
}

```

---

### Post by nicolasdiogo on 2015-01-31
yep ..

i have seem that.
unfortunately my ubuntu client is not changing its hostname as expected (and shown on the website that you listed)

annoying when things refuse to work; despite the documentation saying how they should operate.

---

### Post by SeijiSensei on 2015-01-31
Do you have send-hostname disabled and request host-name enabled in /etc/dhcp/dhclient.conf?

---

