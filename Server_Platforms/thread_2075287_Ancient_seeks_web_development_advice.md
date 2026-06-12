---
title: "Ancient seeks web development advice"
date: 2012-10-23
forum: Server Platforms
---

### Post by bouncingwilf on 2012-10-23
An errant nephew has asked for my assistance in developing a web application and I must confess that despite 40 odd years of tinkering with code, this is an area I have avoided like the plague ( seemed to me it involved far too much "format" type typing rather than the mathematical/science stuff I am used to) .

Now I've done a little background research and have identified a number of methodologies /approaches I could use, all of which appear capable of "doing the job". However, as there seem to be multiple possible approaches I thought I would seek the guidance of wiser, more experienced heads as to the best . The application is relatively simple but could get messy in the future if the wrong approach is chosen. What is required is as follows;

1. A backend database that holds the raw data (SQL I can Manage!) 
2. A web page from which the user can choose a number of options which will be used as a query generator 
3. The results of the query ( which is geolocation data etc.) should be then displayed on a map using e.g. openstreetmap/openlayers. 

Now this is all pretty standard stuff to web developers but my questions are 

a) Which backend database mysql/postgresql etc?

b) which is the best server scripting language for this type of Application - Ruby On Rails/PHP etc. Security will be required to limit access to registered users. 

Having quickly  looked at PHP and Ruby, I have no  strong preference ( perhaps slightly biased towards PHP ) but as either will be a new experience I'd prefer to learn just one!

The client side web page "pretty stuff" will, I'm glad to say, not be my concern !

Thanks in advance for any advice. - Bouncingwilf

---

### Post by Warprunner on 2012-10-23
My votes:
MySql and PHP

---

### Post by sandyd on 2012-10-23
Moved to server platforms

---

### Post by CharlesA on 2012-10-23
LAMP gets my vote, but be sure to read up on securing apache and php (and mysql).

---

### Post by Cheesemill on 2012-10-23
Another +1 for MySQL and PHP.

Mostly because there are likely to be far more tutorials and documentation available than for anything else.

---

### Post by koenn on 2012-10-23
> **Cheesemill said:**
> Another +1 for MySQL and PHP.

Mostly because there are likely to be far more tutorials and documentation available than for any else.

and another +1

LAMP is  trivial to set up,
php is quite easy to get the hang of, especially if you have some coding experience. 


The thing to watch out for is, probably, to maintain some separation between form/presentation (html) and processing (php). php and html mix very easily, but I guess that can lead to an unmaintainable mess quite quickly as your application grows or needs modifications. And you don't want to rewrite an application just because someone wants a new color scheme on the site, that sort of thing. 
PHP lets you get away with that sort of mix, so you need to make a conscious effort to keep it clean.

---

### Post by drdos2006 on 2012-10-23
Who will the audience be ? Is it also going to be for hand held mobile devices ? With the changes in hardware plus the fact that Windows 8 will be concentrating on touch screens more so than standard screens, will the program be designed for Windows users as well ?

Have a look at Maqetta [http://maqetta.org/](http://maqetta.org/) from IBM with an emphasis on HTML5 and database connection. Here is a video [http://thenewboston.org/watch.php?cat=43&number=50](http://thenewboston.org/watch.php?cat=43&number=50) and here [http://thenewboston.org/watch.php?cat=43&number=51](http://thenewboston.org/watch.php?cat=43&number=51)

regards

---

### Post by bouncingwilf on 2012-10-25
Many thanks for the replies - apologies for the slow response but a small family crisis developed! 

Seems like lamp is the way to go but as mobile devices feature strongly in the mix, I shall definitely look into the maqetta option - who knows - maybe MS is not fatally holed below the waterline.

Bouncingwilf

---

### Post by LHammonds on 2012-10-26
I could have swore I added my response a couple days ago...guess I was typing on my phone and never hit submit. hehehe.

Anyway, I'm also a +1 to the MySQL and PHP crowd.

I keep my servers separated so I don't ever use the lamp install directly.

You can check out how I install a base Ubuntu Server that is ready for production use as well as MySQL in my signature links below.  I don't have an Apache/PHP-only server setup documentation but I do make use of my mediawiki server for various tasks (quick pages to connect/display/update MySQL data)

Also, there are a ton of MySQL+PHP projects out there that you can take a peek at how they develop/maintain their codebase and remain flexiblity.  Here are just a few:

[LIST]
[*][phpBB]("https://www.phpbb.com/")
[*][WordPress]("http://wordpress.org/")
[*][Drupal]("http://drupal.org")
[*][MediaWiki]("http://www.mediawiki.org/wiki/MediaWiki")
[/LIST]
LHammonds

---

### Post by CharlesA on 2012-10-26
Just wanted to add a +1 to LHammonds's howtos. :)

They are a good starting point, and if you wanted to have seperation of services, you could install apache and php on one machine and mysql on another.

---

### Post by lisati on 2012-10-26
> **CharlesA said:**
> Just wanted to add a +1 to LHammonds's howtos. :)

They are a good starting point, and if you wanted to have seperation of services, you could install apache and php on one machine and mysql on another.

+1 from me too. A lot can be learned from taking a peek at how others have tackled the different tasks that might be useful when setting up your system.

---

### Post by CharlesA on 2012-10-26
> **lisati said:**
> +1 from me too. A lot can be learned from taking a peek at how others have tackled the different tasks that might be useful when setting up your system.
Indeed. That is how I have learned most of what I know now.

---

### Post by lykwydchykyn on 2012-10-26
If you're going to deploy this on some cheap, public web host, then PHP + MySQL is a safe choice in terms of compatibility.  If you use anything else (except maybe Perl), good luck finding a host that supports it.

If this is going on a server over which you can exercise control, then I would strongly recommend Postgresql as a database.  It's got some really nice elegant SQL syntax features and a lot of advanced capabilities that an experienced programmer can leverage.

I'd also recommend checking out Python for web development.  PHP is popular and easy, and I write boatloads of PHP code on a weekly basis, but overall it's a crummy language IMHO.  If you have experience in well-designed languages, PHP is going to drive you batty.

---

### Post by spynappels on 2012-10-29
If setting up a separate MySQL server, make sure that the user you want to use to connect as is not limited to localhost connections only.

Ask me how I know that...:)

That's a couple of hours of my life I'll never get back, although I've never made the same mistake again, so I'll not say it was wasted.

---

