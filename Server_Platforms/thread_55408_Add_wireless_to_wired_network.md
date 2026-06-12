---
title: "Add wireless to wired network"
date: 2005-08-08
forum: Server Platforms
---

### Post by joepotter on 2005-08-08
We have been using a 3Com wireless router plus electronic switch, but we now need to use the server box as the router so that all net connections go through this box. We are testing content filtering via Dansguardian.

So, now what? I put the wireless router back in the parts bin and get a wireless access point? No way to use this expensive wireless router as just an access point?

Note: for many reasons I need all boxes to receive dhcp from the server box and be on 192.168.0.x because of the content filtering idea.

Any thoughts? Thanks.

---

### Post by costoa on 2005-08-09
[QUOTE=joepotter]We have been using a 3Com wireless router plus electronic switch, but we now need to use the server box as the router so that all net connections go through this box. We are testing content filtering via Dansguardian.

So, now what? I put the wireless router back in the parts bin and get a wireless access point? No way to use this expensive wireless router as just an access point?

Note: for many reasons I need all boxes to receive dhcp from the server box and be on 192.168.0.x because of the content filtering idea.

Any thoughts? Thanks.[/QUOTE]

Short answer: it can't be done the way you want. You could:
- Install a PCI 802.11x card in the server and use it as also a wireless router.
- Use the 3com router and connect it directly to the new server (via an extra eth card and crossover cable) and use it as a upstream router.
- Put the Dansguardian server anywhere reachable by all hosts, block port 80 et al and require users to add proxy server info in web browser.

If you really need to lock down your network go with the second suggestion, otherwise the third.

This is a really simple answer that will need clarification. What's the layout of your network (numbers and topography)?

Why do you have to use 192.168.0.x?

---

### Post by joepotter on 2005-08-09
[QUOTE=costoa]Short answer: it can't be done the way you want. You could:
- Install a PCI 802.11x card in the server and use it as also a wireless router.
- Use the 3com router and connect it directly to the new server (via an extra eth card and crossover cable) and use it as a upstream router.
- Put the Dansguardian server anywhere reachable by all hosts, block port 80 et al and require users to add proxy server info in web browser.

If you really need to lock down your network go with the second suggestion, otherwise the third.

This is a really simple answer that will need clarification. What's the layout of your network (numbers and topography)?

Why do you have to use 192.168.0.x?[/QUOTE]


Thanks for your thoughts.

I do not *have* to use 192.168.0.x but the network printer is 192.168.0.25 and I would like everyone to be able to print to it. It could be re-set to a different sub-net, of course, but then I would want to use whatever that new sub-net was to be sure that we could all reach the printer.

Plus, I need all to see 192.168.0.10 since that is the file server and it is a must for the kids to log on and see their /home which comes from nfs and 192.168.0.10.

I want to move several boxes to wireless but still have them on the same sub-net so they are filtered, can print to the network printer, and have access to the file-server.

I thought the 3Com wireless router/gateway would still work when I no longer needed the routing feature, but after studying the on-line docs I think I was mistaken. It gave an error when I wanted to set a static IP that was in the same sub-net as the DHCP output for the wireless side.
I should have guessed that.

So, I think I want:

Internet --> cable modem --> server(dhcp/nat/files) --> electronic switch --> wireless access point + rest of network. Then perhaps several other wireless access points later as we try to go wireless as much as possible. (boss wants that)

Then everything should be on sub-net 192.168.0.x and I should be able to treat all boxes as if they were wired and in our lab no matter where on campus they are.

The 3Com access point (3CRWE454G72) came today, but I have not tried it yet. My first problem is getting a windows box so that I can set the darn thing up. Seems you can use any browser on it, but you need to know its address first. The winders software will find it for you but Linux guys are left to hunt for it.

Do you see any flaws in this setup I have in mind? 


Thanks for all your help.

---

### Post by costoa on 2005-08-09
[QUOTE=joepotter]
 Seems you can use any browser on it, but you need to know its address first.
[/QUOTE]


Try 192.168.1.70. If that doesn't just hook it up to a hub (not a switch), fire up ethereal and watch for the ARP packets.

---

### Post by joepotter on 2005-08-10
[QUOTE=costoa]Try 192.168.1.70. If that doesn't just hook it up to a hub (not a switch), fire up ethereal and watch for the ARP packets.[/QUOTE]


As it turns out, you can look at the logs (dhcp3) and see it on the server box, but I still think 3Com should consider all the GNU/Linux guys and make life a little easier for us. But, I preach to the choir no doubt.

These access points are just the trick, and i ended up not wasting the wireless router in that one laptop needs to be treated as separate and special --- the bosses. Hence, I needed both devices in the end.

Thanks for all your help.

---

