---
title: "Apache sometimes lists directory contents instead of executing PHP"
date: 2013-04-02
forum: Server Platforms
---

### Post by isecore on 2013-04-02
The last few months I've noticed a very annoying behavior from my server. Instead of executing the PHP as it should, occasionally it lists the directory contents instead. This is very annoying despite it happening only occasionally. I've attempted various things to try to remedy this as well as spending a large amount of trying to google it down - to no avail. Most of the articles I've found deals with the problem of not having the PHP module properly loaded. This is not the problem since Apache properly displpays PHP content around 98% of the time.

It's those other 2% which is incredibly frustrating and which shouldn't happen. It's also extremely difficult to troubleshoot since it only happens randomly and intermittently. Does anyone have experience with this and can point me in the proper direction? I can't quite remember all the things I've tried, but among other giving Apache more servers (I run the standard prefork MPM on Apache 2) as well as upping the keep-alive and PHP memory.

Machine is running Ubuntu Server 12.04 LTS. Appreciate any help!

---

### Post by mojorising on 2013-04-03
Hi, there. 

This is a strange problem indeed and I haven't seen it before. The first thing that springs to mind is that maybe the request is not quite right. Have you checked the logs to see which requests produce this intermittent result? Maybe you can rewrite bogus requests or at least serve them a 404 page instead of directory contents. 

After you have checked that, take a look at permissions. Does the apache or other appropriate user own and have proper permission to the files/directories requested?

KeepAlive should have nothing to do with this sort of problem, as with PHP memory. I recommend setting a KeepAlive to less than five seconds, if on at all (I often prefer two seconds) unless you have unusual circumstances. PHP memory depends on your system and application so you'll have to do more research for optimum settings there. I also wouldn't go crazy with the prefork settings as they aren't the problem here and setting them too far out of optimum range for your application can cause other issues.

It is a good idea to turn off directory listing for security reasons anyway, unless you really need it turned on.

It seems that maybe when you or your users are requesting this PHP code, the request is for a directory, rather than a specific PHP file. Can you put the exact PHP file in your request and see if you can reproduce it then (after trying the above things)? It might be a good idea to use Apache Bench, JMeter, or similar to test both URIs while tailing the Apache access and error logs to get a good look at what's really going on. If you don't have experience with either of these tools, then Apache Bench is your best option. It's easy to learn and you can be productive with it right away. Install it via "sudo apt-get install apache2-utils". Run it by typing "ab" at the command line. 

I've given you fairly general advice but that's the best I can do without more detail on your stuff. This should get you in the right direction, however, and I think if you follow those steps above, you should get a lot closer to solving the problem.


Best,
Mike

---

### Post by SeijiSensei on 2013-04-03
If you have the Indexes option enabled in the virtual host declaration or in an .htaccess file, then Apache will list the contents of directories that do not have an appropriate index.* file like index.php or index.html.  To disable this behavior, make sure there is no "Options Indexes" or "Options All" in any of your virtual host configurations.  Then, visiting a directory without an index file Apache will return a "directory listing denied" error page.

---

### Post by isecore on 2013-04-03
Hi, thanks for your answers. This behavior is not on empty directories. Yes, for various reasons I have the Indexes enabled on some sites, but this random behavior happens on index-directories containing a functioning index.php and a running site. Almost everything on my machine is various Wordpress-installations, and like I said - about 98% of the time there are no interruptions or other strange behavior. It just happens randomly and about 2% of the time. 

I've looked at the access logs but all I see are HTTP 200 OK responses, nothing out of the ordinary. The problem is mostly because this is a relatively rare instance and it's not reproducible on demand it's also very difficult to know where to look in the other logs. I mostly just try to reload the sites and hope the error appears so I know where to look in the logs.

Again, thanks for your input. I haven't seen this error for the last 24 hours, and the only change I've made is put the KeepAlive at a more sane level (2 secs now) and also I've uninstalled mod_security which I installed 2 years ago for reasons I cannot remember now.

---

### Post by isecore on 2013-04-05
So, I had a stroke of luck last night and managed to catch one of the sites. I've disabled Directory Listing by disabling mod_autoindex. However, one of the sites gave the error and I managed to look it up in the logs. It gets served as a 404. It happens on the site index, no subdirectory. Almost all of the sites run Wordpress and like I said 98% of the time everything works fine.

---

### Post by isecore on 2013-04-28
So, for what it's worth, I seem to have nailed this down after A LOT of trial and error. The culprit was memcached which I installed a few months back in the hopes of possibly speeding up sites in the future. I installed it and then realized that it wasn't quite what I expected or wanted and then I just basically forgot/ignored it and everything seemed fine. It's been a week after I uninstalled it now and NO ERRORS or other funky behavior.

Thus I can only conclude that the culprit was memcached. I'll be keep an eye on my sites but haven't seen anything for a week. If the odd behavior returns, I'll let y'all know but until then you can consider this matter closed.

---

