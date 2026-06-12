---
title: "access.log blocked - can I generate one with php?"
date: 2009-01-14
forum: Server Platforms
---

### Post by swharden on 2009-01-14
I have a PHP-enabled website that's hosted professionally, but they don't give me access to my logfiles.  Is there an easy way to use PHP to generate my own "access.log", so that I can analyze it myself with stats programs (like awstats)?

Thanks!!  --Scott

---

### Post by swharden on 2009-01-20
anyone?

---

### Post by drubin on 2009-01-20
not with out writing your own logging into your php scripts. But this would have to appear in a globally included file so that it is on every page.

Also lots of files writing to the same logfile. opening and closing it might be a bit load intensive. 

Apache keeps the logfile open and has correct threading to handle this.

Have you tried [google analytics]("https://www.google.com/analytics/")? It provides and online logging facility with graphs and charts.

---

### Post by swharden on 2009-01-22
> **drubin said:**
> Have you tried [google analytics]("https://www.google.com/analytics/")? It provides and online logging facility with graphs and charts.

Yes, but I want to see IP addresses and match them with requests (which is against Google's privacy policy)

SOLUTION:  It's not amazing, but it works.  **[http://www.swharden.com/blog/2009-01-22-using-php-to-create-apache-style-accesslog/]("http://www.swharden.com/blog/2009-01-22-using-php-to-create-apache-style-accesslog/")**

---

### Post by drubin on 2009-01-23
> **swharden said:**
> Yes, but I want to see IP addresses and match them with requests (which is against Google's privacy policy)

SOLUTION:  It's not amazing, but it works.  **[http://www.swharden.com/blog/2009-01-22-using-php-to-create-apache-style-accesslog/]("http://www.swharden.com/blog/2009-01-22-using-php-to-create-apache-style-accesslog/")**

for highload/traffic servers that is going to cause a dead lock with all the file locks at the same time. For simple none highloads it will be fine :)

Only issue is that it doesn't log image/css/javascript...* requests since they aren't php files. It might also interfere with your php CLI scripts since it was configed in php.ini and not apache.

---

### Post by swharden on 2009-01-23
> **drubin said:**
> for highload/traffic servers that is going to cause a dead lock with all the file locks at the same time. For simple none highloads it will be fine :)

Only issue is that it doesn't log image/css/javascript...* requests since they aren't php files. It might also interfere with your php CLI scripts since it was configed in php.ini and not apache.

I can't think of a better option.  Can you?  I'd love to have apache give me log files, but since my webhost doesn't give me that option, I'm kind of stuck.  There isn't *ANY* way I could log file access anyway given my situation, right?

An alternative to file opening/closing would be to use a SQL database... perhaps it'd be more load-friendly.

---

### Post by drubin on 2009-01-25
> **swharden said:**
> I can't think of a better option.  Can you?  I'd love to have apache give me log files, but since my webhost doesn't give me that option, I'm kind of stuck.  There isn't *ANY* way I could log file access anyway given my situation, right?

An alternative to file opening/closing would be to use a SQL database... perhaps it'd be more load-friendly.

How highload are these sites? If they do not get an excessive high traffic then don't worry to much about it. I just mentioned it as it is a point to take note of for higher pageviewed sites (Also this doesn't log images/files).

The db option is a pretty nice one since the DB would handle the thread syncronisation but you would have to build custom reporting = mission unless it is needed.

---

