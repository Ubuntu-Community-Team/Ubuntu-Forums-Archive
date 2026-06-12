---
title: "i want to create a private messaging platform"
date: 2020-02-21
forum: The Cafe
---

### Post by Skaperen on 2020-02-21
i want to create a private messaging platform.  it would not be like twitter at all.  it would be like a limited form of email.  it would be like the private message facility here on Ubuntu Forums and many others, but would be the prominent feature.  signups would require some form of bot filter up front, through email (like sending a question to answer in addition to a confirmation code), and maybe another bot filter.  it would not interface to outside email for messaging in either direction.  users can only message to other users that have signed up.  but the messages can be much larger/longer than tweets and can be searched only by sender and recipient.

i would probably create an API that can be used after signup.  i am wondering what form of two-factor authentication i can use and if i should make it optional or mandatory.

---

### Post by TheFu on 2020-02-23
Sounds like IRC over SSL to me.

---

### Post by Skaperen on 2020-02-25
the messages are not chat-like.  it might not be visible to the recipient until many seconds later, possibly a minute in extreme cases.  it might be more like email.  i'm hoping to make it more like twitter with only direct to recipient messaging (maybe reflectors, too)and longer posts (8k or more).  its kinda what i feel is missing in twitter.  if i include reflectors, then it would be like a forum, too, where users can create their own "channel".  there would be many options to control where you get postings from (anyone, only those in this whitelist, anyone except those in this blacklist) and the reflectors might have forum moderators.

---

### Post by mastablasta on 2020-02-25
so if it's like email and forums is this public or private? forums are public, emails are private.

this sounds something like Microsoft Teams.

will this be super private? is this something like Tox? will users need keys?

---

### Post by Skaperen on 2020-02-25
the forums can be public or public-approved or invite-only.  and members can be silent or not.  a forum might be public to silent and public-approve to be non-silent, for example.

i don't know what Teams or Tox are like.  i'll go wiki them when i get some time.

---

### Post by EuclideanCoffee on 2020-02-25
Why not use an already established technology? The trouble with making your own is that you must rely on security processes, and they are only improved when heavily tested. System administration already is a full time job. Why bother doing two full time jobs for fun? 

When using software someone already built, there is a community using the software with you who will report security related problems to developers who will likely get around to fixing the problem sooner than just you. And I say this with good intention. I've supported my own applications before, and it becomes a bit much. :)

Matrix - [https://github.com/matrix-org/synapse](https://github.com/matrix-org/synapse)
phpbb - [https://www.phpbb.com/](https://www.phpbb.com/)
Jabber - [https://www.ejabberd.im/](https://www.ejabberd.im/)

---

### Post by Skaperen on 2020-02-25
i like being the sysadmin.  i'm not opposed to using something that already exists but it has to have everything i want to do or be written in a language i can add on to (C, Pike, or Python).  i don't see what i want to have in those systems.  what does twitter run?

---

### Post by EuclideanCoffee on 2020-02-26
Twitter is closed source, but you might want to look into these:

[https://github.com/tootsuite/mastodon](https://github.com/tootsuite/mastodon)
[https://en.wikipedia.org/wiki/GNU_social](https://en.wikipedia.org/wiki/GNU_social)
[https://en.wikipedia.org/wiki/Pump.io](https://en.wikipedia.org/wiki/Pump.io)
[https://en.wikipedia.org/wiki/Identi.ca](https://en.wikipedia.org/wiki/Identi.ca)
[https://en.wikipedia.org/wiki/Diaspora_(social_network)](https://en.wikipedia.org/wiki/Diaspora_(social_network))

I wish to warn you against using any federated service. It is a stressful job since many users assume things are permissible due to a sense of anonymity. You also have limited control on what goes into your webserver.

---

### Post by Artim on 2020-02-26
I second the warning about using any of the federated services.  They are heavily populated with people who were kicked off of other platforms (Twitter, Facebook, etc).  Diaspora in particular has become a digital sewer.

---

### Post by Skaperen on 2020-02-27
i am not planning distributed in the sense of Diaspora.  i would keep full master control.  creators of groups/reflectors would have further control over their group, but not control over allowing users onto the site.  there would be scaling distribution that allows running many server instances in the cloud to scale up the activity level, including geographically distributed clusters.

---

### Post by Skaperen on 2020-02-27
did i mention that i want to stay away from PHP, Perl, Ruby, and Java?  i would do this in Python, adding C, Pike, and/or bash for components where they are helpful.

---

### Post by EuclideanCoffee on 2020-02-27
No particular programming languages is specifically superior. You choose whatever you can write. If you don't want to use a platform, start with building a server and move from there. Good luck. It's a lot of work.

---

### Post by CelticWarrior on 2020-02-28
> **EuclideanCoffee said:**
>  It's a lot of work.

An understatement, obviously.

---

### Post by EuclideanCoffee on 2020-02-28
I did 6 years of community building for video game modding forums prior to going to college for CS and then graduating to do this sort of thing more full time (system administration). On both layers there were challenges that resulted in a lot of my time being spent doing work that I could've spent doing something far more interesting.

I won't say don't do it, but be prepared to spend 6 years not knowing exactly what you will be doing, what the pay off will be, and how it will be done.

I don't really have time like that. :)

---

### Post by Skaperen on 2020-02-28
i'm now retired.  in theory, i have more time.

---

