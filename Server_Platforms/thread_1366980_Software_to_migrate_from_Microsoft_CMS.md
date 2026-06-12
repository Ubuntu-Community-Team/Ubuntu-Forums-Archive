---
title: "Software to migrate from Microsoft CMS?"
date: 2009-12-29
forum: Server Platforms
---

### Post by halfthelaw on 2009-12-29
Hello,
Is anyone aware of software to migrate content from Microsoft CMS 2001/2002 to some sort of open source LAMP or LAMP like stack? I believe it should be theoretically possible, since content is stored in an SQL database, with formatting templates exportable as XML. However, I've not been able to find a suitable tool :( Any help or suggestions would be appreciated, apologies if this is in the wrong forum.

Thanks,
Law/2

---

### Post by michaelzap on 2009-12-29
Info and a list of tools here:
[http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html](http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html)

But first you'll need to choose a MySQL CMS that you want to use instead, since just converting the data to MySQL won't automagically format it into the tables that the new CMS uses. You'll need to do that conversion one way or another, and you'll need to have decided what the final database structure will be before you get started. If I were doing this I would probably just cut and paste into the new CMS if I had only a few (<50) web pages to migrate, and I'd use a text editor with a good search and replace tool to import the data into MySQL in the proper tables and formats if I had a lot of data to import.

I highly recommend MODx CMS, but there are other good PHP/MySQL CMS programs out there (check out opensourcecms.com).

---

### Post by halfthelaw on 2009-12-29
Given the size of the site I need to migrate, a cut-and-paste solution is simply not feasible.
The conversion of data from one db to another is not what I'm after per se. Rather, I'm looking for a wholesale migration tool, especially including templates. Obviously templates are more programmatic in nature than simple content, so converting them requires more than copying over, but translation into the language of the new CMS.
I'm not particular about which CMS I use. At this point, any CMS that can automagically import an MCMS site basically wins instantly.

---

### Post by Vegan on 2009-12-29
I have seen several people come to my shop with this exact problem as we use Linux and Windows together.

The problem is that you are using a complicated setup that would require a fair bit of work to migrate into a new platform.

I like PHP as its ported everywhere and its free. Microsoft has not been so open.

---

### Post by michaelzap on 2009-12-29
> **halfthelaw said:**
> Given the size of the site I need to migrate, a cut-and-paste solution is simply not feasible.
The conversion of data from one db to another is not what I'm after per se. Rather, I'm looking for a wholesale migration tool, especially including templates. Obviously templates are more programmatic in nature than simple content, so converting them requires more than copying over, but translation into the language of the new CMS.
I'm not particular about which CMS I use. At this point, any CMS that can automagically import an MCMS site basically wins instantly.

If this is a website, then the content will likely be (X)HTML. That should be easy enough to migrate to whichever CMS you decide to use. If by "templates" you are referring to (X)HTML layouts (not ASP or other programming code), then that should also be relatively straightforward.

I have no idea what MCMS' database structure, placeholder tags, etc. are. Most of the support links that I just tried to check out return Page Not Found errors. So you're going to have to investigate that and figure out how to map from it to your new CMS, since I doubt you're going to find anything that just converts it all for you effortlessly.

Start by getting an export file in SQL text format. You can probably just convert the relevant sections of this file to use the syntax and structure of your new MySQL CMS. I just use Geany's find and replace tool to do things like this all the time, and you'd be amazed how quickly you can convert between alien systems with a little forethought and patience.

---

