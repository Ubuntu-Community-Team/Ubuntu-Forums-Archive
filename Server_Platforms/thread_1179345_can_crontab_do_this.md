---
title: "can crontab do this"
date: 2009-06-05
forum: Server Platforms
---

### Post by dan98 on 2009-06-05
I need to run a shell script on a series of dates. The dates don't follow a pattern ex. 
run the shell script on 06/09/09, 06/14/09, 07/01/09, and 07/28/09. 
 
I could put the dates in a database and use command substition but I would like to know if there is an easier way to do this in the shell.

---

### Post by DBrocks on 2009-06-05
```
 
crontab -e

```
 
Put this in
 
Replace XX with the minute you wish the script to be run on (0-59)
Replace YY with the hour you wish it to run on (0-23, 0=Midnight)
```
 
XX YY 09 06  * /path/to/your/script
XX YY 14 06  * /path/to/your/script
XX YY 01 07  * /path/to/your/script
XX YY 28 07  * /path/to/your/script

```
 
Read up on this as well. [http://ubuntuforums.org/showthread.php?t=102626&highlight=cron](http://ubuntuforums.org/showthread.php?t=102626&highlight=cron)

---

### Post by dan98 on 2009-06-16
Thanks. This should work fine. I just have to remember to delete the old dates and add the new dates each year.

---

