---
title: "Webalizer error"
date: 2005-07-30
forum: Server Platforms
---

### Post by drummer on 2005-07-30
Hi all, 

I'm hoping to get some help with webalizer, I installed it but when I run webalizer from the terminal I get an error, thus:```
Webalizer V2.01-10 (Linux 2.6.10-5-386) English
Using logfile /var/log/apache2/access.log.1 (clf)
Creating output in /var/www/webalizer
Hostname for reports is 'ubuntuserver'
History file not found...
Previous run data not found...
Error: Unable to save current run data
Generating report for July 2005
Error: Unable to open file usage_200507.html!
Generating summary report
Error: Unable to open file index.html!
Error: Unable to write history file webalizer.hist
4678 records in 0.21 seconds

```and nothing is is the directory /var/www/webalizer.

Is there something I've missed? (there isn't much instruction on the homepage) extra parameters, and should I add it to cron when of if it works eventually?

---

### Post by heimo on 2005-07-30
File permission error? Can the user that runs webalizer, create files to the  output directory?

---

### Post by drummer on 2005-07-30
Scratch that about the error, it suddenly seems to be working now. Maybe I just needed to be a bit more patient.
EDIT - thanks anyway

---

### Post by eltaito on 2006-03-30
I know this is a bit late...but incase anyone else comes across this problem......it is really simple and usually occurs when you don't run webalizer as root....just type:

sudo webalizer

and that problem shoudl go away

---

### Post by Verbergen on 2007-03-19
Hey guys,
I know this is VERY late. But I had exactly the same problem and spent 30mins or so reinstalling and reading stuff to fix it!!
All you need to do is just run as root ... darn!! 
Why doesn't ubuntu just tell us??:mad: 
Anyways, it works great. 
Thanks for the help guys, this forum was better than the main search engines. 
Cheers.

---

