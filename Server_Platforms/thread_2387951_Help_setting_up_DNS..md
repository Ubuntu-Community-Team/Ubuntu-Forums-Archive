---
title: "Help setting up DNS."
date: 2018-03-26
forum: Server Platforms
---

### Post by gamerliko on 2018-03-26
Morning,

I have been running a MUD server for little bit for my personal mud.  You can connect to the server thru putty remotely and locally, but have to use my ip site to connect.  I decided to buy a domain name from namecheap.  (mudhaven.net is what I bought).  

I want to make it so players can connect by putting in their mudclient: dbt.mudhaven.net port 2500(port is already open as players can connect to the game).   
Does anyone have a guide or can point in the right direction?  Thanks in advance!

---

### Post by darkod on 2018-03-26
I assume the server has a static public IP right? In such case you simply have to use namecheap dns manager to create one A record named dbt pointing to the public IP.

After that any client trying to reach dbt.mudhaven.net will get resolved to your server public IP.

---

### Post by gamerliko on 2018-03-26
> **darkod said:**
> I assume the server has a static public IP right? In such case you simply have to use namecheap dns manager to create one A record named dbt pointing to the public IP.

After that any client trying to reach dbt.mudhaven.net will get resolved to your server public IP.

I don't believe I do.  This is what I have assigned to namecheap:

A Record Host: dbt  value: 1.2.3.4(this is what people use to connect to the game and also to see the apach2 default) TTL: automatic.

Note: players are saying they can connect to the game with dbt.mudhave.net now :)

Note 2: I did set some host for @, www, and *.  So far I haven't seen them taking affect like dbt.  Could this just be it taking take for the DNS to correct it self?  I can't connect to the server with mudhaven.net, but can with dbt.mudhaven.net

---

### Post by darkod on 2018-03-26
Hmmm, not sure.

For @ and www, those are standard for a domain and if they point to the same public IP as dbt then in theory people should be able t use them in the same way.

For the * record I think that is designed by providers to allow you any URL containing your domain to be resolved to some host. Basically I wouldn't use it, but the choice is yours...

---

### Post by gamerliko on 2018-03-26
> **darkod said:**
> Hmmm, not sure.

For @ and www, those are standard for a domain and if they point to the same public IP as dbt then in theory people should be able t use them in the same way.

For the * record I think that is designed by providers to allow you any URL containing your domain to be resolved to some host. Basically I wouldn't use it, but the choice is yours...

Could I have the wrong ports not open? I do have port 80/443 open.

Note: ping mudhaven.net gives me this:
```

mud@mudhaven:~$ ping mudhaven.net
PING mudhaven.net (192.64.119.19) 56(84) bytes of data.
64 bytes from 192.64.119.19: icmp_seq=1 ttl=48 time=90.6 ms
64 bytes from 192.64.119.19: icmp_seq=2 ttl=48 time=92.3 ms
64 bytes from 192.64.119.19: icmp_seq=3 ttl=48 time=94.3 ms
64 bytes from 192.64.119.19: icmp_seq=4 ttl=48 time=90.1 ms

```

and pinging dbt.mudhaven.net

```

mud@mudhaven:~$ ping dbt.mudhaven.net
PING dbt.mudhaven.net (68.44.138.187) 56(84) bytes of data.
64 bytes from c-68-44-138-187.hsd1.in.comcast.net (68.44.138.187): icmp_seq=1 ttl=64 time=0.220 ms
64 bytes from c-68-44-138-187.hsd1.in.comcast.net (68.44.138.187): icmp_seq=2 ttl=64 time=0.261 ms
64 bytes from c-68-44-138-187.hsd1.in.comcast.net (68.44.138.187): icmp_seq=3 ttl=64 time=0.217 ms

```

It looks like mudhaven.net is going to a differnet ip site.

---

### Post by gamerliko on 2018-03-26
Now ping is showing all the above coming from the proper site.  Can connect thru the shell with dbt.mudhaven.net, but not mudhaven.net

---

### Post by gamerliko on 2018-03-26
and its all working correctly!  Thank you Darkod for helping me thru this!

---

### Post by darkod on 2018-03-27
No problem. To answer your question about the ports opening. If the players need to connect to 2500 then 2500 also needs to be open in the FW in front of the server (if there is one) and on the server itself.

Any ports that you want to be used from the internet towards the server have to be open.

If you have resolved everything and is working OK you can mark the thread Solved. You can do that in Thread Tools above the first post.

---

