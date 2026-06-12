---
title: "Problem With DHCP/DNS &amp; Media Devices"
date: 2012-05-02
forum: Server Platforms
---

### Post by jlacroix on 2012-05-02
Hello everyone. I have a very strange problem and I'm not sure where to turn. I've been trying to figure this out for a while and so far, I've gotten nowhere.

I have a DNS/DHCP server running (now) Ubuntu 12.04 (the server is called "Hermes" so that's what I'll call it henceforth). I set up Hermes in my home for the purposes of learning, and also so I can have more control over my network. Other than the problem I'm about to mention, I absolutely love it. 

The problem I have is with my Roku and PS3, both of which use Hulu and Netflix on our televisions. If I shut Hermes down for maintenance or whatever, both the Roku and PS3 cannot access the Internet. On the other hand, my other computers (one Windows 7 machine, at least four Linux PC's at any one time) have no issues at all. They just use the secondary DNS that I have set up, which points to my D-Link router.

So in short summary, if I shut Hermes down, all my PC's seem to be accessing my D-Link router directly (which is correct, since it was set up as the secondary DNS server) but the PS3 and Roku just won't, even though I check the network properties and the secondary DNS address IS set.

The only difference I can think of between the Roku and PS3 is that they use DHCP, whereas all my other computers are static. But, even with DHCP, those two boxes should be using the secondary DNS to get name resolution, right?

I have a feeling that this is something outside of the realm of Ubuntu (or something I missed in setup) but I have a feeling if I start talking about my DNS server in a PS3 forum, it will go over peoples heads. So I'm hoping it's something on the Ubuntu side I can fix.

Is there something I may have configured that isn't allowing the other devices to fail over to their secondary DNS and continue working when Hermes is shut down?

---

### Post by dgorack on 2012-05-02
Can you use your router as the DHCP server instead and keep DNS on Hermes?

I think that you could also set a DHCP reservation on your router, depending on your router of course, so both get the same IPs each time.

---

### Post by jlacroix on 2012-05-02
> **dgorack said:**
> Can you use your router as the DHCP server instead and keep DNS on Hermes?

I think that you could also set a DHCP reservation on your router, depending on your router of course, so both get the same IPs each time.
I'd rather keep DHCP on the server for now.

If I set a reservation, how would that prevent the media boxes from not using secondary DNS when the server is shut down? I'm sure there's probably something obvious that I'm missing.

---

### Post by newbie-user on 2012-05-03
Have you set up your Roku and PS3 to use static addresses instead of DHCP? If not, that's probably the problem right there. DHCP tells the devices all about the network, including where to find the DNS servers, the gateways, and how big the network is.

Your computers work fine when Hermes is down because you manually specified network information on each one. Do that for Roku and PS3 and you won't have any more problems.

---

### Post by jlacroix on 2012-05-03
> **newbie-user said:**
> Have you set up your Roku and PS3 to use static addresses instead of DHCP? If not, that's probably the problem right there. DHCP tells the devices all about the network, including where to find the DNS servers, the gateways, and how big the network is.

Your computers work fine when Hermes is down because you manually specified network information on each one. Do that for Roku and PS3 and you won't have any more problems.
I'll definitely try that when I get home.

But I'm not completely understanding yet. If a machine reaches out for an IP address and DNS servers, it forgets that as soon as the machine that provided DHCP is no longer turned on? I was thinking that the DHCP devices would only look for new network information whenever the lease expires, but continue to use the information that was provided during the initial lease. Unless, maybe the DHCP server is providing a default gateway for the IP address of Hermes and not the router?

Just want to make sure I'm understanding properly :)

---

### Post by Jonathan L on 2012-05-03
> But I'm not completely understanding yet. If a machine reaches out for an IP address and DNS servers, it forgets that as soon as the machine that provided DHCP is no longer turned on? I was thinking that the DHCP devices would only look for new network information whenever the lease expires, but continue to use the information that was provided during the initial lease. Unless, maybe the DHCP server is providing a default gateway for the IP address of Hermes and not the router?

Hi jlacroix

I'd check the DNS servers, router, and least times on your DHCP server (/etc/dhcp3/dhcpd.conf)
```

option routers 192.168.0.1;
option domain-name-servers 192.168.0.2;
default-lease-time 7200;
max-lease-time 7200;

```
Clients should use the information they get from the DHCP server only until lease expiry.  They will first start contacting the server for renewal at 50% lease time, and start looking for any DHCP server at 87.5% of the least time.  They should stop using it after the expiry, but lots of clients will keep using their details in a desperate "might-work" attitude.  (If you care, details in [http://tools.ietf.org/html/rfc1531](http://tools.ietf.org/html/rfc1531), section 4.4.4, percentages typical not mandatory.)

So: suppose your DHCP server (192.168.0.254) gives out a router address (.1) and a DNS server address (.2) ... then the clients should operate for their lease times so long as .1 and .2 are running.  The DHCP server is only required during renewal.

Hope that helps.

Kind regards,
Jonathan.

---

### Post by SeijiSensei on 2012-05-03
I'd just use static configurations on the PS/3 and Roku boxes.  Give them addresses outside the range assigned by DHCP and the appropriate gateway address (your router) and DNS.  Frankly since they are going to be accessing off-site servers all the time, I'd make the router the primary DNS for these boxes or use something like Google's 8.8.8.8 and 8.8.4.4 addresses.  Then they'll be resistant to any failure by Hermes.

---

### Post by jlacroix on 2012-05-03
> **Jonathan L said:**
> Hi jlacroix

I'd check the DNS servers, router, and least times on your DHCP server (/etc/dhcp3/dhcpd.conf)
```

option routers 192.168.0.1;
option domain-name-servers 192.168.0.2;
default-lease-time 7200;
max-lease-time 7200;

```
Clients should use the information they get from the DHCP server only until lease expiry.  They will first start contacting the server for renewal at 50% lease time, and start looking for any DHCP server at 87.5% of the least time.  They should stop using it after the expiry, but lots of clients will keep using their details in a desperate "might-work" attitude.  (If you care, details in [http://tools.ietf.org/html/rfc1531](http://tools.ietf.org/html/rfc1531), section 4.4.4, percentages typical not mandatory.)

So: suppose your DHCP server (192.168.0.254) gives out a router address (.1) and a DNS server address (.2) ... then the clients should operate for their lease times so long as .1 and .2 are running.  The DHCP server is only required during renewal.

Hope that helps.

Kind regards,
Jonathan.
Thanks for your reply! Your explanation is where my mindset was at, that as long as it's not expired, the hosts should use the DHCP/DNS addresses that were provided to them. I didn't know that it checked a bit prior to the expire time.

My dhcpd.conf is actually located at /etc/dhcp/dhcpd.conf (not dhcp3) is that okay? Here is that file:
```
# Sample /etc/dhcpd.conf
# (add your comments here)
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 172.16.254.255;
option routers 172.16.254.1;
option domain-name-servers 172.16.254.5, 172.16.254.1;
option domain-name "localnet";

subnet 172.16.254.0 netmask 255.255.255.0 {
range 172.16.254.200 172.16.254.250;
}
```

Is that lease time in seconds? If so, I'd say that is pretty short. I just changed both the default and max to 1209600 which I think is two weeks. Maybe that will help?



> **SeijiSensei said:**
> I'd just use static configurations on the PS/3 and Roku boxes.  Give them addresses outside the range assigned by DHCP and the appropriate gateway address (your router) and DNS.  Frankly since they are going to be accessing off-site servers all the time, I'd make the router the primary DNS for these boxes or use something like Google's 8.8.8.8 and 8.8.4.4 addresses.  Then they'll be resistant to any failure by Hermes.
That's an awesome idea, I'll definitely do that!

---

### Post by Jonathan L on 2012-05-03
For just a couple of computers, doing them static makes a lot of sense.  Or all DHCP, possibly with fixed addresses.  I certainly wouldn't do both: just a duplication of effort.  If your server isn't going to be up continuously, don't use it for DHCP: do DHCP on the router and DNS on the router, ISP, or Google.

But for four computers, like everyone says: static is fine.

Kind regards,
Jonathan.

---

### Post by jlacroix on 2012-05-03
> **Jonathan L said:**
> For just a couple of computers, doing them static makes a lot of sense.  Or all DHCP, possibly with fixed addresses.  I certainly wouldn't do both: just a duplication of effort.  If your server isn't going to be up continuously, don't use it for DHCP: do DHCP on the router and DNS on the router, ISP, or Google.

But for four computers, like everyone says: static is fine.

Kind regards,
Jonathan.

My server isn't down continously, I had to take it down twice to do maintenance on it (one time of which was to upgrade to 12.04). It just alarmed me that the media boxes weren't working while I performed the upgrade.

---

### Post by jlacroix on 2012-05-04
I'm going to mark this complete for now. The problem is solved with the PS3 and I implemented the changes suggested here. However, Roku cannot have a static IP so there's probably nothing I can do about that.

Thanks guys!

---

