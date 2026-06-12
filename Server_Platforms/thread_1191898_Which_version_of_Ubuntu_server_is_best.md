---
title: "Which version of Ubuntu server is best?"
date: 2009-06-19
forum: Server Platforms
---

### Post by ZackM on 2009-06-19
I'm using 9.04 for client use, but I'm thinking about getting an old computer set up as a server, and I want to know which version of Ubuntu Server is best. I could figure out which I'd like more, but I just want some opinions. I really like Jaunty thus far as client, but I don't know if I want the latest version for a server. I was thinking maybe Hardy. What do you think?

---

### Post by ZackM on 2009-06-19
bump

---

### Post by ZackM on 2009-06-19
Anyone? Lol.... I don't like bumping things, but I'd like to get some personal views on this.

---

### Post by Cheesemill on 2009-06-19
I always go with 8.04 with my servers because it's LTS (Long Term Support).
8.04 will be supported with security updates until 2013.

---

### Post by ZackM on 2009-06-19
> **Cheesemill said:**
> I always go with 8.04 with my servers because it's LTS (Long Term Support).
8.04 will be supported with security updates until 2013.

Thanks. That's what I was thinking as well. Client wise, having the most updated version is okay in my opinion. It's fun to play around with new looks, apps, and everything else that has changed. However, for a server I think it'd be more prudent to stick with something that has been around a little longer, and has a larger knowledge base.

---

### Post by cinestar on 2009-06-19
Latest version is always the best LOL

---

### Post by ZackM on 2009-06-19
> **cinestar said:**
> Latest version is always the best LOL

Okay... Why do you think that? Stating it's the best and giving no reasoning doesn't really help. I'd like to know why you think it's best to use the latest version, versus using one that's been around awhile.

---

### Post by Cheesemill on 2009-06-19
When you're running a large number of Ubuntu servers the last thing you want to do is have to upgrade them all every 18 months when support runs out. By only running LTS versions you increase the upgrade lifecycle to 5 years.

---

### Post by ZackM on 2009-06-19
> **Cheesemill said:**
> When you're running a large number of Ubuntu servers the last thing you want to do is have to upgrade them all every 18 months when support runs out. By only running LTS versions you increase the upgrade lifecycle to 5 years.

Haha yeah. Upgrading that many would be a job in itself, especially if you run into problems. However, I'll be using one, maybe two, for a personal home network. But, even then, I wouldn't want to upgrade every 18 months. And if I'm going to have it constantly running, and keeping media and files that I wouldn't want to just disappear to run on something that's brand new in comparison to something that's been out for awhile and more problems have been solved with it.

---

### Post by cinestar on 2009-06-19
> **ZackM said:**
> Okay... Why do you think that? Stating it's the best and giving no reasoning doesn't really help. I'd like to know why you think it's best to use the latest version, versus using one that's been around awhile.

You used the word "best" which is a subjective term. 

It's like asking, "What tastes better an orange or a frog?" The answer you receive will be just as subjective because it will be based on personal tastes and oppinions as opposed to actual fact LOL.

So to answer you latest question,why is the latest version always the best? By definition an upgrade to anything is always an improvement over it's predesessor thats the whole point of an upgrade. 

Perhaps the original question should have been, "Which version is most recommended...?" ...know what i mean vern?

---

### Post by ZackM on 2009-06-19
> **cinestar said:**
> You used the word "best" which is a subjective term. 

It's like asking, "What tastes better an orange or a frog?" The answer you receive will be just as subjective because it will be based on personal tastes and oppinions as opposed to actual fact LOL.

So to answer you latest question,why is the latest version always the best? By definition an upgrade to anything is always an improvement over it's predesessor thats the whole point of an upgrade. 

Perhaps the original question should have been, "Which version is most recommended...?" ...know what i mean vern?

I elaborated on saying that I wanted personal opinions, I do believe. However, in an upgrade having improvements I agree, however some of the improvements they have made may actually help to develop other issues in which not much is known, nor the answers to the issues. I meant which is recommended, so I can admit that the question was worded rather poorly, and I thank you for your elaboration.

---

### Post by ibutho on 2009-06-19
For production servers, I usually stick with LTS releases because of the length of time that they are supported. For anything else, I just use the latest release.

---

### Post by Cheesemill on 2009-06-19
> **cinestar said:**
> You used the word "best" which is a subjective term. 

It's like asking, "What tastes better an orange or a frog?" The answer you receive will be just as subjective because it will be based on personal tastes and oppinions as opposed to actual fact LOL.

So to answer you latest question,why is the latest version always the best? By definition an upgrade to anything is always an improvement over it's predesessor thats the whole point of an upgrade. 

Perhaps the original question should have been, "Which version is most recommended...?" ...know what i mean vern?

When I'm wearing my sysadmin hat then best = most stable. There are usually always unforeseen difficulties when you upgrade which cost you time/money, I'd take stability over new features any day of the week :)

From [http://dictionary.reference.com](http://dictionary.reference.com) 
Upgrade - To replace (a software program) with a more recently released, enhanced version.

This doesn't necessarily mean it will be an improvement!!

---

### Post by terazen on 2009-06-19
I normally would agree, but ubuntu 10.04 lts should be out before 9.04 support expires if I read the release cycle right.

With that in mind it's a bit of a toss-up.  There is a 6 month gap next year that both will be supported so you have a decent amount of time to upgrade off jaunty.

Just another opinion...

---

### Post by cariboo on 2009-06-19
Personally I can't help playing with my server, so I seem to rebuild it every 6 months, and always with the latest release. I have had servers running for over two years, depending on the usage, there is no reason to upgrade when the version eol's. If you have an outward facing server, then you always need to keep up on the updates, but if it is inward facing, it shouldn't make any difference.

That being said, my personal inward facing server only gets a kernel update when I install a new version.

---

### Post by Cheesemill on 2009-06-19
> **cariboo907 said:**
> Personally I can't help playing with my server, so I seem to rebuild it every 6 months

I'm actually rebuilding my home server as we speak. I'm putting 8.04 on it but that's only becuase the 8.04 Mini CD was the first thing I could lay my hands on that will do a server install.

I have several Pisa like stacks of unlabelled burnt CD-R's on my desk - if only I was more organised 8-[

---

### Post by TwiceOver on 2009-06-19
While I would normally say 8.04 for the LTS, as of today I'm going to say 9.04 the latest.

The reason is that though LTS is great, it includes "Security" updates... Not program updates.  So if you rely on things like Samba (version 2.f'ing old on 8.04), you'll want something like 9.04 which includes the newer version 3.2.x

I have tried everything to get 3.3 on my 8.04 production server to no avail.  Tried backports and PPA, no go.  I'll either have to upgrade or compile myself.

---

