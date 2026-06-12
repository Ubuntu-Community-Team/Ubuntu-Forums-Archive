---
title: "Dansguardian on Home Network"
date: 2007-08-16
forum: Ubuntu Christian Edition
---

### Post by guypilkinton on 2007-08-16
Hi I got your new dansguardian gui to work on ubuntu thanks very much. Can you just tell me how to set up another user account so my kids don't have access to the GUI too. And I have noticed that with Dansguardian going we loose network access to folders on other computers in the house. How can I fix this?

Thanks for your help

---

### Post by urukrama on 2007-08-18
To set up another user account, go to System > Administration > Users and Group .  and make sure you don't give that user administrative privileges.

---

### Post by guypilkinton on 2007-08-19
Thanks for your help, I've set up another user.  How about allowing that user access to other folders on the home network with an xp machine.

---

### Post by cafluegg on 2007-08-20
I haven't had problems seeing shared folders on xp machines. However, I have had issues seeing shared folders on my two ubuntu ce machines.  They're both running dansguardian and I cannot - for the life of me - see their respective shared folders. I haven't tried accessing my ubuntu ce shares from my xp machine, but the ce machines cannot see each other. 

To view my xp shares, I open up /places/network in my main menu. My windows network pops up right away.

hope you get your answer. :-)

---

### Post by tak1150 on 2007-08-20
this thread might be of interest
[http://ubuntuforums.org/showthread.php?t=453527]("http://ubuntuforums.org/showthread.php?t=453527")

Tak

---

### Post by guypilkinton on 2007-08-21
Thanks that thread has solved my problem.  Its all working fine now.

---

### Post by nitep on 2007-10-13
Hi look at my tutorial [http://ubuntuforums.org/showthread.php?t=566698](http://ubuntuforums.org/showthread.php?t=566698)
OpenDNS is faster than an on-site filter such as Dansguardian or other  on-site filters. Also see [http://nbcf.witnesstoday.org/links.html#safe](http://nbcf.witnesstoday.org/links.html#safe)
Regards
Peter

---

### Post by urukrama on 2007-10-14
OpenDNS would only filter the sites you tell it to filter. That's quite unpractical for porn filtering.

---

### Post by jonathonblake on 2007-10-14
[QUOTE=nitep]
OpenDNS is faster than an on-site filter such as Dansguardian or other  on-site filters.[/QUOTE]

a) Faster?  Only if one uses caching DNS with a provider who uses caching DNS.  (It doesn't matter how few, or how many DNS servers your ISP has.  Nor does it matter where those servers are located, _IF_ the DNS server is correctly configured. The more people making DNS requests, the more data will be cached for users. There are ways to increase the speed for frequently visited sites, without using DNS caching.)

b) OpenDNS blocks "adult" and "phishing" sites.  There are numerous other sites that are "undesirable" for one reason or another.  (Timewasters such as /. or privacy violators such as Google are some examples.)

c) Whitelists and blacklists only work with "known" content. They don't work with new sites, or unrated sites. Furthermore, such lists are prone to error. "Phrase matching", PICS filtering and similar techniques  will accept/reject content that in either new, or unknown;

xan

jonathon

---

### Post by grendelkhan on 2007-10-16
Dans Guardian has been a Godsend for us.  My 15 year old son had no content filtering and no time restrictions when he lived with my ex wife and is fighting it very hard now that he's living with us.  But we actually do sleep a lot sounder knowing that we've locked down his internet to our satisfaction.  It may not be perfect, but running Linux lets us lock his system down much better than under Windows.

Besides the fact that I'm a unix geek and run Ubuntu for my system.

---

