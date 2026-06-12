---
title: "Web Server development suggestions, please."
date: 2013-09-06
forum: Server Platforms
---

### Post by schema2 on 2013-09-06
I am new to web server dev. I set up a local server with ubutnu server. I've installed LAMP settings with phpmyadmin and webmin. My goal is to have a nice environment to practice programming, hosting, and protocol. Now that I have my server set up, where do I go from here? What are some suggestions? I would like to start learning how to write apps, web pages,  and how to manage data on the backend. Specifically, among other things, I would like to focus on programming a sql database and being able to query it from a php app on the server. How do I get started doing this and what additional software will I need? Any other suggetions regarding server development for beginners would be appreciated.

---

### Post by Bucky Ball on 2013-09-06
*Thread moved to **Server Platforms**.*

Welcome. You may well have more luck here for the moment as you are looking for server directions for now rather than programming support directly.

All the best with it. ;)

---

### Post by CharlesA on 2013-09-06
What sort of code do you want to learn? I took a class on HTML5 and CSS in school, but I've been using this site: [http://www.codecademy.com/](http://www.codecademy.com/) to learn some more PHP and JavaScript.

---

### Post by houstonbofh on 2013-09-06
First, if this is Internet facing, either remove phpmyadmin, or change the path.  Look in your access and error logs to see why...

Next, build a website.  Break it a few times and fix it.

---

### Post by SeijiSensei on 2013-09-07
Your question is much too broad to be answerable here, but my first suggestion is to find a specific task that you would like to try to implement.  The first time I used PHP and an SQL database (PostgreSQL for me), I was building an address directory to attach to a web site I had previously written for my college reunion class.  Having a specific project helped to focus my mind on what was involved.

However I strongly recommend you dump phpmyadmin and start teaching yourself how to write SQL using the mysql or psql command-line clients.  If you want to understand how to write SQL-based applications, you need to learn SQL and not have some graphical client generate the code for you.  I'd start by creating a small database in a spreadsheet program, then saving the data and loading it into an SQL database.  Then teach yourself how to run SELECT queries with WHERE clauses like this:

```
select * from myfriends where lastname='Jones' and firstname='Shirley';
```

Then try some INSERT and UPDATE commands.  After that you can write a couple of simple PHP scripts to run those queries and display the results.

Expect to spend at least a few person-weeks on just simple tasks like these if you have no experience with SQL or programming.  If you've written programs in a procedural language like Python or perl before, you'll find the PHP part less daunting than the SQL part.  If you're starting from scratch, I suggest using PostgreSQL rather than MySQL. Postgres [conforms]("http://www.postgresql.org/about/") more closely to the SQL standards than MySQL, so what you learn will be more transferable to other SQL databases like Oracle or MS-SQL.  I once had to write an application that queried an Oracle DB and found the syntax pretty similar to what I was used to from using Postgres.

---

### Post by CharlesA on 2013-09-07
I did my SQL class using MSSQL, but I prefer MySQL/MariaDB (but PostgreSQL is good too!). I've found the syntax is similar between MS SQL and MySQL, but they are a little bit different when it comes to actually working with them.

---

### Post by schema2 on 2013-09-07
> **SeijiSensei said:**
> Your question is much too broad to be answerable here, but my first suggestion is to find a specific task that you would like to try to implement.  The first time I used PHP and an SQL database (PostgreSQL for me), I was building an address directory to attach to a web site I had previously written for my college reunion class.  Having a specific project helped to focus my mind on what was involved.



That is sort of my dilemma. My local server doubles as a lab. I haven't an actual reason for a server, I don't plan to make it live. I just need an environment to write the code, dissect it, understand how it works. I was asking for ideas because I lack the creativity to develop anything of my own. I was hoping someone could offer up some ideas on what to do.

---

### Post by schema2 on 2013-09-07
> **CharlesA said:**
> What sort of code do you want to learn? I took a class on HTML5 and CSS in school, but I've been using this site: [http://www.codecademy.com/](http://www.codecademy.com/) to learn some more PHP and JavaScript.

