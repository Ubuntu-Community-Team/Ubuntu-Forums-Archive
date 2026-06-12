---
title: "Dns"
date: 2017-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by sosproject on 2017-07-15
How i can regist my server with [www.exemple.org](www.exemple.org)

---

### Post by sosproject on 2017-07-15
How i can regist dns (i use Ubuntu server)

---

### Post by oldos2er on 2017-07-15
Are you asking how to register a world-readable DNS server? If so, that's a question that's beyond the scope of this support forum to answer. It's ok to ask for pointers in Ubuntu, Linux & OS Chat, where I'm moving your post.

---

### Post by unityforever on 2017-07-18
To do this, you need money.
first you need to confirm you have independent external IP address, this kind of server is provided by you ISP and usually require extra fee.
second you need search for the domain registering agent
third you pay them to applicant a domain which you like for you
forth you have to set some parameters, corresponding external IP for instance, on your domain to make sure it resolving correctly.
(sometimes people can only afford dynamic external IP, this means you have to set parameters of domain everytimes when your IP is changed, luckily many agents give people a tool, if the agent you choose have this artifact, you just need to install it on your computer, and everything will be done automatically, sometimes this even working in the situation where you don't have independent Internet IP, in a NAT environment for example.)
then everyone in the world can connect to your computer via this domain.
if you wanna establish a website, install related software and set them correctly. This is another long topic then.

If you just need people in LAN or internal network can resolve the domain correctly
precondition is you have the permission to control the router of LAN
first set static IP on your computer.
then you can use the function of specific DNS redirecting in router, redirect the requirement to you LAN IP.
if you don't meet the precondition, you can modify the host files on computers in LAN, and surely you need the permission to access their computer first.

If you just wanna achieve this on your own computer.
just modify the host file.

---

