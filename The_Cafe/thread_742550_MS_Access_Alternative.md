---
title: "MS Access Alternative?"
date: 2008-04-01
forum: The Cafe
---

### Post by hizaguchi on 2008-04-01
Looking for a little constructive input here. :)   At work, I've been tasked with creating a new database-driven application for managing order data.  The old database was done in Microsoft Access, so everybody that will be using this is already familiar with Access and most users (there are only 10 or so users) occasionally add in their own custom queries and macros.  I'm pretty familiar with Access and can manage with Visual Basic, so I'm very tempted to just throw this together in Access and be done with it.

But I figure before setting out on this sizable project, I should ask around and see if there is a better choice.  I need a relational database that I can easily create and modify forms for that are easy for former Access users to use.  I need some kind of scripting support for handling notifications and cross-referencing and things.  I need customizable reports that can be exported to a common format.  I need importing and exporting compatibility, however hacked together it may be, with Excel.  And maybe most importantly, I need something that works like Pivot Tables for displaying order data over time with easily-customized filters.

I know, at least in the past, OpenOffice has some shortcomings in some of these areas.  Has that changed?

Is there any cross-platform (at least Linux and Windows), open source alternative for what I'm trying to do?  Or should I just go ahead and get Crossover and lock us in to Microsoft?

---

### Post by LaRoza on 2008-04-01
You can try the latest OpenOffice Base, and see if it works.

---

### Post by retrow on 2008-04-01
sudo apt-get install openoffice.org-base

---

### Post by igknighted on 2008-04-01
You can use Kexi for MS Access databases in linux IIRC

---

### Post by angryfirelord on 2008-04-01
Base is about the closest thing you can get to, but be aware that it cannot open Access files. If you wanted to use Base, you'd have to rewrite your database. (unless there's some import tool that I'm not aware of)

---

### Post by Mateo on 2008-04-01
^^^ export your tables to spreadsheets, then copy+paste into base.

---

### Post by angryfirelord on 2008-04-01
> **Mateo said:**
> ^^^ export your tables to spreadsheets, then copy+paste into base.
You could do that for the raw data, but you'd still have to make note of how the tables are set up, such as any primary/foreign keys used, relationships between tables, data types, etc.

---

### Post by macogw on 2008-04-02
> **angryfirelord said:**
> Base is about the closest thing you can get to, but be aware that it cannot open Access files. If you wanted to use Base, you'd have to rewrite your database. (unless there's some import tool that I'm not aware of)

OOo 1 didn't work with MS Access files.  OOo 2 does.  OOo 1 required converting it to ODBC or something like that.  OOo 2 (the one included in Ubuntu) should open it directly, except in cases where you have 1GB of memory and a 350MB MS Access db in which case you'll run out of memory before it gets open.  I had that little problem when trying to open Montgomery Co, MD, USA's voter registration database.  Yeah, they use Access for it, because that's totally gonna scale better than Postgresql...:rolleyes:

---

### Post by LaRoza on 2008-04-02
> **macogw said:**
> OOo 1 didn't work with MS Access files.  OOo 2 does.  OOo 1 required converting it to ODBC or something like that.  OOo 2 (the one included in Ubuntu) should open it directly, except in cases where you have 1GB of memory and a 350MB MS Access db in which case you'll run out of memory before it gets open.  I had that little problem when trying to open Montgomery Co, MD, USA's voter registration database.  Yeah, they use Access for it, because that's totally gonna scale better than Postgresql...:rolleyes:

Voter registration database in MS Access? It isn't 01 April anymore...

---

### Post by macogw on 2008-04-02
> **LaRoza said:**
> Voter registration database in MS Access? It isn't 01 April anymore...

I wish it was a joke.

---

### Post by LaRoza on 2008-04-02
> **macogw said:**
> I wish it was a joke.

:shock:

---

### Post by hizaguchi on 2008-04-02
Wow, I appreciate all the feedback.  I think I should clarify some things though.

