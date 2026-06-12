---
title: "moving from vista/sql server to ubuntu/mysql"
date: 2008-05-30
forum: Server Platforms
---

### Post by remeron on 2008-05-30
Hello all,
I'm quite a newbie at linux but i'm quite comfortable with CLI and some other stuff.  I have about 4 computers where I work and all of them are running WIndows Vista and one of the computers has Microsoft SQL Server 2005 installed.  The sql server holds a database for patients that visits the clinic.  The front end of it as a *.adp file that runs on microsoft access 2007.

I want to convert all the computers to Ubuntu and i hope to retain the function of the database. Hence what do i need to make this work?  The back end I can think of is MySQL but I'm not sure what to use for the front end and my knowledge of mysql is very limited.  Furthermore, i have backed up the database from the microsoft sql server, will i be able to restore it using MySQL?  Is there any way i could convert the ADP file to a format that OpenOffice Base can use?

thanks.

---

### Post by quelx on 2008-05-30
for the database
[http://www.mysql.com/products/tools/migration-toolkit/](http://www.mysql.com/products/tools/migration-toolkit/)

From what I see the .adp (Microsoft Access Project) is just connection information (presumably to connect to the MSSQL database) but I am not sure.

See if this gives you the same functionality...
[http://bobpeers.com/linux/mysql_ooffice.php](http://bobpeers.com/linux/mysql_ooffice.php) 
(ignore the java bit, just install java from synaptic/apt-get/aptitude)

---

### Post by remeron on 2008-05-30
> **quelx said:**
> for the database
[http://www.mysql.com/products/tools/migration-toolkit/](http://www.mysql.com/products/tools/migration-toolkit/)

From what I see the .adp (Microsoft Access Project) is just connection information (presumably to connect to the MSSQL database) but I am not sure.

See if this gives you the same functionality...
[http://bobpeers.com/linux/mysql_ooffice.php](http://bobpeers.com/linux/mysql_ooffice.php) 
(ignore the java bit, just install java from synaptic/apt-get/aptitude)

The migration looks really helpful and will give it a try.

With regards to the *.adp file, it's actually a Microsoft Access Data Project file, which is a front end for the database and contains my forms, codes and such.  Is there a way of converting it to a web based format?

I know my question might seem a tad naive :) so any help would be appreciated or point me to the right direction so i can read about it.

---

### Post by quelx on 2008-05-30
> With regards to the *.adp file, it's actually a Microsoft Access Data Project file, which is a front end for the database and contains my forms, codes and such. Is there a way of converting it to a web based format?

If you mean is there a way to convert that file into a web page with another program specifically designed to convert such files to web pages, no.

However the end product (a web page with a database backend) is one of the selling points for using mySQL.  With some coding in PHP you can create the same frontend that interacts with the mySQL database on an Apache webserver on GNU/Linux.  Such a thing is call ed LAMP (**L**inux-**A**pache-**m**ySQL-**P**HP) installation.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by dkasak on 2008-05-30
> **remeron said:**
> The back end I can think of is MySQL but I'm not sure what to use for the front end and my knowledge of mysql is very limited.

I've been developing Gtk2-Perl front-ends for about 3 years now. They absolutely rock. I've developed 3 Perl modules to replace the 3 main features of MS Access: forms, datasheets and reports. I originally looked into Base, and it's not really up to the job yet. It's very slow, difficult to use, and the form builder is horrible. Gtk2 is WAY better. Trust me.

Other advantages include record paging ( so you can run your application across a slow internet connection ... tunneled through openssh of course ), advanced data formatting ( currency, date, etc ), recordset action triggers ( eg on_update, on_apply, etc ) and the project is in active development.

You can see my projects on cpan:
[http://cpan.uwinnipeg.ca/search?query=dkasak&mode=author]("http://cpan.uwinnipeg.ca/search?query=dkasak&mode=author")

I would normally point you to my website that has screenshots, but unfortunately I **deleted** the whole damned thing while I was upgrading my home server. Damn.

Anyway, if you know Perl, then you'll absolutely love these modules. If you don't know Perl, I recommend you use this as a good opportunity to learn :)

If you want a hand, a brief overview, some screenshots, etc, email me at [EMAIL="dkasak@nusconsulting.com.au"]dkasak@nusconsulting.com.au[/EMAIL] and I'll get in touch with you. I aim to get some form of website up soon with some download links, screenshots, etc.

I've just done a screenshot of our main CRM package at work ( running on my laptop at home ). This form has about 60 different form and datasheet objects on it. It's also very fast. The whole thing refreshes in about 10 seconds ( as opposed to about 80 seconds with MS Access ). Screenshot:

[IMG]http://www.nusconsulting.com.au/client_services.png[/IMG]

Obviously I can't show you any data, but you get the idea.

---

### Post by remeron on 2008-05-31
@quelx
yea..i think LAMP is the way to go for me.  it's gonna be a huge and steep learning curve for me.  

@dkasak
wow, that gtk2-perl module looks good.  looks like something i'd want to have for my clinic.  time to learn perl...LAMP......arrgghh..me head's gonna burst!

---

