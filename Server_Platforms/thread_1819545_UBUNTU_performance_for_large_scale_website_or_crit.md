---
title: "UBUNTU performance for large scale website or critical mission"
date: 2011-08-06
forum: Server Platforms
---

### Post by ngno on 2011-08-06
folks,

anyone of you could share if you have been using ubuntu for large scale website or critical mission project, say for 500.0000 secure transaction per 3 hours with 4 million users accessing server. how does ubuntu perform? 

appreciated your sharing

---

### Post by SeijiSensei on 2011-08-06
> **ngno said:**
> folks,

anyone of you could share if you have been using ubuntu for large scale website or critical mission project, say for 500.0000 secure transaction per 3 hours with 4 million users accessing server. how does ubuntu perform? 

appreciated your sharing

At those kinds of loads you need to be looking at a server farm with methods to distribute requests to multiple back end servers.  I doubt there's any operating system that would support that many requests on a single server.

The other option is using a "content-distribution network" like [Akamai](http://www.akamai.com/).

If you're asking this question at Ubuntuforums, I suspect you need to learn a lot more about how large sites are managed than you do now.

But, yes, with the right architecture Linux would be a fine platform for such an endeavor.  You might want to consider going with RedHat Enterprise Linux and pay for professional support, particularly in areas like clustering servers.  Those support fees will be just a small item in the budget for a site this size.

---

