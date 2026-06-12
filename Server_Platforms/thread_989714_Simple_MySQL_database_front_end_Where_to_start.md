---
title: "Simple MySQL database front end: Where to start?"
date: 2008-11-21
forum: Server Platforms
---

### Post by Rounan on 2008-11-21
Hello,

My engineering company is trying to set up a simple database to keep track of part numbers for our CAD models. We already have an ubuntu LAMP server running Zoneminder, and I was thinking it would probably be easy to add this database along with a simple web front end. However, I have no SQL experience and only a basic idea of how it works. Because what we want to do is fairly trivial, I am hoping there is some "off the shelf" open source package that will either do exactly what we need, or will do so with minimal tweaking.

Here is what we need:

- small database of CAD parts (<1000 parts at this point)
- required fields are:
  -part number, format : ####-####. This corresponds to the CAD part's filename, located on another server's network share.
  - several text fields for material, date, etc.
  - a tags field with a bunch of search terms
- web front end that can:
  - request the next available part number, and create the new entry
  - search for existing parts matching the fields.

That's pretty much it. I believe I may have just defined "database", but I truly have no experience in this. I've googled a bit and searched Ubuntu's repos, but can't find a good starting point. Any advice would be appreciated!

Thanks.

---

### Post by rustutzman on 2008-11-22
I think I'd start by putting all the info into a spreadsheet and then use phpmyadmin to import that spreadsheet into the database. I just went through a similar process. I created the database, created the tables, and imported the data from the spreadsheet using a saved a .csv file.

HTH
Russ

---

### Post by volkswagner on 2008-11-22
You can also use Webmin to help with the mysql.  It makes a nice frontend.

---

### Post by Thirtysixway on 2008-11-22
Once you get your mysql/phpmyadmin setup you could set this up on the web server and use it as a frontend to enter data into the system.

[http://sourceforge.net/projects/item-inventory/](http://sourceforge.net/projects/item-inventory/)

---

### Post by Iowan on 2008-11-22
I haven't (yet) used **webmin** or **ebox** to remotely access a mySQL database, but **phpMyAdmin** seems to work OK... although it is a challenge from the **elinks** text-only web browser. It's probably as easy (or easier) to use the CLI if you're working from the server itself.

---

### Post by Rounan on 2008-11-23
From what I've read here and from some googling, I am not looking for a web frontend for database administration, such as webmin or phpmyadmin.

Rather, what I'm looking for is an end-user frontend to search and add entries to a (relatively simplistic) database without knowing anything at all about SQL or database structure.

ThirtySixWay, I took a look at the Inventory project and it is indeed the type of project i'm looking for - only, it's about 10x more complicated than I need or want, and I'm having trouble deciphering it.

Does anyone know of a more basic end-user frontend that I could use as a starting point? Google and sourceforge have failed me...

---

### Post by Thirtysixway on 2008-11-23
> **Rounan said:**
> From what I've read here and from some googling, I am not looking for a web frontend for database administration, such as webmin or phpmyadmin.

Rather, what I'm looking for is an end-user frontend to search and add entries to a (relatively simplistic) database without knowing anything at all about SQL or database structure.

ThirtySixWay, I took a look at the Inventory project and it is indeed the type of project i'm looking for - only, it's about 10x more complicated than I need or want, and I'm having trouble deciphering it.

Does anyone know of a more basic end-user frontend that I could use as a starting point? Google and sourceforge have failed me...

I think if you were looking for something even more simple than that, you may need to either code a frontend yourself or hire/find someone who can do it.

---

### Post by rslrdx on 2008-11-23
i might be going off in a different direction here... but if its something simple, and you cant currently afford to hire someone to code something for you... you might want to look at the problem differently... It might sound as a wild idea at first, and may not fit as a solution at all, but its worth a shot here i think... you COULD setup osCommerce on your intranet lamp server and that would kind work for you...

basically, you are looking for a simple, end-user friendly way to catalog your parts and information, so with osCommerce, you can add all of your CAD parts and you can easily have the required fields, most seem to be there already, part numbers, tags, text areas, web based and search. As for the part number request, I'm not sure which plugin you would need but i'm sure there is some that will generate some sort of numbering, in fact, i think there is a plugin for creating serial numbers for people who sell software licenses... it just might work... might even do some sort inventory if needed.

Again, this is a long, loooong shot in the dark here.. but it might work for you, and thinking of it, you may even add pictures of your parts to it, not to mention that its fast, locally hosted, and you don't need a fast computer to host this for you... 

hehe.. just a wild idea.. 

I'll check back on this later... maybe you'll like the crazy idea

---

### Post by cariboo on 2008-11-23
Have a look at [Freshmeat]("http://freshmeat.net") and search for **inventory database** in projects. I found a few that may be what you are looking for, but it is better if you have a look at them yourself. One that looks like it might work for you is called gCatalog.

Jim

---

### Post by infallible on 2009-02-27
bump. I'm looking for this too.

---

### Post by koenn on 2009-03-02
[http://users.telenet.be/mydotcom/library/databases/ooofrontend.htm](http://users.telenet.be/mydotcom/library/databases/ooofrontend.htm)

[http://dev.mysql.com/doc/refman/5.1/en/connector-odbc-examples-tools-with-access.html#connector-odbc-examples-tools-with-access-linked-tables](http://dev.mysql.com/doc/refman/5.1/en/connector-odbc-examples-tools-with-access.html#connector-odbc-examples-tools-with-access-linked-tables)

[http://sourceforge.net/softwaremap/trove_list.php?form_cat=68](http://sourceforge.net/softwaremap/trove_list.php?form_cat=68)

[http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

---

### Post by petebouch on 2009-08-19
What about OpenOffice Base? It's the database application that comes with OpenOffice.org and you can set up a standalone database on the client or use a shared MySQL database on your server:
> For power users in the enterprise, BASE delivers native support drivers for a variety of multi-user database engines: MySQL, Adabas D, MS Access and PostgreSQL. In addition, support for JDBC and ODBC standard drivers allows you to connect to virtually any existing database. [http://www.openoffice.org/product/base.html](http://www.openoffice.org/product/base.html)

---

