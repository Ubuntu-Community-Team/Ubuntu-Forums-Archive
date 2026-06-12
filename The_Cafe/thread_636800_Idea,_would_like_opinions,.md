---
title: "Idea, would like opinions,"
date: 2007-12-10
forum: The Cafe
---

### Post by Nolander on 2007-12-10
I thought i would throw it out there.

basically my idea is an application that allows u to access/use a forum without a web browser. Don't know how useful it would be. but i reckon it would be fun to try and make it.

So dont be shy, if im crazy tell me,
Nolander

---

### Post by lyceum on 2007-12-10
IF you could pull that off, I think it would be cool. Could it auto update, so no need to refresh? I would like to see it show you who has responded to threads you are interested in, a box for "user control panel". Also, what would keep it from looking at other websites? Could it be used with any forum?

---

### Post by jken146 on 2007-12-10
That is a nice idea.  I've no idea how feasible it is, but I'd like that sort of app.

---

### Post by 23meg on 2007-12-10
There's a project in those lines called Forum Grabber, but the lack of anything beyond a description in Launchpad and a blueprint wiki page seems to indicate that its development hasn't kicked off:

[https://launchpad.net/forum-grabber](https://launchpad.net/forum-grabber)

You may want to contact the developers and learn its status.

---

### Post by technoidiot on 2007-12-10
I am currently using Akregator for all new feeds and this includes forum posts from Ubuntu and Kubuntu. It supplies me the option to read the post and if I log in I can reply to any give post. Not sure if this is what you are after but this might be the solution.

---

### Post by n3tfury on 2007-12-10
> **Nolander said:**
> I thought i would throw it out there.

basically my idea is an application that allows u to access/use a forum without a web browser. Don't know how useful it would be. but i reckon it would be fun to try and make it.

So dont be shy, if im crazy tell me,
Nolander

out of curiosity, why do you not want to use a browser?

---

### Post by Nolander on 2007-12-10
I Dont not wanna use a browser, i just think it would be fun 2 see if i could pull it off.

i was thinking insted of using the site the app would interact directly with the database.

---

### Post by n3tfury on 2007-12-10
"the site app"?  im confused, what's the apps name.  so the idea of an aggregator doesn't appeal to you either?

---

### Post by 23meg on 2007-12-10
RSS won't cut; you can't reply inside the aggregator, feeds are delayed, you can't see replies, so on.

---

### Post by Nolander on 2007-12-10
> **n3tfury said:**
> "the site app"?  im confused, what's the apps name.  so the idea of an aggregator doesn't appeal to you either?

sorry i missed a comma :P

The application(no name just an idea, atm) will connect to the forum Database, instend of doing it the way [ this]("https://launchpad.net/forum-grabber") guy/girl wants to do it.

and this would be like a fully functional forum.

Nolander.

---

### Post by DrMega on 2007-12-10
> **Nolander said:**
> I Dont not wanna use a browser, i just think it would be fun 2 see if i could pull it off.

i was thinking insted of using the site the app would interact directly with the database.

Are you saying that you want to write an app that conects to, reads and writes data directly to the backend database that the forum uses?

If that's the case I don't think it would be that big a job really (depending on how far you want to take it of course). Your biggest obstacle (and potential show stopper) is that the database server is likely to be firewalled off from the outside world. Even if it isn't, you'd need to know exactly where it is hosted (may not be on the same domain as the website of the forum), what DB engine it is (MySQL, MSSQL etc) and you'd need to know about the schema.

Some of that info will be available for some forums. Many forums are based on a fairly standard open source one (can't remember its name but phpBB springs to mind). That being the case, you could no doubt get the schema info for that.

The other option is to send HTTP packets directly to the website on port 80, but if you do that you're effectively building another web browser.

---

### Post by 50words on 2007-12-10
This sounds like a great idea. I would love to be able to aggregate my favorite forums similarly to the way I aggregate my blog feeds, but with posting/replying capabilities, as well.

---

### Post by Nolander on 2007-12-10
@DrMega
That is exactly right. the problem, i think, will be forum admins freely giving out the info to there forum's db so the application can connect. but i was thinking 2 make it more secure i use a db of me own that they can register 2. and make it so the passwords were encrypted or something like that. 

nolander

---

### Post by n3tfury on 2007-12-10
> **Nolander said:**
> @DrMega
That is exactly right. the problem, i think, will be forum admins freely giving out the info to there forum's db so the application can connect. 

nolander

and that alone is probably not going to happen with larger forums.

---

### Post by popch on 2007-12-10
The people who are running the forum will not love it when you use a foreign application which completely bypasses the forum application in accessing and modifying the forum database.

That's a very good way to ruin that database. Besides, whenever the forum application is updated, you risk that this will affect the database schema as well. Thus, it would most likely break your application.

I could imagine that you could write some kind of front end which processes whatever the forum sends. 

That used to be done with applications running on the ancient IBM host computers. You intercepted the traffic between the application and the terminal and wrapped your own front end around it. That went by name of 'screen scraping', if I remember it correctly.

---

### Post by jlinho on 2007-12-10
This would be easy using Atom Publishing Protocol

---

### Post by 50words on 2007-12-10
Why would you need to go into the forum backend? Can't you just send the text by "spoofing" (not a developer, so I'm sure that is not the right term) the "submit reply" button?

---

### Post by popch on 2007-12-10
> **50words said:**
> Why would you need to go into the forum backend? Can't you just send the text by "spoofing" (not a developer, so I'm sure that is not the right term) the "submit reply" button?

