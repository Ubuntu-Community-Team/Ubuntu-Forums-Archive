---
title: "What can I read on how to actually set up my web site?"
date: 2019-09-27
forum: Server Platforms
---

### Post by dora5 on 2019-09-27
What can I read, preferably online, that tells me specifically where to put my web site files and how to configure my web site?

When I google how to set up ubuntu server, I get every sort of instructions on how to set up LAMP, apache, PHP, whatever, without even any explanation what I need them for.  For isntance what would I need a relational database for for a straightforward HTML web site?  They click on the link, I would think it finds it, don't know what one would need to query or for what one would need tables.   Ditto php.    I'm not going to be using Word Press!

And ALL of it stops far short of telling me specifically where to put my files and how to configure it so the public can see my web site.

Thanks!

Dora Smith

---

### Post by Doug S on 2019-09-27
did you try the [Ubuntu Server guide]("https://help.ubuntu.com/lts/serverguide/index.html")? (Also available in [PDF]("https://help.ubuntu.com/lts/serverguide/serverguide.pdf"))

---

### Post by TheFu on 2019-09-27
That's because there isn't any single answer.

"It depends" is the only possible answer.  Plus, you can place static web files almost anywhere you like. Just 1 line config change is needed.  Since most web servers don't host just one website, I have about 20 static sites on my reverse proxy system.

Also, it depends on which web server you are using.  There are 5 extremely popular web servers and probably 50 others used in special situations.

Linux/Unix isn't like Windows. There isn't 1 way or 1 answer.  Plus different distros will have different default location for html files in a trivial, 1-site, setup.

If you aren't using a DB, then you don't need a DB. If you don't know whether a DB is required or not, then you have no business trying to deploy a website.  IMHO.

If you aren't using php, then you don't need PHP.  Ditto about the no business, if you don't know.

LAMP means Linux Apache MySQL PHP most of the time, but it can mean Linux Apache, MariaDB, Perl/Python too.  People assume it is the first, if they don't specify.  LEMP just swaps out Apache for Nginx.  "EngineX" ---> E.

So, it depends.

I've deployed websites under /opt/www, /opt/html, /var/www, /var/html, /var/www/html, /export/www and in ~/public_html.
For web virtual hosting, I tend to use 
/export/www/www.domain1.com
/export/www/www.domain2.com
/export/www/www.domain3.com
....
You get the idea.  I like to make my static web files read-only mounted over NFS. It is a security thing.  Historically, /export/ is for NFS mounts.
Without NFS, I'd do 
/var/www/www.domain1.com
/var/www/www.domain2.com
/var/www/www.domain3.com
...
assuming /var has sufficient storage available.

Clear as mud?

Oh ... every website needs to have a config file.  Inside that config file, the root directory of the website is specified. How depends on web server used.  Most webservers have staging areas (sites-available/) and production areas (sites-enabled/).  Symbolic links are used to "enable" a site for production use, then just reload or start the web server to bring it online.

And don't forget that web servers are almost always multi-user, with each userid controlling access to a specific website.  File and directory permissions are absolutely critical to security of web sites.  This is a common reason that websites get hacked. The webmaster doesn't secure the permissions correctly.

---

### Post by dora5 on 2019-09-27
No.  The answer might be there, in extremely scattered little bits and pieces, that I wouldn't know what they are.   

But I need something readable that puts it all together for me.  And remember, I want to know how to actually set up my web site, not how to install LAMP!  Noone has even explained to me for what I would need which pieces of LAMP!

---

### Post by TheFu on 2019-09-27
> **dora5 said:**
> No.  The answer might be there, in extremely scattered little bits and pieces, that I wouldn't know what they are.   

But I need something readable that puts it all together for me.  And remember, I want to know how to actually set up my web site, not how to install LAMP!  Noone has even explained to me for what I would need which pieces of LAMP!

Nobody **needs** LAMP.  You can install one at a time, if you like, if needed. Don't install what you don't need.

