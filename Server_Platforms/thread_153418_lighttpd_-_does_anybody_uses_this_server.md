---
title: "lighttpd - does anybody uses this server?"
date: 2006-03-31
forum: Server Platforms
---

### Post by pedrotuga on 2006-03-31
Ok... they say wonders abut it in their website, of course.

"beter for peak performance, fast, ligh, bla bla bla"... ok...

opinions about it?

do u like it? do you not like it? is it faster than apache? why did u change? what does it lacks? etc etc etc...

tell me about it... i am considering to change :)

thx

---

### Post by onaquest on 2006-04-01
The main advantage of lighthttpd for casual/home users is its small footprint. 
For instance I used it on a small appliance-like device (Kuro box), that had very limited RAM. Apache wasn't an option there.

The main drawback of lighthttpd would be if you want to start using PHP and the wealth of packages preconfigured for Apache. While you might be able to get them to work with lighthttpd, be ready for some extra steps.

As far as speed goes, unless you're trying to optimize a heavy-traffic website I doubt you will feel a significant difference between Apache and Lighthttpd on a full-size PC.

So it boils down to what you want to do with your web server. For anything beyond serving static webpages you might want to stick to Apache, for convenience. This said, if you know what you're doing and want the pedal to the metal...

---

### Post by adamkane on 2006-04-01
See:
[http://www.xorg.us/news.php](http://www.xorg.us/news.php)

> 
29/03 :  Eaccelerator + Zend OptimizerWell after trying to figure out how to squeeze every last bit of performance out of a PHP + MySQL web server I came upon Eaccelerator and the Zend Optimizer.

My webserver of choice right now is Lighttpd. Its a little faster than Apache in my personal tests. I will include my Apache benchmark in the test just for reference. So i will also include lighttpd, lighttpd + Zend optimizer, and lighttpd + Zend + Eaccelerator. Here's my results in how many hundreths of seconds it took to load the calander page on this site. The test was just reloading the page twice a second, 10000 times with no browser caching.

 [IMG]http://www.xorg.us/e107_images/newspost_images/graph23.gif[/IMG] 

Zend just barely helps it seems, but hot damn, Eaccelerator is incredibly fast. Apparently Eaccelerator caches the PHP page so it does not have to keep reparsing the same code over and over again. We are blazin now!!


---

### Post by LordHunter317 on 2006-04-01
[QUOTE=onaquest]As far as speed goes, unless you're trying to optimize a heavy-traffic website I doubt you will feel a significant difference between Apache and Lighthttpd on a full-size PC.[/quote]Yes, you will.  The difference for certain types of serving is so large it's not even funny.

---

### Post by pedrotuga on 2006-04-05
[quote=LordHunter317]Yes, you will.  The difference for certain types of serving is so large it's not even funny.[/quote]

mmmm... ok.... what kind of serving then?
when is it recomended the most?

---

### Post by dermotti on 2006-04-07
Lighttpd is faster and uses less memory/cpu that Apache in my personal experience. Granted I am not a Apache Guru, I'm sure there are things that can be tweaked on it, but vanilla Lighttpd beats Apache hands down for speed and uses alot less resources at the same time.

Apache does have alot of cool features, like mod_bandwidth and others that lighttpd doesnt have.

---

### Post by pedrotuga on 2006-04-07
i think i will try it sometime. I like minimalist peak performance stuff... well... or maybe i just cant afford confortable hardware for the needs...


thank you... btw... how old is lighttpd?

---

### Post by dermotti on 2006-04-11
Looks about 3 years old

---

### Post by jdonnell on 2006-04-12
a lot of ruby on rails sites use lighttpd. I use it for my 3-4 rails sites. I prefer it to apache these days because the config is simpler.

---

