---
title: "More Resources / Database"
date: 2012-11-20
forum: Ubuntu Application Development
---

### Post by Dan Again on 2012-11-20
So, two questions, really...

[LIST]
[*]What are your recommendations for Ubuntu application development resources? The YouTube video on the Ubuntu website was a great start, but I'm looking for some more in-depth information.
[*]What is the best tool to maintain persist data for an Ubuntu application. Let's say, for instance, that I was writing an app to keep track of a baseball card collection; what is the best tool to use to maintain this data? I'm assuming it will be some sort of database system, but I'm just wondering which is the preferred/recommended for beginner Ubuntu developers.
[/LIST]

Thanks!

---

### Post by oldfred on 2012-11-20
If doing a list or collections:

       Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[http://www.gcstar.org/](http://www.gcstar.org/)

    
But if you just want a database to build your own there are many. 
The two most popular
       MySQL or PostgreSQL
       
 [http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL](http://www.wikivs.com/wiki/MySQL_vs_PostgreSQL)
        
And with python and some others you can use sqlite. Firefox & Thunderbird use sqlite for storing most of your data.
[http://www.sqlite.org/](http://www.sqlite.org/)

---

### Post by Dan Again on 2012-11-23
Thanks for the suggestions! Maybe I was being a little specific with my question. I guess I'm just wondering, in general, what is the best way to maintain persistent data for applications? I'm totally new to Ubuntu application development. Is storing data in an XML file and just reading it in every time the app starts an acceptable solution?

---

### Post by oldfred on 2012-11-23
I have not seen a definitive answer. And I think it depends on how much data, and what type of data. Some even suggest that text files can work. 

I have seen a few Linux apps convert to a DB for settings, then convert back to text or XML. 

But lots of data and where Codd's rules would eliminate duplication of data, then a database makes sense.

---

