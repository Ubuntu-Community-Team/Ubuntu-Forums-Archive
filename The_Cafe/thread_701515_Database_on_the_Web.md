---
title: "Database on the Web"
date: 2008-02-19
forum: The Cafe
---

### Post by chalewa on 2008-02-19
Anyone know of any good tutorials out there on the internet that might help me integrate a user generated database on the web?

Im looking for people to be able to enter info into a field, have it stored in a database, and then recalled when the user wants with a username password combo. the database is already built (access...not my choice).

i know this is kinda alot, but any info would be helpful, even what books i should read and whatnot. 

thanks

---

### Post by frrobert on 2008-02-19
If you are going to use Access as the database.  That means you will need a Windows solution. 

 I would suggest ASP.NET as your tool to connect to the database.

Unless you are hosting your site, you will have to find a web hosting company that supports asp.net and access.

I believe some of the big boys do offer either windows hosting or linux based hosting.


First depending on the provider use may be using asp.net 1.1 or 2.0.  You will want to focus on learning the version you will need to use.
Also, you can write your code in either VB or C# which ever one you are more comfortable with.

Most of what I learned about asp.net and C#  I learned from the Visual Studio help files and other online help including forums such as Microsoft's MDN forums and [http://www.devshed.com/](http://www.devshed.com/).

Hope this provides some helpful ideas

---

### Post by OffAxis on 2008-02-19
you're not limited to a microsoft solution; you can connect to an access backend with php, or you can dump your access tables into a mysql database and connect to that with php.

There's a lot of mysql/php tutorials out there online; just google it.

If you're interested in using mysql, you can install **phpmyadmin** from the repositories and use that to import your access dump file into mysql.

You could even use kexi (koffice database) or openoffice's database instead of Access. I think they open Access files natively, although they may have problems with the VBA modules.

---

### Post by OffAxis on 2008-02-19
Just came across this; maybe it'll help you.

[http://blogs.techrepublic.com.com/msoffice/?p=437]("http://blogs.techrepublic.com.com/msoffice/?p=437")

---

### Post by frrobert on 2008-02-19
> **OffAxis said:**
> you're not limited to a microsoft solution; you can connect to an access backend with php, or you can dump your access tables into a mysql database and connect to that with php.

There's a lot of mysql/php tutorials out there online; just google it.

If you're interested in using mysql, you can install **phpmyadmin** from the repositories and use that to import your access dump file into mysql.

You could even use kexi (koffice database) or openoffice's database instead of Access. I think they open Access files natively, although they may have problems with the VBA modules.

OffAxis is right

I'm sorry my previous answer made two assumptions one you HAD to use the access database and you were using a hosting provider.  Most hosting providers if they are hosting an Access database lock you into a Windows solution.

But if you are hosting your own box or willing to migrate the DB to another DB solution you have a lot of different options

If you are willing to migrate your DB to a non Access solution, then I agree I would use mysql and php running on apache that is the best solution whether you use host your own box or use a hosting provider

I have not had any luck with openoffice.org base, I find it too unstable.

If you have to stay with Access
and are using your own box you have the choice of several configurations
a windows box running your Access Database then running 
1.  apache with php
2. IIS with php
3.  IIS with ASP.net

My first choice if you are running your own box would be apache with php, my  second choice would be IIS with ASP.NET

---

### Post by chalewa on 2008-02-19
hi guys, thanks for the help


basically what i have is that the access database is already built for the most part, and that i just have to link this database up to the website. 

the host that i have to use is godaddy, so that i think that it would just make more sense to stick with the windows solution? unless it is easier to go with the mysql/php option

---

### Post by frrobert on 2008-02-20
Check with godaddy but I believe if you want to use an Access database you have to use either ASP, ASP.NET 1.1 or  ASP.NET 2.0.

Given those choices I would use ASP.NET 2.0

---

### Post by DrMega on 2008-02-20
> **frrobert said:**
> Check with godaddy but I believe if you want to use an Access database you have to use either ASP, ASP.NET 1.1 or  ASP.NET 2.0.

Given those choices I would use ASP.NET 2.0

Classic ASP will do just fine, you don't need to use .Net. Although if you have the choice to use .Net that's the route I would go down if I had to work with MS technologies.

If there is any way at all that you could use a DB engine other than Access, I would look into that. Access is fundamentally a single user system. It has been patched up many times since it first came out, but fundamentally it is still limited. The practical implications of this really is performance and security.

Performance:

Being fundamentally a single user system, it means that if two people view the page at the same time, whoever gets the first will ock the DB and the second person has to wait. In the case of two users the likelihood of this being a problem is remote and even if it does happen, the delay will be milliseconds. However in the case of 200 users, you may get lots of timeouts.

Security:

If a user can guess where your Access file is stored, and it is in a folder that the webserver can access directly, then they can download the entire DB file. With a proper DB server (MS SQL Server, MySQL etc), there is no flat file to download as such, and the webserver talks to the DB server which may not be directly accessible to the webserver other than by ODBC, which doesn't allow you to do anything except talk to the DB in the manner intended.

If you are just starting out, now is the best time to avoid bad habits that will come back to haunt you later. Do a google search for SQL Injection attacks, it can be a real eye opener.

---

