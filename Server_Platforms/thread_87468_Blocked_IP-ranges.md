---
title: "Blocked IP-ranges"
date: 2005-11-08
forum: Server Platforms
---

### Post by mulux on 2005-11-08
I'm running a webserver, and several people reported they couldn't access the website. At first I was pretty sure the problem was on their side, because I didn't block any traffic - or so I thought.

After some research, I found out that iptables is setup to block several IP-ranges, which were inactivated but are now in use! I'm running Firestarter and I believe this is the application who wrote the iptable-rules. The chain is called NR (for no route?), here's a listing of it:
```
Chain NR (1 references)
target     prot opt source               destination
LS         all  --  0.0.0.0/8            81.236.152.0/24
LS         all  --  1.0.0.0/8            81.236.152.0/24
LS         all  --  2.0.0.0/8            81.236.152.0/24
LS         all  --  5.0.0.0/8            81.236.152.0/24
LS         all  --  7.0.0.0/8            81.236.152.0/24
LS         all  --  10.0.0.0/8           81.236.152.0/24
LS         all  --  23.0.0.0/8           81.236.152.0/24
LS         all  --  27.0.0.0/8           81.236.152.0/24
LS         all  --  31.0.0.0/8           81.236.152.0/24
LS         all  --  36.0.0.0/8           81.236.152.0/24
LS         all  --  37.0.0.0/8           81.236.152.0/24
LS         all  --  39.0.0.0/8           81.236.152.0/24
LS         all  --  41.0.0.0/8           81.236.152.0/24
LS         all  --  42.0.0.0/8           81.236.152.0/24
LS         all  --  49.0.0.0/8           81.236.152.0/24
LS         all  --  50.0.0.0/8           81.236.152.0/24
LS         all  --  71.0.0.0/8           81.236.152.0/24
LS         all  --  72.0.0.0/8           81.236.152.0/24
LS         all  --  73.0.0.0/8           81.236.152.0/24
LS         all  --  74.0.0.0/8           81.236.152.0/24
LS         all  --  75.0.0.0/8           81.236.152.0/24
LS         all  --  76.0.0.0/8           81.236.152.0/24
LS         all  --  77.0.0.0/8           81.236.152.0/24
LS         all  --  78.0.0.0/8           81.236.152.0/24
LS         all  --  79.0.0.0/8           81.236.152.0/24
LS         all  --  89.0.0.0/8           81.236.152.0/24
LS         all  --  90.0.0.0/8           81.236.152.0/24
LS         all  --  91.0.0.0/8           81.236.152.0/24
LS         all  --  92.0.0.0/8           81.236.152.0/24
LS         all  --  93.0.0.0/8           81.236.152.0/24
LS         all  --  94.0.0.0/8           81.236.152.0/24
LS         all  --  95.0.0.0/8           81.236.152.0/24
LS         all  --  96.0.0.0/8           81.236.152.0/24
LS         all  --  97.0.0.0/8           81.236.152.0/24
LS         all  --  98.0.0.0/8           81.236.152.0/24
LS         all  --  99.0.0.0/8           81.236.152.0/24
LS         all  --  100.0.0.0/8          81.236.152.0/24
LS         all  --  101.0.0.0/8          81.236.152.0/24
LS         all  --  102.0.0.0/8          81.236.152.0/24
LS         all  --  103.0.0.0/8          81.236.152.0/24
LS         all  --  104.0.0.0/8          81.236.152.0/24
LS         all  --  105.0.0.0/8          81.236.152.0/24
LS         all  --  106.0.0.0/8          81.236.152.0/24
LS         all  --  107.0.0.0/8          81.236.152.0/24
LS         all  --  108.0.0.0/8          81.236.152.0/24
LS         all  --  109.0.0.0/8          81.236.152.0/24
LS         all  --  110.0.0.0/8          81.236.152.0/24
LS         all  --  111.0.0.0/8          81.236.152.0/24
LS         all  --  112.0.0.0/8          81.236.152.0/24
LS         all  --  113.0.0.0/8          81.236.152.0/24
LS         all  --  114.0.0.0/8          81.236.152.0/24
LS         all  --  115.0.0.0/8          81.236.152.0/24
LS         all  --  116.0.0.0/8          81.236.152.0/24
LS         all  --  117.0.0.0/8          81.236.152.0/24
LS         all  --  118.0.0.0/8          81.236.152.0/24
LS         all  --  119.0.0.0/8          81.236.152.0/24
LS         all  --  120.0.0.0/8          81.236.152.0/24
LS         all  --  121.0.0.0/8          81.236.152.0/24
LS         all  --  122.0.0.0/8          81.236.152.0/24
LS         all  --  123.0.0.0/8          81.236.152.0/24
LS         all  --  124.0.0.0/8          81.236.152.0/24
LS         all  --  ppp-net.infoweb.ne.jp/8  81.236.152.0/24
LS         all  --  YahooBB126000000000.bbtec.net/8  81.236.152.0/24
LS         all  --  127.0.0.0/8          81.236.152.0/24
LS         all  --  169.254.0.0/16       81.236.152.0/24
LS         all  --  172.16.0.0/12        81.236.152.0/24
LS         all  --  173.0.0.0/8          81.236.152.0/24
LS         all  --  174.0.0.0/8          81.236.152.0/24
LS         all  --  175.0.0.0/8          81.236.152.0/24
LS         all  --  176.0.0.0/8          81.236.152.0/24
LS         all  --  177.0.0.0/8          81.236.152.0/24
LS         all  --  178.0.0.0/8          81.236.152.0/24
LS         all  --  179.0.0.0/8          81.236.152.0/24
LS         all  --  180.0.0.0/8          81.236.152.0/24
LS         all  --  181.0.0.0/8          81.236.152.0/24
LS         all  --  182.0.0.0/8          81.236.152.0/24
LS         all  --  183.0.0.0/8          81.236.152.0/24
LS         all  --  184.0.0.0/8          81.236.152.0/24
LS         all  --  185.0.0.0/8          81.236.152.0/24
LS         all  --  186.0.0.0/8          81.236.152.0/24
LS         all  --  187.0.0.0/8          81.236.152.0/24
LS         all  --  189.0.0.0/8          81.236.152.0/24
LS         all  --  190.0.0.0/8          81.236.152.0/24
LS         all  --  192.0.2.0/24         81.236.152.0/24
LS         all  --  192.168.0.0/16       81.236.152.0/24
LS         all  --  197.0.0.0/8          81.236.152.0/24
LS         all  --  198.18.0.0/15        81.236.152.0/24
LS         all  --  223.0.0.0/8          81.236.152.0/24
LS         all  --  BASE-ADDRESS.MCAST.NET/3  81.236.152.0/24
```

