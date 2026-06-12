---
title: "Web site hosting"
date: 2011-01-06
forum: The Cafe
---

### Post by john77eipe on 2011-01-06
Hi,

I'm planning to host a website. Please guide me on what technologies I need to focus. I just know basic HTML. And already planned to install Ubuntu server edition. 

I heard that LAMP is very effective. What are the other alternatives? I'm still confused about the categories.:confused:
For eg:
ASP / JSP / PHP for server-side programming?
JavaScript / ActionScript for client-side scripting? and so on.

---

### Post by lykeion on 2011-01-06
It all comes down to what kind of website you're planning. If it's a simple site which doesn't handle data you don't need to bother with server/client-scripting or databases. However if you plan to have some kind of forms and handle the data the user inputs, you'll most likely use PHP for server-side scripting and MySQL if you need to some persistent storage in a database. Wordpress sites (and Facebook too in the beginning) was built with PHP/MySQL.

LAMP stands for Linux-Apache-MySQL-PHP and is a web server "bundle" (or "stack" as the tech-savvy people call it). The description on the Ubuntu documentation is good, check [here]("https://help.ubuntu.com/community/ApacheMySQLPHP"). Learn how to setup a site in Apache, and if you'll use PHP/MySQL you should read how to secure your site.

Client-side scripting with Javascript is often used for dynamic functions of web sites, like form validation, checking browser version, etc. There are lots of Javascript resources available on the web, so you shouldn't need to reinvent the wheel.

I should also tell you about HTML5 which adds lots of features of HTML. Few browsers have 100% HTML5 support at the present, but in the future it'll probably be more and more HTML5.

The web are full of reading material, Wikipedia is excellent in explaining the many acronyms used in web programming/hosting (like ASP, JSP, etc).

Good luck, and post if you have more questions.

---

### Post by samalex on 2011-01-06
Something else is where will you be hosting this site?  If you have a corporate network with a dedicated IP then you're golden, but if you're planning on hosting it at home that might take alittle extra work since most home IP addresses use DHCP.  Post back and we can give some options if you're in the latter category.

But as lykeion mentioned LAMP is Linux, Apache, MySQL, and PHP... and if you know Linux then installing Ubuntu Server will give you the option to setup a LAMP server outta the box.  

As for coding, regardless of what content you want to host check out some of the canned content managers.  Unless you just want to write something from scratch, apps like Joomla, MediaWiki, WordPress, and others are wonderful and can give you a completely dynamic and customized site in no time.  It never hurts to learn PHP and MySQL so you can customize the site more, but it's not a requirement -- just know MySQL enough to setup a blank database which can be done easily enough via CLI or something like Webmin.

Hope this helps --

---

### Post by slackthumbz on 2011-01-06
LAMP does not necessarily have to include PHP. As a web developer I refuse to touch PHP because it's a terrible, terrible, nasty hack job concoction of a language. I'd recommend learning perl and using that to power your backend via cgi and sensible use of REST urls.

Also, you should learn CSS, javascript (+jQuery) and never forget to taint-check your inputs. Can't stress that last point enough ;)

---

### Post by sanderd17 on 2011-01-06
Setting up a LAMP server is easy. Just install ubuntu (server for big sites, for smaller, you can also use ubuntu desktop edition) and install some php5 packages and MySQL. Apache will come with the php packages.

I imagine you don't want to program a complete website yourself. So if you want a dynamical website, install something like Drupal, Joomla, worldpress...

Most packages like that work the same: you download a zip, unzip it in /etc/www (or some similar directory) and visit your site. If your site isn't online yet (but everything is installed), you can go to [http://localhost]("http://localhost") in the browser of the server machine (this is only possible with ubuntu desktop because server doesn't have a GUI by default). You should see some index page which guides you to the rest of the setup.

