---
title: "Idea for new HTML tag (parental filtering)."
date: 2008-07-21
forum: The Cafe
---

### Post by frup on 2008-07-21
I was just reading an article on Linux.com about a piece of software called guble or something that is a plug-in to firefox for parental filtering.

The review was rather negative and cited some important problems and it got me thinking that a lot of web filtering problems for children could be fixed in a simple way.

If the w3c were to accept a simple HTML tag that allowed a rating system similar to how movies are classified plug-ins and browsers could easily read it. Developers could have guidelines on how to rate their sites and the plug-ins browsers could have a number of options on how strict they are.

inactive... doesn't filter
moderate... trusts web-developers rating, blocks all no rated sites
strict... only allows ratings that have been verified by an online database. (developers could submit their sites)

This could be done with a tag in <head> either with a new tag eg <rating content="violence" age="r13" />
or <rating content="pornography">r18</rating>

The bit in between the tags could maybe be the message that is displayed when filtered out or possibly the plug-in/browser could handle that.

or through something like a meta tag

<meta name="PGR" content="cartoon" />

It would allow individual sites to take responsibility for their own content and stop a lot of false and broken filtering.

---

### Post by LookTJ on 2008-07-21
I still think a DNS filtering system(like OpenDNS) is much more efficient than HTML filtering tags.

But it's still a nice idea for the site owners being responsible for their content. :)

Edit: You know, now that I think about it. I think DNS+HTML tags could work nicely together. So you go to configure your filtering options on your DNS website. Then the DNS system will look for the tags before directing you to the page, if that content is blocked, it would redirect to a custom block message.

---

### Post by bruce89 on 2008-07-21
> **Taylor said:**
> But it's still a nice idea for the site owners being responsible for their content. :)

Therein lies the problem. People could leave the tag out, or rate things lower than it should be.

I think that the <meta> tag could do this anyway.

---

### Post by frup on 2008-07-21
> **bruce89 said:**
> Therein lies the problem. People could leave the tag out, or rate things lower than it should be.

I think that the <meta> tag could do this anyway.

That's why combining it with a peer reviewed online database during strict filtering would provide a good service for those who need it.

With out the tag people would just get blocked.

I do not think there would be many people who would intentionally put false ratings just to harm impressionable people. The tag being opt in would remove people who were indifferent.

I'd be willing to to think that government, education and business sectors would pay attention to this, especially if it had a combined backing of say yahoo, MS and google.

---

### Post by bruce89 on 2008-07-21
> **frup said:**
> That's why combining it with a peer reviewed online database during strict filtering would provide a good service for those who need it.

With out the tag people would just get blocked.


Have fun getting people to check the billions of Webpages out there.

---

### Post by frup on 2008-07-21
> **bruce89 said:**
> Have fun getting people to check the billions of Webpages out there.

So you have a free service where existing members confirm the rating of sites.

A paid service that places a site at the top priority for entry in to the database and then staff who have ultimate prerogative.

Well that's my thoughts on this used up.

---

### Post by LaRoza on 2008-07-21
Actually, there is a rating system for it already. I forget the exact name though...

---