I'm not too concerned about importing old data or structure.  I figure I can find a way to get data from Access into any other database, especially since it only has to be done once.  And I'll be rebuilding the structure of the database anyway because I'm not happy with the way the current one was done.

I have played around with OpenOffice quite a bit in the past, and then uninstalled it because it didn't meet my needs at all.  Mostly then I was using Writer and Calc, and even they were sub-par.  Now with a little more experience, a different set of needs, and several new versions released, I'll reinstall and try again.  But since I don't expect things to be much different, I'll move along to the meat of my questioning.

I've done some more research and I think what I need is a PostgreSQL database with some kind of form and report designing software to use as or use to make a front end.  I'm looking at using BOND for this, but then nobody else will have a clue how to customize the database without them having to learn XML.  So really I'd love something like Access or Kexi or even Base for making the forms, but then I want the finished product to stand alone without needing to run a clunky database environment to do simple data entry or look something up.

Is there a graphical database GUI designer that is intuitive and easy to learn that will produce cross-platform forms that I can use with a PostgreSQL database?

---

### Post by Mateo on 2008-04-02
To answer your question plain; no, there are no form designing software that is intuitive and allows you to run the forms standalone.  there are some forms software out there, but they are either a) very primitive and unintuitive (postgres forms) or b) too restrictive and require its own application (glom).  i'm currently using base as the frontend for my postgresql databases.  i'm looking for a better solution that doesn't require learning a programming language.  let me know if you find something.

---

### Post by hizaguchi on 2008-04-02
That's what I was afraid of. :(  I'm playing with both Base and Kexi now, and neither really measures up to Access for speed or ease of use.  Still to early to say whether they're better or worse overall, but I'm leaning toward Access as my favorite of the three.

---

### Post by madjr on 2008-04-02
> **hizaguchi said:**
> That's what I was afraid of. :(  I'm playing with both Base and Kexi now, and neither really measures up to Access for speed or ease of use.  Still to early to say whether they're better or worse overall, but I'm leaning toward Access as my favorite of the three.

was it base in Ooo 2.4 ?

i hear is much better than the one in ubuntu 2.3

you could also try IBM's lotus symphony, it has some nice features and it's FOSS.

your findings could help a lot in the dev of the big OOo 3.0 release if you find the time to ask for the features.

anyway even if you end up with access, you tried all the other options first. Trying not to get locked, as you state, to 1 vendor is is always a good thing and FOSS's primary goal :)

good luck on your proyect :)

---

### Post by jflaker on 2008-04-02
The ultimate direction would be to develop a PHP/MySQL version of the application you use today..........With MySQL, you can develop table relationships as well as data normalization, as you can in Access......plus, with the PHP web, you can quickly change your interface without much effort.........



It is probably a much larger undertaking than you are ready for, but to make your current application truly portable would mean bringing it to the web.

---

### Post by thisllub on 2008-04-02
> **hizaguchi said:**
> That's what I was afraid of. :(  I'm playing with both Base and Kexi now, and neither really measures up to Access for speed or ease of use.  Still to early to say whether they're better or worse overall, but I'm leaning toward Access as my favorite of the three.

There is a better way.

I have a large legacy Access site. Access 97 in fact. Access 2000 was a dog and I haven't tried anything newer.
I have replaced about 60% of it and hope to entirely replace it with AJAX / PHP by next year at the latest.

Look at Firebird [www.ibphoenix.com](www.ibphoenix.com).
Free and open source it works flawlessly with Access and has many advantages over MySQL and POSTGRESQL.


There are some excellent GUI tools - Flamerobin (Linux) Marathon (Windows) for database management.

Although I wouldn't start a project with Access today it doesn't mean that it  would be wrong to do so.
You can use Access for some tasks, write all of your reporting in PHP and get the best of both worlds.
Trust me on the reporting side PHP is the best report generator you can get.
As your PHP skills improve you can replace Access with PHP.
I will probably always use Access for importing data and as a tool for quickly generating SQL for complicated queries.
Unless I have to use a new version of Access.

