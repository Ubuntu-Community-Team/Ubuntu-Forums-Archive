---
title: "Popular sites using opensource technologies"
date: 2016-06-12
forum: The Cafe
---

### Post by tech291083 on 2016-06-12
Hi Friends,

I just came across the following piece of information, which basically gives an idea of the various open-source technologies used by a popular question and answer site name Quora. I would love to learn more about other popular sites on the web that also rely on open-source technologies, any ideas? Thanks.

> Quora uses the [Pylons]("https://en.wikipedia.org/wiki/Pylons_project") and [Comet]("https://en.wikipedia.org/wiki/Comet_%28programming%29") technologies for its backend and [Ubuntu Linux]("https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") as its operating system with [MySQL]("https://en.wikipedia.org/wiki/MySQL") as its [database]("https://en.wikipedia.org/wiki/Database"). It also uses [Git]("https://en.wikipedia.org/wiki/Git_%28software%29") and [memcached]("https://en.wikipedia.org/wiki/Memcached"). Quora uses [Nginx]("https://en.wikipedia.org/wiki/Nginx") as a reverse proxy server and [HAProxy]("https://en.wikipedia.org/wiki/HAProxy") for load balancing.[SUP][*[citation needed]("https://en.wikipedia.org/wiki/Wikipedia:Citation_needed")*][/SUP] Quora has developed its own algorithm to rank answers, which works similarly to Google [PageRank]("https://en.wikipedia.org/wiki/PageRank").[SUP][[32]]("https://en.wikipedia.org/wiki/Quora#cite_note-32")[/SUP] Quora uses [Amazon Elastic Compute Cloud]("https://en.wikipedia.org/wiki/Amazon_Elastic_Compute_Cloud") technology to host the servers that run its website.[SUP][[33]]("https://en.wikipedia.org/wiki/Quora#cite_note-33")[/SUP][SUP][[34]]("https://en.wikipedia.org/wiki/Quora#cite_note-34")[/SUP] In August 2011, Quora switched its infrastructure's [Python]("https://en.wikipedia.org/wiki/Python_%28programming_language%29") implementation from [CPython]("https://en.wikipedia.org/wiki/CPython") to [PyPy]("https://en.wikipedia.org/wiki/PyPy"), to speed response time.
 

