---
title: "Possible cracking attempt or DOS"
date: 2007-03-13
forum: Server Platforms
---

### Post by madsporkmurderer on 2007-03-13
I have just noticed an abnormally high amount of traffic to a webserver I have running and have found the traffic to be directed towards vsftpd. It appears to be someone attempting to brute force the ftp access password or possibly a very poor DOS attack.

The logs show:```
Tue Mar 13 22:11:56 2007 [pid 9970] CONNECT: Client "217.23.140.157"
Tue Mar 13 22:12:07 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:11 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:13 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:15 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:17 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:19 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:27 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:29 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:35 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:37 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:39 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:44 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:48 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:51 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:12:57 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:06 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:09 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:11 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:13 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:16 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:18 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:20 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:22 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:24 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:27 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:29 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:31 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:33 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:35 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:37 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:39 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:42 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"
Tue Mar 13 22:13:43 2007 [pid 9969] [Administrator] FAIL LOGIN: Client "217.23.140.157"

```

with the failed logins continuing for pages. There are also 2 different sets on 2 different days from different IP addresses; one is from Russia and one from China if that holds any significance.

I have stopped vsftpd as a precaution as it is not absolutely critical as its primary purpose is as a LAMP server, but I am concerned about this and ftp is useful to have.

Is this normal, how could it have happened, should I be worried and how do I stop it?

Thanks in advance,
Mike

---

### Post by MJN on 2007-03-13
Sad to say, but in this day and age this is indeed quite normal!

Many solutions exist all of which have been widely discussed including strong(er) passwords, public key authentication (where supported), 3rd part apps to monitor for failed logins and block their IP (e.g. fail2ban which I use and can recommend), moving to non-standard ports etc.

Mathew

---

### Post by madsporkmurderer on 2007-03-13
Thanks a lot for the quick reply, I was quite worried for a while.

by the seems of it they won't be getting anywhere as the is no 'administrator' user, but thanks for the advice on fail2ban; I'll look at that tomorrow until when it should be ok as I have also blocked the offending IP at my router

---

### Post by MJN on 2007-03-13
Give it time and they'll be changing login names, some of which will exist on your system!

As mentioned, strong passwords are the minimum and with fail2ban I can't see any remaining room for much further worry.

Incidentally, from my albeit limited testing, I've found generally that once an IP is blocked at the network layer they soon move along to their next targets. I've got fail2ban set to ban IPs for only 10 minutes and I rarely, if ever, see a 'repeat offender' come back for more once initially blocked. The repeated attempts you're seeing are because they're getting a response, and so they're just going through their common password list(s) hoping to strike it lucky.

Mathew

---

### Post by Nikron on 2007-03-13
It's kinda sad really, my ssh server has gotten hit with about 3k brute force hack attempts... in 3 weeks..

So far, picktek.com is leading with 746 attempts before being auto banned...

---

### Post by primski on 2007-03-14
I have lots of those attack attempts too :s Solved it (i hope) with loooong passwords as suggested, but suffered a major hack recently (yesterday :S), but wasn't through ftp server, but buggy phpnuke cms system using sql injection's and deleted half my database.

I even wrote an email to the traced IP's ISP abuse account, hope to get some answer. Tell me, what are the laws in the US about this ? Must ISP keep confidential about client's data, or will they take any legal actions?

---

### Post by Frosty Cold Drink on 2007-03-14
> **primski said:**
> I have lots of those attack attempts too :s Solved it (i hope) with loooong passwords as suggested, but suffered a major hack recently (yesterday :S), but wasn't through ftp server, but buggy phpnuke cms system using sql injection's and deleted half my database.

I even wrote an email to the traced IP's ISP abuse account, hope to get some answer. Tell me, what are the laws in the US about this ? Must ISP keep confidential about client's data, or will they take any legal actions?

If sensitive, personaly identifiabe information is leaked, it often must be reported to those affected.

Unless the damage is over a few thousand dollars, the FBI typically won't get involved.

Most of these attempts come from machines that have already been compromised. While you are finding the offending machine, the actual attacker is long gone.

---

### Post by primski on 2007-03-15
> **Frosty Cold Drink said:**
> If sensitive, personaly identifiabe information is leaked, it often must be reported to those affected.

Unless the damage is over a few thousand dollars, the FBI typically won't get involved.

Most of these attempts come from machines that have already been compromised. While you are finding the offending machine, the actual attacker is long gone.

Yea, agree, the damage is not so high tho. I run a gaming site to a small clan, we had some forums talks, wars etcetc, nothing money related. 

We had several (smaller) attacks previously, coming from Turkey, some hacker group, they even put a link to their hp in it (cant remember no more tho :S ) so we are suspecting its been the same group this time, only using proxy from the other side of the world, smwh in California.

Ah well, you win some, you loose some. Best bet is, to learn from this crap and build a better site.

greetz
-preem

---

