---
title: "php5-cgi -- ideal number of max child processes?"
date: 2010-11-11
forum: Server Platforms
---

### Post by gewone on 2010-11-11
Hi guys!

Just curious if any of the experienced enthusiasts around here could point me in some direction. It's like this, I have a small home web server running nginx and php5-fpm (for FastCGI spawning).

Now, the computer is really not made of server hardware. In fact, it's actually a really old laptop that will probably burst of overheat or something any month, but I can cope with that.

However. Specs in short are Pentium 3 (1200Mhz) w/ 512MB (SO-DIMM) RAM and ~1500MB swap. Now, per default php5-fpm pulled 10 instances of php5-cgi running in the background. I figured, since this is a simple single core machine, 10 processes would be more of a memory eating monster with no real scaling functionality, than a good choice.

Thus, I investigated *'/etc/php5/fpm/php5-fpm.conf'* for clarificaiton.


```

; The number of child processes to be created when pm is set to 'static' and the
; maximum number of child processes to be created when pm is set to 'dynamic'.
; This value sets the limit on the number of simultaneous requests that will be
; served. Equivalent to the ApacheMaxClients directive with mpm_prefork.
; Equivalent to the PHP_FCGI_CHILDREN environment variable in the original PHP
; CGI.
; Note: Used when pm is set to either 'static' or 'dynamic'
; Note: This value is mandatory.


pm.max_children = 10
```

Obviously, this is the line. It's will explained and since my server hardly get any visits at all, a figure of 1 would probably suffice. Each child process eats over 40MB of memory, so the default 10 was [so to speak] a nagging b-tch.

I finally set it to three. Does this sound good? By the way, how would excessive connections be handled? Gateway error 403 or something? So that that visitor needs to do CTRL+R in their browser to (hopefully) get one hook? I'm just curious, got no real experience in these matters.



[I]
Ty in adv~
Regards~[/I]

---

### Post by wongo888 on 2010-11-11
You may want to stress test your system to find an optimal setting. From another (faster and better) machine use something like Apache Bench or Siege. Both are very easy to use.

[http://httpd.apache.org/docs/2.0/programs/ab.html](http://httpd.apache.org/docs/2.0/programs/ab.html)

[http://www.joedog.org/index/siege-manual](http://www.joedog.org/index/siege-manual)

---