If you go via [http://localhost]("http://localhost"), your php files will be executed, if you just open the php files in your browser, the php files won't be executed, so you will see nothing.

This is basically the method to get a local test site up. I can't help you with requesting a domain name which leads to your IP. Until now, I tried test sites with this configuration and then went to a host to host the real site. That way, I didn't waste money on testing the site while the contract was already running. You do have to search a host which has the things you ask: php server, mysql server and unlimited number of files.

If you want to change some things to the normal config or program some things yourself, you need to learn the different languages. [http://www.w3schools.com/]("http://www.w3schools.com/") is a good source for learning the basics.

---

### Post by juancarlospaco on 2011-01-06
Consider ::1

---

### Post by perspectoff on 2011-01-06
You should see Ubuntuguide.org or Kubuntuguide.org.

there are lots of server instructions there.

Drupal for websites

Mediawiki for Wikis

Moodle for online teaching

BigBlueButton for Teleconferencing

WebDAV for web-accessible folders (through HTTP)

FTP

Backup, network monitoring, multiple servers on a LAN. Lots and lots of info condensed in one place.

You'll save a year or two in hunting down info (and avoiding a lot of misinformation) by checking out those places first.

---

### Post by john77eipe on 2011-01-06
I'm setting up a server at home. And for that I guess I would have to get a static IP address and also a domain. 

Here is what i have in mind.

1. My site wouldn't be large scale but it will contain, say 60-70 webpages.
2. I would like to provide register/login for the users. So that I can contact them using their email addresses.
3. I would like to do it from scratch. As I like to learn about web development. I know basics of HTML, mySQL and servlet/JSP. (in descending order of proficiency)I'm now learning some basics in javascript.

Isn't it possible to do it with the above technologies? or Should I study PHP or perl?

---

### Post by sanderd17 on 2011-01-06
> **john77eipe said:**
> I'm setting up a server at home. And for that I guess I would have to get a static IP address and also a domain. 

Here is what i have in mind.

1. My site wouldn't be large scale but it will contain, say 60-70 webpages.
2. I would like to provide register/login for the users. So that I can contact them using their email addresses.
3. I would like to do it from scratch. As I like to learn about web development. I know basics of HTML, mySQL and servlet/JSP. (in descending order of proficiency)I'm now learning some basics in javascript.

Isn't it possible to do it with the above technologies? or Should I study PHP or perl?

None of the languages you use are server-sided. So you can't access your MySQL database with those languages.

---

### Post by sujoy on 2011-01-06
> **sanderd17 said:**
> None of the languages you use are server-sided. So you can't access your MySQL database with those languages.

whoa, servlets/jsp ain't "server-sided"? last i checked, they were.

---

### Post by sanderd17 on 2011-01-06
> **sujoy said:**
> whoa, servlets/jsp ain't "server-sided"? last i checked, they were.

Oops, sorry for giving the wrong info.

---

### Post by john77eipe on 2011-01-07
Thanks everyone.

I will study the below technologies in this order: 
HTML and CSS, (for presentation) 
Javascript (for client side scripting)
Servlets and JSP (for server side)
Postgre (for Database)
Apache Tomcat (for hosting).

I think the above will suffice for my simple website. If there are any "don't miss" technologies of today that I'm not aware of please mention it.

---

### Post by juancarlospaco on 2011-01-07
Python.

---

### Post by cgroza on 2011-01-07
> **juancarlospaco said:**
> Python.
With web2py library, very similar with Ruby on Rails. I think you should take a look at these options too.

---

### Post by DataflowHosting on 2011-01-07
Hello John!

As some guys already pointed everything depends of the nature of what you want your application(web site) to do. But I am going to describe **some** pros and cons for you...

PHP Pros:
1. PHP is easy to learn and there are very good PHP frameworks out there for rapid PHP development, event tough you should not jump learning the framework at the beginning.
2. There are already so many open source PHP scripts that you can use by simply installing them and eventually doing some HTML/CSS redesign.
3. Almost all(if not all) web hosts will handle PHP without any problems.
4. PHP is free, all Web servers are having *free* modules and etc for running PHP. In order for you to write PHP scripts the least you will need to do is to have one simple Text editor and a server to launc your scripts to - that is everything!

PHP Cons:
1. If you want to commersialise your products PHP might not be too good idea - you will need to protect your propriatery source codes by doing some kind of code encryption that can eventually be decrypted just from those guys that are having the right license keys.
2. PHP is a language at low level, compared to Java and all the ASP/.NET languages. Even tough the last years PHP is doing a very good progress.
3. PHP might not be as fast as ASP and JAVA, even tough all depends on the quality of the code that you write.

JAVA - Pros:
1. Java is free, All OS are able to handle JAVA without any problems.
2. Java is fast - after compiling Java WEB projects, the compiled Java native code is several ideas faster than the PHP interpretator code.

Java - Cons:
1. Java has a very big learning curve - you will need months if not even yers to learn Java
2. Java is hard to manage - you will need to learn so many other things like working with IDEs, deploying your Java WEB projects and so many other things...
3. Java is complex, this actually is a good thing, but for a beginners it might be a very bad thing actually :)
4. To do something good and really professional you will need to jump into some kind of Java framework, which additionally adds some time to the Java learning curve.

.NET/ASP Pros:
1. Fast and easy to be used
2. True OOP languages

.NET/ASP Cons:
1. The .NET/ASP will require a Windows server, which is not free.
2. The .NET/ASP might need to work with Visual Studio, whcih is payed. Although there are some free IDEs, but I am not sure what is their quality...
3. The .NET/ASP is hard to be managed

Please, keep in mind that you will need to learn some kind of SQL server like MySQL, PostgreSQL, Oracle or MS SQL. If you really start doing some dynamic PHP programming, then I recommend MySQL 5.0 or later - it is free and present on akmost all(if not all) web hosts.


John, I am not sure what you try to achieve, but keep in mind that learning to programm is not that easy and if you go into the wrong dirrection you might just loose your time...

You can also check if there is not anytingh out there ready to be used, you can check with the Open Source projects and see if someone did not propose the product that you are searching for. There is great projects like Wordpress, Drupal, OsCommerce, ZenCart and so many others - just name it... :)

