---
title: "Do u use opendns?"
date: 2008-08-04
forum: The Cafe
---

### Post by sharks on 2008-08-04
Do u use [opendns]("http://www.opendns.com/")?

---

### Post by sisco311 on 2008-08-04
no. i like porn.

---

### Post by kerry_s on 2008-08-04
i don't like there caching system, when i search google, i don't want there cache of google, i want google.

---

### Post by LookTJ on 2008-08-04
> **sisco311 said:**
> no. i like porn.
irrelevant reason. Opendns gives you the choice to block stuff you don't want, not just porn.

And yes, I use opendns. :D and love it.

---

### Post by init1 on 2008-08-04
Interesting. I'll consider it.

---

### Post by Kingsley on 2008-08-04
I used to but dropped it. Opendns was more trouble than it's worth when I used it on my university's network. I also didn't see any speed benefits.

---

### Post by Silpheed2K on 2008-08-04
Actually I do and I have been for a while now.
Makes browsing much more responsive and plus I like the features like the ability to block out bad content if you make an account.

---

### Post by kaibob on 2008-08-04
My ISP is Time Warner, and their DNS servers have been an ongoing issue. I switched to opendns about a month ago--things have worked better ever since.

---

### Post by david_lynch on 2008-08-04
I run linux - bind9 does everything I need. Seriously, a local linux box is a much faster dns server than any ISP or remote service I've looked at.

Ubuntu had the bind vulnerability patched within hours. Why on earth would I need to mess around with opendns?

:guitar:

---

### Post by Dr. C on 2008-08-04
No. One can very easily run one's own DNS with Ubuntu

```
sudo apt-get install bind9
```

The trick is to use a static IP address for the Ubuntu box running bind and then set your DNS for all the machines on your network to the IP address of your Ubuntu box running bind There are many resources that explain how to set up one's own DNS using Ubuntu. Just search for bind9 on the Ubuntu forums. 

This is great for privacy and for dealing with ISPs that try to "monetize" typing errors by messing around with the DNS

---

### Post by Polygon on 2008-08-04
no, i see no benefit. comcast's dns servers work fine.

---

### Post by stmiller on 2008-08-05
> **kerry_s said:**
> i don't like there caching system, when i search google, i don't want there cache of google, i want google.

**Their** caching system? you mean when you type gibberish in the address bar and it doesn't resolve?

---

### Post by EdThaSlayer on 2008-08-05
I used to use it. But at the moment my internet is too slow to even consider using OpenDNS.

---

### Post by Sealbhach on 2008-08-05
Yeah I use it. Isn't there some security benefit?

I like the sound of having my own DNS server though. Cool!


.

---

### Post by prshah on 2008-08-05
I considered changing to OpenDNS server, but gave up quickly when I conducted this little check: (The first is my ISP-assigned DNS servers, the second OpenDNS servers) (IP Addresses screwed with) ```

Sun Jun 29 12:53:40 ~:$ ping -c 5 258.228.255.145 
PING 258.228.255.145 (258.228.255.145) 56(84) bytes of data.
64 bytes from 258.228.255.145: icmp_seq=1 ttl=253 [color=red]time=8.55 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=2 ttl=253 [color=red]time=8.30 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=3 ttl=253 [color=red]time=8.37 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=4 ttl=253 [color=red]time=8.77 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=5 ttl=253 [color=red]time=8.58 ms[/color]

--- 258.228.255.145 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 8.308/8.519/8.777/0.202 ms

Sun Jun 29 12:54:54 ~:$ ping -c 5 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=53 [color=red]time=292 ms[/color]
64 bytes from 208.67.222.222: icmp_seq=2 ttl=53 [color=red]time=292 ms[/color]
64 bytes from 208.67.222.222: icmp_seq=5 ttl=53 [color=red]time=294 ms[/color]
--- 208.67.222.222 ping statistics ---
5 packets transmitted, 3 received, 40% packet loss, time 3998ms
rtt min/avg/max/mdev = 292.752/293.268/294.135/0.878 ms

```

---

