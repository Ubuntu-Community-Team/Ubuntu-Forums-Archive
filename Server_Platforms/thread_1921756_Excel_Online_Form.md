---
title: "Excel Online Form"
date: 2012-02-07
forum: Server Platforms
---

### Post by pepsifx357 on 2012-02-07
Hey all,

My boss is asking for me to look into creating a website for our company that will provide our employees with an online time sheet form.

Right now he's got a time sheet that he made in excel with drop down menus and such.

I'm thinking that he wants something like an online form tied to a database so that when someone fills it out and submits it, he can open an excel sheet that is tied to that database.

I'm no expert, which is why I am posting.

Can someone point me in the right direction?  Like how to get apache or IIS to serve the excel sheet that can be edited easily and republished.

Thanks

---

### Post by SeijiSensei on 2012-02-07
To be honest, if you've never done something like this before, you'll need to learn a number of skills. Unless you've got a lot of time on your hands, your company might be better off hiring someone for this task. Here's a quick overview of how I'd approach this problem:

1) Install Apache, PHP and PostgreSQL (I don't use MySQL.)

2) Create a PHP script that by default generates an HTML form emulating the Excel sheet.  The employee fills in the form and presses a Submit button.  The data will then be POSTed back to the script for processing.  I'd include some basic integrity checks and either prompt the person to fix the problem or post the data to PostgreSQL.

3)  You could then write another PHP script to present the data, generate summaries, etc.  Alternatively, you can install the PostgreSQL ODBC driver in Windows and set up an Excel or Access application that takes the data from Postgres and repackages it as desired.

---

### Post by rubylaser on 2012-02-07
> **SeijiSensei said:**
> To be honest, if you've never done something like this before, you'll need to learn a number of skills. Unless you've got a lot of time on your hands, your company might be better off hiring someone for this task. Here's a quick overview of how I'd approach this problem:

1) Install Apache, PHP and PostgreSQL (I don't use MySQL.)

2) Create a PHP script that by default generates an HTML form emulating the Excel sheet.  The employee fill in the form and presses a Submit button.  The data will then be POSTed back to the script for processing.  I'd include some basic integrity checks and either prompts the person to fix the problem or posts the data to PostgreSQL.

3)  You could then write another PHP script to present the data, generate summaries, etc.  Alternatively, you can install the PostgreSQL ODBC driver in Windows and set up an Excel or Access application that takes the data from Postgres and repackages it as desired.

+1 

With a  Google search, and you'll find tons of Open Source apps that can be modified to meet your needs. Or, this would be a very simple project to learn a new programming language.  But, in the case of a business, if you don't have the skillset, just hire someone, this is a very simple task for most web developers.

EDIT: beaten to the punch by SeijiSensei.

---

### Post by pepsifx357 on 2012-02-07
Ok, I can do number 1.

Number 2...I might could find something that would work.

Number 3 out of my knowledge realm.

Are there any open source php apps that do something close to this?

---

### Post by SeijiSensei on 2012-02-07
> **pepsifx357 said:**
> Ok, I can do number 1.
Number 2...I might could find something that would work.

Number 3 out of my knowledge realm.

Are there any open source php apps that do something close to this?

Actually the Windows part of #3 is relatively easy compared to the PHP scripting.  (You install [this driver]("http://www.postgresql.org/ftp/odbc/versions/") via the ODBC Administrator applet in the Windows Control Panel, then configure a connection to your server. The .msi packages probably install the driver for you.)  If you can accomplish #2 yourself, then the scripting part of #3 to report the data isn't really any harder.

I write applications from scratch so I don't know of any pre-existing ones.  On the other hand, a Google search for 'php employee time sheet' brings up, among others, [this page]("http://www.debianadmin.com/opensource-timesheet-management-tools.html") at debianadmin.com with a number of alternatives.

---

### Post by memilanuk on 2012-02-07
Perhaps a slightly simpler approach might work... like a Google Docs spreadsheet, with an associated form that you can embed in a web page.  When people fill out the form and submit it, the data is entered into your spreadsheet automagically, which can then be viewed or edited by whoever you've assigned such privileges to.

Biggest limitation so far IMO is that the field validation is weak or a bit of a struggle compared to a straight-up Excel spreadsheet.  Biggest benefit is that if you understand spreadsheets you can probably get a prototype up and running in about 15 minutes with basically no programming...

---