---

### Post by Mateo on 2008-04-02
i always edited queries in SQL code, even when i was using access. it just seemed more simple to understand for me.  access was just nice to quickly create a table, which is cumbersome in SQL.  And of course it's nice to be able to build a form without taking weeks.  usually when i'm building a database I need to use it *now*.  i'm building a checkbook application in ruby/postgres but i'm also using Base for my day-to-day account organization.

I wouldn't give up on Base.  It might not be as good as Access but it's not exactly a bad product either.  It can do most of what Access can do.  Unless you use some truly advanced features in Access that i'm not aware of.  Mostly it's just that Access' report designer is more intuitive (though I think Base is better for form letters).  You can use Base with a MySQL or PostgreSQL database (which is what I do), and it works pretty well as a frontend for that.

edit:  i wouldn't go the PHP route, personally.  It's too sloppy and teaches bad habits IMO.  though the one advantage is that it's fairly easy to learn.

---

### Post by thisllub on 2008-04-02
> **Mateo said:**
> 
edit:  i wouldn't go the PHP route, personally.  It's too sloppy and teaches bad habits IMO.  though the one advantage is that it's fairly easy to learn.

I have never agreed with that as justification for non-use of a language / system.

Sloppy code might be a justification for not hiring a developer though.

I see a gulf between application and system programming. PHP is more than adequate for app programming.  It may *allow* bad habits but it doesn't each them.

---

### Post by hizaguchi on 2008-04-03
I hadn't really considered PHP because I associate that with web applications and I *hate* web applications.  Maybe I need to research some more, because my total lack of experience probably gives me tunnel vision.  But still, if it's going to involve much of a learning curve I'm doubtful I can justify it to an office full of Access power users.

Yeah, the version of Base I'm tinkering with is 2.4.  It is much better than the last time I gave it a try, but it's still got a long way to go.  The interface is organized nicely and it didn't take me long to figure out how to do alot of the things I needed to do, so it isn't a terrible program.  But Access is faster (performance wise), integrates with Excel seamlessly, is already installed, and everybody in the office knows exactly how to use it.  I could probably get everything I need working in OpenOffice (though some things not as smoothly), but it doesn't bring anything new to the table in exchange for the slight learning curve and sluggish performance I'd be forcing on everybody.

Update:  I've just run across Qt Designer, which from what I can tell has some graphical form designing capability.  This may be exactly what I need.  Currently downloading the new GPLed Windows version of Qt to see how well I can expect it to work.

---

### Post by Tundro Walker on 2008-04-04
I was digging around for an MS Access-like db for Linux, too, and I could have swore there was some KDE equivilent.  Maybe that's Kexi, which you've been mentioning?

I really hate to do this, but as much of a pain in the butt as MS Access can be at times, you're probably better off sticking with it for now.  It's very flexible, and provides a decent common ground for beginner's and advanced users.

I think what I would do in your situation, though, is try to farm the back-end database tables off onto like MySQL or MS SQL Server, or Oracle, then use MS Access as a thin-client to store all the forms, queries, etc.  Instead of linking in the server tables and making queries from them, opt for pass-through queries, which run much faster since they're done server side.  Access' query engine is notoriously slow sometimes with linked tables.

So, you'd have this back-end data server, and each person would have their own copy of the MS Access db client, which they could bloat up with their own queries and such.  You'd keep a main development copy of the Access db, which you'd make the base changes to common forms and things to, then everyone can just import the updated common forms, queries, etc.  You can even do up a macro or VBA script that would delete all the old common stuff before re-importing it, that way folks don't get stuck renaming things to get the "2" off the end.

If you're strapped for developer resources, then MS Access is a low-cost solution.  However, due to its limitations, it's really just for small-scale db operations.  If you're just using it with 10 folks, then no problem.  You could even use on MS Access db as your "back-end" to store the tables everyone's client-side version links in to.  You just need to make sure it doesn't get too bloated.  MS Access has a nasty habit of "going critical" if it reaches like 500mb or such.  The db can crash, and you might be able to compact/repair, but more likly you end up having to import all the stuff into a new MS Access db to recover from it (had a guy at EDS that this would happen to a lot until I broke his main MS Access data db into sub db's that each stored chunks of tables ... the developers wouldn't let us turn it into a SQL Server table structure, so we were kind of limited on our options.)

