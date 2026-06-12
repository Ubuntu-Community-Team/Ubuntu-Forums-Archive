---
title: "WordPress NAT problem"
date: 2008-04-04
forum: Server Platforms
---

### Post by mr_fong on 2008-04-04
Hello everyone,

I'm running my own little webserver behind my router/firewall (Linksys WRT54G). It's an old 230 MHz thin client, so slow for today's standards. The site is [http://neo.dyn-o-saur.com]("http://neo.dyn-o-saur.com") and the dns service links via NAT to my internal address of 192.168.1.100. 

I want to run my own blog and installed WordPress. Within my network the [blog]("http://neo.dyn-o-saur.com/garden2008") loads in about 10 seconds. From outside it times out because it gets no response from the address 192.168.1.100. 

Can anyone tell me what is going wrong here? And maybe in what direction I should be looking for solutions? (Please don't tell me I should be buying a faster server, because then I'll cry :-?

Oh yes, I did try another blog engine (Pivot), but I found the configuration too cumbersome. It only relies on PHP though and this did work. Thanks for the help.

Hans

---

### Post by Oldsoldier2003 on 2008-04-05
Seems to work fine from here. depending on your network config and your router you may just have to access it with the internal IP when you are on your internal network, I have to do that with my server.

---

