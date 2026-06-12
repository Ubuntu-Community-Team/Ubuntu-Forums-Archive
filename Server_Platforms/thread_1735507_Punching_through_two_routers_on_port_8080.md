---
title: "Punching through two routers on port 8080"
date: 2011-04-21
forum: Server Platforms
---

### Post by Josiah4jc on 2011-04-21
Hey, I know this isn't really related strictly to ubuntu, but I'm using ubuntu for my apache server, I seem to be stuck getting incoming connections to punch through on port 8080.

so, let me describe my setup.

I have a westell 6100 dsl modem/router plugged into the WAN port of a linksys wgrt54g.

the westell is running a dhcp on 192.168.1.x and the linksys is running a dhcp on 192.168.0.x. my host is connected to the linksys via wireless.

So, just to get things rolling, I put the linksys on the dmz of the westell, and my host on the dmz (I also tried port forwarding here on 8080) of the linksys.

I fire up a web proxy, punch in myhost.dns.org:8080/
and I get nada, request timed out.
I punch in 127.0.0.1:8080/ and I get my test page.

Any advice? There must be some sysadmins out there who can help.

---

### Post by LingaringBell on 2011-04-21
I'm sorry but you will need to explain a little bit more.  By "myhost.dns.org:8080" do you mean a public web address?

---

### Post by Josiah4jc on 2011-04-21
> **LingaringBell said:**
> I'm sorry but you will need to explain a little bit more.  By "myhost.dns.org:8080" do you mean a public web address?

sorry, that should be "myhost.dyndns.org:8080", and yes, I do mean that it is publicly available, though generally: That is not my actual host name.

---

### Post by mbaas on 2011-04-21
Are u testing from within your own network? This can cause problems if your router doesn't support loopback connections

---

### Post by LingaringBell on 2011-04-21
Even without loop back the connection would just go out into the WAN then back in.  Are you sure that your NAT rules are correct?  Have you tried using the public IP instead of the dyndns name?

---

### Post by LingaringBell on 2011-04-21
Just thought of something else.  Where is your NAT taking place, on the Westell or the Linksys?  Westell routers won't do NAT for more than one subnet (very irritating).

---

### Post by Josiah4jc on 2011-04-21
Ok, so I solved the problem.

I did the following:
set the westell modem in bridge mode, as explained here:
[http://www.dslreports.com/faq/13600](http://www.dslreports.com/faq/13600)

And configured the WRT54GS to connect via PPPoE with the following settings:

username: newdsl
pass: newdsl1
host name: verizon.net
domain name: myhome.westell.com

I enabled MAC cloning and used the mac address of the dsl modem (it was clearly visible on the underside of the modem).

I already had configured the linksys router to forward port 8080 to my ubuntu box, so I fired up a web proxy, typed in my host on port 8080, and bingo! My test page loads.

A big shout-out to webmin, it made working with apache much more friendly.

---