Do you need **L**inux?
Do you need **A**pache?
Do you need **M**ySQL/MariaDB?
Do you need **P**hp?

If you need all those things, then choosing the LAMP option during the Server setup would be easier, because it makes config changes in each so they are connected.  If you don't know which parts you need, then you don't need it.  **For a 1 page, static website, you don't need php or a DB.  **

You might choose apache, but it is sorta like bringing a motor home to the corner market.  Apache is huge with thousands of options.  Complexity is the price for capability.  The specific version of Ubuntu and the specific version of the web server would help someone help you.  Different versions all have slightly different configuration.

Why don't I just say the steps?  Because it is too easy to leave something out here and there are hundreds of other places with the steps. If you choose to use apache, try apache.org or the link provided by  Doug S above.  Looks like it answers the question to me.  If you expect to run 5 lines and be done, forgetaboutit.

We aren't here to do your homework.

---

### Post by SeijiSensei on 2019-09-28
1) Install apache
```
sudo apt install apache2
```

2) Put website files in /var/www/html. There will be an existing index.html that is the demo page. You would obviously need to replace that with the index.html for your site.

This assumes that the machine has only one website accessible as [http://ip.addr.of.server/](http://ip.addr.of.server/) or as [http://hostname/](http://hostname/) or as [http://host.domain.name/](http://host.domain.name/) if you have a domain. In the latter cases you'll need to have some method to resolve names, either using /etc/hosts on the server and on all client machines, or using a DNS server.

You should always be able to see the site from the server itself with [http://localhost/](http://localhost/).

If you need to serve multiple websites with different names, you'll need to create multiple configuration files and use the /etc/apache2/sites-available and /etc/apache2/sites-enabled apparatus. For that you should read the Server Guide.

---

### Post by dora5 on 2019-09-28
Right.  But is there any reason why I need a database or php to make my web site public?  And, is there any reason my umpteen million pages that already exist need to have php extensions instead of html?!

I don't know which part of I need to know the PROCESS people aren't getting.

---

### Post by Irihapeti on 2019-09-28
If you're only going to be using static html pages, you don't need php or a database.

---

### Post by SeijiSensei on 2019-09-28
> **dora5 said:**
> Right.  But is there any reason why I need a database or php to make my web site public?
You'll notice I didn't mention either of them because, as lrihapeti said, you don't need either for a site with static HTML pages.

---

### Post by dora5 on 2019-09-28
It's absolutely astounding what the web sites I found don't mention.  They tell how to set up LAMP or something equivalent without explaining why and then don't say what to do next.  

None of the web sites I found explained what I specifically needed a database or php for.   

Under what conditions would I need the database?   

What can I read that explains in clear English when I need what?  Not I don't believe you, but we only covered a small part of the ground!

---

### Post by TheFu on 2019-09-29
Seems you might not have the background needed for anything other than simple, html-only, websites.  We all started there.  I still make HTML-only websites and I'm trying to move a blog that I run from ruby webapp + DB towards a static website.  Complex webapps are harder to secure, but easier to make for client-side interactivity.  Hacking a set of static HTML files making up a website is much harder than hacking a php or python or ruby or perl webapp. Very few moving parts in static HTML enhances security.

You need a Database if you are going to use a database.  Learning about databases is usually 3 different course in college. Databases store data either permanently or for a transaction.  When would you use a database outside a website?  That is when you would want to use a database inside a website.  If a website needs to save any information, that's usually when a DB might be employed.  I won't get into the different types of DBs, but an RDBMS is just one.  MySQL is 1 specific type of RDBMS, there are many others.  I've used tab-delimited text files as DBs for a very long time. MySQL can't use that sort of file directly.

You need php if you are going to use the php programming language.  Learning about php is 1-3 different college courses.  I would never say that anyone needs php, ever.  I have a personal bias against the php language and some of the choices the php project leadership has made over the decades which make me not trust them to try and do the right thing for the php community.  They are a little too practical for my tastes.

Please do some reading on DBMS and programming languages, if still confused.  If you need to be hand-fed information, then you don't want to be a webmaster.  Nobody anywhere will provide all the information necessary to create and run a website.  You'll need to become comfortable learning from 50 different places, as you need to know things.

Did you actually use [https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html) ? Anything that references mysql or php can be ignored.

---

### Post by dora5 on 2019-09-29
Don't just tell me in plain English when and for what that I might actually do, I would need a database, or anything.

You evidently need a database to use Word Press, for starters.   What else in common use would one specifically need it for?

Php isn't hard, it's actually structured exactly like HTML, it's just not clear what I need it for.   And people are saying I don't.

No, I didn't read serverguide, because it's far too complicated to answer my questions.   I need the procedure to set up a web server and get my web site online, thank you very much!

Did you actually need three phd's to figure out how to walk down the street?  That seems to be the jist of what you are trying to tell me.    Please, what advanced degrees should I go for to learn how to walk down teh street?  Is there a server guide for that?

---

### Post by TheFu on 2019-09-29
> **dora5 said:**
> Don't just tell me in plain English when and for what that I might actually do, I would need a database, or anything.
How do I know what you might do?

> **dora5 said:**
> You evidently need a database to use Word Press, for starters.   What else in common use would one specifically need it for?
What do you consider "common use?"

> **dora5 said:**
> 
Php isn't hard, it's actually structured exactly like HTML, it's just not clear what I need it for.   And people are saying I don't.
I have to let someone who know php answer that.  I've never found any basic programming or web use for php, but I've only been doing websites for 25 yrs. Problems that some people solve with php, I solve with other methods.

> **dora5 said:**
> No, I didn't read serverguide, because it's far too complicated to answer my questions.   I need the procedure to set up a web server and get my web site online, thank you very much!
Actually, it isn't.  There is a page there about "web servers" - if you didn't find it and read that, perhaps web sites aren't a good fit?

> **dora5 said:**
> 
Did you actually need three phd's to figure out how to walk down the street?  That seems to be the jist of what you are trying to tell me.    Please, what advanced degrees should I go for to learn how to walk down teh street?  Is there a server guide for that?

I don't have any PhDs.  Maybe a youtube video "how-to" is more what you need?  There are millions and millions of websites and millions of people setup websites every year, so it can't be too hard, but it isn't 5 trivial commands either.

Apache is mainly a web server, but it can do much, much more than just serve webpages.  What I'm reading here is "tell me about shipping."  I'm not in the shipping business, but I know that ships, engines, navigation, maintenance, logistics, loading plans, weather, and import/export laws are involved.  That's sorta how apache is.
If you aren't shipping from/to different countries, then you don't need import/export stuff.  If you aren't using a DBMS, then you don't need MySQL.  You would 100% KNOW if you are shipping to a different country, right? The same applies to MySQL.  It isn't any harder than that.  Why make it harder?

I'm out of ideas. Good luck.

---

### Post by LHammonds on 2019-09-29
I have seen plenty of those tutorials online that tell you how to make a web server....that fits on a single page!  Never enough detail for me so I made my own.

Here is a step-by-step how-to guide for setting up an [Ubuntu Server](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244).

If all you want to do is use HTML (non-dynamic) web pages, you do not need a database.  Just install Apache and PHP.  Here is a step-by-step guide on how to install [Apache web server](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=261).

LHammonds

---

### Post by mastablasta on 2019-09-30
> **dora5 said:**
> 
None of the web sites I found explained what I specifically needed a database or php for.   
Under what conditions would I need the database?   


you don't need it.

sites like wodpress, drupal, joomla... need it. why? because for one they have user data base (admin user, moderators, users that post comments...). php is used for more complex sites where you want to add scripts. for example if you want a nice revolving picture gallery on your site, or you maybe you want drop down menues, buttons that change colours when you go over them with a mouse....

so for plain static site - web server (apache, nginx...) is enough.
for more complex website with users, various scripts, modules, plugins etc. etc. - you need a database (mysql, postgresql, mariadb, sqlite...) and PHP. well actually there is also asp and a few other alternatives to PHP. but PHP is programming language of choice for many websites, so it became part of the basic stack.

linux is modular OS. you install what you need. if you think you want a complex site you need to install many things. if you want a simple HTML website (the kind we had back in the 90's) a webserver will do and maybe openSSH to control it and administer it.

---

### Post by walts48 on 2019-09-30
> **dora5 said:**
> I need the procedure to set up a web server and get my web site online, thank you very much!


Here is the procedure for a NGINX server.

[https://linode.com/docs/web-servers/nginx/nginx-installation-and-basic-setup/](https://linode.com/docs/web-servers/nginx/nginx-installation-and-basic-setup/)

For an Apache server.

[https://help.ubuntu.com/lts/serverguide/httpd.html](https://help.ubuntu.com/lts/serverguide/httpd.html)

---

### Post by SeijiSensei on 2019-09-30
You need PHP or some other language like Python or Perl to create "dynamic" websites that function as applications. Such websites deliver different content depending on inputs from the visitor.  For instance, suppose you have a page that offers the user a choice among options in a drop-down box:
[html]
<p>Choose one of the following options:
<select name='myoption'>
<option value='opt1'>Option 1
<option value='opt2'>Option 2
<option value='opt3'>Option 3
</select></p>
[/html]
A PHP script could take that input and generate an entirely different page in reply based on the option chosen. In essence a language like PHP makes a web site into a computer application rather than simply a collection of static pages.

One typical use for a database is when you need to gather information from the visitor and store it beyond the lifetime of a session.  For instance, any site that does authentication has a database that includes visitors' usernames and password information. A PHP script would take the entered username and password and generate a query against the database to lookup the user and return whether the person is authorized. It might also return other information about the user like her name and address that was previously stored in the database.

Here on Ubuntuforums, a database powers the entire apparatus. The postings are stored in a database and indexed by thread, author, etc. Each of us has an entry in a members' database where our profile information is stored.

The first time I used PHP and a database was when I was building a directory service for my college classmates on our class website two decades ago. I haven't designed a static website pretty much ever since then.

Does that make things clearer?

---

### Post by Skaperen on 2019-09-30
i've seen websites made entirely in JavaScript for the the dynamic aspect.  JavaScript can access lots of services more directly, now.  it's more like time-of-use-loaded apps.

---

### Post by Skaperen on 2019-09-30
a "database" can be a lot of things and accessed a lot of ways, too.

---

### Post by DuckHook on 2019-09-30
> **dora5 said:**
> …Did you actually need three phd's to figure out how to walk down the street?  That seems to be the jist of what you are trying to tell me.    Please, what advanced degrees should I go for to learn how to walk down teh street?  Is there a server guide for that?
Your expectations are not realistic.

LAMP is admittedly arcance and obscure, but it is referenced so often only because almost any serious Linux user is aiming to build a website of high complexity and/or potentiality. These days, if you just want a simplistic site, myriad providers will sell websites-as-services to fulfill that need. Such prepackaged sites are so simple that a child could build one. There is no point—and never was any point—in the Linux-sphere trying to reinvent this wheel.

If you wish to use Linux as the foundation for your website, then there is no escaping the fact that the typical set of instructions, here and elsewhere, assumes a depth of knowledge that is non-trivial.

Your dig about requiring three PhDs is a sarcastic exaggeration. Thousands—dare I say millions—of Linux geeks have built websites without even one PhD. However, they are not allergic to the learning curve that LAMP demands. Linux remains, after all, a geek's OS.

You obviously have no desire to take on that learning curve. This is fine—most people feel the same way. But it's unrealistic to reject that learning curve and then get upset at not being able to obtain the goodies that rely on it. The most realistic and practical course of action for you is to use one of those much simpler pre-built website providers. Here is a site with instructions that bypass the LAMP requirement altogether: [https://websitesetup.org/](https://websitesetup.org/)

---

