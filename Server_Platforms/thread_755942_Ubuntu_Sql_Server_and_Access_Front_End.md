---
title: "Ubuntu Sql Server and Access Front End"
date: 2008-04-15
forum: Server Platforms
---

### Post by ASherbuck on 2008-04-15
This is something I've been getting nearer too now and it's almost to the point where I need to start running my DB, which is currently Access 2007, on SQL. It's growing too big and is going to be having more users than it can handle and I am curious, as I have not seen anything in the manual or through out the forums, if it is possible to have the sql back end on a linux box? 

Creating the Access front end and sql back end was pretty easy on my trial runs on my test machines, I'm just curious if anyone knows this answer before I take the time to download, install and setup ubuntu server edition. I'd rather spend the install time reading up on my ventures.

If you are not familiar with Access, and I don't blame you, it can connect to a SQL database using an ODBC connection and you can effectively perform every task through Access without having to know a lick of SQL. 

I'd like to make this switch because I'd rather have a server running with Linux, than have to use a windows server.

---

### Post by Deathrend on 2008-04-15
Is your current Database MySQL, or other? Even converting from MSSQL2000, to 2005 is a reach, going from one flavor to another would be nasty.

Access is a really.. reallly.. off program.  To run a query, it downloads the /full/ table you're trying to read, if it's to large it will download the full database, something to watch out for, as this will expand the que times much much longer.  You could consider a ruby on rails access db, that's used to then access the SQL database and run querys.  We use Cognos to bring all of our databases togather, however that sounds very overkill from what I'm reading.

Sounds like you just need a better start point for your DSBC's, you would probably be in decent shape using what you currently have.

If you're runny out of memory on a windows 2003 server (Non Enterprise) consider adding /PAE to the boot.ini, this will give you the ability to expand past the normal 4 GB limitation on 32 bit OS's.  We currently have an MSSQL Enterprise server using 16 GB's of ram, on 2k3 Standard.

You need a smaller system that accesses the database for you, per say, Ruby On Rails is a start, however very painful at times to manage. If you ever change the ODBC's, you will have to rlink all of the tables one by one.. by one..

---

### Post by ASherbuck on 2008-04-16
No, the DB is currently MS Access 2007, on a windows box. Access has the ability to split the tables to sql server and keep the forms, queries, reports as part of the front end in Access. You can continue to work with your DB through access, you just get the benefits of having SQL under the hood instead of Access. 

My question is, instead of running my sql server on windows can I just run it on linux and still use my access front end, access only needs to communicate with SQL, but would the fact that it is hosted on a linux box be a problem ?

---

### Post by Deathrend on 2008-04-16
Ahh, No way, shouldn't be a problem at all.  You should really consider porting it into a normal SQL database though.  I would also suggest running the compress and compat option for just sheer size reduction.

I assume you're talking about just the DB file access itself makes, which can be saved anywhere.  We currently host several directly on a SAN (Which is Linux, for the most part).  As far as windows knows, Saba is just another Windows PC sharing folders.

For speed, I would go with a real SQL database however.  You can get MSSQL 2005 for free, and it's really easy to import access databases into.  From there you can either connect directly, or use ODBC's.

You can also do this with Linux SQL servers, however some of the functionality won't be as easy, however it's still very much doable.

But yes, if I understand the question correctly, that shouldn't pose a problem at all :)

---

### Post by Alterax on 2008-04-16
Shouldn't be that difficult an ordeal.  You'll need to get an export of the SQL code to rebuild your entire database.  Since all SQL implementations are very different, you may want to check the code to make sure it's compatible.  Load that into your MySQL backend, then create an ODBC connection to the frontend.

I'm sorry I don't have the particulars, but I had to handle a job like this a few months ago for a company.  The results were good; I'm still trying to convince them of the advantages of replacing the Access frontend with a custom php interface.

---

### Post by Deathrend on 2008-04-16
[QUOTE=Alterax;4728739]Since all SQL implementations are very different, you may want to check the code to make sure it's compatible. QUOTE]

That's the portion I was refering to.  MSSQL just makes it really.. stupid-friendly.. per-say.  You can directly import an access database,where as with others, you have to export it, convert it, then import it.  Not hard, unless you're new to databases.

You can probably find converters that will change the syntax for you.

---

### Post by ASherbuck on 2008-04-16
That's good to know, I definately have some reading to do. Thanks for the info.

---

