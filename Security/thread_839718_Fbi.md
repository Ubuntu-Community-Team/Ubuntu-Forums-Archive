---
title: "Fbi"
date: 2008-06-24
forum: Security
---

### Post by xlinuks on 2008-06-24
Hi,
I don't have a clue how to break sites and will never do that.

However I'm very curious, I noticed that they happily provide info about software that runs their site - why do you think they do that?
Just look at the source of the page and it tells they use Plone (it's open source so one could search for bugs):
```

<meta name="generator" content="Plone - http://plone.org" />

```
Besides, they seem not to care much about the page itself, for instance the description says just "the FBI home page." (notice the dot at the end, and no keywords like "crime", "wanted terrorists" or alike):
```

<meta content="the FBI home page." name="description" />

```
Their server tells it's name (apache) and so on, so I wonder why do they do it?
If this post violates something please just delete it, I'm not sure it's ok to discuss it.

---

### Post by lisati on 2008-06-24
It's "one of those things"  - a lot of people are unaware that whenever they visit a web site, their browser can provide information to where they were before..... 

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) is an interesting site which provides information about internet security.

---

### Post by Yuki_Nagato on 2008-06-24
The guy in this article is "white-hat" and has made his exploits public because he was paid to do it.

[U][http://www.computerworld.com/action/article.do?articleId=9087441&command=viewArticleBasic]("http://www.computerworld.com/action/article.do?articleId=9087441&command=viewArticleBasic")
[/U]
"Black-Hat" crackers do not need to make what they do public: they could be rolling all over the website right now.

This article

_[http://news.softpedia.com/news/Government-Also-Likes-Porn-72846.shtml]("http://news.softpedia.com/news/Government-Also-Likes-Porn-72846.shtml")_

just confirms that security is not high on their list of priorities.

---

### Post by p_quarles on 2008-06-25
Hiding details such as operating system, server software or database handling is known as "security by obscurity." This method has been repeatedly proven absolutely ineffective against any serious or determined attacker. 

So, the fact that a site tells you its running Plone says nothing whatsoever about how secure that site is.

---