### Post by gletob on 2008-08-05
> **prshah said:**
> I considered changing to OpenDNS server, but gave up quickly when I conducted this little check: (The first is my ISP-assigned DNS servers, the second OpenDNS servers) (IP Addresses screwed with) ```

Sun Jun 29 12:53:40 ~:$ ping -c 5 258.228.255.145 
PING 258.228.255.145 (258.228.255.145) 56(84) bytes of data.
64 bytes from 258.228.255.145: icmp_seq=1 ttl=253 [color=red]time=8.55 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=2 ttl=253 [color=red]time=8.30 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=3 ttl=253 [color=red]time=8.37 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=4 ttl=253 [color=red]time=8.77 ms[/color]
64 bytes from 258.228.255.145: icmp_seq=5 ttl=253 [color=red]time=8.58 ms[/color]

--- 258.228.255.145 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 8.308/8.519/8.777/0.202 ms

Sun Jun 29 12:54:54 ~:$ ping -c 5 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=53 [color=red]time=292 ms[/color]
64 bytes from 208.67.222.222: icmp_seq=2 ttl=53 [color=red]time=292 ms[/color]
64 bytes from 208.67.222.222: icmp_seq=5 ttl=53 [color=red]time=294 ms[/color]
--- 208.67.222.222 ping statistics ---
5 packets transmitted, 3 received, 40% packet loss, time 3998ms
rtt min/avg/max/mdev = 292.752/293.268/294.135/0.878 ms

```

I get about 15 ms I like it cause I can block stuff my kids shouldn't see

---

### Post by RATM_Owns on 2008-08-05
I use it.
'Nuff said.

---

### Post by PCessna on 2008-08-15
> **sharks said:**
> Do u use [opendns]("http://www.opendns.com/")?


Yeah, It lets me use port 80, some now pcessna.is-a-geek.com:81 = pcessna.is-a-geek.com... YEAH :D

<3333

---

### Post by defri on 2008-08-15
I have try it. But i can get any benefit from it. So i choose to roll back to my standard dns. Did anyone really have a good reason for using opendns ??

---

### Post by Kernel Sanders on 2008-08-15
Is the main reason to use it privacy? As in, your ISP can't see what your browsing if you use OpenDNS?

---

### Post by timzak on 2008-08-15
I use it to protect my family from undesired internet content.

---

### Post by stimpack on 2008-08-15
I did, but following FineE's post on page 1, I installed bind9 and now 5mins laters I use my own dns server. caching with opendns in the forwarders.

---

### Post by andrek on 2008-08-15
I use it. Although I don't see any real benefits of opendns, I just got used to it.

---

### Post by rickyjones on 2008-08-15
I use it at home and at various customer sites for content filtering. I also like when a user mistypes a URL it will bring them to a search page which usually has the correct result listed.

-Richard

---

### Post by aysiu on 2008-08-15
> **Kernel Sanders said:**
> Is the main reason to use it privacy? As in, your ISP can't see what your browsing if you use OpenDNS?
While that's true, it also means OpenDNS can see what you're browsing. Supposedly they keep that information for only two days, though.

---

### Post by Bachstelze on 2008-08-15
> **aysiu said:**
> While that's true, it also means OpenDNS can see what you're browsing. Supposedly they keep that information for only two days, though.

No, that's not true. Your ISP can see what you're browsing anyway.

---

### Post by regomodo on 2008-08-15
#

---

### Post by dje on 2008-08-15
yes my home network uses it only for increased speed and because you can refresh the cache for websites ([here]("http://www.opendns.com/support/cache/")), not for the content filtering though

dje

---

### Post by Kernel Sanders on 2008-08-15
> **HymnToLife said:**
> No, that's not true. Your ISP can see what you're browsing anyway.

What is it's advantages then? Besides content filtering?

---

### Post by Bachstelze on 2008-08-15
> **Kernel Sanders said:**
> What is it's advantages then? Besides content filtering?

If your ISP's DNS servers are a bit flakey, it can be a faster and more reliable alternative. That's pretty much the only thing I can think of, but it's definitely at the cost of privacy, since they can see what you're browsing and no one really knows what they do with this.

The content filtering can be a plus too, but I don't use it, and I don't like the idea of filtering in the first place. Yeah, I know, I don't have kids and maybe I won't say the same when/if I have some, but that's what I think for now.

---

