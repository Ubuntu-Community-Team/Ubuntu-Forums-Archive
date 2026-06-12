---
title: "Which database would you suggest?"
date: 2007-01-06
forum: Server Platforms
---

### Post by Eastex Cruiser on 2007-01-06
Which would be better for my situation: MySQL or Firebird? I'm wanting to setup a database server to be shared among a max of 6 people at a time. Primarily we're interested in managing equipment resources out on pipeline jobs. My only experience with databases is Microsoft Access, in a local environment. I've never networked Access.

I'll be running the database app on Ubuntu 6.10 with the GUI installed. I tried running the server version minus the GUI and I was lost. Reminds me of why I never really got into computers until Windows came along (for the record, I'm an Ubuntu convert at home!).

Also, would I be correct in thinking that I could use MySQL, Firebird, or other alternative RDBMS's, and then use MS Access or OpenOffice.org as a front end, provided I have the right drivers? 

For the record, I have absolutely no experience with SQL statements, programming in Pearl, PHP or any other language other than Basic on an old Texas Instruments TI99/4A, and that was back in 1987. I'm a pretty quick learner, but with all the information that's out there, it's hard to know which path to take.

---

### Post by tturrisi on 2007-01-06
mysql is probably the most robust & versatile opensource dayabase around.  But you will need to know some scripting language to be able to easily use it via a gui.  phpmyadmin can be used to setup your databases and tables via web browser forms and is wasy to use.  You'll need to do a little reading here & there.  The simplest solution would be to install apache2, php5, phpmyadmin and mysql-server, then browse some of the freeware php scripting sites and download a suitable already built application that runs in the web browser.  Look here for free scripts, there are thousands and I'm sute you'll find exactly what you need:
[http://www.scriptsearch.com/PHP/Scripts_and_Programs/](http://www.scriptsearch.com/PHP/Scripts_and_Programs/)
[http://www.hotscripts.com/PHP/Scripts_and_Programs/index.html](http://www.hotscripts.com/PHP/Scripts_and_Programs/index.html)
[http://php.resourceindex.com/Complete_Scripts/](http://php.resourceindex.com/Complete_Scripts/)
[http://www.tqnyc.org/tutorial/mysql/](http://www.tqnyc.org/tutorial/mysql/)
[http://www.itc.virginia.edu/desktop/web/database/inventory/display/home.html](http://www.itc.virginia.edu/desktop/web/database/inventory/display/home.html)

---

### Post by kebes on 2007-01-06
MySQL is a good choice. There are many options for interacting with it, which is nice. You can set up "MySQL Browser" to run queries, and "MySQL Administrator" to manage the database.

Also very nice is to setup "phpmyadmin" (requires a web server and PHP to be installed), which is a web-based interface to MySQL databases. If you don't have much experience with databases, this can be a real timesaver. And of course you can interact with MySQL on the command line, or query it using your web scripting language of choice (PHP, etc.).

And note that all of the above ways of interacting with it work from the local computer or any remote computer (with the appropriate port opened, of course). So for simple things you can have a MySQL Browser on each client computer, and then just open the database, change a value, and you're done. MySQL Browser is a nice spreadsheet-like interface.


Of course if you need to "protect" the users from the raw structure of the database you can write web pages that provide controlled access. I know that the OpenOffice database program can also interface with MySQL databases (and so can the Spreadsheet and Writer I think). I'm not sure how easy it would be to have MS Access open a MySQL connection (never tried).

Hope that helps.

---

### Post by Brazen on 2007-01-07
As said, MySQL is your best choice.  It is hands down the most supported database on Linux, and for good reason.

Yes you can connect MS Access to MySQL.  Basically you'll have to install the ODBC driver and then link Access tables to MySQL (not sure on the terminology Access uses for this, but I had done it before, knowing nothing about Access or MySQL at the time).

You will need to be sure tcp port 3306 is open in your firewall (if you use one) in order to access MySQL from outside the local box.  I believe their is also a change you will need to make in the my.cnf also.  There is some option called bind or bind-address that you just need to comment out (put a # in front of it).

People love phpMyAdmin, and so do I.  As stated, you'll need a webserver with php installed to use it.  This webserver does not need to be on the same box as the MySQL server, but that would be the easiest thing to start out with.  I myself have a separate Apache server and a separate MySQL server, and phpMyAdmin is set up to connect to the remote MySQL server.

---

### Post by Eastex Cruiser on 2007-01-07
If MySQL is the way to go, then what's everyone's opinion of XAMPP? I actually managed to get it to work, though I knew not what to do with it. I've read in some instances security might be an issue. Not sure if there is a problem once you've installed the "security" add-on. I mention XAMPP, because I tried the LAMP inclusion in Ubuntu and I was lost on what to do with it. I'm thinking maybe I just didn't dive deep enough, not certain I was taking the right path. 

Another quick question regarding my server. Currently our router assigns IP addresses. Am I correct in thinking that I need to assign it a static IP? And if so, can I just do this in Ubuntu, or do I need to assign it through the router?

I really appreciate the input you are giving me. Great forum!

---

### Post by gaebriel on 2007-01-07
Have you considered using Derby/JavaDB? Cross-platform, plenty powerful for what you're talking about, embedded or network accessible, and easy to work with. I just started using it a couple weeks ago for a couple of apps I'm developing and it's working great. Check out [http://developers.sun.com/prodtech/javadb/]("http://developers.sun.com/prodtech/javadb/"). 

For what it's worth. :)

---

### Post by deRusett on 2007-01-07
Ok,  first let it be known,  my experince with Xampp was only with Windows.

I found Xampp to be great for a quick WAMP set up.  if nothing else needs to be connected to it then it is great.  if you want to run a basic LAMP set up and not worry about .net or .jsp  I say Xampp is a great easy toy,  much nicer then "WAMP" for windows based computers.  Xampp makes it easy to secure some of the silly things you can forget.  it would be a good intro to webserver set up I would think.  especially in linux which I am discovering is a little more challenging then windows.

---

### Post by kebes on 2007-01-07
There's nothing wrong with XAMPP. I've used it on Windows because it's so easy to get up-and-running. However on linux I must admit I prefer a standard LAMP stack. Setting up LAMP in Ubuntu is quite straightforward (and I'd be happy to help, of course).

As for the IP issue... if access will always be within the local network, and you have the ability to set static IPs then this is indeed the easiest way to do it. Just set your server (with MySQL) as 192.168.0.100 (or whatever) and then all the other computers will just be hardcoded to look for that internal IP. To accomplish this depends on the router I think. For some, if you set a static IP (that doesn't conflict with something else on the network) then the router will let the computer have that IP. For some other routers you need to go into the configuration and set it to "static IP mode".

---

### Post by Eastex Cruiser on 2007-01-07
Does anyone have any experience with the [SQuirreL]("http://www.squirrelsql.org/") frontend?

---

### Post by benow on 2007-01-22
Firebird is a great database, but not really for the novice.  MySQL will be easier to setup and phpmyadmin is a great frontend.

---

### Post by msimon1960 on 2007-03-23
My impression is that MySQL is the database (table) storage system but there isn't an integrated programming language for developing applications.  I'm coming at this from a dBase / FoxPro perspective which is an integrated database/programming environment for developing applications.

If I were to use MySQL as the database what would be the group's recommendations on a programming environment.  dBase and FoxPro are xbase (BASIC) variants with simple syntax for if..endif,do while..enddo, do case..endcase constructs.  Foxpro comes with a decent screen designer and report writer.  Is there something similar in linux-land?

I'm looking to dump FoxPro but I'm loath to go back to coding in a low-level code (been there, done that -- and not interested in writing screen interfaces and reports from scratch anymore.  I need a rapid app development tool).

Matthew.

---