[https://en.wikipedia.org/wiki/Quora#Operation](https://en.wikipedia.org/wiki/Quora#Operation)

---

### Post by fkkroundabout on 2016-06-13
don't know too much about the intricacies, but everything below is from memory -

wikipedia is run on ubuntu, previously on red hat.
google like debian for servers, with a customized file sytem, and use ubuntu LTS & macs for workstations. puppet is used for mac workstations. think they previously used red hat, at some point
youtube built with python
dropbox built with python
pinterest built with python
twitter was built with ruby up until it started crashing alot. they switched one part to java a while before ~50M and then the rest to java by the time it hit ~50M users
yahoo was (is?) a heavy user of BSD, which leads onto the next one...
whatsapp is based on freeBSD, just 20 developers, various having come from yahoo
OSX has some freeBSD roots
PS3 & PS4 is based on freeBSD. previously had linux compatibility but they blocked it, because often videogame consoles are sold at a loss and money made on selling games, and people started buying them just for the linux compatibility - or so i have read
wordpress and facebook were, infamously, built with PHP
ebay i think i read has some perl roots ?

i don't know what's happening over on the chinese internet, as many of  the technically most popular websites are chinese, but i'd bet it's not a  too dissimilar situation

in conclusion it's probably only microsoft not using open source technologies, but apparently that's not strictly true nowadays. never cared to look into microsoft though

---

### Post by tech291083 on 2016-06-14
> **fkkroundabout said:**
> don't know too much about the intricacies, but everything below is from memory -

wikipedia is run on ubuntu, previously on red hat.
google like debian for servers, with a customized file sytem, and use ubuntu LTS & macs for workstations. puppet is used for mac workstations. think they previously used red hat, at some point
youtube built with python
dropbox built with python
pinterest built with python
twitter was built with ruby up until it started crashing alot. they switched one part to java a while before ~50M and then the rest to java by the time it hit ~50M users
yahoo was (is?) a heavy user of BSD, which leads onto the next one...
whatsapp is based on freeBSD, just 20 developers, various having come from yahoo
OSX has some freeBSD roots
PS3 & PS4 is based on freeBSD. previously had linux compatibility but they blocked it, because often videogame consoles are sold at a loss and money made on selling games, and people started buying them just for the linux compatibility - or so i have read
wordpress and facebook were, infamously, built with PHP
ebay i think i read has some perl roots ?

i don't know what's happening over on the chinese internet, as many of  the technically most popular websites are chinese, but i'd bet it's not a  too dissimilar situation

in conclusion it's probably only microsoft not using open source technologies, but apparently that's not strictly true nowadays. never cared to look into microsoft though

Excellent research, well done!

If this is just based on your memory, then its even more commendable. I am impressed. I would request other members to share their info on the subject. Thanks a lot.

---

### Post by user1397 on 2016-06-16
One thing I used to do out of curiosity was use the [w3 validator site]("https://validator.w3.org") and tick the verbose output box to show the server stats for any particular website, which usually included both the server software such as apache or IIS, and the OS such as debian or redhat.  I've noticed lately that the OS does not show for most of the popular websites, and sometimes even the server software doesn't show.  No idea why :(

---

### Post by tech291083 on 2016-06-16
> **user1397 said:**
> One thing I used to do out of curiosity was use the [w3 validator site]("https://validator.w3.org") and tick the verbose output box to show the server stats for any particular website, which usually included both the server software such as apache or IIS, and the OS such as debian or redhat.  I've noticed lately that the OS does not show for most of the popular websites, and sometimes even the server software doesn't show.  No idea why :(

Well, this is a really good idea. Thaks for sharing the same, please have a look at an article telling us about a few sites that one can use in order to figure out the CMS ie content management system used by a particular site, if any, thanks.


Top 5 Free Web Tools To Find What CMS a Website is Using

[http://allusefulinfo.com/top-5-free-web-tools-to-find-what-cms-platform-or-framwork-a-website-is-using/](http://allusefulinfo.com/top-5-free-web-tools-to-find-what-cms-platform-or-framwork-a-website-is-using/)

---

### Post by tech291083 on 2016-06-16
I used to figure out what programming language a particular site was written in long time ago, when I was learning a bit of programming myself, may be more than a decade ago. I just used to focus on the URL and look for extensions such as .asp, .aspx, .php and .jsp etc, as you know. But I just came to know, after a while though, that programmers/system admins can easily hide these obvious extensions in order to ramp up security and below is a good piece of discussion on this very subject, hope you will like it, thanks.

> 
    file extensions: .php indicates that the site is written in PHP, .asp indicates classic ASP, .aspx indicates ASP.NET, .jsp indicates Java JSPs, ...
    cookie names: JSESSIONID is a widely used cookie name in Java servers
    headers: some systems add HTTP headers to their responses
    specific HTML content:
        patterns such as lots of div-wrappers with a consistent class-naming scheme as used by CMSes like Drupal.
        comments in the HTML or meta tags in the head directly/indirectly indicating tool usage
    Default error messages or error page design (e.g. pinging a fake URL to see their 404)
    Sometimes comment tags are placed in the page for versioning purposes which provide a clue
    ...

But all of those can be remove/changed/faked. Some are easier to change than others, but none are 100% reliable.


[http://programmers.stackexchange.com/questions/151472/is-it-possible-to-know-what-programming-language-a-web-site-uses](http://programmers.stackexchange.com/questions/151472/is-it-possible-to-know-what-programming-language-a-web-site-uses)

---

### Post by tech291083 on 2016-06-16
Although, I find the below statement from the above site a bit more suspicious, correct me if I am wrong, thanks.

> 
It should be noted that the  extension of a requested file by URL need not map directly to a file on  the filesystem.  One can quite easily map an extension like .php to a CGI-Script written in C or a Servlet written in Java.


[http://programmers.stackexchange.com/questions/151472/is-it-possible-to-know-what-programming-language-a-web-site-uses](http://programmers.stackexchange.com/questions/151472/is-it-possible-to-know-what-programming-language-a-web-site-uses)

---

### Post by fkkroundabout on 2016-06-20
i forgot that netflix were also previously using freeBSD for the large majority of traffic. however i just saw a talk with mark shuttleworth from this year where he says everything has been moved to ubuntu ! [https://youtu.be/geiG3qYeCOI?t=4m40s](https://youtu.be/geiG3qYeCOI?t=4m40s)

---

### Post by HermanAB on 2016-06-23
Well, pretty much everything runs on Linux.

MS Windows is a small niche OS used on business and home desktop computers.

---

### Post by tech291083 on 2016-07-03
> **HermanAB said:**
> 
Well, pretty much everything runs on Linux.


yes, these days Linux just rocks, thanks a lot for sharing your thoughts on the subject.

---