---

### Post by john77eipe on 2011-01-08
@DataflowHosting
Thanks a ton.
I have got 1 year and I'm good at core Java (i didn't mention this before) so I think a long curve would be OK :D.

As far as python goes. I'll definitely look into it. I heard from many that it's an excellent scripting language.

---

### Post by john77eipe on 2011-01-08
I installed tomcat and mySQL. Having some initial trouble though.

---

### Post by john77eipe on 2011-01-08
mySQL problem:
[http://ubuntuforums.org/showthread.php?p=10330575](http://ubuntuforums.org/showthread.php?p=10330575)

---

### Post by perspectoff on 2011-01-08
No, you don't need a static IP address to host a website. Dynamic IP addressing works fine with DynDNS.com, Namecheap, or several other Dynamic DNS providers. You would use a client like ddclient to keep the Dynamic DNS updated.

I run several servers this way.

Constructing a website by writing code for it in PHP, Perl, Rython, or RoR is a thankless task. It is better to stand on the shoulders of giants. 

If you are just planning to set up a CMS, choose Drupal or Joomla or Wordpress and then add modules whjich have already been coded in their respective language (PHP for the most part).

You indicated you are a novice, and you will lose interest far earlier if you don't have some happy product.

My sister said the same thing as you about 3 years ago -- she finally hired someone to create her site for her. 

That is, in fact, the goal of much advice you will hear -- some coder trying to convince you of the benefit of one method or the other that is overly complex, in the hopes you will get frustrated and hire them.

I've been in the software business a long time and recognize the tactics.

Of course, if you really are a serious coder, by all means choose something like RoR or PHP and code in it. 

BTW I firmly believe in hosting your own server. You don't need a server edition of (K)Ubuntu any more. All server software is available for all editions.

You can install a Desktop edition and then add server software as easily as you can do (sometimes more easily) with a Server edition, nowadays. The server edition, IMO, is really only for finished product that needs to be deployed with great speed. 

For info on setting up a server with a Dynamic DNS, see

Ubuntuguide.org:
[http://ubuntuguide.org/wiki/Dynamic_IP_servers](http://ubuntuguide.org/wiki/Dynamic_IP_servers)

or Kubuntuguide.org
[http://kubuntuguide.org/Dynamic_IP_servers](http://kubuntuguide.org/Dynamic_IP_servers)

---

### Post by linuxforartists on 2011-01-08
+1 for WordPress.  I'm deep into learning it now and using it to build websites.  Huge and dedicated community always innovating with new plugins.  Great to know HTML and CSS so you can dive in and customize it.  

You said you wanted to have users be able to register.  For a robust user website, you might want to look into Drupal.  It's a high-level content management system (CMS), great for social networks and large-scale news websites.  Good time to get into it too, as Drupal 7.0 just came out.  You can check out an overview of it in this [marketing video]("http://vimeo.com/18352872").

> **john77eipe said:**
> Thanks everyone.

I will study the below technologies in this order: 
HTML and CSS, (for presentation) 
Javascript (for client side scripting)
Servlets and JSP (for server side)
Postgre (for Database)
Apache Tomcat (for hosting).

I think the above will suffice for my simple website. If there are any  "don't miss" technologies of today that I'm not aware of please mention  it.

That's a solid list. The only thing I can add is [jQuery]("http://jquery.com/"). Then you can really make some slick-looking effects in the browser.  Save you from writing Javascript from scratch every time you needed something.  

As others have said, later you can get into PHP, Python, or Ruby on Rails.  RoR seems to be the hot language to learn now, if you're looking at future job opportunities.

For self-study, I really like the [Head First books]("http://headfirstlabs.com/") by O'Reilly Media.  Until I read those, I never really understood web design and programming.  The illustrations and diagrams made everything so clear.  I like how they use real-world-type projects and walk you through how to do them.  The humor is lame sometimes, but that's a minor flaw.

Good luck with your learning!

---

