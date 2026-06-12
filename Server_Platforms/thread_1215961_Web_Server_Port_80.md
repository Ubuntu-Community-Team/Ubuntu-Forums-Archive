---
title: "Web Server Port 80"
date: 2009-07-17
forum: Server Platforms
---

### Post by ericwj08 on 2009-07-17
If i was to change apache from using port 80 to port 85 because my ISP blocks port 80, will my ISP be able to tell what I'm doing and then in turn block port 85 also?

---

### Post by shredkingj on 2009-07-17
HTTP is a clear text protocol, so they could detect this if they wanted to.  They'll probably never notice.  That is the technical answer.  I would read the service agreement with them before doing this.  Could be grounds for getting your service terminated.

---

### Post by ronaldprettyman on 2009-07-17
> **ericwj08 said:**
> If i was to change apache from using port 80 to port 85 because my ISP blocks port 80, will my ISP be able to tell what I'm doing and then in turn block port 85 also?

Change the port to verify that you have it setup correctly. ISP always say port 80 is blocked but usually on go as far to have low lease times and mandatory changes in DHCP. You can more then likely go off port 80. They usualy only make a big deal if you start sucking down bandwith and effecting other customers. Worse case scenario they cut you off till you fix it, charge you for excessive bandwidth, or ask you to upgrade to a commercial account. I've setup home servers for friends on verizon fios/dsl comcast cable, and some other smaller cable companies. Verizon claims to block port 80 and some other ones. But again. I wouldn't worry to much about it if your just trying to learn about apache and not trying to stream illegal video feeds.

And no, even if they knew. I guarantee they don't care. They may have as few as 1 admin for every 1000 customers or even less depending on their setup.

Note: Proxy services are a good way to test your webserver from outside your home network. Or have a friend check it.

---

### Post by ericwj08 on 2009-07-17
> **ronaldprettyman said:**
> Change the port to verify that you have it setup correctly. ISP always say port 80 is blocked but usually on go as far to have low lease times and mandatory changes in DHCP. You can more then likely go off port 80. They usualy only make a big deal if you start sucking down bandwith and effecting other customers. Worse case scenario they cut you off till you fix it, charge you for excessive bandwidth, or ask you to upgrade to a commercial account. I've setup home servers for friends on verizon fios/dsl comcast cable, and some other smaller cable companies. Verizon claims to block port 80 and some other ones. But again. I wouldn't worry to much about it if your just trying to learn about apache and not trying to stream illegal video feeds.

And no, even if they knew. I guarantee they don't care. They may have as few as 1 admin for every 1000 customers or even less depending on their setup.

Note: Proxy services are a good way to test your webserver from outside your home network. Or have a friend check it.

Thanks!  This was very helpful!  I have Cox, and I know that they block port 80.  I never could get it working, but I was able to get 85 working.  Now I have another issue though...  I just got to work and wanted to see if it would work from my work computer, but it says that the server was taking to long to respond, but when I check it from my laptop here at work It works.  At home I have cox high speed, but for my laptop I have Sprint.  So I know that I'm accessing it from a different IP on my laptop, so theoretically shouldn't it work on my work computer as well?

---

### Post by Thirtysixway on 2009-07-17
I'd say that if it was against their TOS, they would contact you about it.

In one version of Comcast's TOS, it pretty much says no providing services to others incluidng web and things like that.  But then in another TOS booklet, it pretty much said "we're not responsible if you get hacked for running services."

I have yet to be contacted or anything.  I'm pretty sure they don't care.

---

### Post by kustomjs on 2009-07-17
best way to find out if your ISP blocks port 80 is going to this website [canyouseeme.org]("canyouseeme.org").

---

