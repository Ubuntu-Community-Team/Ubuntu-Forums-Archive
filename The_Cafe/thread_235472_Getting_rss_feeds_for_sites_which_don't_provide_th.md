---
title: "Getting rss feeds for sites which don't provide the option"
date: 2006-08-13
forum: The Cafe
---

### Post by Mishal on 2006-08-13
How do I get feeds from let's say:
[http://www.gregmankiw.blogspot.com/](http://www.gregmankiw.blogspot.com/)

Notice that there's no provision for feeds from the above blog. Is there a way out? I use Liferea by the way...
[http://sourceforge.net/projects/liferea/](http://sourceforge.net/projects/liferea/)

---

### Post by bjweeks on 2006-08-13
gregmankiw.blogspot.com/atom.xml?

---

### Post by Mishal on 2006-08-13
Great. Thanks! But will this work for any blog site or in fact ANY website?

Let's say [http://www.thedailystar.net/](http://www.thedailystar.net/) This is the site for of the newspaper in my locality. The site does not offer feeds at all. And it's not a blog site. So is it possible to get feeds from there?

Thanks :)

---

### Post by bjweeks on 2006-08-13
Nope, the site has to offer a feed. You should get the little feed icon in firefox if a site offers a feed.

---

### Post by blackened on 2006-08-13
It's possible to scrape the html page using wget, then reformat the html into rss compliant xml using a bash script. The problem is that it would be site specific.

---

### Post by Mishal on 2006-08-13
I am not exactly an expert at bash scripts neither do I have a clue how to reformat the html into rss compliant xml. So I think I will let that go :)

Anyway, thanks people!

---

### Post by ice60 on 2006-08-13
hi, the feed is in the address bar, at the very right side, the orange thing.

[http://gregmankiw.blogspot.com/rss.xml](http://gregmankiw.blogspot.com/rss.xml)

or

[http://gregmankiw.blogspot.com/atom.xml](http://gregmankiw.blogspot.com/atom.xml)

OK now i see what the problem is (i'm using Opera which lets you edit the feed so you can see the urls) maybe you can use an RSS extension if you're using Firefox??

---

### Post by blackened on 2006-08-14
> **ice60 said:**
> OK now i see what the problem is (i'm using Opera which lets you edit the feed so you can see the urls) maybe you can use an RSS extension if you're using Firefox??

Firefox adds an icon to the right side of the urlbar when a feed is available.

---

### Post by WildTangent on 2006-08-14
> **blackened said:**
> Firefox adds an icon to the right side of the urlbar when a feed is available.

Only if the appropriate meta take is added. A site could have the feed, but doesn't use the proper code to "advertise" it.

-Wild

---

