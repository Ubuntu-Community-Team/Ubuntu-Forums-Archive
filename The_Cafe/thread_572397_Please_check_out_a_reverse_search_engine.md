---
title: "Please check out a reverse search engine"
date: 2007-10-10
forum: The Cafe
---

### Post by scooper on 2007-10-10
Hi,

I've created an experimental "reverse search engine", called SiteSig for now.  If this is the wrong forum to post this, I'll gladly re-post in the Marketplace.  I'm not selling anything, and I think it may be of interest.

[SiteSig Reverse Search Engine]("http://sitesig.wijjo.com/")

Why a reverse search engine?  The [FAQ]("http://sitesig.wijjo.com/faq/") might explain it better.  But basically it helps you track down static content that disappears and wanders.  Kinda like a lot of OSS documentation does, except for Ubuntu of course. :)

For now, the best way to use it is at the moment you would save a bookmark to an interesting document.  While visiting the site, you could use the [SiteSig bookmarklet]("javascript:(function(){m='http://sitesig.wijjo.com/results/?url='+encodeURIComponent(document.location);w=window.open(m,'addTab','');setTimeout(function(){w.focus();},%20250);})();") to generate a Google search link, and bookmark that link in addition to, or instead of, the direct link.  The generated search is very tight, i.e. it typically places the very document you're looking for at the top of the search results.  It accomplishes this by performing a detailed lexical analysis of the document content.  The search terms are chosen to uniquely identify the document in Google's (or any other search engine's) database.

Eventually I'll be storing URLs and their generated searches so that documents can be re-discovered without needing to save the search up front.  E.g. if you get a 404 error you could visit SiteSig, plug in the URL, and get a saved search that will find it wherever it exists on the Web.  There might also be a browser extension that can automatically handle errors and track down the document.

Please let me know what you think.  There's a contact link in the About page, or PM me here.

Enjoy!
Steve

---

### Post by Namtabmai on 2007-10-10
While the idea seems sound I think you're going to run in to difficultly with dynamic site, or site with dynamically generated ad words.

For example take any news article from [http://news.bbc.co.uk](http://news.bbc.co.uk), almost half the content is dynamical generated (the right side bars) which your engine uses to pick out keywords. Perhaps a news site is a bad example due to how frequently it gets updated compared to how often google will index.

I tried it with a page from my blog;
[http://www.keyboardcowboy.co.uk/2007/10/01/web-frameworks-and-db-xml/](http://www.keyboardcowboy.co.uk/2007/10/01/web-frameworks-and-db-xml/)
And again it failed to create a link. One of the words it picked out is "canonical" which appears at the end of the recent posts list. So one more comment on my site and that word will get pushed off the page.

Perhaps it would be better to weight words that come from the description/keyword tags (assuming you don't already do this) as I can retrieve the BBC news article above by searching on the contents of the description meta tag.

---

### Post by scooper on 2007-10-10
> **Namtabmai said:**
> While the idea seems sound I think you're going to run in to difficultly with dynamic site, or site with dynamically generated ad words.

Yes, it definitely works better with static content.  I can tune it to filter adwords, etc.  It will need to get more complex in order to work better with more things.  In general, it's not meant to be a universal big deal, just something that can help a lot with certain types of content.  If there's a market, it might be more for companies and intranets.

We're just testing the waters to see if people find uses (and problems) we didn't think of.

Thanks for checking it out.
Steve

---

