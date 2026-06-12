---
title: "What is your web site speed?"
date: 2010-12-02
forum: The Cafe
---

### Post by lovinglinux on 2010-12-02
I'm setting up a new web site for my stuff and I am kind of worried about the speed. The hosting company says everything is normal, but it feels slow. So I did a few tests.

One test that is pretty simple is this one:

[http://www.iwebtool.com/speed_test](http://www.iwebtool.com/speed_test)

My site scored 0.15 seconds per Kb on that test, which seems pretty high to me, specially when compared to giants like Google, which scores 0.01.

Well, I can't really compare it to Google, so I was wondering what the results for other web sites owned by the Ubuntu community members?

There is no need to specify your site address or web hosting service, but would be useful if you mention if the site is build on top of a CMS like Joomla, Drupal or Wordpress. I'm particularly interested on Joomla results, since is the platform I use. Also please specify if you are using a shared, clustered or dedicated server.

---

### Post by Quadunit404 on 2010-12-02
```
qu404.com	6.61 KB	4.71 seconds	0.71 seconds
```

4.71 seconds and 0.71 seconds per KB... not bad... I think.

It used to be MUCH slower than that until I tweaked some settings in my custom php.ini.

---

### Post by lovinglinux on 2010-12-02
> **Quadunit404 said:**
> ```
qu404.com	6.61 KB	4.71 seconds	0.71 seconds
```

4.71 seconds and 0.71 seconds per KB... not bad... I think.

It used to be MUCH slower than that until I tweaked some settings in my custom php.ini.

I guess you meant 0.071, not 0.71 ;)

---

### Post by RandomJoe on 2010-12-02
It seems to get iffy numbers on small pages.  If yours are currently short you may want to try tossing in some long text to test with.

I tried mine, and it said it only downloaded 320 bytes for the main page, and reported 0.96 sec/kb the first time, 0.71 the second.  (My /index.html is actually just a redirect to the "real home" in a different directory so is a very short file.)

The "real home" page reported 7.81kB and 0.05 sec/kb.  

Tried another page with a lot more text, and it reported 16.6kB dl and 0.02 sec/kb.

---

### Post by MechaMechanism on 2010-12-02
Mine is a hobby site.  Runs off the computer I'm typing this post on.  My ISP is a cable company and my upload speed is 1 mb/s or 125 Kb/s.  Strictly plain html and no PHP or JavaScript.  I do have Google Analytics which is JavaScript.  I went to that site and did the test.  It don't seem very accurate to me.

[http://universal-mechanism.org](http://universal-mechanism.org)

One thing to keep in mind about shared hosting is that server responsiveness is often much worse that a home computer.  Even if the shared hosting has more bandwidth it often don't matter because responsiveness off the server sucks.  Since my home computer has all it's resources available to Apache, it's not uncommon for my little hobby web site to feel quicker.  However when the going gets tough the shared hosting will win in the bandwidth department but the shared server will still suck at responsiveness.

---

### Post by Viva on 2010-12-03
0.4 seconds	0.05 seconds

---

### Post by mcduck on 2010-12-03
If you feel the site is slow, you might want to also analyze the *content* of the site, not just the server speed.

Try this one, for example. it can also be used directly from the Web Developer Extension's Tools-menu, if you use that Firefox extension...)
[http://websiteoptimization.com/services/analyze/]("http://websiteoptimization.com/services/analyze/")

---

### Post by TNT1 on 2010-12-03
I get 0.08 seconds /kb, and a load time of1.78 seconds...

---

### Post by Verbeck on 2010-12-03
1.38 seconds  0.28 seconds, using drupal

must find a better isp :/

---

### Post by undecim on 2010-12-03
Getting 0.02 seconds for my blog which is 56.04 KB (running WP with SuperCache)

---

### Post by lovinglinux on 2010-12-03
I guess I should complain to my web hosting :(

---

### Post by Viva on 2010-12-03
You should. If you're on a shared host, they're probably limiting the number of connections.

---

