---
title: "database program suggestion?"
date: 2010-04-18
forum: The Cafe
---

### Post by rebeltaz on 2010-04-18
I am trying to find a program that I can use to keep track of items and their associated model and serial numbers, preferably in a table format. Years ago, on a windoze computer, I used a program called ListPro, and I have just made a table in Word. I was hoping to find a dedicated database program, though. Maybe with the ability to export to a comma delimited text file? 

As you can guess, when I do a search for 'linux database', 99.99999% of the results deal with MySQL...

Any suggestions would be great. Thanks....

---

### Post by tica vun on 2010-04-18
So why not MySQL? Myself, I can't be bothered with spreadsheet programs that advertise themselves as a database. Might as well use a real database management scheme.

---

### Post by jkxx on 2010-04-18
I'm quite sure OpenOffice can do this and it should already be installed for you. It even has a special app called 'OpenOffice Base' which works with databases similar to Microsoft Access. The different OO apps work together so you should be able to take any database you make with Base and import it into OO Word.

---

### Post by swoll1980 on 2010-04-18
> **tica vun said:**
> So why not MySQL? Myself, I can't be bothered with spreadsheet programs that advertise themselves as a database. Might as well use a real database management scheme.

Another vote for MySQL. Only because I know how to use it, and it works, so why not?

---

### Post by lovinglinux on 2010-04-18
I vote for sqlite. It is already installed and it is file based, so there is no need to setup a server. 

You can create and manage sqlite databases with [SQLite Manager](https://addons.mozilla.org/en-US/firefox/search/?q=SQLite+Manager) extension for Firefox. It works like a charm.

You can also install [sqlite3](apt:sqlite3) and crate bash scripts to perform sql queries or do that from command-line.

If you are planning to setup a huge database, then go with MySQL, but for small databases, sqlite is awesome. Firefox stores a lot of stuff on sqlite databases.

---

### Post by Mike'sHardLinux on 2010-04-18
I am a big proponent of DB and especially MySQL, when it is the right tool. But, in your case, it seems way overkill. 

Just use 2 or 3 columns in a spreadsheet program. You can save it as a CSV in any spreadsheet program I have used from the past decade (at least). You can search, re-sort, etc. You can generate reports or charts.....

For this particular application, I see no advantage of MySQL over, say OOo Calc, unless you consider unnecessary complexity an advantage. And, a spreadsheet is about as tabular as you can get.

PS: MySQL is only a back-end. You'd need to build or otherwise get a front-end, hence, what I mean by unnecessary complexity....

> **rebeltaz said:**
> I am trying to find a program that I can use to keep track of items and their associated model and serial numbers, preferably in a table format. Years ago, on a windoze computer, I used a program called ListPro, and I have just made a table in Word. I was hoping to find a dedicated database program, though. Maybe with the ability to export to a comma delimited text file? 

As you can guess, when I do a search for 'linux database', 99.99999% of the results deal with MySQL...

Any suggestions would be great. Thanks....

---

### Post by new_tolinux on 2010-04-18
> **Mike'sHardLinux said:**
> I am a big proponent of DB and especially MySQL, when it is the right tool. But, in your case, it seems way overkill. 
+1

> **Mike'sHardLinux said:**
>  Just use 2 or 3 columns in a spreadsheet program. You can save it as a CSV in any spreadsheet program I have used from the past decade (at least). You can search, re-sort, etc. You can generate reports or charts.....
-1

MySQL is way overkill to what the OP wants, but "abusing" a spreadsheet as a database isn't the right thing to do in my opinion.
I would suggest OpenOffice Base, as mentioned above. I haven't used it (I use MySQL, because it fits my needs) but I guess it has some simple form-gadgets because MS Access had them since (at least) Office 95. That way you have a real database (with real database-options) and a way to build yourself a quite useful GUI in a quite easy way if you want to.

---

### Post by Mr. Picklesworth on 2010-04-18
Try [Glom]("http://www.glom.org/wiki/index.php?title=Glom"). It's a really fantastic database app. Its web site will show you how :)
It's flexible and pretty, and a bit like FileMaker.

The only problem I have with it is that it drags in the entire PostgreSQL database (which has a daemon that sits in the background). On the bright side, that means it seamlessly works over a network!

---

### Post by rebeltaz on 2010-04-18
OpenOffice Base - works great. Exactly what I was looking for. OOo was installed on my system, but strangely, the Base component wasn't. Installed that and I am a happy camper. Thank you all for your suggestions!

MySQL was way overkill, BTW.

---

### Post by Beanyhead on 2010-04-18
Yeah I don't think Base installs by default.

---

### Post by new_tolinux on 2010-04-18
> **rebeltaz said:**
> OpenOffice Base - works great. Exactly what I was looking for. OOo was installed on my system, but strangely, the Base component wasn't. Installed that and I am a happy camper. Thank you all for your suggestions!

MySQL was way overkill, BTW.
Not really strange......

Ubuntu fits on a CD...... which means not everything can be installed by default.
Since Base isn't used that much (as most home users also don't use MS Access), I guess they left it out to put something else on that limited amount of space.

