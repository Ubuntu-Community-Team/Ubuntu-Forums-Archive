---
title: "a good counter"
date: 2009-07-26
forum: Server Platforms
---

### Post by cazz on 2009-07-26
Hi

I going to have a own webserver and I wonder what program/script can I use to read all information about the visitors on the apache server.

I dont like to add any script on every page I create but I like to know what they are doing on the server and what page is the popular or what take most traffic.

I have no idea what to search for, have only find script that I can use on a homepage but I'm not going to have a homepage, more like a lab server with alot of file and pages.

So do anyone know any good program/script that is easy to install on a apache server that I can use??

---

### Post by Vegan on 2009-07-26
PHP or any server side language is fine for this. Its a simple program.

```

open the count file
get count
count = count + 1
put count
echo count
close count file

```

its that simple

---

### Post by cazz on 2009-07-26
> **Vegan said:**
> PHP or any server side language is fine for this. Its a simple program.

```

open the count file
get count
count = count + 1
put count
echo count
close count file

```

its that simple

Well yes, I have work with different programming language but I was looking for something more advance that can read alot information about the visitor, what they are doing and where they come from without add alot of script.

so the topic is not so good but I have no idea what to write :)

---

### Post by R.Bucky on 2009-07-26
I came across Piwik [http://piwik.org/](http://piwik.org/) on SourceForge the other day. It was the Project of the Month. I host a half dozen sites and it tells you everything that you would want to know. A great open-source project.

---

### Post by FakeOutdoorsman on 2009-07-27
> **R.Bucky said:**
> I came across Piwik [http://piwik.org/](http://piwik.org/) on SourceForge the other day. It was the Project of the Month. I host a half dozen sites and it tells you everything that you would want to know. A great open-source project.

Thanks, R.Bucky.  We dumped Urchin and this looks promising.

---

### Post by hictio on 2009-07-27
> **cazz said:**
> Hi

I going to have a own webserver and I wonder what program/script can I use to read all information about the visitors on the apache server.

I dont like to add any script on every page I create but I like to know what they are doing on the server and what page is the popular or what take most traffic.

I have no idea what to search for, have only find script that I can use on a homepage but I'm not going to have a homepage, more like a lab server with alot of file and pages.

So do anyone know any good program/script that is easy to install on a apache server that I can use??

Have you thought in using Google for this? Take a look at Google Analytics, its free, easy to setup, and it provides an amazing amount of information.

- [Google Analytics](http://www.google.com/analytics/) - Homepage
- [Google Analytics](http://en.wikipedia.org/wiki/Google_analytics) - Wikipedia

---

### Post by TuckLive on 2009-07-27
[[COLOR="Blue"]Woopra[/COLOR]]("http://www.woopra.com") is a nice tracker.  It's not open source, but it has an open API.

---

### Post by Cheesemill on 2009-07-27
I use [AWStats]("http://awstats.sourceforge.net/").

---

### Post by cazz on 2009-07-27
> **Cheesemill said:**
> I use [AWStats]("http://awstats.sourceforge.net/").

yes it was a very nice counter. just like that I was after.

and it was easy to install :)

---

