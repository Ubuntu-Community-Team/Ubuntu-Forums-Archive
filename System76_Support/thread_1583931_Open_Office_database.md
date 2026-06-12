---
title: "Open Office database"
date: 2010-09-28
forum: System76 Support
---

### Post by ShowMeGrrl on 2010-09-28
Hello All,

The transition from WindowsXP to Lucid Lynx for my home desktop uses continues. I have all my phones and addresses stored in a Microsoft Access database. I would like to be able to access this database in Linux. 

(I do have a WindowsXP VM and can access the database using Microsoft Access there, but I would also like to have this database on my Linux machine.)

I know that Open Office has a database program called Base. As I recall, Base can handle or convert MS Access databases. However, I notice that Base has not come installed with my System76 Wild Dog desktop PC, even though the other Open Office programs, such as the spreadsheet, word processor and presentations do come installed.

I'm wondering if this means that the Base program is considered problematic or not very good or if it just means that System76 thinks the average desktop user would not use Base much.

Second, when I go to Synaptic Package Manager, it provides only one option and that is to install the entire Open Office suite, which I'd rather not do, since, as I mentioned, I already have most of the suite. Those apps are working and I'd just as soon not mess with them. So my question is, how would I go about installing only the Base app?

Thanks much if you can address these two questions:
1) Is Open Office's Base app OK?
2) How would I install only the Base app to fill out the Open Office suite that I already have on my Wild Dog?

Jane

---

### Post by lfforman on 2010-09-28
I did not used base yet but i installed i think it does not came installed just because people do not use it on normally productivity tasks. also there is another program called MDB visualizer that allow you to open Access databases. i saw it on ubuntu software central.

---

### Post by isantop on 2010-09-28
Hi.

I think ifforman has the reasoning perfect. It's not a widely used component, and ona CD, every byte counts. To install it, open up Ubuntu Software Center (Applications > Ubuntu Software Center) and search for "openoffice.org". The package you need to install should be the only result.

---

### Post by ShowMeGrrl on 2010-09-28
> **lfforman said:**
> I did not used base yet but i installed i think it does not came installed just because people do not use it on normally productivity tasks. also there is another program called MDB visualizer that allow you to open Access databases. i saw it on ubuntu software central.

This sounded as if it would be just what I'm looking for. I installed MDB Viewer application from the Ubuntu Software Central and tried it. 

Unfortunately, this app, for whatever reason, did not work for me. It looked promising, in that it showed the two tables, the dozen or so queries and forms. But the app just doesn't seem to do much. I was able to view the tables in the database in a spreadsheet type form. Also, it showed the schema for the table. That is the good part. I was not able to view anything else -- no queries, no forms, no reports. 

Worse, when I clicked on the "Export" button for the main table, the MDB Viewer GUI simply vanished from my desktop. When I searched my Documents folder to see if it had produced an exported file, I found none. And, worst of all, my formerly 900 kb .mdb file with all my phones and addresses was now shown as a 0 kb file. 

I copied this .mdb file and tried to open it using Microsoft Access in my WindowsXP VM and it wouldn't open. So, in other words, the MDB Viewer trashed my database. Fortunately, I had backed it up!

Based on my experience, I would recommend against MDB Viewer. And if you try it out, I strongly recommend you back up your database first.

---

### Post by ShowMeGrrl on 2010-09-28
> **isantop said:**
> Hi.

I think ifforman has the reasoning perfect. It's not a widely used component, and ona CD, every byte counts. To install it, open up Ubuntu Software Center (Applications > Ubuntu Software Center) and search for "openoffice.org". The package you need to install should be the only result.

Ian, when I do that, I am shown the entire Open Office suite.
As I mentioned above, I would like to avoid installing the entire suite, since I already have most of the suite installed. I just want to install the database module. Is that possible?

---

### Post by jdb on 2010-09-28
> **ShowMeGrrl said:**
> Ian, when I do that, I am shown the entire Open Office suite.
As I mentioned above, I would like to avoid installing the entire suite, since I already have most of the suite installed. I just want to install the database module. Is that possible?

Strange, I have an entry:


[IMG]http://jdbowman.com/pictures/Screenshot.png[/IMG]


 Just for the heck of it, I put a check next to openoffice.org
& clicked apply.
The only thing that installed was base since the rest of it was already there.

jdb

---

### Post by msrinath80 on 2010-09-28
Sorry for hijacking this thread. But jdb, what font are you using on that screenshot? Specifically, can you post a screenshot of your Preferences -> Appearance -> Fonts window?

Thanks!

---

### Post by jdb on 2010-09-28
> **msrinath80 said:**
> Sorry for hijacking this thread. But jdb, what font are you using on that screenshot? Specifically, can you post a screenshot of your Preferences -> Appearance -> Fonts window?

Thanks!

[IMG]http://jdbowman.com/pictures/Screenshot-1.png[/IMG]

jdb

---

### Post by msrinath80 on 2010-09-28
Thanks!

