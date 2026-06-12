---
title: "How does Ultrasurf work?"
date: 2012-07-10
forum: The Cafe
---

### Post by ki4jgt on 2012-07-10
So I've went to Windows for a temporary period. Back in my Windows days, I always carried a copy of Ultrasurf around with me because of network blocks in hospitals (youtube and flickr were blocked in a hospital with guest wifi???) Now I'm really interested in what makes this little booger tick. I did a little experiment and my IP before using US is the EXACT same as after using US?? I still get their block notice for "inappropriate content" (wanted to test it out) and Facebook still checked to make sure who I was by making my identify pictures of my friends (what they usually do when you're using a proxy) but no matter what I tried, I couldn't get my IP to change while using the UltraSurf program. I also proxied all communications from Firefox into the program. It did no good. How is it that they can bypass restrictions and set off Facebook's alarms while still using you IP address?

---

### Post by Nixarter on 2012-07-10
It isn't as much about how ultrasurf works as how the block software works.  It is made to limit traffic, so they do simple blocks at the DNS level for the computer.  If attempts to query a DNS server about the IP address of youtube.com, a blocked site, the query gets denied and rerouted.  Youtube itself is not blocked, it blocks your computer from finding youtube.com.

Ultrasurf is probably just an automated version of the simplest of work-arounds... that is to not use a DNS.  It takes your typical DNS queries and routes them to a static IP, instead of asking for one (much like modifying your HOSTS file or equivalent).  That way you are connecting to port 80 on the unblocked IP address 74.125.224.160 (youtube.com), instead of making a disallowed DNS query.

In regards to the last question.  All the website you are connected with knows is that you are connected with it.  I does not have a means to know whether you queried a DNS for the IP, whether you manually typed it, or whether adware hijacked your browser.  It doesn't matter to the site how you got their IP address.  It's all the same to them.

They still use the strategy because it is very simple and the vast majority of people have no idea how the internet works, so they have no clue that there can be work-arounds (much less what they are).

---

### Post by CharlesA on 2012-07-10
Better idea: Do not try to bypass rules set in place by the network administrator.

---

### Post by Nixarter on 2012-07-10
> **CharlesA said:**
> Better idea: Do not try to bypass rules set in place my the network administrator.

This.  I agree.

But then again, that was not the question.. He did bring up some valid questions, and this does add to community knowledge.  Should people be forbidden to know how the internet works?  I thought about mentioning that, but I did not want to derail the topic.  Had it been a question about HOW TO bypass their blocks, I would not have posted, but since he was curious about how they work, it is a legitimate topic.

---

### Post by lisati on 2012-07-10
I agree that it's a good idea not to circumvent restrictions imposed by network operators. Sooner or later, you'll get noticed.

You might want to take a look here: [http://lisati.homelinux.com/whoami](http://lisati.homelinux.com/whoami)

---

### Post by CharlesA on 2012-07-10
> **lisati said:**
> 
You might want to take a look here: [http://lisati.homelinux.com/whoami](http://lisati.homelinux.com/whoami)

ZOMG!

Browser header sniffing ftw! :P

---

### Post by sffvba[e0rt on 2012-07-11
Not wanting to go off-topic but having a look at that whoami link gave me an odd statememnt:

> Note:

There could be a problem sending email from the same IP address as your compuer to mine.

Your IP address (X.XX.XXX.XXX) appears to be listed by the following service(s): 

zen.spamhaus.org

For more information, click here

zen.spamhaus.org... good name for a bad book.


404

---

### Post by MG&amp;TL on 2012-07-11
> **not found said:**
> Not wanting to go off-topic but having a look at that whoami link gave me an odd statememnt:



zen.spamhaus.org... good name for a bad book.


404

Yeah, mine too. What does that mean? Also zen.spamhaus.org doesn't appear to be online.

---

### Post by sffvba[e0rt on 2012-07-11
> **MG&TL said:**
> Yeah, mine too. What does that mean? Also zen.spamhaus.org doesn't appear to be online.

[www.spamhaus.org/zen](www.spamhaus.org/zen) is :p


404

---

### Post by MG&amp;TL on 2012-07-11
> **not found said:**
> [www.spamhaus.org/zen](www.spamhaus.org/zen) is :p


404

Duh. For once I should have actually paid attention to chrome's autocomplete.

Thanks.

---

### Post by ki4jgt on 2012-07-13
> **Nixarter said:**
> It isn't as much about how ultrasurf works as how the block software works.  It is made to limit traffic, so they do simple blocks at the DNS level for the computer.  If attempts to query a DNS server about the IP address of youtube.com, a blocked site, the query gets denied and rerouted.  Youtube itself is not blocked, it blocks your computer from finding youtube.com.

Ultrasurf is probably just an automated version of the simplest of work-arounds... that is to not use a DNS.  It takes your typical DNS queries and routes them to a static IP, instead of asking for one (much like modifying your HOSTS file or equivalent).  That way you are connecting to port 80 on the unblocked IP address 74.125.224.160 (youtube.com), instead of making a disallowed DNS query.

In regards to the last question.  All the website you are connected with knows is that you are connected with it.  I does not have a means to know whether you queried a DNS for the IP, whether you manually typed it, or whether adware hijacked your browser.  It doesn't matter to the site how you got their IP address.  It's all the same to them.

They still use the strategy because it is very simple and the vast majority of people have no idea how the internet works, so they have no clue that there can be work-arounds (much less what they are).

> Ultrasurf is a product of Ultrareach Internet Corporation. Originally created to help internet users in China find security and freedom online, Ultrasurf has now become one of the world's most popular anti-censorship, pro-privacy software, with millions of people using it to bypass internet censorship and protect their online privacy.

Wouldn't a simple DNS walk-a-round set off firewall alerts for China or is that all they have in that huge investment? Back when I was in school though, school administrators were having a hectic time blocking this application. There were school administrators from all over the district trying to find a way to do it. I in an attempt to find out if it could be blocked did some google searching back in the day. Let's just say our district wasn't the only one trying to get rid of Ultrasurf. People tried blocking ports, changing proxy settings. Our school had a mandated proxy sign in process (this was 08). Every time you started IE you had to provide a username and password. Ultrasurf just walked right around that. You started the program and then it opened IE for you and you were able to do as you pleased.

Also another inquirey, if it's just using your IP, why do they block sites?

---

### Post by Lucradia on 2012-07-13
Well, I might not be able to send emails to lisati :V

"
    zen.spamhaus.org
    dnsbl.sorbs.net
"

are in my IP address. Too bad IPv4 is pretty much exhausted, so this is expected.

---

### Post by Nixarter on 2012-07-13
> **ki4jgt said:**
> Wouldn't a simple DNS walk-a-round set off firewall alerts for China or is that all they have in that huge investment? Back when I was in school though, school administrators were having a hectic time blocking this application. There were school administrators from all over the district trying to find a way to do it. I in an attempt to find out if it could be blocked did some google searching back in the day. Let's just say our district wasn't the only one trying to get rid of Ultrasurf. People tried blocking ports, changing proxy settings. Our school had a mandated proxy sign in process (this was 08). Every time you started IE you had to provide a username and password. Ultrasurf just walked right around that. You started the program and then it opened IE for you and you were able to do as you pleased.

Also another inquirey, if it's just using your IP, why do they block sites?

The main clue is the reporting of the correct IP address (unless it is f\getting it from FLASH, etc).

I do know that the main way to block is by DNS query blocking and/or re-routing.  The last time I checked, all that was needed in China was to simply connect to the IP address for blocked sites instead of relying and DNS's for human-readable-to-IP conversions.  This may have changed, but I doubt it.  MITM attacks are still possible, of course.  The fact is, there are lots of ways to do lots of things, so I don't know how Ultrasurf does it.  Honestly, I do not know enough to know why it is so challenging to block IP addresses directly.  It seems like that would be the easiest solution... but obviously such isn't the case.

---

