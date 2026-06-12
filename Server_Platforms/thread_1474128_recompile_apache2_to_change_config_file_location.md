---
title: "recompile apache2 to change config file location?"
date: 2010-05-05
forum: Server Platforms
---

### Post by jld186 on 2010-05-05
I'm hoping to try this experiment out where I have ALL of apache's files in a single folder in my home directory. I started thinking the process through and realized I needed to get the start up daemon httpd to look for the initial configuration file in the right place. Which will be in ~/apache2


According to [http://httpd.apache.org/docs/2.0/invoking.html](http://httpd.apache.org/docs/2.0/invoking.html)

"The first thing that httpd does when it is invoked is to locate and read the configuration file httpd.conf. The location of this file is set at compile-time, but it is possible to specify its location at run time using the -f command-line option"

Is there a way to change the way httpd is invoked so that is applies that "-f" option at EVERY runtime?

Or do I have to recompile apache to get this effect? And if so, how would I recompile to get this effect?


I'm running Ubuntu 9.04 Server and I'm trying this because I don't understand why apache's files are spread everywhere and why each OS is different in where stuff get's put.  I have been using MacOSX to serve my sites up and now that i'm moving to Ubuntu I have to keep looking up where things are at since it's not the same from system to system.

---

### Post by windependence on 2010-05-06
Doing this is going to cause you LOTS of problems but to answer your question, you wouldn't have to recompile to get the -f switch applied each time, simply modify the Apache startup script and add the -f option along with the correct parameters to specify your config file and then every time you start your server, Apache will start with the -f option applied. 

The reason Apache's files are "spread everywhere" as you say is because the old way of having one big config file was getting too big for some people. While I agree with you, the reason for all the modules is actually to "simplify" the configuration and make it easier to find things. For old timers like me it's confusing because I'm used to having them all in one file which BTW you can still do if you want as the old httpd.conf  is still there and can be used if you so desire.

-Tim

---

