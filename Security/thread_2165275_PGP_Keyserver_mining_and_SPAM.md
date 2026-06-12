---
title: "PGP Keyserver mining and SPAM"
date: 2013-08-04
forum: Security
---

### Post by martinr on 2013-08-04
I'm contemplating to get my PGP public key signed, but I have the following concerns. (Way) in the past I was active in some (usenet) newsgroups. Back then it was normal to include one's email address in the from field of the postings for private responses. Years later I came to regret this very much, because spammers came up and harvested the old newsgroups for email addresses. After a while I got so much junk email (600+ messages a day), that eventually I had to close down my email account.

Now I'm weary about getting my public PGP key signed. After reading [this thread]("http://ubuntuforums.org/showthread.php?t=1717049&p=10623540#post10623540") and doing a lot of follow up reading. I got the following impression:

I think the whole PGP Web of Trust (WoT) model is at risk of 
1) email address harvesting and 
2) exposing your trusted social network.

Technically email addresses can be harvested from the public keys, certificates and key chains that are stored at key / certificate servers. You don't even have to be the person to upload your key. If somebody else uploads their key, which you signed, your information is also exposed (see [mining-pgp-keyservers]("http://cryptome.org/2013/07/mining-pgp-keyservers.htm")).

Furthermore the social network of people one trusts (via other's keys one has signed) is exposed, which opens you up to a whole other category of threats (from social engineering to implication by association in totalitarian regimes for example, etc.).

If you don't provide your real name or email address, it leaves the purpose of a certificate somewhat useless. The model seems to be broken. 

Another model that addresses the two privacy concerns described above somewhat better, seems to be certification by a trusted third party like a Certificate Authority (CA).

Should one not add one's email address in a key (which renders it kind of useless for email signing)?
Should one not add one's real name in a key (which renders it kind of useless for identification purposes)?
How should one sign repository commits without exposing one's email address to spam?
How can these concerns be addressed and what are the implications of that?

Very little seems to have been written about these privacy concerns about a technology that was invented to enhance privacy.

What are your views about this?

---

### Post by ottosykora on 2013-08-06
Yes sure it is possible to harvest addresses from pgp key server, but it is not very efficient and so far as long as those servers are operated and free accessible to everybody there were apparently no real signs of harvesting addresses from it.
I have number of addresses of mine on my keys, all of them are in fact active and some not used any more much. Some of my keys exist since early 90ties and their included addresses as well. I still have no grow of spam on those addresses.

---

### Post by martinr on 2013-08-07
> **ottosykora said:**
> Yes sure it is possible to harvest addresses from pgp key server, but it is not very efficient and so far as long as those servers are operated and free accessible to everybody there were apparently no real signs of harvesting addresses from it.
I have number of addresses of mine on my keys, all of them are in fact active and some not used any more much. Some of my keys exist since early 90ties and their included addresses as well. I still have no grow of spam on those addresses.

Hi ottosykora, thanks for your reply.

To get things clear, are you saying because it is not being taken advantage of right now, one might just as well put their email address out there for grabs?

I learned my lesson well in the past with usenet news. If something is possible it eventually will be done.

Are there any alternatives and what would be the consequences of them?

---

