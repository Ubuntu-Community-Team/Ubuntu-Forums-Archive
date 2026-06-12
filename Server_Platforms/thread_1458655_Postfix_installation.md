---
title: "Postfix installation"
date: 2010-04-20
forum: Server Platforms
---

### Post by philavia on 2010-04-20
Dear all,

It is my first post on this forum.  I read you a lot and get valuable help from the different topics.  But, this time I am really completely stuck and even google with its thousand of links was not helping.

What I am trying to do is the following:

1/ I have a server (at gandi.net),
2/ I have a domain name: domain.org,
3/ I would like to be able to send/receive mail with an own mail server.

For the point 3 above, I would like to be able to do:
a/ Send from [email]user1@domain.org[/email] to [email]user2@domain.org[/email]
b/ Send from [email]user@domain.org[/email] to [email]anybody@anywhere.tld[/email]
c/ Receive from [email]anybody@anywhere.tld[/email]

Actions a/ and c/ are working, but I am unable to send mail to the "outside world" from my mail server.

In my research on forums and google, one of the thread stated that postfix, SMTP, ... installation is extremely complex and necessitate months of reading to start to get some knowledge.
Is it true that it is so complex and that a mail server installation is nearly impossible for a newbie ?

By the way, Web server, FTP server installation was rather easy to perform.

Is do you know an easy, nicely explained, step by step and working tutorial permitting to install a mail server on Ubuntu 9.10.

Thanks for help.

Phil

---

### Post by dudumomo on 2010-04-20
Hi philavia
Having a mail server correctly running is not that difficult. But indeed because there are a lot of different way to set up such a server (A lof ot features in postfix and co), it can be quite tricky if you don't know where to start.

I'm a beginner too in server installation. But actually it wasn't so difficult. I even wrote a tutorial: [http://www.freelydifferent.com/self-hosting/self-hosting-for-dummies/](http://www.freelydifferent.com/self-hosting/self-hosting-for-dummies/)

I hope it can helps you.

But your server is almost working correctly as I can see.
Are you sure your mail are not detected as SPAM ?

---

### Post by KB1JWQ on 2010-04-20
[http://www.postfix.org/BASIC_CONFIGURATION_README.html](http://www.postfix.org/BASIC_CONFIGURATION_README.html) : a good starting place for Postfix beginners, many common questions are answered here.

A very common problem is that some people prefer to follow a step-by-step tutorial that shows them how to setup their server without reading the documentation or understanding what they are doing. If something goes wrong, they have no clue whatsoever about where to find hints, and they sometimes decide to start from scratch using a different tutorial. This is not The Proper Way(tm).

---

### Post by philavia on 2010-04-20
Hi KB1JWQ,

"If something goes wrong, they have no clue whatsoever about where to find hints, and they sometimes decide to start from scratch using a different tutorial." : You have a point :)

Thanks for the links, I will check that.

Phil

---

### Post by philavia on 2010-04-23
Hi dudumomo,

I tried exactly your tutorial with no luck.
I still have the same symptoms:
- nmap localhost 25 gives smtp open
- nmap domain.org 25 (from another PC) gives smtp filtered

- able to access port 25 in local (netcat domain.org 25)
- unable to access port 25 from another pc (netcat domain.org 25) 

- trying to send mail to [email]anybody@anywhere.tld[/email], and receiving relay access denied.

I am afraid that I have to give up due to lack of time (already few weeks of reading, searching, trying).
I must admit that the remark of KB1JWQ is perfectly correct: you need to understand what you do instead of using blindly some kind of recipe.  This remark associated to the other one that I found before seems to form a sound conclusion: Mail server is extremely complex and necessitate quite important competences.

So, I stop playing with fire, I lack those competences.

Thanks for trying.

Phil

---

### Post by noway2 on 2010-04-23
Relay access denied indicates an authentication problem.  Basically, in order to send mail to a host other than yours (your recipient domain), you need to authenticate to the server.  This is a VERY important anti-spam measure.

Unfortunately, other to than to say that setting up Postfix is complex, which it is, and that it isn't working, you haven't provided much information to work with.

Try this document:[http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html).  It will at least get you started and explain why you are having trouble.

---

### Post by ruuden on 2010-04-23
if you just have a basic default postfix installation and you get relay access denied, you should probably check your /etc/postfix/main.cf file for the my_networks parameter. Make sure your domain, localhost and your lan (ex. 192.168.1.1/24) is listed there. And then check your log file with:

```
tail -20 /var/log/mail.log
```

---

### Post by philavia on 2010-04-23
Thanks for insisting to help :)

But, to avoid loosing your time, I just stop trying to install postfix.
I have no more time for the moment to try further and certainly lack competencies ... even to provide a good question on this forum :confused:

I will try to find "generic" info on what is a mail server and on its technology (philosophy, I should say).  If possible a kind of not too specialised description.  For the moment the only info found is more a description of the configuration options, which is of no help in my case, as I suspect that I really do not understand something related to the really basics.
The reason for opening this thread was more related to this kind of information.  I read the postfix doc, but its level of complexity is too high for me:  I definitely lack some background knowledge.

For information, the server I tried to install postfix onto is a server space that I acquire from Gandi.net with Ubuntu 9.10 installed on it by Gandi (Expert configuration).
So, this is not a machine present on my LAN.  I only have access to its console via ssh.

Phil

---

