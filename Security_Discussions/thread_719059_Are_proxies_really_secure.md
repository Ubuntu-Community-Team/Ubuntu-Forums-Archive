---
title: "Are proxies really secure ?"
date: 2008-03-08
forum: Security Discussions
---

### Post by RumorsOfWar on 2008-03-08
I've been getting concerned about internet privacy as bill 1959 may be passed into law.:( [http://dovelove.wordpress.com/2007/11/30/senate-bill-1959-to-criminalize-thoughts-blogs-end-of-free-speech/]("http://dovelove.wordpress.com/2007/11/30/senate-bill-1959-to-criminalize-thoughts-blogs-end-of-free-speech/")
And of course;
[http://www.informationclearinghouse.info/article11901.htm]("http://www.informationclearinghouse.info/article11901.htm")
    So I've been a good boy and now use Ixquick instead of google, and I'm looking into using a proxy server. 
   But I'm thinking, if I was the government, intent on controlling all information, I would set up a bunch of free proxy servers myself, and let that act as natural bait for anyone trying to keep private.!!!
After all, the proxy servers themselves will have records of everything, even some passwords. And a higher likelihood that clients are avoiding their control.
 
 Is there any way to tell who owns and operates these proxies?
Am I better off just trusting http encryption?

---

### Post by Dr Small on 2008-03-08
Governments hate Tor, so I use Tor. And of course, it is not secure because you pass your information through several nodes, but it can hide your trail.

Just don't use it for banking sites and such.

Dr Small

---

### Post by Neovos on 2008-03-10
> **Dr Small said:**
> Governments hate Tor, so I use Tor. And of course, it is not secure because you pass your information through several nodes, but it can hide your trail.

Just don't use it for banking sites and such.

Dr Small

But isn't that what the SSL connection to your bank is for? Isn't the only difference with doing that on tor the fact that what was once a 3 party transaction (you, ISP, banking site) now is a multi party transaction? (you, tor(if using privoxy), isp, tor, banking site) and other then the fact that an exit node is a beacon for people to flock to for "interesting information," isn't it still safe to use just because your connection to the bank site is done over https? Isn't in theory, the financial information over the tor network double encrypted?

---

### Post by bmora96 on 2008-03-10
hello all
I am not famliar with proxies. I have heard that it has been used for a firm to login to unaccessed  sites without knowing the superiors.I think its not much secure.
Thanks,
Bmora96

---

### Post by raul_ on 2008-03-10
> **Dr Small said:**
> Governments hate Tor, so I use Tor. And of course, it is not secure because you pass your information through several nodes, but it can hide your trail.

Just don't use it for banking sites and such.

Dr Small

[http://www.theage.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html]("http://www.theage.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html")

You still have to know what your doing

---

### Post by Dr Small on 2008-03-10
> **Neovos said:**
> But isn't that what the SSL connection to your bank is for? Isn't the only difference with doing that on tor the fact that what was once a 3 party transaction (you, ISP, banking site) now is a multi party transaction? (you, tor(if using privoxy), isp, tor, banking site) and other then the fact that an exit node is a beacon for people to flock to for "interesting information," isn't it still safe to use just because your connection to the bank site is done over https? Isn't in theory, the financial information over the tor network double encrypted?
In theory, the information is encrypted over a SSL connection, but that information is passing through multiple nodes to the SSL server. I would be a little leery of actually doing that, because if somebody was sniffing your connection, they can still see that you are connecting to the bank site, albeit the information is encrypted.

That still doesn't mean it couldn't be cracked. But just the same, you generally don't publically post your password on the internet as an encrypted string, for fear of someone actually decrypting it eventually.

Personally, I do not like the idea of transporting sensitive data via several nodes. Encrypted or Unencrypted.

Dr Small

---

### Post by Neovos on 2008-03-10
> **Dr Small said:**
> Personally, I do not like the idea of transporting sensitive data via several nodes. Encrypted or Unencrypted.
Dr Small

I'm still on the fence with this. I have it all setup correctly but I think for financial sites and sites I know personally, the only thing safer then encryption is encryption with less middle men. But thanks to the tor button for making it easy to switch I guess.

---

### Post by RumorsOfWar on 2008-03-13
Thanks for the advice guys. I've learned much. 
I'll probably use Tor, at least when I'm doing anything political. Not just for me, but using it helps others too.

---

### Post by The Tronyx on 2008-03-13
Eh, TOR isn't all it's cracked up to be, take a look at this:

[http://www.theage.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html](http://www.theage.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html)

Hack of the year simply from hosting a TOR node.  If this dude can yank out all this information, like login information for foreign embassies, why couldn't the government do it?

Besides, as far as political postings, this might be bordering on paranoia, but if they REALLY wanted to know and REALLY wanted to put an end to your anti-Iraq agenda, don't you think they could do so regardless of a proxy?

---

### Post by raul_ on 2008-03-13
> **2point0 said:**
> Eh, TOR isn't all it's cracked up to be, take a look at this:

[http://www.theage.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html](http://www.theage.com.au/news/security/the-hack-of-the-year/2007/11/12/1194766589522.html)

Hack of the year simply from hosting a TOR node.  If this dude can yank out all this information, like login information for foreign embassies, why couldn't the government do it?

Besides, as far as political postings, this might be bordering on paranoia, but if they REALLY wanted to know and REALLY wanted to put an end to your anti-Iraq agenda, don't you think they could do so regardless of a proxy?

already posted it

---

### Post by RumorsOfWar on 2008-03-13
> Eh, TOR isn't all it's cracked up to be, take a look at this:

[http://www.theage.com.au/news/securi...766589522.html](http://www.theage.com.au/news/securi...766589522.html)
That is something to be wary of, but that Swedish hacker was warning people about the hazards of not using Tor correctly.  I don't know the difference yet, but its something to learn from. 

> Besides, as far as political postings, this might be bordering on paranoia, but if they REALLY wanted to know and REALLY wanted to put an end to your anti-Iraq agenda, don't you think they could do so regardless of a proxy?
 At the risk of getting political on the wrong board, I'm actually not too worried about Iraq ( I'm not Iraqi). I'm worried about North America, and the loss of our rights. 
  They probably could do something to shut me down, but all I really need to do is inform people. That may be hard to stop.
  It's worse than most people realise...but that's for another board.

---

### Post by The Tronyx on 2008-03-13
> **RumorsOfWar said:**
>  At the risk of getting political on the wrong board, I'm actually not too worried about Iraq ( I'm not Iraqi). I'm worried about North America, and the loss of our rights. 
  They probably could do something to shut me down, but all I really need to do is inform people. That may be hard to stop.
  It's worse than most people realise...but that's for another board.

Sorry, I hope you didn't misconstrue what I was saying.  My intention wasn't to cast aspersions or ridicule your political leanings.  It was merely an example.

On another note, he was hosting a TOR node and if I am not mistaken, TOR welcomes volunteers to host nodes.  Individuals host a node which is added to the network so if anyone can host a TOR node, then in theory, anyone could do what he did or worse.  For example, someone you don't want reading your information which is sent over a proxy that they host and in turn, intercept.

"We need more good ways to intercept DNS requests so they don't "leak" their request to a local observer while we're trying to be anonymous. (This happens because the application does the DNS resolve before going to the SOCKS proxy.)"

That is also found on the tor volunteer section.

---

### Post by Neovos on 2008-03-13
> **2point0 said:**
> Eh, TOR isn't all it's cracked up to be

That wasn't a flaw in tor itself. It was the misunderstanding of those particular tor users. They equated anonymous with secure. Anonymity is useless if the information your sending has your name and information on it.

---

### Post by Neovos on 2008-03-13
> **2point0 said:**
> "We need more good ways to intercept DNS requests so they don't "leak" their request to a local observer while we're trying to be anonymous. (This happens because the application does the DNS resolve before going to the SOCKS proxy.)"

That is also found on the tor volunteer section.
I'm not sure if that was a question, but you can use privoxy for that exact problem.

---

### Post by The Tronyx on 2008-03-13
> **Neovos said:**
> I'm not sure if that was a question, but you can use privoxy for that exact problem.

That was not a question.  Perhaps what I meant to say, I didn't say clearly.

You cannot prevent the people that host tor nodes from viewing data being transmitted through it.  You can use TOR in conjunction with Privoxy for final destination anonymit but when it's in transit it's pretty much fair game.

I mean, TOR is a sweet theory but you can be targetted through Flash applications too, those don't hide your IP.  Cookies from previously visited sites accessed when not using TOR can ID you as well.  People could also possibly redirect your TOR communications or inject hostile scripts, frames, etc.

---

### Post by Dr Small on 2008-03-13
> **2point0 said:**
> That was not a question.  Perhaps what I meant to say, I didn't say clearly.

You cannot prevent the people that host tor nodes from viewing data being transmitted through it.
Well, while Tor is encrypted, the exit node isn't. That's how the Swedish fellow collected the information.

> Tor anonymizes the origin of your traffic, and it encrypts everything inside the Tor network, but it can't encrypt your traffic between the Tor network and its final destination. If you are communicating sensitive information, you should use as much care as you would on the normal scary Internet &#8212; use HTTPS or other end-to-end encryption and authentication.

---

### Post by The Tronyx on 2008-03-13
> **Dr Small said:**
> Well, while Tor is encrypted, the exit node isn't. That's how the Swedish fellow collected the information.

W0rd.

P.S. Hi DrSmall :)

---

### Post by Dr Small on 2008-03-13
Hi there, tronyx :)
Long time no see.

---

### Post by ubuntu27 on 2008-03-13
> **RumorsOfWar said:**
> I've been getting concerned about internet privacy as bill 1959 may be passed into law.:( [http://dovelove.wordpress.com/2007/11/30/senate-bill-1959-to-criminalize-thoughts-blogs-end-of-free-speech/]("http://dovelove.wordpress.com/2007/11/30/senate-bill-1959-to-criminalize-thoughts-blogs-end-of-free-speech/")
And of course;
[http://www.informationclearinghouse.info/article11901.htm]("http://www.informationclearinghouse.info/article11901.htm")
    So I've been a good boy and now use Ixquick instead of google, and I'm looking into using a proxy server. 
   But I'm thinking, if I was the government, intent on controlling all information, I would set up a bunch of free proxy servers myself, and let that act as natural bait for anyone trying to keep private.!!!
After all, the proxy servers themselves will have records of everything, even some passwords. And a higher likelihood that clients are avoiding their control.
 
 Is there any way to tell who owns and operates these proxies?
Am I better off just trusting http encryption?

Wait, that blog and article was written at November 30, 2007. Did it already pass? What's the situation now?

Thank you for the link, really informative.

---

### Post by RumorsOfWar on 2008-03-14
> Wait, that blog and article was written at November 30, 2007. Did it already pass? What's the situation now?

Thank you for the link, really informative.
You're welcome. 
Since it passed the congress with a ridiculous majority, it has not been slated for debate. If they use the same m.o. as the patriot act I suspect they will wait for a major news event to distract people from its sudden passage into law.  The CFR also wants the Amero currency by 2010, my best guess (%65 chance) is an economic collapse to end Bush's term, and the next pres will pick it up from there.( They'll say the amero will save our economy, and while we're worried about that, bill 1959 will pass.) 


As for the original anonymity problem, I found out ( by using grc.com) that my ISP attaches a 'machine name' to everything I do on the net. I'll have to find out if that gets anonimised too.
*edit*
I've started using a router, and now the 'machine name' attached to my connection has changed. At least I know I can change my hookup, change that info and breakup any log files about my surfing activities.:)

---

