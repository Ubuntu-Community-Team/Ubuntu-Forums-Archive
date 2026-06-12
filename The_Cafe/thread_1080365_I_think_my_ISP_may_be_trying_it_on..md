---
title: "I think my ISP may be trying it on."
date: 2009-02-25
forum: The Cafe
---

### Post by sanderella on 2009-02-25
I keep getting emails from BT Internet, my ISP, warning that if I go over my MB allowance I will be charged extra. They ask me to upgrade to a more expensive package. :mad:

My question is, how do I know they are not trying it on? How can I check my internet usage in terms of MBs?

Any help appreciated.

---

### Post by howefield on 2009-02-25
System monitor will tell you how much data you are transferring up/down. Keep a tally from there.

There are programs also which will monitor the router and keep a running total of data up/down going through the router. Also some routers will store this info in its logs.

What is your data limit/cap ?.

---

### Post by abhilashm86 on 2009-02-25
the connection properties will tell u how much usage in mb's. how much is your download limit?

---

### Post by Barrucadu on 2009-02-25
Don't they provide a way for you to check? With my ISP I can log in to their website and see how much I've used, and how much I have remaining.

---

### Post by hoboken on 2009-02-25
Call your ISP and ask them..?

---

### Post by ice60 on 2009-02-25
i use conky to show me what i've used since i booted. it shows the up and download amounts. this is the bit that does it -

```
${color #909090}Down:$color ${totaldown eth0} ${alignr}${color #909090}Up:$color ${totalup eth0}
```
that's for eth0, the color bits aren't important.

i think you can get the same thing if you run this in a terminal though, without having to use conky -
```
sudo ifconfig | grep "bytes:"
```
RX is download amounts and TX is upload.

i don't know that for a fact, it's just the first thing i thought of.

EDIT: just incase you want something to keep track of your network traffic, i had a look and saw vnstat. i think it looks good!

[http://humdi.net/vnstat/](http://humdi.net/vnstat/)

checkout the frontend for it 8) lol
[http://www.sqweek.com/sqweek/index.php?p=1](http://www.sqweek.com/sqweek/index.php?p=1)

---

### Post by sujoy on 2009-02-25
if your ISP has a limit, then they ought to have a place where you can check it ...

---

### Post by billgoldberg on 2009-02-25
I can check it when I login to my account on my ISPs website.

Any ISP with caps should provide such services.

---

### Post by jacz on 2009-02-25
log in to your BT account at the website, i switch from BT to tiscali long time ago

---

### Post by sanderella on 2009-02-25
Thanks very much or all these useful suggestions. 

I ran **sudo ifconfig | grep "bytes:"** in the terminal and it gave me the info. And System Monitor gives a snapshot too.

I'll look into all the other ones, too. You are great guys.:popcorn:

---

