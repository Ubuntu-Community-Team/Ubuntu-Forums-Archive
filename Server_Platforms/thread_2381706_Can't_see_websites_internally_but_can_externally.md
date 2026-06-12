---
title: "Can't see websites internally but can externally"
date: 2018-01-04
forum: Server Platforms
---

### Post by eddie19 on 2018-01-04
Hi
I'm using Ubuntu 16.04 LTS. Installed LAMP and bind. I am really confused on what I need to change on my server to enable me to see my sites locally. I'm using FreeDNS Afraid.org and that looks good. I have one virtual site. I can see it outside my network. I can't see on my network unless I use the IP. I am so confused on what exactly I need to configure on my server. Is it the hosts file? Is it the network interfaces file I should add my dns-nameservers. I have googles listed first then NS1.AFRAID.org. Below that I have my website linked to dns-search. The resolv.conf file looks correct ( I know that any changes here will be overwritten).

One more thing. I previously had a home web server work using Apache2, but I was using a microtek router that I was able to add a hairpin rule to the firewall. This allowed me to see my websites internally. Now I am using a comcast wifi modem with no way to set a NAT hairpin rule. Do I have to use a NAT hairpin rule?

I am off to work and I will be back to check for your solutions. I am sure that its something easy, but I'm totally lost at this point!

Thanks
Eddie

---

### Post by darkod on 2018-01-04
For a quick fix and for few home clients, the fastest way is to simply use an entry in the hosts file on each client. That would also be most efficient because basically the traffic from your local LAN never needs to go out to the internet at all, the server is right there...

---

### Post by eddie19 on 2018-01-05
Thanks for your quick response. Your idea worked great. Have a nice day mate.

---