That depends a bit on the quality of HTML code the forum produces.

I tried once to extract technical information from an online reference about a programming language. It turned out the HTML was severely damaged. Not even well formed, let alone valid. That was rather an impediment for the tool kit which ought to have parsed the HTML.

---

### Post by DrMega on 2007-12-10
One option might to write a small server that runs on the forum's web server, and using one of the various XML based protocols to transfer data back and forth, and handling remote procedure calls (web services).

You'd still need to get the cooperation of the forum owners, but this would give the advantages such as:
* More secure - no need to disclose port numbers, DB server IP addresses etc.
* More robust - Any breaking changes to the DB schema could be handling in the web service layer.
* More secure (again) - The forum owners could scrutinise your web service code until they were satisfied that nothing in it could break their data or compromise their security.

As it would be a web service (serving up XML instead of HTML) it would sit happily on their web server, accessible on port 80 and with limited access via PHP to their database. They could configure the database connection details without telling you what they were.

---

### Post by LaRoza on 2007-12-10
> **50words said:**
> Why would you need to go into the forum backend? Can't you just send the text by "spoofing" (not a developer, so I'm sure that is not the right term) the "submit reply" button?

Probably not. The forum uses (hopefully) server side authentication, and use that, you would need to basically make a browser.

---

### Post by popch on 2007-12-10
> **LaRoza said:**
> Probably not. The forum uses (hopefully) server side authentication, and use that, you would need to basically make a browser.

Yes, but that 'browser' would not need to be very powerful. Writing a program which reads and writes over http is not all that difficult, and quite a few programming languages provide at least a skeleton for that task.

---

### Post by psusi on 2007-12-10
Such a thing was already around long before the advent of the web.  It's called a newsreader.  Newsgroups kind of fell out of favor though when mailing lists became popular, so a plain old mail client works.

---

### Post by LaRoza on 2007-12-10
> **popch said:**
> Yes, but that 'browser' would not need to be very powerful. Writing a program which reads and writes over http is not all that difficult, and quite a few programming languages provide at least a skeleton for that task.

I know, but the point was, it isn't just a matter of "spoofing" the reply button, as stated.

---

### Post by 23meg on 2007-12-10
This discussion can be much more fruitful if everyone interested reads the Forum Grabber blueprint.

[http://wiki.ubuntu.com/ForumGrabber](http://wiki.ubuntu.com/ForumGrabber)

---

### Post by toupeiro on 2007-12-10
heh.  console based bulletin boards and forums.  been there, they were called [BBS's!]("http://en.wikipedia.org/wiki/Bulletin_board_system")

While nostalgia makes me think it would be a golden thing to revitalize these things using connection methods like SSH, truthfully, it may never happen

ubuntuforums BBS. hehe, if only.

---

### Post by psusi on 2007-12-10
Actually if you google for telnet bbs, you will find a number of telnet accessible old school bbses.  Every once in a while when I get the urge, I log onto one and fire up some old school Operation Overkill II or Trade Wars.

---

