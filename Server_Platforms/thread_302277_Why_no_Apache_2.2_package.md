---
title: "Why no Apache 2.2 package?"
date: 2006-11-18
forum: Server Platforms
---

### Post by dave uk on 2006-11-18
Hi

I have had a search for this but can not find any answers, why is there not an apache 2.2 package available for Ubuntu through apt-get?

As I understand, it was available well before Edgy shipped but still was not included. Is there a specific reason for this or was it a matter of a lack of time or something similar?

Cheers
Dave

---

### Post by emperon on 2006-11-21
I agree with you. IMO many people satisfied with the current version. Note that apache has tremendous amount of 3rd party libraries for its modules. When developers start building packages they have to consider packaging these modules as well. This could be the reason as well as the satisfaction with the current version.

Note that many apache gurus will recommend compiling the source code even if the packages are available. Having packages with package manager is a good thing. But when you lean to server side, you are brave enough to deal with the source codes  and the mess  that manual installation brings to your filesystem.

Frankly this is why linux has been week till these years. Programmers were so good that the better they are, the more manually they would like to do the things.

Anyway if we go back to apache, seriously developers should bring apache 2.2  to repos and I'll tell you why

Q: What is the best web application development framework ? 
A: Ruby on Rails

Q: What is the best practice to deploy your Rails applications to a production platform ?
A: Using Apache and Mongrel together so that Apache acts as a front end server, proxying and load balancing, and many instances of Mongrel runs the ruby code so that you have excellent scaling

Q: What do I need to use Mongrel with Apache ?
A: You need the proxy balancer module for Apache which is only available in  Apache 2.2+

In conclusion, in order to follow the best practice for the best development environment for web applications , we need Apache 2.2

Note :AFAIK, Apache 2.2 only works with subversion 1.4+ which is also not available in repos.

---

