---
title: "Squid Proxy Problems"
date: 2008-12-23
forum: Server Platforms
---

### Post by Drezard on 2008-12-23
I have an ssh connection from my host here to my host at home. My home computer is a Ubuntu server 8.04 box. I have forwarded port 8080 (via putty) through my SSH connection from this host to my Ubuntu server box at home. 

I have squid installed on my host at home, the only two changes I have made to the default configuration file are.... Ive added the visible_hostname variable so squid will start and Ive changed the http_port variable that squid uses by default (from 3128) to 8080. Then I rebooted the host completely. Now,

I have set up Firefox to use the proxy localhost:8080 (which should work because im port forwarding localhost:8080 so it goes to my box at home and pops out there, through the use of putty).

I can not seem to forward data thro my proxy at home.

Ideas?

Daniel

---

### Post by erwall on 2008-12-23
> **Drezard said:**
> I have an ssh connection from my host here to my host at home. My home computer is a Ubuntu server 8.04 box. I have forwarded port 8080 (via putty) through my SSH connection from this host to my Ubuntu server box at home. 

I have squid installed on my host at home, the only two changes I have made to the default configuration file are.... Ive added the visible_hostname variable so squid will start and Ive changed the http_port variable that squid uses by default (from 3128) to 8080. Then I rebooted the host completely. Now,

I have set up Firefox to use the proxy localhost:8080 (which should work because im port forwarding localhost:8080 so it goes to my box at home and pops out there, through the use of putty).

I can not seem to forward data thro my proxy at home.

Ideas?

Daniel
You don't need squid to do what you're trying to do.  You need to setup a dynamic forward on 8080 in putty, it should show up in putty as D8080.  Then connect to your home machine and set your browser to use localhost 8080 in the socks server setting.  That should do it.

---

### Post by Hobgoblin on 2008-12-23
> **Drezard said:**
> 
I have squid installed on my host at home, the only two changes I have made to the default configuration file are.... Ive added the visible_hostname variable so squid will start and Ive changed the http_port variable that squid uses by default (from 3128) to 8080. Then I rebooted the host completely. Now,


Because by default squid only allows access from 127.0.0.1

Just tried it myself and the requests come from 127.0.1.1

---

### Post by Drezard on 2008-12-24
Thank you so much Hobgoblin!

You are my hero!

---

### Post by Drezard on 2008-12-25
Still having a couple of problems here...

Adding the acl to allow 127.0.1.1 only delayed the error about 3 mins before it displays the no data throughput error. I can access the proxy, it then takes about 2 - 3 mins of just a blank screen then throws the error.

Other ideas?

---