Well I've mastered the markup languages and client-side scripting. I sort of skipped programming- C and Assembly. I am trying to move in to server-side langages and app languages now but I honestly don't know how to get started. I lack the "vision" to undertake an original project. Creating a database and php apps to query it was the only thing I could think of to get started with.

---

### Post by schema2 on 2013-09-07
I don't believe it is. My server is hosted on VM, no ports forwarded on the router. I don't believe it is accessbile outside of my network. I will remove phpadmin but I am new to this so I owe it to myself to ask why?

---

### Post by tgalati4 on 2013-09-07
There are vulnerabilities to leaving PHP open to the outside world.  As a next step, install a Content Management System (like Drupal).  Understand how it works and dig into the programming.  [http://drupal.org](http://drupal.org)

Put on some white gloves if you want to practice protocol.

---

### Post by CharlesA on 2013-09-07
> **schema2 said:**
> I don't believe it is. My server is hosted on VM, no ports forwarded on the router. I don't believe it is accessbile outside of my network. I will remove phpadmin but I am new to this so I owe it to myself to ask why?

I think tgalati4 covered it pretty well. I try to not use web frontends on anything that is publicly accessible.

I know a lot of shared hosts use things like cPanel and phpmyadmin for administration because the user does not actually have root access to the servers. I see it as a convenience that adds extra risk to your server. Of course with that being said, I do use Roundcube for accessing my mail on the go, but I make sure I keep it patched.

> **tgalati4 said:**
> There are vulnerabilities to leaving PHP open to the outside world.  As a next step, install a Content Management System (like Drupal).  Understand how it works and dig into the programming.  [http://drupal.org](http://drupal.org)

Put on some white gloves if you want to practice protocol.

+1. A friend of mine swears by Joomla!.

---

### Post by sandyd on 2013-09-07
> **CharlesA said:**
> I think tgalati4 covered it pretty well. I try to not use web frontends on anything that is publicly accessible.

I know a lot of shared hosts use things like cPanel and phpmyadmin for administration because the user does not actually have root access to the servers. I see it as a convenience that adds extra risk to your server. Of course with that being said, I do use Roundcube for accessing my mail on the go, but I make sure I keep it patched.



+1. A friend of mine swears by Joomla!.

If you
a) setup phpmyadmin/admin panels on _seperate_ ports
b) ip-restrict them with either iptables/csf so that they can only be accessed from certain ip addresses/vpn
there is nothing to worry about

There are also lots of other CMSes (sorry, I do swear by joomla...), which sometimes may be more useful for smaller sites, Wikipedia produces a nice [list]("http://en.wikipedia.org/wiki/List_of_content_management_systems")

---

### Post by Kevin_Arnold on 2013-09-07
I love Drupal (I'm a Drupal dev at work) but it adds a lot of framework on top of normal PHP/MySQL. I think it is good to learn how the basic stuff works before slapping frameworks on top of it.

I'd follow this guide: [http://www.w3schools.com/php/](http://www.w3schools.com/php/)  It steps you through everything including MySQL towards the end. Then, just decide to create some simple web app. I'd do a company phone directory or something, where you have first name, last name, department and extension. Once you can get that stuff to display, you can start adding filtering and searching. Then you can add an administration screen to add new entries, etc. Just start small and keep adding features until you understand it all.

---

### Post by CharlesA on 2013-09-07
> **sandyd said:**
> If you
a) setup phpmyadmin/admin panels on _seperate_ ports
b) ip-restrict them with either iptables/csf so that they can only be accessed from certain ip addresses/vpn
there is nothing to worry about


+1.

---

### Post by schema2 on 2013-09-09
> **tgalati4 said:**
> There are vulnerabilities to leaving PHP open to the outside world.  As a next step, install a Content Management System (like Drupal).  Understand how it works and dig into the programming.  [http://drupal.org](http://drupal.org)

Put on some white gloves if you want to practice protocol.

thanks

---

### Post by schema2 on 2013-09-09
thank you for the responses.

---

