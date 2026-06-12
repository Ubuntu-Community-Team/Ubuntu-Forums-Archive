---
title: "what do ubuntuers use for database work?"
date: 2006-01-06
forum: The Cafe
---

### Post by twowheeler on 2006-01-06
I have a file in CSV format with something like 285,000 rows.  It is 94 MB of mostly numeric data although the column headers are in the first row.  I need to be able to manipulate this data and do calculations.

I mostly use spreadsheets at work but this is too big for that.  In windows I would open up MS access and fumble around with it in spreadsheet mode until I got something useful.  So I have managed to avoid learning any SQL which I suppose is the correct way to do this.

How do you do this in linux?  I grabbed mysql from the repositories but I am totally lost with it.  It looks like a network app, as it wants a server name to connect to.  I don't have a server, it is just me and my little ubuntu box here.  Mysql is way more than I need.

Suggestions appreciated!

---

### Post by YourSurrogateGod on 2006-01-06
Well, if you want to do some simple DB manipulating, I'd try Java (it has oodles of little functions, utilities and god-knows what.)

---

### Post by twowheeler on 2006-01-06
Err ... java?    :confused: 

I don't think a programming language is what I am looking for.

---

### Post by briancurtin on 2006-01-06
ive never used mysql, but its asking for the server address that the database is on i think. i have no idea how to set it up for using your box locally, but plenty of people have used mysql and would know how. i will actually be doing the same thing soon with either mysql or postgresql so id like to see the answer

as for me, ive used MSSQL (boo) in an ASP.NET (boo) project i did once, and i have also used Sybase with a JSP/Java web app i did this past summer. i loved working with Sybase

also, my project i just talked about where i used JSP/java/sybase was actually replacing the group's spreadsheets/CSVs, exactly what you are trying to do. they wanted a web interface, so i threw the data all into CSV and inserted it all into Sybase, and developed a pretty powerful web front end for it.

---

### Post by kassetra on 2006-01-06
[yamysqlfront]("http://www.gnomefiles.org/app.php?soft_id=1116") is my first choice; [mergeant]("http://www.gnomefiles.org/app.php?soft_id=199") would be my second.


When it comes to dbs in linux - you have extremely powerful tools - but sometimes they are ugly or unwieldy.  Those two tools are my top choices.

---

### Post by kassetra on 2006-01-06
[quote=twowheeler]I have a file in CSV format with something like 285,000 rows. It is 94 MB of mostly numeric data although the column headers are in the first row. I need to be able to manipulate this data and do calculations.

I mostly use spreadsheets at work but this is too big for that. In windows I would open up MS access and fumble around with it in spreadsheet mode until I got something useful. So I have managed to avoid learning any SQL which I suppose is the correct way to do this.[/quote]
See my previous post for gui tools to use on this.

[quote=twowheeler] How do you do this in linux? I grabbed mysql from the repositories but I am totally lost with it. It looks like a network app, as it wants a server name to connect to. I don't have a server, it is just me and my little ubuntu box here. Mysql is way more than I need.

Suggestions appreciated![/quote]

Ok, mysql isn't more than you need - it's what you need to work with database-type files in linux.  It looks like a lot and unwieldy - but that's only because you don't get to see all these innards on a Windows box when you install Access.

The "server name" it means/needs is "localhost" ... i.e. where the mysql process is running so that you can use mysql commands to work with your data.  The applications I mentioned in my previous post will allow you to work on your data without knowing those sql commands to use.

---

### Post by twowheeler on 2006-01-07
Many thanks for the replies.  I will look at the front end products.  

Can someone give me a clue about what command is used to load up a CSV file into mysql?  That is, without manually defining all of the columns in the table?

---

### Post by majikstreet on 2006-01-07
<3 mysql....

I don't really use GUI tools, I've only used Cpanel a bit and PHPMyAdmin

---

### Post by WildTangent on 2006-01-07
I use MySQL/PHPmyadmin for my webserver databases. Really easy to use for my purposes. Though I rarely have to manually edit my database tables.

-Wild

---

### Post by kassetra on 2006-01-07
[quote=twowheeler]Many thanks for the replies.  I will look at the front end products.  

Can someone give me a clue about what command is used to load up a CSV file into mysql? That is, without manually defining all of the columns in the table?[/quote]

The tools I've suggested both actually help you *quite* a bit in this regard (they can take your csv file and turn it into a table near instantly) - as the command to do this is quite ugly:

```
load data infile '/path/to/table_name.csv' into table table_name FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' (field1,field2);
```

Make sure that the first row of your csv doesn't have the field names and make sure the field list lines up with your commas.  Remember, you're having to give commands to a powerful but dumb (problem-solving-wise) database engine, if things don't line up exactly, it doesn't know what to do.

---

