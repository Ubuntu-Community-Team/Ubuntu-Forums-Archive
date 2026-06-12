---
title: "Web Server, Viewable on Network, Not on Internet"
date: 2008-02-04
forum: Server Platforms
---

### Post by ExtremeClean on 2008-02-04
This is my story

Basically the university i go to let me build a web server to host my student societies websites.


I built it using the latest version of ubuntu server edition at home, It worked fine, I was able to easily get it on the internet by opening up my port 80 on my router and pointing to the ip address that was randomly assigned to me.



This is my problem :

Now i brought it to the university, the university admins provided me an ip on the network 137.122.xxx.xxx , which I used to get the server on the internet, no problem.

However when I try to connect to the server from any pc on this network, It works fine, but when I try to connect from something off campus, it times out.

The tech guy upstairs assures me port 80 is open.
when i go to WhatsMyIp.org , it tells me that 137.122.xxx.xxx is indeed my ip address.

When I monitor traffic, I can see all incoming requests on port 80 from anyone else on the network.

But when i monitor traffic for my test connections that ARE NOT on the network, they never appear.


My guess is that anything off the network is getting stopped somewhere along the line before it reaches my server.

OR 

For some reason my ip address is not the one being broadcasted over the internet ( Even though whatsmyip.org says it is : / )

help plz :D


NOTE: All my firewalls are working properly, as I have tried on 3 networks before ( all without static ips though) and the server worked completely fine.


-=Edits=-
I have tried using port 8080 instead, to no success
I do have permission from the network admin to host a webserver, and the tech guys 'know this'.

---

### Post by jonabyte on 2008-02-04
you may want confirmation from the network guy, sounds like the port is not being forwarded properly.

---

### Post by stalker145 on 2008-02-04
> **ExtremeClean said:**
> However when I try to connect to the server from any pc on this network, It works fine, but when I try to connect from something off campus, it times out.

The tech guy upstairs assures me port 80 is open.
when i go to WhatsMyIp.org , it tells me that 137.122.xxx.xxx is indeed my ip address.

When I monitor traffic, I can see all incoming requests on port 80 from anyone else on the network.

But when i monitor traffic for my test connections that ARE NOT on the network, they never appear.


My guess is that anything off the network is getting stopped somewhere along the line before it reaches my server.

To me it sounds like your tech guy hasn't properly forwarded port 80 to your computer. Since I'm sure your University already has a web server running, it's probably not likely that they'll blindly forward 80 to your IP. Probably the next best thing would be to have your web page admin put a link on one of the menus pointing at your server since you said this is a student society site.

Check into that with the administrators. I think that's the issue here.

---

### Post by ExtremeClean on 2008-02-04
Ya i did that, according to him i 'should' have unrestricted access. Meaning all ports are open and i just use my firewall to close off what I want closed.

---

### Post by ExtremeClean on 2008-02-04
I have already sat down and talked with the Admin for the entire university network, and he gave me full permissions to put up a web server.

---

### Post by stalker145 on 2008-02-04
> **ExtremeClean said:**
> I have already sat down and talked with the Admin for the entire university network, and he gave me full permissions to put up a web server.

But are the Uni's outside routers pointing port 80 at your computer? Since people on the inside can get to you but people on the outside can not, I still say that's where the issue lies.

---

### Post by p_quarles on 2008-02-04
> **stalker145 said:**
> But are the Uni's outside routers pointing port 80 at your computer? Since people on the inside can get to you but people on the outside can not, I still say that's where the issue lies.
I agree, that sounds like the only real possibility here. If the address works inside the network, but not from outside, it's a port forwarding problem. 

You can find out for sure by using nmap:
```
sudo apt-get install nmap
```Scan the address of your server from both inside and outside the network:
```
nmap -P0 137.122.x.x
```I'm guessing that the results will show that port 80 is open from within the network, but not from without.

---

### Post by ExtremeClean on 2008-02-04
Thats currently what i think it is,  however the tech guys seem to enjoy taking their sweet time in responding to email.


However until then I had tested it with ports like 8080 and still no luck

---

### Post by p_quarles on 2008-02-04
> **ExtremeClean said:**
> the tech guys seem to enjoy taking their sweet time in responding to email
Having worked with several tech departments in universities, I can say that this doesn't surprise me in the slightest. ;)

---

### Post by ExtremeClean on 2008-02-04
ya when i had my meeting with the Admin, when i walked through the employee office to get to his, I saw a dude playing starcraft : /

---

### Post by ExtremeClean on 2008-02-04
oh ya, and i did nmap from inside and i got the standard all my ports were open but filtered display


and when i did it from my mint pc @ home 

nmap -P0 137.122.xxx.xxx

All 1697 scanned ports on 137.122.xxx.xxx are filtered

Nmap finished: 1 IP address (1 host up) scanned in 351.128 seconds

---

### Post by ExtremeClean on 2008-02-04
so that pretty much confirms that my stuff is all being dropped before reaching the server eh.

---

### Post by ExtremeClean on 2008-02-04
Thanks to everyone so far

I showed the tech guys the nmap results and now they gave me 

"The new IP you should be getting is 137.122.xxx.xxx
This should resolve the problems you were having"

the new ip they gave me still says 

All 1697 scanned ports on 137.122.xxx.xxx are filtered

---