Anyways, make sure you untick the "Track changes" and stuff, too, since that's been known to corrupt an MS Access db over time.

I'd say just stick with it, and use MS Excel as your output / reporting tool.  I personally automate MS Access db's with VBA to tap into various data sources (SQL Servers, Oracles, etc) compile data, spit out MS Excel reports with pivot tables, save it some where, then automate MS Outlook (using Redemption .dll to avoid the security pop-up) to email the reports to folks.

That trio is a very good, low-budget office automation grouping if you're lacking real software developers to make things more robust and large scale.

You're right, though.  It'd be nice if Base would finally catch up to Access.  I'd like to really mess around with using an MS Access-like db that uses the simpler Python scripting instead of jacking around with VBA all the time.

So, I guess if you had the choice, rely on in-house software development to build & develop your solution, or see if the budgeting and tech departments can help you purchase a third-party tool along with a service level agreement stating the third-party will help you implement, upgrade and keep it going.  Using a third-party tool means it's faster to implement, but it may not have all the bells and whistles you want.

If you're stuck with a low budget and very little development resources, just stick with what you know.  If the MS Access db you create turns into something the company can't live without, they'll eventually figure out a larger-scale replacement for it soon enough.  But for now, at least you'd be in control of developing it and getting it running just the way you like (which can be good if you're good with MS Access, or a nightmare if you're not so good with it.)

---

### Post by mariuz on 2008-04-16
i agree with the firebird post from above 
an good openoffice+firebird backend can replace access and mssql anytime , here is the howto for firebird + openoffice setup

[http://jobinau.googlepages.com/OOFB.htm]("http://jobinau.googlepages.com/OOFB.htm")

another guide here 
[http://www.firebirdnews.org/?p=1589](http://www.firebirdnews.org/?p=1589)

---

### Post by Tundro Walker on 2008-04-16
Forgot to mention the main annoyances with MS Access ...

1) If you have folks using different versions of MS Access tapping the same db (front-end, for instance), then the folks with the highest MS Access version will end up setting the MS Access code reference to their version, and folks with lesser versions logging in will get an error saying "can't find the MS Access code library."

EG: Had some folks at one job using MS Access 2003 (MS Access version 10 lib).  I did a db in MS Access 2000 (MS Access version 9 lib).  They got into my db to do some stuff, then I tried getting in, and it told me I didn't have the version 10 lib.  Turns out their more recent version of MS Access "upgraded" the lib reference, with no reference to the old lib.  So, I had to find some really annoying jury-rigs around this.  (Basically had to make different version 10 & version 9 front-ends for whomever was using the different versions of MS Access).

2) Some folks end up with a "crippled" MS Office installation that can't run advanced VBA code.  You can test for these setups easily by making a small VBA function that simply does ...

```
function test_msg()

 msgbox currentdb.name

end function
```

If it gets an error code, then they have a hobbled VBA install.  Error message usually says something like the .dll isn't found or something.  It might be that their version is having a hard time re-referencing the lib like I mentioned above.  

In any case, both of these are very annoying, because you might develop some good stuff that works on your comp just to find out it fails miserably on other peoples machines.

I think those are two very solid points for looking into alternate db solutions than MS Access.  (Stupid Microsoft keeps renaming the *** **** lib every version of Access they dump out ... *grumble-grumble*)

---

### Post by Jenske on 2008-05-12
I've been working with Access for about 15 years now (on Windows). At home and since about 4 years, I've been exclusively working with Ubuntu.
I _HAD_ some databases, "written" in MS Access, that worked perfectly for me, so I was very interested in any good db-system that would more or less have the same possibilities as Access.
Unfortunately, until now and to my opinion, there is none. Base is quite good, but only recently it is able to alter field names or field order in the database _without_ deleting all data (sic!).

