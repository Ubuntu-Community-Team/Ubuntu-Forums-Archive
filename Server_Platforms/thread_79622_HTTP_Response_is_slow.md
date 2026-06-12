---
title: "HTTP Response is slow"
date: 2005-10-20
forum: Server Platforms
---

### Post by theQmaster on 2005-10-20
Hi,

I found some of the http requests are treated slower than should be.
Especially when the calls originates outside of my net. Since I disabled the ipv6 in my aliases folder things got a bit better but not as they were when I was running the same server configuration on Win XP.

All this cr*p is since I did the "mistake" to upgrade to the lastest kernet two weeks ago. 

How do I track down where the bottle neck are in my network ? Any tool you recommand ? I used netstat and nmap, is good I need more control and flexibility.

My best,
theQMaster
[http://www.goodstockimages.com](http://www.goodstockimages.com)

Ps.
The above link is the site. It's too slow, isn't it ?

---

### Post by chanders on 2005-10-22
Actually it was quite fast..... I think it has more to do with your site design. But I think it just as fast as any other comparable site with images etc...

---

### Post by theQmaster on 2005-10-23
Thanks for checking...

I think I fixed the matter 3 days ago but I'm not sure what it was...
One of the following did it
- disabled the ipv6 via alliases file
- one dns ip out of three was bad(typo)
- i used a sudo apt-get remove --purge  after adpkg -l | grep apache , then I reinstalled apache2
- added the site domain to the host

Now is much much better!

theQMaster

---

### Post by iamtaylormade on 2005-10-23
Qmaster, nice site. I have been looking for a few quality photos for my business site. My time for loading your site (home page) was 7.49 secs using Verizon DSL (3MBs). Not terribly slow considering the content. I may be in touch a little later, once I get my server set up. I am looking to host my own sites as well (I assume you are). Do you recommend the latest kernel?
Thanks in advance

---

### Post by LordHunter317 on 2005-10-23
It's your layout.  This is what happens when you use nested table layouts.

---

### Post by theQmaster on 2005-10-23
[QUOTE=iamtaylormade]Qmaster, nice site. I have been looking for a few quality photos for my business site. My time for loading your site (home page) was 7.49 secs using Verizon DSL (3MBs). Not terribly slow considering the content. I may be in touch a little later, once I get my server set up. I am looking to host my own sites as well (I assume you are). Do you recommend the latest kernel?
Thanks in advance[/QUOTE]


Thanks. I had no problems with the lastest Kernel besides the ipv6 problem.

QM

---

### Post by theQmaster on 2005-10-23
[QUOTE=LordHunter317]It's your layout.  This is what happens when you use nested table layouts.[/QUOTE]

What makes you say that LH ?
Redering happens on client side, if would be rendering would be visible even in my intranet.

I had a problem, not anymore, one of the previously posted message describes what fixed it.


QM

---

### Post by LordHunter317 on 2005-10-23
A nested table layout the way yours is configured forbids any rendering until the entire page is loaded.  This can make on a slower link (i.e., Internet) the page look really slow until all the HTML and image headers have been pulled down.

---

