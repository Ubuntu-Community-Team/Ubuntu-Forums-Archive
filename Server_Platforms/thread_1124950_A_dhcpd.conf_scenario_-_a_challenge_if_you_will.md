---
title: "A dhcpd.conf scenario - a challenge if you will"
date: 2009-04-13
forum: Server Platforms
---

### Post by ivaarsen on 2009-04-13
Good day (or night) sirs and madams!

I'm working on a little project here, and I'm needing my DHCP server configured in a certain way to continue.  Can't quite get it figured out.

My network is normally a simple 192.168.x.0/24 network, but right now I want to configure my DHCP server to give random addresses from this subnet only to machines I define by mac address.  (<-- Actually, I got this part figured out)  I want all other 'unknown' hosts to get an IP address on a different subnet (ie. 192.168.y.0/24).

It's the second part of my plan that needs help.  Here's my attempt. I just started with this part of my project, one of the first things I tried.  But I can't really find anything clear about it on the internet, so any pointers or help would be appreciated.  The result is machines that are supposed to be on 'x.0' get their normal IP addresses, 'Rogue' machines - machines that I have not defined (and hopefully will end up on 'y.0') - do not find a DHCP server.

```
ddns-update-style none;
authoritative;
log-facility local7;

shared-network local {
        subnet 192.168.x.0 netmask 255.255.255.0 {
                range 192.168.x.100 192.168.x.200;
                default-lease-time 600;
                max-lease-time 7200;
                option subnet-mask 255.255.255.0;
                option broadcast-address 192.168.x.255;
                option routers 192.168.x.1;
                option domain-name-servers 192.168.x.10;
                option domain-name "domain.local";
                deny unknown-clients;

                host host1 {
                        hardware ethernet *:*:*:*:*:*;
                }
                host host2 {
                        hardware ethernet *:*:*:*:*:*;
                }
        }

        subnet 192.168.y.0 netmask 255.255.255.0 {
                range 192.168.y.100 192.168.y.200;
                default-lease-time 600;
                max-lease-time 7200;
                option subnet-mask 255.255.255.0;
                option broadcast-address 192.168.y.255;
                option routers 192.168.y.1;
                option domain-name-servers 192.168.y.1;
                allow unknown-clients;
        }
}

```

Thanks for the help, and Cheers!

---

### Post by Iowan on 2009-04-14
'Nother Iowa-resident (Iowan?)... We should start a LoCo.
I presume you've seen the **man** page for dhcpd.conf?  It has some examples about what you're trying to do... can't say I've tried it.

---

### Post by ivaarsen on 2009-04-15
Aww hell!  And I was just received a private message from anther Iowan who lives rather close to me!  We're comin' out!  Guns blazin'!  :D

To answer your question... Well, no, I haven't.  I'm pretty technically minded, but usually have a hard time understanding man pages.

After a quick once-over (I'm at work and will try later when I'm home) of the man page, what I saw seems like applying addresses from different pools, but still on the same subnet.  I need different subnets.  Like I said, though, I'll take a closer look later.

Could it have anything to do with my DHCP server having an address on one subnet not being able to complete a DHCP transaction on a different subnet?  Would I get anywhere by trying to configure 2 addresses (from 2 different subnets) on the same interface?

---

### Post by qwerty555 on 2009-05-20
This should get you started
 
```
ddns-update-style none;
authoritative;
log-facility local7;
 
class "allowed"  {
     ( match if substring(hardware,1,6) = 00:00:00:00:00:00 ) or
     ( match if substring(hardware,1,6) = 00:00:00:00:00:00 );
  }

 
shared-network local {
        subnet 192.168.x.0 netmask 255.255.255.0 {
                range 192.168.x.100 192.168.x.200;
                default-lease-time 600;
                max-lease-time 7200;
                option subnet-mask 255.255.255.0;
                option broadcast-address 192.168.x.255;
                allow members of "allowed";
                deny unknown-clients;
                option routers 192.168.x.1;
                option domain-name-servers 192.168.x.10;
                option domain-name "domain.local";
                deny unknown-clients;
 
                host host1 {
                        hardware ethernet *:*:*:*:*:*;
                }
                host host2 {
                        hardware ethernet *:*:*:*:*:*;
                }
        }
 
        subnet 192.168.y.0 netmask 255.255.255.0 {
                range 192.168.y.100 192.168.y.200;
                default-lease-time 600;
                max-lease-time 7200;
                option subnet-mask 255.255.255.0;
                option broadcast-address 192.168.y.255;
                deny members of "allowed";
                option routers 192.168.y.1;
                option domain-name-servers 192.168.y.1;
                allow unknown-clients;
        }
}

```

---

