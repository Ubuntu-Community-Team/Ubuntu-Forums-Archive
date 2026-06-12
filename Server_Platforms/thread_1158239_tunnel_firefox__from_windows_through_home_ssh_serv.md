---
title: "tunnel firefox  from windows through home ssh server"
date: 2009-05-13
forum: Server Platforms
---

### Post by Sir_Sid on 2009-05-13
Hi
I had a couple questions. The first question is I guess almost a definition question. Here is what I would like to do currently. In windows, I would like to use Putty to ssh to my home ubuntu server and then have firefox run all traffic through that connecton. More or less I want to be browsing the web from my home server. Is this called https tunneling?


My second question is how do I do this. I found some guides online, but I was not able to follow them as they seem to use older versions of putty. I know how to configure firefox to use a socks proxy but I dont know how to set up putty to make one.

---

### Post by cdenley on 2009-05-13
In putty, configure a dynamic port forward before you connect.
[ATTACH]113650[/ATTACH][ATTACH]113651[/ATTACH]
Then in firefox, under network settings, configure it to use localhost or 127.0.0.1 as a socks proxy on the port you specified for the dynamic port forward.
[ATTACH]113653[/ATTACH]

And no, this is not called https tunneling. It may be called ssh tunneling, although everything done through ssh is tunneled through the encrypted connection. Dynamic port forwarding with ssh would probably be more descriptive.

---

### Post by Mythbuster1848 on 2009-05-13
Hi,

The previous reply is bang on. I do this all the time. The only difference is that I use the Firefox FoxyProxy extension so I can specify which websites I want to go through the tunnel and which ones I don't. This is useful if you have bandwidth concerns at home. 

Also, if you're concerned about privacy and you're using a computer you don't own or control, I've found the PortableApps ([www.portableapps.com]("http://www.portableapps.com")) version of Firefox quite useful. It runs from a self-contained folder (on a USB key or elsewhere) so it doesn't touch the Windows registry and doesn't leave temporary internet files (like history and cache) all over the place.

---

