---
title: "Facebook code leaked onto internet ... does it matter?"
date: 2007-08-14
forum: The Cafe
---

### Post by aysiu on 2007-08-14
[Facebook code leaked onto internet](http://www.cbc.ca/technology/story/2007/08/13/tech-facebook-code.html)

> The breach of the code, first reported by technology website TechCrunch, raises questions about the level of security on a website where users post personal information.

In theory, access to code from a website could provide computer hackers a chance to look for potential loopholes to exploit. But Facebook downplayed the significance of the code leak. Isn't this sort of like criticizing open source? Or does having access to the source code of a website (as opposed to normal software) actually pose a security risk?

The reasoning seems similar to a lot of anti-open source FUD.

---

### Post by 23meg on 2007-08-14
[QUOTE=aysiu]Or does having access to the source code of a website (as opposed to normal software) actually pose a security risk?[/QUOTE]

It can. The code that was revealed was part of the software that generates the web pages that one views on Facebook, not of the pages themselves, which is already open, like in any web page.

---

### Post by proalan on 2007-08-14
Like the article stated, it was a misconfiguration NOT a security exploit.

I seen the code that was published in the blog in question and seen little that suggests that it could be exploited as most of the authentication stuff was defined elsewhere. All I saw was php code generating the home page layout with numerous placeholders for adverts. 

Having said that any system can be broken into given enough resources, time and effort regardless of being open source or not.

---

### Post by original_jamingrit on 2007-08-14
Most hackers, even ones with bad intentions, couldn't really care much about people's personal information unless they were being paid by a company to search for it.  People would be more likely to look at the code and send Facebook the necessary fixes.

I wouldn't think that an open source project would be the same, because that would require the writers of the code to notice a security hole before simple viewers of the code could.  And people are encouraged to proofread code for FOSS projects.

---

### Post by tcpip4lyfe on 2007-08-14
[http://albumoftheday.com/facebook/](http://albumoftheday.com/facebook/)

That's what they want us to think!  :P

---

### Post by Tomosaur on 2007-08-14
If the developers of the website (the stuff that goes on under the hood) were conscious of security and that something like this could happen in the future, then a leak like this should not pose a security risk. It's been proven time and time again that security by obscurity doesn't work. You can't protect something by hiding it - eventually something like this happens and if the code is insecure-by-design, then you'll have problems somewhere down the line.

Fortunately for Facebook, it seems like their developers know what they're doing.

---

### Post by cunawarit on 2007-08-14
> **aysiu said:**
>  does having access to the source code of a website (as opposed to normal software) actually pose a security risk?

I managed to find the one place where a commercial CMS was vulnerable to SQL injection attacks partly because I had access to the source.

Obviously the site SHOULD be secure even if you know exactly how it works, security by obscurity is not security. 

PS: The commercial CMS got fixed after I reported the issue.

---

