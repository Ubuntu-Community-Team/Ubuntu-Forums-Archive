---
title: "Advice about database"
date: 2009-09-22
forum: Server Platforms
---

### Post by mgchan on 2009-09-22
I'm working on setting up a database server for a research project, and considering Ubuntu as I've had pretty good results using the desktop versions on my own laptops and it will help keep our costs down.  Basically, I'll be dealing with a large number of images, each with its own meta-data, and other layers of information about each of those images (or sets of images).

I'd like to be able to run a query - find me all images fitting these criteria - which of course I know SQL can do.  We'll probably want to interface with the web, which I think php will be fine.  However another requirement is expandability in adding a lot of images, grouping these images and having information specific to those groups (e.g. group A will have features 1, 2, and 3, while group B will have features 4, 5, and 6), as well as being able to add new "features" (i.e. start with a list of 100 images with 5 features each, then dynamically add 5 more features and 200 more images).

The last thing is what I'm most unsure about - is there any issue with adding more information (e.g. columns in an excel sheet) to a MySQL database?  I'd assume so, but I've had other programs that required long conversions of databases which makes me wonder how dynamic a database can be.

Just to help explain, we did consider using Amazon's SimpleDB, because it offers the following:
```
Flexible &#8211; With Amazon SimpleDB, it is not necessary to 
pre-define all of the data formats you will need to store; simply add 
new attributes to your Amazon SimpleDB data set when needed, and the 
system will automatically index your data accordingly. The ability to 
store structured data without first defining a schema provides 
developers with greater flexibility when building applications, and 
eliminates the need to re-factor an entire database as those 
applications evolve.
```
Thanks for the help.

---

### Post by John Cheng on 2009-09-22
A relational database such as MySQL and PostgreSQL can be very dynamic. For example, you can represent a picture as a single column on a "picture" table, a separate table called "picture_feature", then join them such that one picture can be associated with many features. 

I would say that it sounds like you have very little experience with databases, so learning a RDBM (again, such as MySQL or PostgreSQL) might get in the way of "actual project stuff", so be careful with your choice. However, ultimately I don't think you can go wrong with either.

---

### Post by Ozitraveller on 2009-09-22
Or a simpler (maybe) solution might be something like these

[http://www.openoffice.org/product/base.html](http://www.openoffice.org/product/base.html)

[http://www.koffice.org/kexi/](http://www.koffice.org/kexi/)

---

### Post by mgchan on 2009-09-22
Great, that's the kind of info I needed to know.  I realize it will be a limitation on my part - I am pretty good with programming and scripting but have been away from computers for a while.  Most likely I'll just need to set up the basics, and will have plenty of help.

Regarding the KOffice and OO.o options, the reason we wanted to go with something more of a low level database is because we eventually want to have things set up where images are automatically scanned when added to the server, and added to the database.  To give you an idea of the scale of images here, we are working with CT scans and MRIs of patients - where each study may contain several thousand images that all need to be indexed and easily searchable using a variety of tools.  In my experience (at least with Access) these databases tend to break down either in their memory limits or speed when they reach a certain size.  Our initial data set has at least 800k images with another set that is larger that would be added shortly thereafter.

---

### Post by openfly on 2009-09-22
I highly recommend PostgreSQL.  It sees huge usage in academia... lots of people use it because its the opensource alternative to oracle.  As a result it has a lot of very cool custom data structures and compilable triggers available for it that make it one of the best research databases on the planet.

---

### Post by John Cheng on 2009-09-22
> **openfly said:**
> I highly recommend PostgreSQL.  It sees huge usage in academia... lots of people use it because its the opensource alternative to oracle.  As a result it has a lot of very cool custom data structures and compilable triggers available for it that make it one of the best research databases on the planet.

And PostgreSQL has a lot of commercial use as well! We've been using PostgreSQL in our commercial product for the last 4 years, and I've been very happy with it in terms of performance, features, and support (from the mailing list). Also, PostgreSQL does have a very useful full-text indexing/searching feature that might be useful for a project like this. Of course, my Postgres advocacy might be taking this post off subject... my point is that you won't go wrong with a relational database!

---