Everyone on several forums said "they" were working on it, but it's pretty damn annoying if, having installed this or that database system, having tried to simply copy data from my old MS Access data to this new system and having to discover that ...
-- the database explodes in size (base makes a database about a zillion times the size of a spreadsheet containing the same data)
-- OO Base works with my data, but works extremely slow (worse than using a Commodore 64 ???)
-- Kexi is still in its developmental stages

_BUT_ since several months there have been major improvements to db-systems that work in Linux. I've tried Kexi, OpenOffice base, even Tellico. Depending on what you need, I'm pretty sure these days it _IS_ possible to use these--especially OO Base--for 'normal' home databases.

Biggest problem: I've no clue on performance in a multi-user environment.

Based on my current experience I'd set up a database like this:
-- have data stored in a MySQL system ('backend')
-- address data from MS Access or Base ('frontend')

---

### Post by Mr. Picklesworth on 2008-05-12
[Glom]("http://www.glom.org") is one really interesting database tool, although a tad different from Access. Extremely flexible, of course, and quite useful :)
It's in the repositories, via Add / Remove Programs. Unfortunately, the version packaged with previous Ubuntu releases has generally been a bit ugly. If you are running Hardy, though, it should be quite satisfying!

---

### Post by Crick on 2009-02-20
> **hizaguchi said:**
> 
I've done some more research and I think what I need is a PostgreSQL database
Absolutely. It's an extremely sound choice for a typical business database, especially to replace an MS access backend. Security, data integrity, flexibility, speed, it has it all. I use it, and it's brilliant. The user community is wonderful.

I looked into the choice of frontend two years ago. I'm not sure glom existed then. Unfortunately, nothing had the speed and convenience of application development that Access has. I didn't want to cripple my users with a web front end - the speed would be too slow for lots of data entry.

Probably the biggest thing missing for me with the alternatives was the ease of designing forms with subforms. I use that all the time and I didn't find it in the FOSS offerings.

There are a lot of things you have to do to workaround issues with Access and Postgresql, but most can be worked around I've found. Let me know how you go with Glom.

---

### Post by Mr. Picklesworth on 2009-02-20
May be worth trying [Glom 1.8]("http://www.murrayc.com/blog/permalink/2009/02/19/glom-18-bug-fixes-ubuntu-packages/"), by the way. It's in the [Openismus PPA]("https://edge.launchpad.net/~openismus-team/+archive/ppa").
Lots of bug fixes :)

(Although it also needs an "unofficial" backport of libgoocanvas, which other apps *should* be fine with but we can never be sure, so use at your own risk).

---

### Post by 7penselen on 2011-02-27
I'm needing a good and userfriendly database frontend.

I tried OOBase 3.21 which is really not working well and it misses any sense of logic. Esspecially the form designer. This program costs a lot of time without getting real results. Oldy MS-Access 2000, which I've used 10 years ago works 10 times better

Kexi 2.2.2. This program is not ready and cannot link several databases well. I think this program has potential but I need it now and not over 2 years. 

and finally i tried GLOM didn't startup. 
 Not the repos and not 
openismus-team-ppa-maverick.list

~$ glom 
ConnectionPool::get_and_connect(): m_backend is null.
**
Gtk:ERROR:/build/buildd/gtk+2.0-2.22.0/gtk/gtkrecentmanager.c:1942:get_icon_fallback: assertion failed: (retval != NULL)
Aborted

Is their a database frontend with reasonable features like linked forms of linked databases which are working? I'm more than a week busy without any result? Is their a web-based on PHP tool I can install on my computer who can make forms with subforms?

I use Kubuntu 10.10 on a eeePC and on my main PC.

---

### Post by Perfect Storm on 2011-02-27
[[img]http://s4.postimage.org/jbyj0j85e/Thread_Necromancer.jpg[/img]](http://www.postimage.org/)

Thread closed.

---

