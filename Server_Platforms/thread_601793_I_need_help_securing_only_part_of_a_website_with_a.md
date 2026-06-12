---
title: "I need help securing only part of a website with apache2"
date: 2007-11-03
forum: Server Platforms
---

### Post by stormlongfella on 2007-11-03
I have set up 4 websites on my server. Now I want to secure only portions of 2 of the websites ([www.domain1.com/mail/](www.domain1.com/mail/) & [www.domain2.com/store/](www.domain2.com/store/)). I have been reading for the past 6 days and they only thing I have found was a post that suggested to create a seperate site-enable file with SSL enabled and listening on port 443 that points to the directory i want secured. After doing this I am able to secure only one directory, and anything with https gets forward to that directory. [http://www.domain1-4.com](http://www.domain1-4.com) go to where they are suppose too. but [https://www.domain1-4.com](https://www.domain1-4.com) all go to where [https://www.domain1.com/mail/](https://www.domain1.com/mail/) is point too. I would like for people to get and error message if the type in [https://www.domain1-4.com](https://www.domain1-4.com) instead of beign forwarded to [www.domain1.com/mail/](www.domain1.com/mail/) and have [https://www.domain2.com/store/](https://www.domain2.com/store/) go to where it's suppose too. Can anyone help???

---

### Post by kidders on 2007-11-04
> **stormlongfella said:**
> [http://www.domain1-4.com](http://www.domain1-4.com) go to where they are suppose too. but [https://www.domain1-4.com](https://www.domain1-4.com) all go to where [https://www.domain1.com/mail/](https://www.domain1.com/mail/) is point too.What kind of virtual hosts are domain1.com and domain1-4.com? As you may (or may not) know, you cannot run more than one name-based virtual host over SSL.

---

### Post by stormlongfella on 2007-11-04
> **kidders said:**
> What kind of virtual hosts are domain1.com and domain1-4.com? 

Not sure what you're asking. The company I work for is composed of 4 different business, and my boss wants to have 4 different websites to represent each business. so we've purchased 4 different domains from NetworkSolutions (domain1.com, domain2.com, domain3.com, domain4.com). domain1-4.com is just my lazy way to mean domain1.com, domain2.com domain3.com, and domain4.com. lot less typing.

> **kidders said:**
> As you may (or may not) know, you cannot run more than one name-based virtual host over SSL.

I didn't know that. Is there anyway round this? I read in a post that mentioned a rewrite option that would  redirect everything from http to https, would this work?

---

### Post by kidders on 2007-11-04
> **stormlongfella said:**
> Is there anyway round this?No. If you think about it, it's quite an obvious observation though ... since a HTTP request (and hence the header that identifies the name of the virtual host the user wants) will only ever get sent *after* the initial SSL handshake, there would be no way for a web server to know who to claim to be. Essentially, HTTPS has been explicitly designed not to work with name-based virtual hosting.

The usual choices are...[LIST]
[*]To opt for IP-based virtual hosting. (In my last post, I was basically wondering whether had done this.)
[*]To use the same SSL host for all four of your services.
[*]To run multiple SSL servers on different ports at the same IP (very undesirable).
[/LIST]

---

### Post by stormlongfella on 2007-11-04
Kidders, Thanks for the help. After 7 days of searching I'm finally finding answers...Not the answers I wanted to hear, but answers none the less. 
 
> **kidders said:**
> The usual choices are...[LIST]
[*]To opt for IP-based virtual hosting. (In my last post, I was basically wondering whether had done this.)
[*]To use the same SSL host for all four of your services.
[*]To run multiple SSL servers on different ports at the same IP (very undesirable).
[/LIST]

I see I have 3 options to consider. Okay then, let's see. Since my  budget for this project consist of a free cup of coffee and a donut in the morning, purchasing new ip addresses is out of the question. So option 1 is Xed. Option 3 even if I were willing to over look the *very undesirable* comment, It sounds too complicated to setup. Even on my best days i would barely consider myself a novice to all this. So option 3 is out as well. That leaves me with option 2. If it's not to much of a bother can you give some search phrases that can set me on the right path. After 7 days of this I am totally tapped out.

---

### Post by kidders on 2007-11-05
I'm glad your thread is proving productive ... sort of!

Your comment about purchasing IPs surprises me. Where I live, it's illegal for *anyone* to charge for an IP address -- all that's required is a half-decent reason for wanting more than one. I didn't realise the rest of the world doesn't work the same way lol.

Anyhow, my second option boils down to implementation issues, really. There must be thousands of howtos & discussions on the web about setting up HTTPS, but you'll still have to find a neat way for the secure parts of all your services to play nice on a single virtual host, without crashing into one another. You'll probably need to do some rewriting, so whatever code you're running doesn't assume it's alone on the server it lives on.

Basically, where you would have preferred https://service3.yourhost.com/, you'll have to make do with https://secure.yourhost.com/service3/ instead. Without knowing more about what you're running though, it's difficult to anticipate the sorts of problems you might wind up with. Off the top of my head, one that I have seen before (on poorly-written sites) involves session cookies from one service granting access (albeit not necessarily error-free hehe) to another.

Incidentally, in a commercial setting, the use of SSL does require a budget. You see, without certificates from a well-recognised CA, nobody in his right mind would even dream of buying something on, or handing personal information over to one of your websites -- your users' browsers will actively discourage them from doing so.

Anyway, I hope some of that's helpful.

---

