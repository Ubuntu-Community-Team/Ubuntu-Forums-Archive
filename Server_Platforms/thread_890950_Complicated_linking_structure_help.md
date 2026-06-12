---
title: "Complicated linking structure help"
date: 2008-08-15
forum: Server Platforms
---

### Post by adam35413 on 2008-08-15
I am currently running a website on a Ubuntu 7.10 box.  I am interesting in duplicating the code for the first website in a second website.  Obviously I could just copy the root directory to a new root directory and setup the Virtual Host for the new site, but that is a nightmare to maintain.  My goal is to minimize the duplicate files as much as possible, so I thought about symbolically linking the files.  For example, I have one website's root be:
/var/www/abccompany

and I want the new site to be:

/var/www/defcompany

They will have 90% identical code, with probably a dozen or so files different.  Is there a more efficient way of setting this up than doing this:
[LIST=1]
[*]Create the same directory structure of the first site in the root folder for def company.
[*]Link all the files in each of the sub directories of the old site into the correct directory in the new site..
[*]Remove the links for the files that need to change for the new site and create the file in the new site's directory manually.
[/LIST]

---

### Post by bodhi.zazen on 2008-08-15
What about putting all the common files in 

/var/www/common_files

And the unique files in 

/var/www/ABC

/var/www/DEF

Configure Apache to call common scripts (php, etc) from /var/www/common_files

I don not know if that will work for you, but it allows you to then add

/var/www/GHI and /var/www/JKL down the line ...

---

### Post by adam35413 on 2008-08-15
I would love to use a solution that I can scale to more sites.  However, how would I get apache to selectively pull files?  Here is an example:
 
/common_files: a.php, b.php, c.php, index.html, main.css

/FooCompany: Has a modified version of a.php and index.html

/BarCompany: Has a modified version of b.php and main.css

You are saying that I can setup apache to have both sites use the same c.php, but use their own copies of a.php and b.php?  If Apache can do this, what would this be called so I can look it up in guides/manuals?

---

### Post by adam35413 on 2008-08-16
Would aliases be something that could solve this?

---

