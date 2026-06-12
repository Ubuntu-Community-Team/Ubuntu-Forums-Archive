---
title: "Advantages/Disadvantages of Long/Short Client Lease Times of Routers"
date: 2007-07-04
forum: The Cafe
---

### Post by user1397 on 2007-07-04
[FONT=Tahoma][SIZE=2]I was looking at the settings of my linksys wireless-g router today, and I noticed that in the main setup page, there is an option for "Client Lease Time"

The info on the right says: "The Client Lease Time is the amount of time a network user will be allowed connection to the Router with their current dynamic IP address. Enter the amount of time, in minutes, that the user will be "leased" this dynamic IP address."

I understand all that, but...I don't understand WHY you would put the amount of time as 1 minute, or as 9,999 minutes...

Are there any advantages/disadvantages that I should be aware of when adjusting this setting?

To note: I have 3 wireless computers in my household that connect through this router.
[/SIZE][/FONT]

---

### Post by jrusso2 on 2007-07-04
I don't think in a home network it makes much difference.  When you have a large amount of computers then you run increase the amount of load on the DHCP server if it has to be working all the time renewing leases and it adds traffic to the network.

Also on a large network the chances of a conflict occurring are greater if you use a long lease time

---

### Post by user1397 on 2007-07-04
> **jrusso2 said:**
> I don't think in a home network it makes much difference.  When you have a large amount of computers then you run increase the amount of load on the DHCP server if it has to be working all the time renewing leases and it adds traffic to the network.

Also on a large network the chances of a conflict occurring are greater if you use a long lease timeAh, ok.  So if I set it at like 10 minutes, it'll all be cool, right? (according to my specific situation, i mean)

---

### Post by user1397 on 2007-07-04
bump

---

### Post by jrusso2 on 2007-07-04
I think 24 hours is a good amount of time.

---

### Post by matthinckley on 2007-07-04
If you have a large network with machines being removed and connected to the network a lot.. you may run out of available IP addresses even though some are not being used.. 

for example say you have a dhcp range of 192.168.1.1 -- 192.168.1.20 and a lease time of 1 week.. now say you connect 20 computers to your network and they all lease IP addresses.. if you remove one computer and connect a different machine that machine will not be able to obtain an IP address until the week is up as all 20 available IP addresses have been leased out..

It is doubtful this would ever occur in a home network as most home networks consist of less than 10 workstations and most routers are configured with a dhcp range of well over 100 IP's.

---

### Post by Atomic Dog on 2007-07-04
For a home router it doesn't matter too much, but less than a day could cause issues if gaming with others online.  My buddy has DSL and they release like every hour or two and it's a pain in the butt.  Set it for a couple days or so and you're fine.

Now Matt is 100% on the money as far as a work/large network.  You don't want to run out of ip's.  You should also check your dhcp scope (Matt calls it range) every now and then and adjust if your network is growing.  You can also assign static ip's outside the scope for certain systems/devices on the network.  At my work the scope is between 192.168.100.50 and .150.  We have a bunch of stuff with static ip's above and below that.  (webcams, printers, workstations, servers, switches, routers, kvm's, and a partridge in a pear tree).  So what were we talking about?

---

### Post by matthinckley on 2007-07-04
scope is the correct term.. but I think linksys does call it range.. i could be mistaken though..  :)

---

### Post by Atomic Dog on 2007-07-05
A home router.  No doubt they would use a more "basic" term as to not confuse users.:D

---

### Post by user1397 on 2007-07-05
What about "group key renewals" for the WPA2 encryption key: should this be about the same amount of time as the client lease time, or not?

Thanks for all the answers so far.

---

### Post by Sunforge on 2007-07-05
On networks of less than 10 machines (my arbitrary choice) long DHCP lease times make more sense because the community of machines is unlikely to change, especially on home networks. Setting DHCP to a week wouldn't hurt for three machines and an average subnet on these routers is a class C (254 usable addresses) so you're unlikely to run out of IPs.

For a high level view of DHCP this is about the best guide I've found: it's long but quite comprehensive:

[http://www.dhcp-handbook.com/dhcp_faq.html](http://www.dhcp-handbook.com/dhcp_faq.html)

Wireless key rotation can be as often as you like depending on your paranoia setting. I think every few hours should be enough for most home networks.

This link addresses a Linksys system and might give you some more practical information:

[http://www.networksystemsdesignline.com/howto/197007563](http://www.networksystemsdesignline.com/howto/197007563)

This is a moderately technical look at WEP, TKIP and WPA which might interest you if you want a high level view of how wireless hangs together:

[http://www.embedded.com/shared/printableArticle.jhtml?articleID=34400002](http://www.embedded.com/shared/printableArticle.jhtml?articleID=34400002)

Hope this helps. If anyone has found other good guides to wireless, please let me know as I'm always on the lookout for more stuff to pass on to my guys at work.

---

### Post by user1397 on 2007-07-05
> **Sunforge said:**
> On networks of less than 10 machines (my arbitrary choice) long DHCP lease times make more sense because the community of machines is unlikely to change, especially on home networks. Setting DHCP to a week wouldn't hurt for three machines and an average subnet on these routers is a class C (254 usable addresses) so you're unlikely to run out of IPs.

For a high level view of DHCP this is about the best guide I've found: it's long but quite comprehensive:

[http://www.dhcp-handbook.com/dhcp_faq.html](http://www.dhcp-handbook.com/dhcp_faq.html)

Wireless key rotation can be as often as you like depending on your paranoia setting. I think every few hours should be enough for most home networks.

This link addresses a Linksys system and might give you some more practical information:

[http://www.networksystemsdesignline.com/howto/197007563](http://www.networksystemsdesignline.com/howto/197007563)

This is a moderately technical look at WEP, TKIP and WPA which might interest you if you want a high level view of how wireless hangs together:

[http://www.embedded.com/shared/printableArticle.jhtml?articleID=34400002](http://www.embedded.com/shared/printableArticle.jhtml?articleID=34400002)

Hope this helps. If anyone has found other good guides to wireless, please let me know as I'm always on the lookout for more stuff to pass on to my guys at work.wow, thanks for all those links!

---

### Post by Sunforge on 2007-07-06
Not a problem.

Wireless protocols are a headache, as there are all sorts of theoretical risks that you could fall foul of.
 
Do remember that a healthy dose of common sense always helps when dealing with security.

---

