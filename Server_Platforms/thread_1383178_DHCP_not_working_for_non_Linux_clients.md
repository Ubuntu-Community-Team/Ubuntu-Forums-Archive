---
title: "DHCP not working for non Linux clients"
date: 2010-01-16
forum: Server Platforms
---

### Post by ulnagar on 2010-01-16
Hi guys,

I have a Hardy server that runs DHCP3-Server and Bind9 packages for my local network. I've had a number of Ubuntu servers over the last few years, and never had trouble like this.

A couple of days ago, DHCP stopped giving addresses to non-Ubuntu clients. Or rather, non-Ubuntu clients stopped accepting addresses from the DHCP server. I have a number of devices in the house, an Ubuntu 9.04 media centre pc, an xbox 360, an iMac (PPC 10.4.11), a Vista laptop, and a dual-boot Win7/Karmic laptop. All of these were able to successfully use DHCP until a few days ago.

At the moment the media centre pc and the Karmic install on the laptop still work fine, but all others (including the Win7 install on the same device) does not.

Here is a sample from the syslog:

```
Jan 17 14:00:50 tokyo dhcpd: DHCPDISCOVER from 00:11:24:71:65:d0 via eth0                                                                       
Jan 17 14:00:51 tokyo dhcpd: DHCPOFFER on 192.168.1.193 to 00:11:24:71:65:d0 (cairo) via eth0                                                   
Jan 17 14:00:58 tokyo dhcpd: DHCPDISCOVER from 00:11:24:71:65:d0 (cairo) via eth0                                                               
Jan 17 14:00:58 tokyo dhcpd: DHCPOFFER on 192.168.1.193 to 00:11:24:71:65:d0 (cairo) via eth0                                                   
Jan 17 14:01:07 tokyo dhcpd: DHCPDISCOVER from 00:11:24:71:65:d0 (cairo) via eth0                                                               
Jan 17 14:01:07 tokyo dhcpd: DHCPOFFER on 192.168.1.193 to 00:11:24:71:65:d0 (cairo) via eth0
```

This is the entry for the iMac, but all the others look the same (execpt the MAC and offered address, of course).

Here is my dhcpd.conf

```
server-identifier       tokyo;                                                                                                                  
ddns-updates            on;                                                                                                                     
ddns-update-style       interim;                                                                                                                
ddns-domainname         "mdh.local.";                                                                                                           
ddns-rev-domainname     "in-addr.arpa.";                                                                                                        
ignore                  client-updates;                                                                                                         
include                 "/etc/bind/rndc.key";                                                                                                   
                                                                                                                                                
zone mdh.local. {                                                                                                                               
    primary 127.0.0.1;                                                                                                                          
    key rndc-key;                                                                                                                               
}                                                                                                                                               
                                                                                                                                                
option domain-name "mdh.local";                                                                                                                 
option domain-name-servers 192.168.1.200;                                                                                                       
                                                                                                                                                
default-lease-time 600;                                                                                                                         
max-lease-time 7200;                                                                                                                            
                                                                                                                                                
authoritative;                                                                                                                                  
                                                                                                                                                
log-facility local7;                                                                                                                            
                                                                                                                                                
subnet 192.168.1.0 netmask 255.255.255.0 {                                                                                                      
    range 192.168.1.100 192.168.1.199;                                                                                                          
    option routers 192.168.1.1;                                                                                                                 
    option domain-name "mdh.local";                                                                                                             
    option domain-name-servers 192.168.1.200;                                                                                                   
    option broadcast-address 192.168.1.255;                                                                                                     
    default-lease-time 600;                                                                                                                     
    max-lease-time 7200;                                                                                                                        
}
```

I have done a complete system update on the server, and rebooted. Any help would be greatly appreciated as at the moment I have all non-Ubuntu devices set with static addresses, and I would prefer not to have it like that.

Regards,

Ulnagar

---

### Post by steven.jones on 2010-01-17
Try increasing the subnet range from 199 to say 210...maybe old Ips are not being flushed properly and returned to the pool.

I run lots of different Oses off a Debian DHCP server with no problems (ubuntu, OSX, Vista, XP, iPhone) .....so I cant see why some get but others dont....possibly protocol version? firewall port blocked? a security update recently? 

Clean out the leases file and force all the machines to all update one at a time....maybe one client is repeatedly asking for an IP and using them all up....

---

### Post by ulnagar on 2010-01-17
I did not try to change the range length, since my server is actually sitting at .200 however I have deleted the leases file so it started fresh. Even so, non-Linux clients are still unable to get a DHCP address.

This setup was working perfectly until last week, and I cannot think of anything that changed. I do not have a firewall on this box.

Any other suggestions?

---

### Post by ulnagar on 2010-02-02
Shameless bump.

It's been a few weeks now, and I am getting the exact same behaviour. I've had to set all non-Ubuntu devices to static addresses just to get online. I recently bought a new Wii, and it had exactly the same issue.

Does anyone have any idea whatsoever?

Thanks

---

### Post by mgichoga on 2010-02-03
Hmm...never heard of this before. You could try disable ddns

> dns-update-style none;
ddns-updates off;

---

### Post by R.Bucky on 2010-02-03
Have you tried assigning static ip's to the boxes on your network?

---

### Post by ulnagar on 2010-02-03
I can log into Windows, say, and assign a static address without problems.

Or do you mean assign a static address in the DHCP config?

---

### Post by koenn on 2010-02-04
does it work if you tell the clients to request a new lease, 
eg on windows
```

ipconfig /release
ipconfig /renew

```

---

### Post by terazen on 2010-02-04
What kind of device is 192.168.1.1?  Your server should at least be getting dhcp requests, even if the server doesn't answer them, and you aren't even getting that it seems.

If you have a cheap 4 port hub you can put one of your windows machines and your dhcp server on the same hub and then take the router out of the equation.  Other than that you'd need to run a packet sniffer on your dhcp server to make sure it's even receiving requests.

---

### Post by ulnagar on 2010-02-07
Thanks for all your help guys, but I somehow managed to fix this.

I recreated the dhcpd.conf file, and reloaded dhcp3-server and it is now working. The new conf file contains the exact same commands as the old, so I don't know why it fixed it, but it did.

Thanks again for your help.

---

