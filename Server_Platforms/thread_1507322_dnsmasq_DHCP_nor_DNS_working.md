---
title: "dnsmasq DHCP nor DNS working"
date: 2010-06-11
forum: Server Platforms
---

### Post by joel_gil on 2010-06-11
Hi
I have been rtying for a couple of days now to set up a local dns/dhcp server with dnsmasq on a ubunut server 10.04

I followed the basic instructions from several websites, starting with the ubuntu community one, didnt work, then tried some other, and nothing.

In the server the dns works, i test with dig example.com and i can see the time difference, so dns is working.

so the problem is not making the dns work but to make the server listen for dns and dhcp resquests and respond to them.

I have desactivated the dhcp from the router so thats not the problem. making a windows box ping the server works, so the network is configured correctly.

dnsmaq is listed as "LISTEN" on netstat, i read in some blog that it should be using ports 67 and 68 but those are no listed, neither i configured them in any moments, none of the instructions i followed mentioned sth about that.

i even tried configuring the window box with the ips and dns accordingly and that wouldnt work either.

so in conclusin i have dnsmasq that does have dns set up but wont answer to any requests of either DNS nor DHCP.

any help will be greatly appreciated

---

### Post by koenn on 2010-06-11
your post does not contain enough info and is pretty confusing.

post the parts of your dnsmasq conf that control the dhcp setup + the netwerk conf of the dnsmasq server + your network design

also, 
"and i can see the time difference, so dns is working" doesn't make much sense, you may want to explain what you think it means.

"making a windows box ping the server works, so the network is configured correctly" contradicts "making a windows box ping the server works, so the network is configured correctly", you may want to elaborate and clarify.


lastly, look in syslog, dnsmasq logs any problem it may have there

---

