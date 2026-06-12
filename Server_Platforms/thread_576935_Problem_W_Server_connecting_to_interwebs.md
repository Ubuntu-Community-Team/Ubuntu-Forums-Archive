---
title: "Problem W/ Server connecting to interwebs"
date: 2007-10-15
forum: Server Platforms
---

### Post by mattc908 on 2007-10-15
So this is my set up, I have Dyndns.org link up to my server, I just bought a real name from GoDaddy.com. So I followed the steps in a guide to  set it up on this guide: [http://www.macosxhints.com/article.php?story=20040625012551347](http://www.macosxhints.com/article.php?story=20040625012551347) 

Well Only problem it no longer connects to the internets.........It just broadcasts it on my network....... So I can see the website on my network....But no were else.
What should I change in my apache file or is there an easier way than than that guide.......... I mean the .com name works just not over the internet...........

Thanks much appreciated.......

```

mattc908@mattc908:~$ traceroute insightahoy.com
traceroute to mattc908.dyndns.org (192.168.1.103), 30 hops max, 40 byte packets
1  192.168.1.103 (192.168.1.103)  0.067 ms  0.026 ms  0.017 ms
mattc908@mattc908:~$ 

```

---

### Post by Xarok on 2007-10-15
I don't know your knowledge so don't be offended by this question, but did you set up port forwarding on your router?

Often ISPs block port 80, so if this is the problem you should change your Apache server to listen on port 81 and have your router portforward on port 81.

I have to do this with my server at home.

To have my domain switch to port 81 and find my dynamic IP I use no-ip.com

---

### Post by mattc908 on 2007-10-15
Yup, but I figured it out Dyndns.org reset my ip as the 192.168.1.103 so i set it back to my servers IP.

---