---

### Post by ShowMeGrrl on 2010-09-28
> **jdb said:**
> Strange, I have an entry:


[IMG]http://jdbowman.com/pictures/Screenshot.png[/IMG]


 Just for the heck of it, I put a check next to openoffice.org
& clicked apply.
The only thing that installed was base since the rest of it was already there.

jdb

jdb, thanks. 

If I had just followed Ian's directions, it would have worked out. Instead of typing in "openoffice.org", as he directed, I had typed in "open office". When I do that, I get just a single entry for the entire suite. (Screenshot attached.) When I type in openoffice.org, I get what you got and am able to simply select the database.

So, I'll install the Open Office database and see how it handles the MS Access .mdb. (I guess it will soon be known as LibreOffice.)

---

### Post by frogotronic on 2010-10-02
> **jdb said:**
> Strange, I have an entry:


[IMG]http://jdbowman.com/pictures/Screenshot.png[/IMG]


 Just for the heck of it, I put a check next to openoffice.org
& clicked apply.
The only thing that installed was base since the rest of it was already there.

jdb

Hi jdb,

Install the one above it (openoffice.org) and you should now have the *complete* suite.

- CH

---

### Post by jars_u on 2010-10-03
You might also consider taking a look at [Glom]("http://www.glom.org/wiki/index.php?title=Glom") and [Kexi]("http://www.kexi-project.org/") as database options in Linux.

I personally think [FileMaker]("http://www.filemaker.com/") is one of the best DB solutions - certainly better then [Access]("http://office.microsoft.com/en-us/access/") - but its on the pricey side and only for Win and Mac.

---

### Post by ShowMeGrrl on 2010-10-03
I downloaded the Open Office "Base" database application, to complete my Open Office suite. 

As seems to be the case with most databases I've looked at (including Glom and Kexi), you cannot edit the Access databases or tables that you import. I am paying the price of using Access, which obviously is part of the Microsoft ecosystem and not very 'interoperable.'

I exported my Phone-Address Access database as an Excel spreadsheet. It was really the only export option that seems to work with Base. I connect to it by selecting the 'spreadsheet' option. Then I save it as an Open Office database (.odb). 

I am able to display the tables, search them, and easily create queries and forms based on the tables.

But each time I want to update phones and addresses, I will have to do so using Access in my Windows VM and then re-export and import the database (i.e. spreadsheet) into Base. I don't know yet if I will have to recreate the queries and forms each time I do that. I hope not.

---

### Post by jars_u on 2010-10-09
> **ShowMeGrrl said:**
> I connect to it by selecting the 'spreadsheet' option. Then I save it as an Open Office database (.odb).

It's been a while since I tried Base but instead of opening the spreadsheet have you tried importing the data into the tables directly?  See this [example]("http://linuxtuts.blogspot.com/2008/03/how-to-import-data-from-excel-sheet.html").

---

### Post by ShowMeGrrl on 2010-10-16
> **jars_u said:**
> It's been a while since I tried Base but instead of opening the spreadsheet have you tried importing the data into the tables directly?  See this [example]("http://linuxtuts.blogspot.com/2008/03/how-to-import-data-from-excel-sheet.html").

Thanks much. I finally had a chance to try this method and it does seem to work. There was some funkiness as I did it (described below), but the end result was that I was able to import the spreadsheet as instructed in the link and the resulting database table within Open Office Base is editable from within Base. 

That, of course, is a major improvement over the previous method. It means I can completely abandon the Access program and switch to Base. No more having to fire up Virtual Box and export from Access just to make a change in the database.

Now here's the funkiness and some advice if you are going to do this. 

The first time I did this, the program crashed. I believe the reason was that when I did the "copy" operation, I copied from top to bottom and unintentionally included every potential row in the spreadsheet. My spreadsheet had only 310 records in it yet when I went to do a search in the database after pasting, I noticed it was searching endlessly tens of thousands of (empty) records.

The second time I did this, I did the copy operation from the bottom of my records (i.e. the 310th row) upwards and thus avoided including many thousands of empty records. (The first database was something like 1.5MB, while the second one was 52kb.)

Another strange thing that happened was that after I completed the copy-and-paste to the new Base database, I went to modify it and was able to modify it, but when I tried to close the table, I kept getting a dialogue saying "Your records have been modified, do you wish to save the modification" or something similar. Of course, I clicked "Yes" to that. But it refused to close the program. Finally, I gave in and said 'No' and the program closed. However, when I opened it up again, it had registered the changes.

I think what may have been happening here is that when you are doing this operation, you are really dealing with two copies of things. You have your original spreadsheet and you have your new database. Perhaps the dialog that was refusing to allow me to save my modifications were for that original spreadsheet, which, in fact, remains unmodified. I did do a save at some point for the new database, which did preserve the modifications. I am rather confused about the exact details of what I was doing, so it's possible the only funkiness is that of my own mind!

Thanks for the suggestion jars_u: it has improved my life a lot!

---

