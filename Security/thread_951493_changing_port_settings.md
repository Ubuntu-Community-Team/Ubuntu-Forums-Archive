---
title: "changing port settings"
date: 2008-10-18
forum: Security
---

### Post by jayanthan on 2008-10-18
i am using my university computer with _NO ADMINISTRATIVE PRIVILEGE._
they hav now blocked many ports by firewall and its essential for me to use **pidgin**.

i can use pidgin by changing the port setting for my yahoo id into 80.
but it doesnt work for g-talk id(XMPP)
pidgin version is 2.2.2


PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
111/tcp   open  rpcbind
733/tcp   open  unknown
45519/tcp open  unknown
60687/tcp open  unknown


these are port statistics
i want to use pidgin without much kind of hacking

i tried all these ports with g-talk and no result
how can i use pidgin.

---

### Post by Drezard on 2008-10-19
I'm not sure if this breaks any forum rules. Please delete this post and advise me if it does. But, it seems this is a legitimate none hacking request here.

I had the exact same problem. I setup my ubuntu box at home with SSH access being the only service allowed in, but all services being allowed out. Using Putty from the uni computers (not sure how to do the client side on Ubuntu) I created an SSH tunnel for ports 80, 445 and a few others back home (exchange these ports with Pidgins or any other services you want) to my box at home. So I forward all the traffic through the internet to my box at home, then it on forwards the traffic to the correct destination.

Post problems.

Daniel

---

### Post by mikewhatever on 2008-10-20
Why don't you ask the university's IT guys?

---

### Post by Drezard on 2008-10-21
> **mikewhatever said:**
> Why don't you ask the university's IT guys?

How is that at all fun???

Daniel

---

### Post by jayanthan on 2008-10-21
well,

he himself has banned torrents and he himself is running torrents
and i cant complain head bcoz he's a movie buff and he downloads.
but the prob is that most among has no control over torrenting and they download porns.

that is banned.

so i can't be an exception.
bt i want to download movies and docus (no porn, believe me).

---

### Post by Titan8990 on 2008-10-21
I'm fairly certain that it would be against forum policy to assist a user in getting around administrative regulations.

If it is not then it should be.

---

### Post by nubdora on 2008-10-21
Talk to your local IT prick and request his help to correct pidgin functioning. Beyond that, you are on your own for circumventing University settings no matter what every one else on campus does. The administration has the network settings for a reason and if the IT guy circumvents them to download porn, the University needs to check candidates' ethics before they hire them *tips whitehat*

---

