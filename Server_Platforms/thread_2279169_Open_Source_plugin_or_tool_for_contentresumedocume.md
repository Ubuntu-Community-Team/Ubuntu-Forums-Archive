---
title: "Open Source plugin or tool for content/resume/document management and efficient searc"
date: 2015-05-21
forum: Server Platforms
---

### Post by radheshyam3 on 2015-05-21
I am novice to web-development and web tools.
I need to create a website which will have a lot of documents similar to resume. I will need to be able to perform efficient search from the documents based on keywords and other limitations like date etc. I will need to incorporate some intelligent search functionality later on so please suggest accordingly where I can update/edit/add the search functionality component/engine.
I am looking for some tool or plugin or component which is open source and can be used to easily to develop the necessary with my website.
Thanks.

---

### Post by cariboo on 2015-05-21
What have you tried so far?

---

### Post by TheFu on 2015-05-22
> **radheshyam3 said:**
> I am novice to web-development and web tools.
I need to create a website which will have a lot of documents similar to resume. I will need to be able to perform efficient search from the documents based on keywords and other limitations like date etc. I will need to incorporate some intelligent search functionality later on so please suggest accordingly where I can update/edit/add the search functionality component/engine.
I am looking for some tool or plugin or component which is open source and can be used to easily to develop the necessary with my website.
Thanks.

There are lots of different answers. Full text search capabilities will depend on the input file formats.  If you are a novice, I think you'll have trouble setting up some of the best search tools.
* **recoll** is amazing. It is like google for a desktop. You can connect it to a web-search with a little work.
* htDig is normal static website search. Doesn't work with databases.
* My friend Josh wrote this article: [http://www.linuxjournal.com/article/6652](http://www.linuxjournal.com/article/6652) - *How To Index Anything* which you should read about. [More details.]("http://joshr.com/src/docs/HowToIndexAnything.pdf")
* [http://swish-e.org/](http://swish-e.org/) - another indexing tool for websites.

Or you could go crazy with a full-on document management system like Alfresco. While alfresco is free, the average cost to customize the front-end for users is a few hundred $$$$K. It is an awesome enterprise-class software, but requires specialized knowledge to make it pur and end-users to appreciate it.

If you just want to pay for a product that handles all of this stuff, docuShare from Xerox is an amazing tool. Simple, does the job, and their text searching is great. 

Of course, you'll need to have librarians to carefully manage where documents are stored for any of these solutions - especially the simple web-search ones. Whatever you do, don't trust file attributes for any metadata and don't trust file system times for date information.

BTW, I worked in document management and publishing for about 6 yrs. If you don't have full-text search, you can forget it.

---

