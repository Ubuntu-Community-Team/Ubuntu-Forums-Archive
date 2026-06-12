---
title: "Apache2, Rails and Passenger: Premature end of script headers"
date: 2009-12-04
forum: Server Platforms
---

### Post by DewBoy3d on 2009-12-04
Greetings! I am getting started with rails and am running into an issue with my setup. I have installed rails and everything works when I do a script/server but when attempting to get to the site with Apache2 via Passenger(2.2.7) I am getting "Premature end of script headers" error. I read somewhere that it may be a permissions issue. here is how I'm setup..

I have a site enabled in Apache2 in which the DocumentRoot is /home/dewboy3d/www/ruby/life/public

All the files and directories are dewboy3d:dewboy3d owned and the log directory is chmod 777. I can load any page from the address bar but once I perform an action (GET/POST) I get this in the browser
```
We're sorry, but something went wrong.

We've been notified about this issue and we'll take a look at it shortly.
```

and the Apache2 errors.log file shows 
```
Thu Dec 03 20:46:41 2009] [error] [client xx.xx.xx.xx] Premature end of script headers: contacts
[ pid=7576 file=ext/apache2/Hooks.cpp:682 time=2009-12-03 20:46:41.795 ]:
  The backend application (process 7640) did not send a valid HTTP response; instead, it sent nothing at all. It is possible that it has crashed; please check whether there are crashing bugs in this application.
```

Apache2 is running as the default www-data user.
Rails and Passenger are both running as dewboy3d

I have tried changing ownership on the files to www-data but same thing happens. And again, it all works flawlessly when i do a script/start. How can I get this working normally with Apache2 and Passenger? Any help would be greatly appreciated.

---

