---
title: "Trouble with Raring and IPv6"
date: 2013-01-23
forum: Ubuntu Development Version
---

### Post by mcellius on 2013-01-23
On this computer (a laptop) I have three versions of Ubuntu installed: 12.04, 12.10, and I'm also testing Raring.  Networking - both wireless and wired - works well with all three.  However, the IPv6 address for Raring that is displayed as the public address (e.g. at test-ipv6.com, and all others) for my wired connection, is the one that contains the mac address for my computer.  I really don't want my IPv6 address to display my mac address, of course.  This does not occur with Ubuntu 12.04 or with 12.10, and nothing special has been configured on either system that might make a difference.

I am using a Linksys router that has IPv6 configured manually, using information obtained from Hurricane Electric.  The IPv4 addresses assigned by the router are statically assigned to different computers (by mac addresses), but IPv6 addresses are not statically assigned.  However, after each reboot Raring receives the same public IPv6 address (which displays the mac address), whereas the public IPv6 addresses assigned when I boot either 12.04 or 12.10 vary.

Can this be fixed in Raring?  Have I missed something?  Or is this a bug I should report?

Thanks!

---

### Post by mcellius on 2013-01-25
bump

---

### Post by lemming465 on 2013-01-25
So your network topology looks like
  {client1,client2,client3} --- linksys --- ISP modem ... internet

For IPv4 we assume you have one public IPv4 on the upstream side of the linksys, the ISP modem is bridging, and clients are on private IPv4 addresses (rfc1918) with NAT44 translation by the linksys.

For IPv6 we assume that the linksys is doing a 6in4 tunnel up to a Hurricane Electric proxy, and emitting ICMPv6 router advertisements for a /64 toward your clients.  You can test that assumption by installing the ndisc6 package and running the rdisc6 tool, e.g. **rdisc6 eth0** or **rdisc6 wlan0** or whatever your active network interface is.

If some of the v6 clients are using EUI-64 host parts and some aren't, then their /proc/sys/net/ipv6/conf/*INTERFACE*/use_tempaddr settings are probably different.  I think 0=off, 1=on, and 2=preferred.

We'll have to look into why this is suddenly different in raring.

---

### Post by mcellius on 2013-01-25
Thanks, Lemming.  Your knowledge about all of this is clearly way beyond mine, but I'll try.  :)

This is rdisc eth0 from the problem laptop (running Raring):

```
mdk@Savina:~$ rdisc6 eth0
Soliciting ff02::2 (ff02::2) on eth0...

Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Prefix                   : fda0:77f2:fffe::/64
  Valid time              :         7200 (0x00001c20) seconds
  Pref. time              :         3600 (0x00000e10) seconds
 Prefix                   : 2001:470:1f04:1e14:4200::/64
  Valid time              :         7200 (0x00001c20) seconds
  Pref. time              :         3600 (0x00000e10) seconds
 MTU                      :         1280 bytes (valid)
 Source link-layer address: XX:XX:XX:XX:XX:XX
 from fe80::c2c1:c0ff:fec6:3308
```This, by contrast, is from the same laptop but booted into 12.10, where it works fine:

```
mdk@savina:~$ rdisc6 eth0
Soliciting ff02::2 (ff02::2) on eth0...

Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Prefix                   : fda0:77f2:fffe::/64
  Valid time              :         7200 (0x00001c20) seconds
  Pref. time              :         3600 (0x00000e10) seconds
 Prefix                   : 2001:470:1f04:1e14:4200::/64
  Valid time              :         7200 (0x00001c20) seconds
  Pref. time              :         3600 (0x00000e10) seconds
 MTU                      :         1280 bytes (valid)
 Source link-layer address: XX:XX:XX:XX:XX:XX
 from fe80::c2c1:c0ff:fec6:3308
```I don't see any difference between them.

---

### Post by mcellius on 2013-01-25
I looked in /proc/sys/net/ipv6/conf/eth0/use_tempaddr for 12.10 and for Raring, and they are different.  In 12.10, the setting is "2" and in Raring it is "0".  I'll go ahead and change it in Raring to "2" and see how it does (assuming I'm allowed to change it; I have permission, obviously, but I'm not sure if this is something I ought to do, although I figure I can back out of it if I need to).

Edit: No, I can't edit the file.  I can make the change, but then I'm unable to save it.

---

### Post by lemming465 on 2013-01-28
One wouldn't expect the rdisc6 output to be different between the two OS's, as that's controlled by the RA's from the upstream router, not the ubuntu client.  One would expect the output of "ip address show" to be different if the privacy / temp address settings are different on the clients.

I haven't tried using editors on /proc settings; that might or might not work depending on their strategies with temp files and renames versus rewrite-in-place.   I assume you were running the editor as root.  Things that probably would work:```
sudo -i
echo 2 > /proc/sys/net/ipv6/conf/eth0/use_tempaddr
exit
```
or ```
sudo sysctl -w net.ipv6.conf.eth0.use_tempaddr=2
```

---

### Post by mcellius on 2013-01-28
I tried the second of those two commands, and it worked!  Thanks!

So now my public IPv6 address does not contain the computer's mac address.  I wonder if this will be changed in the Raring defaults when 13.04 is released.  Both 12.04 and 12.10 didn't require any such fiddling around, so this looks to be the result of some networking changes and work in Raring.

EDIT: Nope.  I just ran updates & upgrades and now it's back to not working.  I assume one of the packages "updated" things back to how it was before.

---

### Post by cariboo on 2013-01-28
> **mcellius said:**
> I tried the second of those two commands, and it worked!  Thanks!

So now my public IPv6 address does not contain the computer's mac address.  I wonder if this will be changed in the Raring defaults when 13.04 is released.  Both 12.04 and 12.10 didn't require any such fiddling around, so this looks to be the result of some networking changes and work in Raring.

EDIT: Nope.  I just ran updates & upgrades and now it's back to not working.  I assume one of the packages "updated" things back to how it was before.

I hope you submitted a bug report, for this problem.

---

### Post by mcellius on 2013-01-28
Not yet, but I'll head over there now and do it.  I was hoping I had just missed something, but now it doesn't look like it.

---

### Post by cariboo on 2013-01-29
> **mcellius said:**
> Not yet, but I'll head over there now and do it.  I was hoping I had just missed something, but now it doesn't look like it.

Thanks, I've got buckle down, and do some studying, when it comes to IPv6.

---

### Post by mcellius on 2013-01-29
> Thanks, I've got buckle down, and do some studying, when it comes to IPv6.

Yeah, so do I.  I think I've learned enough to avoid doing much damage, but not enough to be comfortable and flexible with it, and certainly not enough to be much good at solving problems.

---

### Post by lemming465 on 2013-02-02
The first two things to wrap your head around are:

* ICMPv6 RA's + DHCPv6 + ICMPv6 Neighbor Discovery require multicast, and aren't like DHCPv4 + ARP.

* There are way too many tunneling technologies (6rd, 6in4, 6to4, Teredo, ISATAP, 6over4, ...)

---

