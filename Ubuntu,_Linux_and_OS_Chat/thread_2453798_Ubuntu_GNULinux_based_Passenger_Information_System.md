---
title: "Ubuntu GNU/Linux based Passenger Information System"
date: 2020-11-17
forum: Ubuntu, Linux and OS Chat
---

### Post by danceswithcycles on 2020-11-17
Hi folks,
I am launching a new project for an everywhere available,  free as in free speach and universal passenger information system for  public transport.

Can you recommend frameworks, technologies or  programming languages that are running on the server (the back end) to  interact with mobile, smart devices for data exchange?

My prototype is a LAMP server that uses HTTP POST and GET to exchange data from mariadb (mysql) to android apps.

I  have the gut feeling that this strategy is not able to realize more  complex business logic or more elaborate use cases. I am also spending  many thoughts about the interface between back end and mobile device.  Many protocols on application layer for data representation like HTTP,  XML, JSON and so on could be used and I am unsure about pros and cons.  Does anyone has experience with free/libre back end development as well  as protocols and standards for the interface to the mobile device? My  strong domain is embedded systems development. That is why I can make  use of any help for the back end.

Do you think I can stay in the free/libre software domain to realize my project?

I  made first experiences with Replicant as alternative to Android and it  looks quite promising. The limited number of supported devices makes me  some headaches.

Cheers?

---

### Post by TheFu on 2020-11-17
please make it work offline too.

Good frameworks will output whatever data format you like with their REST implementations. I use Dancer and DBIx, but most people would probably choose a different language.  WSGI/PSGI makes scaling out easy.   Obviously, anything using the internet needs to use https.

Avoid coding to any specific dbms ntil much later.  That layer will change a few times, so delay any custom code until an expert joins the team and encourage supporting the main 5 dbms.  Use an ORM.

Never trust any client request.  They can are are often replayed or spoofed.

Don't get into legal trouble "borrowing" schedule data. In some parts of the world, that data is copyrighted and cannot be stolen without prior, paid, written, approval.

---

### Post by danceswithcycles on 2020-11-17
@TheFu: Hi and thank you so much for your thoughts. Are you suggesting Objects relational mapping by using an object oriented database management  system? Or did I get your reply the wrong way? Do you have experience with a concrete candidate? My first idea is to use mariadb but the question how to map the data object model is still open. How does that sound to you? Cheers!

---

### Post by danceswithcycles on 2020-11-17
@TheFu: As I am an embedded software engineer that is new to web development, all that sounds very unfamiliar to me. The only scripting language, apart from bash, that I have slight knowledge of is PHP. WSGI implementation in PHP exist, right? Do you know good examplees or tutorials I can try to learn this approach?  It sounds very resonable on the first glimpse. Cheers!

---

### Post by TheFu on 2020-11-18
> **danceswithcycles said:**
> @TheFu: Hi and thank you so much for your thoughts. Are you suggesting Objects relational mapping by using an object oriented database management  system? 
No to "using OO-DBMS" - the other one.

> **danceswithcycles said:**
> 
Or did I get your reply the wrong way?  
Perl has DBIx. Ruby has RAILs.  Something like that to abstract your code away from direct DB calls. DBIx is almost always faster than custom db calls and supports like 15 DBMS.

> **danceswithcycles said:**
> 
Do you have experience with a concrete candidate?  
I don't work with concrete. Just software. I know about enterprise scaling from years doing at huge companies, but we used commercial solutions most of the time.  There are F/LOSS versions.

> **danceswithcycles said:**
> 
My first idea is to use mariadb but the question how to map the data object model is still open. How does that sound to you? Cheers!
MariaDB is fine, but I like options. sqllite and postgressql are good for specific needs too. Let the customer decide. Don't make a choice today to prevent better options.  When you need to scale out the dbms, mariadb wouldn't be my choice.

Basically, the last SQL command you run directly is **create database** and **grant** for the different dbms userids needed.
Of course, daily db backups probably use dbms commands too, unless you use file system snapshots.

imho.  there are different opinions. Hopefully some others will chime in.

---

### Post by TheFu on 2020-11-18
> **danceswithcycles said:**
> @TheFu: As I am an embedded software engineer that is new to web development, all that sounds very unfamiliar to me. The only scripting language, apart from bash, that I have slight knowledge of is PHP. WSGI implementation in PHP exist, right? Do you know good examplees or tutorials I can try to learn this approach?  It sounds very resonable on the first glimpse. Cheers!

I know next to nothing about php. Our security guys won't allow it directly on the internet. This is probably because we don't have any php experts who are able to write secure php code.

If you plan to use php, best to seek out advice from others here and in your part of the world.  Many cities and colleges have php user groups. Seek one out. Listen, participate, ask questions after listening.  With the pandemic, many UGs have moved online for their meetings so you aren't limited to just your own town.  My Linux group has visitors from thousands of miles away almost every week.

My web-app stuff was for Android and iOS, but I wrote the back-end servers in Dancer, as stated already.  Dancer makes webapps and web-services really easy.  In about 15 lines of code, creating a single table web-app that provides REST for XML, JSON, and a few other formats plus a webapp can be done.  In Ruby+RAILS, it is a little more code. I assume it isn't too hard in python.

Hopefully, some other people who have done this will reply here too.

---

