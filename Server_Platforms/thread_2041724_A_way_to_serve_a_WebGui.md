---
title: "A way to serve a WebGui"
date: 2012-08-13
forum: Server Platforms
---

### Post by MadsRC on 2012-08-13
I'm looking for a way to serve a WebGui for my server?
I have the code(html,css,php etc.), but I don't want it to run ontop of apache, as I would have to have apache installed for every server that is using the WebGui (Don't want to install apache unless the server needs to use apache).

I tried asking in the IRc, but was told not to reinvent the wheel, use ebox or use Zentyal. Let's be clear about that, those aren't a possibility.

I was looking for something like the way Webmin, or unRAId or pfSense (which I know is BSD yes...) and Smoothwall serves their WebGui's?

I know unRAId uses something called emhttp, but a quick google didn't turn up anything.

---

### Post by TheFu on 2012-08-13
So let me try to restate your question.

**Is it possible to create a program that will serve web pages without using Apache?**

The answer is yes, but your program will need to implement the instructions that a webserver implements.  I've seen very simple versions of this written in python, perl, tcl, but never php.  For a hobby project, you can implement the 5 or so HTTP commands yourself, but there is no way that I'd deploy that for a business.  Creating a secure webserver is hard. Leveraging an existing web server for that makes sense unless you want to spend about the same amount of time building your web server as the Apache, nginx, or litehttp teams did.

Like you, I wrote a small web server around 1995 in C++. It was a pain to maintain and CGI was created to make running small external apps very easy.  You need to decide, just like I needed to decide, whether it was worth the effort or not.

If you like the way that webmin serves its interface, pull down the source code and use it for your needs. It is BSD licensed, so you are free to do that.  It appears to be written in Perl, so you might want to rewrite your app into perl or find a php version that you can "reuse."  Just be certain to check the license and follow it.

I googled "php web server" and saw a few results. [http://nanoweb.si.kz/](http://nanoweb.si.kz/) was first. It is GPL, so your program would need to be GPL too.

I will agree with you that installing a full apache when you want a smaller solution isn't a good idea, however, I would strongly recommend that you leverage other people's work, provided the licensing supports your needs AND that you use solutions that leverage the Ubuntu APT repositories so that maintenance and security patches are easier.  Aptitude or apt-get really are fantastic and because there are constant security attacks against any public service, especially web servers. We need to have constant patches available.

Anyway, I hope that I understood your question and provided hints to a good solution.  Good luck.

---

