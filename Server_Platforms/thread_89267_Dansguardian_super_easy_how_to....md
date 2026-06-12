---
title: "Dansguardian super easy how to..."
date: 2005-11-12
forum: Server Platforms
---

### Post by mhancoc7 on 2005-11-12
I finally got dansguardian to work with my laptop running Hoary.

Here is the link to the How To:
[http://www.vollmar.ch/dansguardian-e.html]("http://www.vollmar.ch/dansguardian-e.html")

It uses Tinyproxy which is available in the repos. I installed it with Synaptic.

I hope this helps someone like myself who is having trouble getting Dansguardian working.

God Bless, Jereme

---

### Post by totalshredder on 2005-12-04
[QUOTE=mhancoc7]I finally got dansguardian to work with my laptop running Hoary.

Here is the link to the How To:
[http://www.vollmar.ch/dansguardian-e.html]("http://www.vollmar.ch/dansguardian-e.html")

It uses Tinyproxy which is available in the repos. I installed it with Synaptic.

I hope this helps someone like myself who is having trouble getting Dansguardian working.

God Bless, Jereme[/QUOTE]

Awesome!! Thanks a lot, my inability to get dansguardian working has kept me from using ubuntu in many places. Thank you very much for this how to!

Luke

---

### Post by mhancoc7 on 2005-12-04
I am glad that the link was helpful. 

Dansguardian is really great. The only problem that I see is that it it really easy to turn off. I also had to edit the banned extension list so I could download some zip/tar files.

God Bless, Jereme

---

### Post by escifell on 2005-12-27
Tried to follow instructions have only manged 75% success.

Packet gets redirected to Danguardian who passes it to tinyproxy which sends it on its way through the modem/router (I can see this using tcpdump). The reply comes back through the internet port but then gets lost with an error message on the screen that tinyproxy cannot find the page. I get exactly the same response using squid. Dansguardian appears to work fine on the outward packet and will block listed bad-sites, but I fear the return path between tinyproxy and dansguardian is scrambled. If I issues the command

iptables -t nat -F

I get the web-page but of course no filtering.

Advice please.

PS I have added a script to save and restore iptables in my /etc/init.d (with links to rc5.d) I copied from [http://ubuntuforums.org/archive/index.php/t-19106.html](http://ubuntuforums.org/archive/index.php/t-19106.html).

---

### Post by shane2peru on 2006-07-25
> **mhancoc7 said:**
> I finally got dansguardian to work with my laptop running Hoary.

Here is the link to the How To:
[http://www.vollmar.ch/dansguardian-e.html]("http://www.vollmar.ch/dansguardian-e.html")

It uses Tinyproxy which is available in the repos. I installed it with Synaptic.

I hope this helps someone like myself who is having trouble getting Dansguardian working.

God Bless, Jereme

Jereme,

Thanks for the post.  Unfortuneatly, I'm still relatively new to linux, and I can't get it configured.  I use Kubuntu, and Firefox.  I have tried several HOWTO's and not really had any luck.  It says it is running, but
1.  I don't know how to test it.  
2.  I don't think it is working through Firefox, but am not sure (see 1).  
3.  I don't want to change this thread to a configuring Dan's Guardian thread. (I will start a new thread.)(I was thinking I was in another thread.  I won't start a new one, sorry, got my threads confused.) Thanks.

Shane

---

### Post by mhancoc7 on 2006-07-25
> **shane2peru said:**
> Jereme,

Thanks for the post.  Unfortuneatly, I'm still relatively new to linux, and I can't get it configured.  I use Kubuntu, and Firefox.  I have tried several HOWTO's and not really had any luck.  It says it is running, but
1.  I don't know how to test it.  
2.  I don't think it is working through Firefox, but am not sure (see 1).  
3.  I don't want to change this thread to a configuring Dan's Guardian thread. (I will start a new thread.)(I was thinking I was in another thread.  I won't start a new one, sorry, got my threads confused.) Thanks.

Shane

I wished I could help you more, but it has been so long since I set it up I am not sure I can even remember how. I just happen to remember this thread. If I incorporate it in the next release of Ubuntu Christian Edition, I will try and remember to do another How To.
Sorry, Jereme

---

### Post by shane2peru on 2006-07-25
No problem.  If you get it setup in the next edition, and setup scripts for those of us already using Ubuntu, that would be great for us.  More work for you:-D   We really do appreciate it though!

Shane

---

### Post by mhancoc7 on 2006-07-25
> **shane2peru said:**
> No problem.  If you get it setup in the next edition, and setup scripts for those of us already using Ubuntu, that would be great for us.  More work for you:-D   We really do appreciate it though!

Shane

I definitely want to create a script to do the install for those who already have Ubuntu installed. I just have to find the time:D.
God Bless, Jereme

---

### Post by tonhou on 2006-07-26
Hi,

You may find this howto helpful that I put together. 

[http://www.ubuntuforums.org/showthread.php?t=207008](http://www.ubuntuforums.org/showthread.php?t=207008)


--Tony

---

