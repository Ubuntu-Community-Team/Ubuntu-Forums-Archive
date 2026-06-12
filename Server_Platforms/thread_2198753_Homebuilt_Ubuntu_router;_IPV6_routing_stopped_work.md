---
title: "Homebuilt Ubuntu router; IPV6 routing stopped working, please help!"
date: 2014-01-10
forum: Server Platforms
---

### Post by dan.mclaughlin on 2014-01-10
Hello,
  I'm really stuck on this. I had IPV6 routing working on my Ubuntu homebuilt router, but either because of an Ubuntu upgrade or other it doesn't work. I believe all the interfaces and RADVD are set up correctly, but ping6 and IPV6 traffic just get stuck, and I'm stuck at trying to solve it (have worked on it off and on for months). Also note that my Apple router happily will route IPV6, again verifying that my ISP will serve it up. Any help GREATLY appreciated. 

Now I'm still learning how IPV6 works differently from the IPV4 I'm used to, but from what I understand following [this guide]("http://www.phildev.net/phil/blog/?p=308") which is what I used to get this set up in the first place. I have UFW enabled, with NAT and ipv6 correctly set for forwarding (I believe). I'm running the latest ubuntu version, and I have the problem regardless of whether UFW is enabled or disabled. My external interface is (obscured to protect the innocent)

```
p1p1      Link encap:Ethernet  HWaddr 00:XX:XX:XX:XX:XX
          inet addr:XX.XXX.XX.XXX  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::XXX:XXXX:fea8:d4bb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2217 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3551615 (3.5 MB)  TX bytes:428420 (428.4 KB)
```

and my internal is 

```
p2p1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX
          inet addr:10.0.1.1  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::XXXX:XXXX:fea8:d4bc/64 Scope:Link
          inet6 addr: 2601:X:XXXX:XX::1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9000  Metric:1
          RX packets:2334 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:443299 (443.2 KB)  TX bytes:3327880 (3.3 MB)
```

I have radvd.conf set up

```
interface p2p1 {
   AdvSendAdvert on;
   RDNSS 2001:558:feed::1 2001:558:feed::2 {};
   RDNSS 2001:4860:4860::8888 2001:4860:4860::8844 {};
   prefix XXXX:X:XXXX:X::/64
      {
      AdvOnLink on;
      AdvAutonomous on;
     };
};
```

What other information do you need, and what tests can I run on this? Thank you for any help!

---

### Post by Kirk Schnable on 2014-01-11
First thing's first, is IPv6 connectivity actually working on your router machine itself?  If you try "ping6 google.com" for example, can you actually communicate using IPv6 at all?  

Sometimes when I'm setting up routing and firewalls I get caught up in the advanced steps I'm doing, and forget to check the basics first when something isn't working.  It does look like you have an IPv6 address assigned to your interface, so I'd expect this to work, but just making sure... :)

---

### Post by dan.mclaughlin on 2014-01-11
Thanks Kirk. As often happens, even though I've been working on this problem for months and months, I finally solved it last night, right after I put up this post. It turned out that "dhclient -6 -P -d -v external_interface" was lying to me. It was giving me the wrong prefix all this time. 

This time I poked into the file at "/var/lib/dhcp/dhclient6.leases" and tried that prefix and it worked. 

So my question then is, who is writing to that file, and why is the command line dhclient lying to me?

---

### Post by Kirk Schnable on 2014-01-11
> **dan.mclaughlin said:**
> Thanks Kirk. As often happens, even though I've been working on this problem for months and months, I finally solved it last night, right after I put up this post. It turned out that "dhclient -6 -P -d -v external_interface" was lying to me. It was giving me the wrong prefix all this time. 

This time I poked into the file at "/var/lib/dhcp/dhclient6.leases" and tried that prefix and it worked. 

So my question then is, who is writing to that file, and why is the command line dhclient lying to me?
Unfortunately, using IPv6 on a DHCP network is beyond my scope of knowledge.  Sadly, none of the Internet providers at my home or work offer IPv6 addresses yet.  I've only ever done IPv6 static IPs with my server on the OVH network.

Perhaps network-manager is the application which is writing to the dhclient6.leases file?

---

### Post by dan.mclaughlin on 2014-01-11
> **Kirk Schnable said:**
> Unfortunately, using IPv6 on a DHCP network is beyond my scope of knowledge.  Sadly, none of the Internet providers at my home or work offer IPv6 addresses yet.  I've only ever done IPv6 static IPs with my server on the OVH network.

Perhaps network-manager is the application which is writing to the dhclient6.leases file?

I looked into it. It looks like it's written by the command line "dhclient", but I don't know why the command line output is different and incorrect. 

IPV6 is normally "stateless" and auto configures itself. "dhclient" queries your router to receive a prefix, which it can then serve up to the interior network via radvd. There are some tricks such as the external interface to the Ubuntu router can use the lo "fe::" interface, but it must have an actual IPV6 address on the interior to forward properly. 

Well it works now finally, and I know why which is the important thing.

---

