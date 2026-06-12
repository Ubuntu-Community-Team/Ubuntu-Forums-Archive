---
title: "Rate my web portfolio"
date: 2007-03-01
forum: The Cafe
---

### Post by kthakore on 2007-03-01
For a web developing job, I was asked to make my own web portfolio. I was just hoping to get some feedback to improve it. here is the site [http://kthakore.info]("http://kthakore.info"). All critiques good and bad are welcome, just be fair and let me know how I can improve the site.

---

### Post by notatoad on 2007-03-01
decent, but definitely doesn't stand out from the crowd in any way. 

also, hovering over the main navigation buttons makes the body of the page shift down a couple of pixels.

---

### Post by PartisanEntity on 2007-03-01
spelling mistake:

>  I have struggled **trough** problems and hurdles,  should be 'through'.

I would get rid of the italics, doesnt look good.

---

### Post by kthakore on 2007-03-01
thx a lot I made the changes.

```
 	decent, but definitely doesn't stand out from the crowd in any way. 
```

what would you suggest I do to make it stand out?

---

### Post by Bloodfen Razormaw on 2007-03-01
Have you done anything with enterprise-grade frameworks?  PHP and MySQL won't take you very far.  If you have experience with .NET or Java web frameworks and SQL Server or Oracle you could find yourself making a pretty penny.

---

### Post by teet on 2007-03-01
> The University of Western Ontario, London, Ontario
Bachelor of Electrical Engineering with Medicine, expected Apr 2013.

2013?  Geez, Are you sure that's not a typo :-P

-teet

---

### Post by kthakore on 2007-03-01
```
 	
[CODE]Quote:
The University of Western Ontario, London, Ontario
Bachelor of Electrical Engineering with Medicine, expected Apr 2013.
```
2013? Geez, Are you sure that's not a typo
[/CODE]

nope that is not a typo, that is my degree module right now.

---

### Post by kthakore on 2007-03-01
```
Have you done anything with enterprise-grade frameworks? PHP and MySQL won't take you very far. If you have experience with .NET or Java web frameworks and SQL Server or Oracle you could find yourself making a pretty penny.
```

no I have no experience in enterprise-grade frameworks. What are they? Where can I find information on them?

---

### Post by FyreBrand on 2007-03-02
Your sites look nice.  Just a couple pieces of feedback:

1. You Angelina site has an unsupressed MySQL fetch array warning showing up on the page.  It would be good to fix whatever you did with $result that PHP didn't like or at least suppress the warning so it's not visible.

2. This is more of a personal preference.  I use NoScript and don't let a site run anything until I think it might be safe.  Your sites break almost all the way with script blocking.  I think it's nice when a site at least has content if not dynamic functionality with scripts blocked.  Like I said that's more my personal preference.

3. I'm not a big fan of the floating mouseovers above the portfolio thumbnails.  Again that's just a personal preference so if you like it keep them.  I just don't like that kind of stuff.

Overall very nice work.  I hope you find work soon.  The web seems to show lots of work around for good PHP programmers so good luck!

---

### Post by drfalkor on 2007-03-02
I think you need to have thinner borders, more freshness and sharpness.. this was pretty good: [http://www.saifluidpower.com/](http://www.saifluidpower.com/) ..if it was a media site, I would make it more fresh and wet. But, if it is a company site, I would make it dry, sharp and just a drop of freshness, but no wetness.. just like this: [http://www.saifluidpower.com/](http://www.saifluidpower.com/) :)

---

### Post by kthakore on 2007-03-02
thanks I will work on the sharpness and a handle for javascript turned off.

---

### Post by Bloodfen Razormaw on 2007-03-02
> no I have no experience in enterprise-grade frameworks. What are they? Where can I find information on them?
The ASP.NET and SQL Server combination is getting very popular.  If you have a Windows computer, install Visual Studio Express (C# and Web), and SQL Server Express and learn .NET/C#, ASP.NET, and ADO.NET.  ASP.NET is also doable with Mono and Apache, although it involves lots of config file editing.  You can get into Java frameworks by looking at products like Java Server Pages, Struts, Tomcat, and the list goes on and on.  There are a lot of free Java products from Apache, and even though many of them aren't all that great and won't be used in many production environments, listing them will still show you have Java framework experience and look professional on a resume.

---

### Post by FyreBrand on 2007-03-02
> **Bloodfen Razormaw said:**
> The ASP.NET and SQL Server combination is getting very popular.  If you have a Windows computer, install Visual Studio Express (C# and Web), and SQL Server Express and learn .NET/C#, ASP.NET, and ADO.NET.  ASP.NET is also doable with Mono and Apache, although it involves lots of config file editing.  You can get into Java frameworks by looking at products like Java Server Pages, Struts, Tomcat, and the list goes on and on.  There are a lot of free Java products from Apache, and even though many of them aren't all that great and won't be used in many production environments, listing them will still show you have Java framework experience and look professional on a resume.There is plenty of potential in enterprise java, php, and increasingly python and ruby.  There are plenty of enterprise corporations that use apache as their web server and mysql or postgres for their back-end.  Feel free to point out the glories of Microsoft development but expect that people will point out many of the reasons why companies and developers don't want to work on that platform.  MS SQL server is insanely expensive for what it delivers and working on a MS server with IIS sucks.  Maybe you've locked yourself into MS development but please don't recommend the rest of us do the same.

Ugh.  Should we go buy Vista and Visual Studio 2005 too?

---

### Post by kthakore on 2007-03-02
I agree, I would rather not have to use IIS MSSQL or .NET but if I need these skills to get a job, there isn't much I can do. Thx for the info on java web frame works, I will look into them.

---

### Post by Bloodfen Razormaw on 2007-03-02
> There is plenty of potential in enterprise java, php, and increasingly python and ruby. There are plenty of enterprise corporations that use apache as their web server and mysql or postgres for their back-end. Feel free to point out the glories of Microsoft development but expect that people will point out many of the reasons why companies and developers don't want to work on that platform. MS SQL server is insanely expensive for what it delivers and working on a MS server with IIS sucks. Maybe you've locked yourself into MS development but please don't recommend the rest of us do the same.
That's pretty ignorant.  Microsoft shops are extremely common.  If you think no one wants to use IIS, you clearly don't work in the real world.  Businesses need support options, and there are no free software support options that cover the entire software stack.  A business who doesn't want multiple companies passing the buck on where the problem they are having lies only have three choices for unified OS, database, and web: Sun, Oracle, or Microsoft.

*NO* reasonable production environment uses MySQL.  It isn't a viable option for any serious database use.  It isn't nearly reliable or scalable enough.  We are talking about a DBMS for which ACID compliance is *new*.  Companies are not going to gamble their business on a database which silently errors out and leaves their data inconsistent.  Postgres is good enough, but it doesn't matter since the only vendor that will support it is Sun, and most Sun shops abandoned the Sun software stack before Postgres was supported.

>   I agree, I would rather not have to use IIS MSSQL or .NET but if I need these skills to get a job, there isn't much I can do. Thx for the info on java web frame works, I will look into them.
You can use [Mono and Apache.](http://www.mono-project.com/ASP.NET)  The ASP.NET 2.0 implementation isn't perfect yet, but that's okay since the average ASP.NET developer is still incompetent with even 1.0 features.  You can learn the ADO.NET API with the drivers for Postgres or Oracle in place of SQL Server.

---

### Post by FyreBrand on 2007-03-02
Microsoft shops are common for Microsoft users that's true and there is plenty of call for that but it's no more ignorant than saying "MS is the only enterprise solution".  That *is* a joke.  I'm doing a .NET project right now because that's what the client wants, but I certainly wouldn't promote that as the primary solution.  Why would you want to promote, as a primary solution, the worst alternative imaginable?

I would never recommend a MS solution as a first choice.  I would also never recommend heading in that direction as a developer.  That is a one way ticket to being locked into a very expensive single vendor solution.

Here is a list of [**enterprise corporations using MySQL**]("http://www.mysql.com/customers/"):
Apple, Amazon, Cox Communications, Craigslist, Digg, Google, LiveJournal, NASA, Wikipedia, Sabre, Travelocity, Slashdot, WordPress, and Yahoo!

Here is a list of [**postgresql users**]("http://www.postgresql.org/about/users").

It seems there's billions of dollars of corporate money that disagree with your assertion that "NO reasonable production environment uses MySQL".  Work is work, but you're promoting a bunch of bunk.

Like I asked before do you want him to purchase Vista (enterprise) and MS Visual Studio 2005, and an MSDN subscription?  Because he's going to need it to be a MS developer.  There's more to what you're pushing than what you're saying.

---

### Post by Bloodfen Razormaw on 2007-03-02
> Microsoft shops are common for Microsoft users
How trite.  Microsoft shops usually are Microsoft users, that's true.

> "MS is the only enterprise solution". That is a joke
So far these words have only been uttered by you.  I've listed three supported enterprise software stacks.

> Apple, Amazon, Cox Communications, Craigslist, Digg, Google, LiveJournal, NASA, Wikipedia, Sabre, Travelocity, Slashdot, WordPress, and Yahoo!
None of these are impressive.  I suggest you go compare the number of available jobs for MySQL to those with SQL Server.  On Monster.com it won't even list all the results for SQL Server there are so many (it stops at only 2.5x as many jobs as MySQL).  Same for Oracle.  Try the same for comparing PHP to ASP.NET or Java.  I can find as many jobs in five states for ASP.NET as I can for the entire United States for PHP.  For Java web jobs, it only takes two states.  That's the difference in corporate adoption of PHP/MySQL to ASP.NET/SQL Server and Java/Oracle.

> Like I asked before do you want him to purchase Vista (enterprise) and MS Visual Studio 2005, and an MSDN subscription? Because he's going to need it to be a MS developer. There's more to what you're pushing than what you're saying.
I feel sorry for your .NET customers if this is how little you understand .NET development.  Not a single product you listed is necessary for developing with .NET.

---

### Post by FyreBrand on 2007-03-02
> **Bloodfen Razormaw said:**
> How trite.  Microsoft shops usually are Microsoft users, that's true.


So far these words have only been uttered by you.  I've listed three supported enterprise software stacks.


None of these are impressive.  I suggest you go compare the number of available jobs for MySQL to those with SQL Server.  On Monster.com it won't even list all the results for SQL Server there are so many (it stops at only 2.5x as many jobs as MySQL).  Same for Oracle.  Try the same for comparing PHP to ASP.NET or Java.  I can find as many jobs in five states for ASP.NET as I can for the entire United States for PHP.  For Java web jobs, it only takes two states.  That's the difference in corporate adoption of PHP/MySQL to ASP.NET/SQL Server and Java/Oracle.


I feel sorry for your .NET customers if this is how little you understand .NET development.  Not a single product you listed is necessary for developing with .NET.If you want ot argue a development platform fine.  Ad Hominum attacks because you don't really have an argument isn't.  I see you dismiss Google and Apple as serious enterprise businesses.  Interesting.  It goes a long way towards your credibility.

I see by your previous posts that personal attacks are a norm and that you are a strong Microsoft platform/application supporter.  End of discussion with you.

---

### Post by Bloodfen Razormaw on 2007-03-02
Yes, Microsoft is evil, therefore the fact many many more businesses use SQL Server and Oracle is not proof at all that more businesses use SQL Server and Oracle.  And even thought you are very disingeniously trying to deflect attention from your inability to support what is clearly just Microsoft-hating for the sake of trying to be cool, I will point out that I have yet to attack you personally:

I have jokingly noted that you aren't very experienced in .NET development, a reasonable assumption since your statement that .NET development requires Vista shows you are unaware that .NET works on other Windows operating systems, and that Microsoft provides a shared source .NET implementation for FreeBSD and OS X.  Your statement that Visual Studio 2005 is required shows that you are not aware of .NET IDEs like Sharpdevelop or Monodevelop, or that any text editor can write source code for .NET languages.  Your statement that an MSDN subscription is required shows...that you don't realize an MSDN subscription isn't required.

I have also noted that you were ignorant of the corporate market.  Again, this is true.  Ignorance means you don't have a thorough understanding of the subject.  The fact, again, that a mere job search shows that ASP.NET and Java web frameworks are totally dominant over PHP and MySQL, joined with your insistent to the contrary, shows you do not know the subject well.  Add to that that you then cite Apple, a business notoriously bad at handling server issues, as proof of MySQL's greatness.  Then Google.  Google won't touch MySQL for searching.  They only used it to cobble their advertising system together quickly.  To quote Google: "Using MySQL was acceptable as an expedient to get things up and running quickly and with a minimal of capital outlay, but now that things were settling down it was time to recognize that this was really, fundamentally, a mistake, and it should be fixed sooner rather than later."  They only ended up sticking with MySQL because of problems porting their code to a different database.  That's pretty solid evidence of MySQL's problems.

If you STILL can't find anything to back up your claims, at least don't try to raise red herrings.  I think it has become clear that you are proclaiming MySQL and PHP to be accepted by large enterprise because you WANT it to be, rather than because it is.

---

### Post by kthakore on 2007-03-02
Bloodfen Razormaw stop. This thread is for critique on my website. Please keep comments to that. I don't want to start another Microsoft hating site. Bloodfen, Fyrebrand simply meant to  say that IF I want to make more money in the web development field I should look into these technologies, nothing else. He was not giving preferences to microsoft products or open source ones. And I am a PHP/MYSQL developer, or I want to be one, it is entirly my decision if I end up taking Fyrebrand's advice into consideration or not. Just critique the website that is all. I enjoy your opinions but again keep on topic for this thread. Sorry if this comes across as harsh but there is no need to start getting nasty.

---

### Post by Bloodfen Razormaw on 2007-03-02
Indeed, I shouldn't have gotten distracted, and I apologize to you.  I can get riled up when I see people try to support their position with outright lying (e.g. saying you need Vista/Visual Studio/MSDN subscription).  However I should point out in my defense that *I* was the one suggesting you look into those technologies for more money. :)  Don't ignore Java and .NET, the two dominant web technologies, based on inaccurate information.  You can easily learn both of them in the comfort of your Ubuntu installation, without paying a dime, despite any claims to the contrary.

Your portfolio shows you have plenty of experience as a designer, and fairly varied experience at that.  But I think by being both a web designer AND a web developer, you will end up with employers fighting over you.  It's rare to find someone that can do design and development equally well.  If you can draw up a sample application written in Java, you will open up a HUGE portion of the job market.

---

### Post by kthakore on 2007-03-02
thx for that, how dod you suggest I begin learning java for the web. I mean should I start with applets, jsp or frameworks? I really unsure on why java is need, can't php, DHTML and mysql do anything java can do?

---

### Post by kthakore on 2007-03-02
Also I wanted to know what else I can put on my portfolio to show off my skills in wed development and design.

---

### Post by Bloodfen Razormaw on 2007-03-02
Java isn't a replacement for DHTML.  Java would be a replacement for PHP.  Java is a much more powerful and cleaner language than PHP.  PHP has a lot of poor design decisions; it's inconsistent, weakly typed, and not easy to maintain or change over time, and it's brutally slow.  It also tends to be very insecure.

Java in particular has an especially rich array of mature libraries for data (.NET has a few as well, but nothing as mature).  There are countless persistence libraries, object databases, and web frameworks that make interfacing with data easier.  Java won't replace the database (unless you use something like db4o, which is an object database written in Java).  You can use MySQL easily with Java, it's just that MySQL isn't a very reliable database.  I'd think that installing something like Apache with Tomcat and/or Struts, and Postgres would be a great start.  It really doesn't matter which database you use for the sake of learning; JDBC (Java's data libraries) and ADO.NET (.NET's data libraries) share interfaces among classes that implement drivers, so by learning one driver you learn most of what you need for using any other.  With careful programming you can make your web apps very database-agnostic.

As for your portfolio, I think it's already decent.  I agree with the man who said "it doesn't stick out," but that isn't really such a bad thing.  If I were looking for someone to hire, I'd mostly be looking for someone who I knew could give me what I envisioned, and since each of your sites is a fairly different design, that tells me you probably could do it.  My first instinct would be to look for variety.  Anything that increases the apparent range of experience you have would make a good addition IMO.

---

### Post by pulver on 2007-03-02
```
<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</strong></p>
```

About the site. I think you need to rethink your design, it's bloated and slow, and feels like navigating through mud (does this work better in internet exploder?) which is annoying. And drop the ajax thing. My suggestion would be redo the whole thing from scratch, and learn some dynamic html. 

It doesn't stick out visually, maybe you should get in touch with a visual artist for ideas and feedback, if you want it to sell yourself that is. Or maybe you could specialize in some area of web development like programming or something? Anyway I'm sure you will do fine in whatever you choose to do if you put your mind to it. Your portfolio will not get good ratings from me though.

---

### Post by kthakore on 2007-03-02
```

[CODE]Code:

<p><strong>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</strong></p>

```
About the site. I think you need to rethink your design, it's bloated and slow, and feels like navigating through mud (does this work better in internet exploder?) which is annoying. And drop the ajax thing. My suggestion would be redo the whole thing from scratch, and learn some dynamic html.

It doesn't stick out visually, maybe you should get in touch with a visual artist for ideas and feedback, if you want it to sell yourself that is. Or maybe you could specialize in some area of web development like programming or something? Anyway I'm sure you will do fine in whatever you choose to do if you put your mind to it. Your portfolio will not get good ratings from me though.[/CODE]

oops thats a glicth in my data entry application. Thx for pointing it out. I only used ajax to keep the site small. but I will take your advice and work on it. thx again.

---

### Post by Tomosaur on 2007-03-03
You need a LOT more confidence. Don't admit that there are things you need to learn - just state what you already know, what you've done. Any flaw or weakness will be magnified by any prospective employer. You can overcome those hurdles in the interview when the employer asks you directly about your experience - just keep confident and calm and don't try to bluff it. If they hit you with 'Do you know X language?', turn it to your advantage - say you've read about it but have been busy boning up on Y language (replace Y with a language you know well, but isn't a 'duh' language, like HTML or something).

---

### Post by kthakore on 2007-03-03
good point!!! I missed that completely. I feel stupid. Thx. The reason I put that modesty bit, is because I wanted to say that I am always ready to learn anything to get the job done!

---

### Post by kthakore on 2007-03-03
I was just wondering why exactly JSP is good to know. Can't I continue in PHP and use a MVC framework for it. Why exactly are Java frameworks better than PHP's? Also does anyone know a MVC framework for PHP written only in PHP, or is tat even possible?

---

### Post by s|k on 2007-03-03
I wouldn't say it was professional. Neither in design or functionality (I saw bugs). But we all have to start somewhere.  I like the javascript though.

---

### Post by Bloodfen Razormaw on 2007-03-03
> I was just wondering why exactly JSP is good to know. Can't I continue in PHP and use a MVC framework for it. Why exactly are Java frameworks better than PHP's? Also does anyone know a MVC framework for PHP written only in PHP, or is tat even possible?
You certainly don't have to know Java web development.  But because Java is so much safer, faster, consistent, and has enterprise support, it has become the dominant web technology.  If you learn Java the largest segment of web development jobs become available to you.

---

### Post by kthakore on 2007-03-03
Thx bloody, yeah u are rite, I have no clue about java enterprise. Can you suggest where I can learn more about. 

@S|K 
Thx for the javascript. Can you let me know the bugs you are referring to so I can work on them. Again thx for the reply.

---

### Post by Bloodfen Razormaw on 2007-03-03
There are a lot of Java web solutions.  I think, for ease of setup, you should start with some of the offerings from Apache and Java EE.  Tomcat, Struts, Tapestry etc.  You can find that information at [http://www.apache.org](http://www.apache.org).  Also research JavaServer Faces, as Sun pushes it themselves.

---