There was a guy on the 71.x.x.x range who concated me and said he was having trouble accessing my website, then I tried removing the 71.0.0.0/8 rule, and then it worked!

As you can see here [http://www.iana.org/assignments/ipv4-address-space](http://www.iana.org/assignments/ipv4-address-space) a lot of the blocked ranges shouldn't be blocked!

What should I do? I'm afraid firestarter will recreate the rules if I delete them manually.

Thanks in advance!

---

### Post by souki on 2005-11-08
it is not trivial
there is a document here [http://again.net/cidr](http://again.net/cidr) (sory, I did a mistake in the previous post)
it was discuted in the debian-firewall list

---

### Post by souki on 2005-11-08
I've missed the point:
71.0.0.0/8 and 72.0.0.0/8 have been allocated by IANA to ARIN in August 2004
so, the firerstarter script is out of date

---

### Post by mulux on 2005-11-08
So, where should I report this bug? Also, is it outdated because my ubuntu hoary is running an old version of firestarter, or did the firestarter developers forgot to update the rules?

I suppose I have to remove the rules manually for now.

---

### Post by souki on 2005-11-08
I don't know for your version,
all I can do is to check on breezy: firestarter 1.0.3-1.1ubuntu1

the non-routables rules are in /etc/firestarter/non-routables
they are correct (at least for the 71.0.0.0 network)

I paste you here the content, maybe you can use it
```
0.0.0.0/8
1.0.0.0/8
2.0.0.0/8
5.0.0.0/8
7.0.0.0/8
10.0.0.0/8
23.0.0.0/8
27.0.0.0/8
31.0.0.0/8
36.0.0.0/8
37.0.0.0/8
39.0.0.0/8
41.0.0.0/8
42.0.0.0/8
49.0.0.0/8
50.0.0.0/8
73.0.0.0/8
74.0.0.0/8
75.0.0.0/8
76.0.0.0/8
77.0.0.0/8
78.0.0.0/8
79.0.0.0/8
89.0.0.0/8
90.0.0.0/8
91.0.0.0/8
92.0.0.0/8
93.0.0.0/8
94.0.0.0/8
95.0.0.0/8
96.0.0.0/8
97.0.0.0/8
98.0.0.0/8
99.0.0.0/8
100.0.0.0/8
101.0.0.0/8
102.0.0.0/8
103.0.0.0/8
104.0.0.0/8
105.0.0.0/8
106.0.0.0/8
107.0.0.0/8
108.0.0.0/8
109.0.0.0/8
110.0.0.0/8
111.0.0.0/8
112.0.0.0/8
113.0.0.0/8
114.0.0.0/8
115.0.0.0/8
116.0.0.0/8
117.0.0.0/8
118.0.0.0/8
119.0.0.0/8
120.0.0.0/8
121.0.0.0/8
122.0.0.0/8
123.0.0.0/8
124.0.0.0/8
125.0.0.0/8
126.0.0.0/8
127.0.0.0/8
169.254.0.0/16
172.16.0.0/12
173.0.0.0/8
174.0.0.0/8
175.0.0.0/8
176.0.0.0/8
177.0.0.0/8
178.0.0.0/8
179.0.0.0/8
180.0.0.0/8
181.0.0.0/8
182.0.0.0/8
183.0.0.0/8
184.0.0.0/8
185.0.0.0/8
186.0.0.0/8
187.0.0.0/8
189.0.0.0/8
190.0.0.0/8
192.0.2.0/24
192.168.0.0/16
197.0.0.0/8
198.18.0.0/15
223.0.0.0/8
224.0.0.0/3
```

---

### Post by mulux on 2005-11-08
Ahh, thanks a lot, I didn't know about firestarters non-routable file :)

Though, it looks like your version also is a little out of date (judging from the iana-url I posted earlier). Anyway I fixed that manually and I believe everything is fine now!

---