---

### Post by Paqman on 2010-04-18
How big a database are you talking about rebeltaz? And how important is the interface?

---

### Post by rebeltaz on 2010-04-18
> **Paqman said:**
> How big a database are you talking about rebeltaz? And how important is the interface?

Not really all that big at all... I guess I should have been more specific in the original post. I have more 'toys' that then average bear, so every occasionally I will go around and noting the model and serial numbers of all my important stuff. That way if anything gets stolen, I have a record to show police in the hopes of recovering it.

As for the interface, not really all that important. I guess I could just as easily list everything in a comma-delimited text file to start with, but it makes it easier to find an individual item if the info is in a table format.

---

### Post by samalex on 2010-04-18
> **rebeltaz said:**
> I am trying to find a program that I can use to keep track of items and their associated model and serial numbers, preferably in a table format. Years ago, on a windoze computer, I used a program called ListPro, and I have just made a table in Word. I was hoping to find a dedicated database program, though. Maybe with the ability to export to a comma delimited text file? 

As you can guess, when I do a search for 'linux database', 99.99999% of the results deal with MySQL...

Any suggestions would be great. Thanks....

A different angle but what about looking at a Wiki to save your info?  You could load a local instance of MediaWiki and it'd be completely searchable and easily edited.  

Just a suggestion-- 

Sam

---

### Post by Paqman on 2010-04-19
> **rebeltaz said:**
> Not really all that big at all... I guess I should have been more specific in the original post. I have more 'toys' that then average bear, so every occasionally I will go around and noting the model and serial numbers of all my important stuff. That way if anything gets stolen, I have a record to show police in the hopes of recovering it.

As for the interface, not really all that important. I guess I could just as easily list everything in a comma-delimited text file to start with, but it makes it easier to find an individual item if the info is in a table format.

Keep it simple then, just use a spreadsheet. If you're worried about stuff getting stolen, put it online using something like Zoho, which integrates really nicely into Lucid. That way you've still got the file if someone nicks the computer.

---

### Post by aysiu on 2010-04-19
Another vote for Glom, mentioned earlier.

---

### Post by rebeltaz on 2010-04-19
> **Paqman said:**
> Keep it simple then, just use a spreadsheet. If you're worried about stuff getting stolen, put it online using something like Zoho, which integrates really nicely into Lucid. That way you've still got the file if someone nicks the computer.

I tried the spreadsheet, but I didn't like it. I'm using OOo Base (what is the little 'o' in OOo, BTW?). 

As for online, I don't trust online file storage services. I'm probably paranoid, but better safe than sorry, I say. Any way, I upload it to my own web server and save the file to a disc which I then give copies of to friends and/or family members as well as keeping copies on all of the computers I own. 

Come to think of it, I gues I am a little paranoid, huh? :)

---

