---
title: "ISPconfig help / webserver help"
date: 2007-02-07
forum: Server Platforms
---

### Post by gorilly on 2007-02-07
Hi All,

I'm hoping someone on here has some experience with ISP config.

I set up a ubuntu 6.06LTS server and followed the guide on howtoforge for making the perfect web server.

i then installed ISPconfig and its all running ok.

the question i have is so stupid im embarrased to ask but i cant figure out where i am going wrong.

i am trying to set up a hosting account for one of my friends, he wants to host a web page via my webserver (so i am his ISP).
i made his account in ISP config, he can log into the user control panel etc, he can upload his site etc.

the questions is where do i view his site?!?!

so for example i have a ispconfig server at 192.168.1.100
i have created him a website called websitetest
surely to get to his site internally it will be something like 192.168.1.100/websitetest??

Any help will be much appreciated!

thanks

---

### Post by mkurz on 2007-02-07
Hi,

yes that is a bit strange with ISPconfig, I know. As far as I know there is no URL-Path like you expect. What you can do is to create a subdomain of your webservers name. It should have some kind of name. 

For example: My webserver is server-3.de, it is normally not the name for my customers. But if I want to provide webspace without a real domain name, he will get some sort of: web7.server-3.de. You can define this name. 

The only thing you have to check is, if the DNS-Server can resolve the name.

So far, 
Greetings, Martin

---

### Post by gorilly on 2007-02-07
thanks for your input mate,

i think i kind of understand.

so it should be able to be found at his username OR domain name (not sure which without trying). so for example his username is web1_chris.

so web1.mydomain.com or web1_chris.mydomain.com should work?

i will try this when i get home.


the gap i dont understand now is this. when i buy webspace from an ISP how do they host my domain to begin with? for example i buy domain.com from virtualnames.co.uk

where did virtualnames have it in the first place?!? or was it just an A record pointing at virtual names?

thanks again, you have been a big help! maybe my question was not so silly after all

---

### Post by gorilly on 2007-02-07
ok from what i can gather i can only run one website from my ispconfig server because i only have one IP address.

for multiple sites i must have multiple ips on my WAN connection.

am i right in thinking this??
i thought the whole point of ISPconfig was so you could host multiple sites via one server

---

### Post by gorilly on 2007-02-08
i got it working in the end. not really sure how :confused: 

but the main thing is that it works!!

i have two seperate domains, both pointing at my WAN ip 86.XX.XX.XX and for some reason it just resolves the seperate sites!

now for my SQL/php questions lol

---

### Post by Aberrix on 2007-02-08
> **gorilly said:**
> 
i have two seperate domains, both pointing at my WAN ip 86.XX.XX.XX and for some reason it just resolves the seperate sites!


this is thanks to the DNS server within ISPConfig.

ISPConfig = great stuff!

---

