---
title: "Any Database gurus?"
date: 2011-08-27
forum: The Cafe
---

### Post by greenwom on 2011-08-27
So I've been using, as in end user, mysql with a number of apps.  I've never had to create/design.  So know I'm a bit stuck in a design problem.

I'm trying to build a database for comparable Salaries and benefits. My organization and 15 to 20 others that need to be compared and tracked. 

The Data comes from contracts. The contracts are usually annual and the pay and benefits change year to year. There are two salary points and a number of variable stipends to track.

I know I need a table to define the organizations, then I need to break up the contracts into 30 some line items to define the data points. 

Then there is the date, year to year. 

So I'm stuck on the design, not sure what relationships and tables I should have to follow best practices. 

Once the data is in, custom queries to show percentage changes and pull reports on specific line item from contracts. 

So where do I begin in the design, any suggestions, examples, or a proper tutorial? I've been reading the docs and googling tutorials and the tech side makes sense. Just need help getting started with this level of complexity. 

I hope to make this into something I can share with our sister organizations in other states so any help or a finger in the right direction would be appropriated!

---

### Post by VH-BIL on 2011-08-28
I am not completely sure what tables you need. The comparing and reporting can be done once the database has the data using queries.

I think you need a 'organizations' table:
id, orgname, ...

Maybe a 'users' table:
id, fname, lname, ...

And a 'salary' table:
id, org_id, user_id, date_entered, salary_amount, ...

---

### Post by cprofitt on 2011-08-28
If you want drop me a line with the data fields... I could draft a design for you...  If you want to learn yourself...  [http://www.deeptraining.com/litwin/dbdesign/FundamentalsOfRelationalDatabaseDesign.aspx](http://www.deeptraining.com/litwin/dbdesign/FundamentalsOfRelationalDatabaseDesign.aspx)  [http://en.wikipedia.org/wiki/Database_design](http://en.wikipedia.org/wiki/Database_design)  FYI -- I have been doing DB design since 1990 when I started with Alpha 5.

---

### Post by greenwom on 2011-08-28
> **cprofitt said:**
> If you want drop me a line with the data fields... I could draft a design for you...  If you want to learn yourself...  [http://www.deeptraining.com/litwin/dbdesign/FundamentalsOfRelationalDatabaseDesign.aspx](http://www.deeptraining.com/litwin/dbdesign/FundamentalsOfRelationalDatabaseDesign.aspx)  [http://en.wikipedia.org/wiki/Database_design](http://en.wikipedia.org/wiki/Database_design)  FYI -- I have been doing DB design since 1990 when I started with Alpha 5.

I'll take you up on that, I'll gather my notes into a post.  I'll also be reading through your link thank.  I do need to learn more about this.  As a end user with many CMS systems, I'm finding need to create my own database products for different projects, so I'm motivated.  thanks

---

