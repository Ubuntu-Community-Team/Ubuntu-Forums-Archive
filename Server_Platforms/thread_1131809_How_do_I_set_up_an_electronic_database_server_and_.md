---
title: "How do I set up an electronic database server and search engine?"
date: 2009-04-21
forum: Server Platforms
---

### Post by amylase on 2009-04-21
If I have 10,000 journal articles in electronic forms (eg. PDF, TIFF or Djvu), how do I set up my Ubuntu computer as a server to host all of these articles and allow people to log on using some sort of client and perform searches via a search engine?

What would be some open source applications that I will need to achieve above? (ie. set up a server to host lots of e-journals; set up a search engine for people to search on my server) and how?

Thanks very much.

---

### Post by techstop on 2009-04-21
You might want a document management system such as;

Alfresco
[http://www.alfresco.com/products/dm/](http://www.alfresco.com/products/dm/)

...or

Knowledgetree
[http://www.knowledgetree.com/products](http://www.knowledgetree.com/products)

Neither of these are in the repos though, so you will need to install manually.

---

### Post by BkkBonanza on 2009-04-21
Certainly those two solutions seem comprehensive and have comprehensive prices too. For many businesses I'm sure the price is acceptable.

If you are looking for a simple solution with free tools then you can do quite a bit easily with mysql and php. It isn't hard to create a database of documents and store them in mysql as text objects. You can add columns for any attributes you want to search on and mysql does have a decent text search engine. I used it once for emails and searched 300 MB of text in a few seconds. There is ways to optimize it as well. This requires you to spend time doing some custom search forms and php code with a few sql queries but it is a simple and custom approach if that's the goal.

I'm sure there must be other packages out there in the middle ground. Free but pre-built solutions. Maybe even look at using google to handle site search of content - if you're ok with the info being public.

---

### Post by techstop on 2009-04-21
> **BkkBonaza said:**
> Certainly those two solutions seem comprehensive and have comprehensive prices too. For many businesses I'm sure the price is acceptable.

For both applications I linked to, there is a free download;

Alfresco, the free version is called "Labs"
[http://wiki.alfresco.com/wiki/Installing_Labs_3](http://wiki.alfresco.com/wiki/Installing_Labs_3)

KnowledgeTree - Community Edition
[http://www.knowledgetree.com/try-now/knowledgetree_open_source_download](http://www.knowledgetree.com/try-now/knowledgetree_open_source_download)

---

### Post by estyles on 2009-04-21
I don't have any recommendations on an *electronic* database server and search engine, but I do have some suggestions for a mechanical db server and search engine...  See, if you attach each journal document to a wooden stick, and then put several different length notches in different positions (like a key or a keyhole) on each stick to represent the content of the article, then the user sets some toggle switches on the control panel which raise or lower corresponding notches on the "server", which is like a miller's wheel, and then the user turns the crank to spin up the server, and it should be possible to build it so that the wheel only catches on the data sticks that have the right notches on them, and then it will pull those journals out onto the wheel, and as it keeps spinning, the server wheel will pass the correct documents in front of the user for perusal.

You might even be able to get a monkey to do the spinning.

Sorry, couldn't resist...

---

### Post by amylase on 2009-04-22
Thanks for the recommendations. I found Greenstone which is an open source project by university in New Zealand. It serves my purpose.

About the wooden stick proposal, is there a name to that mechanical system? I am actually writing an article on the evolution of databases. The mechanical one sounds like a good starting point.

---

### Post by estyles on 2009-04-22
> **amylase said:**
> Thanks for the recommendations. I found Greenstone which is an open source project by university in New Zealand. It serves my purpose.

About the wooden stick proposal, is there a name to that mechanical system? I am actually writing an article on the evolution of databases. The mechanical one sounds like a good starting point.

I'm reasonably sure it doesn't exist - it was just a stupid joke...  :(

---

