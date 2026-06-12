---
title: "Namecheap &amp; Python"
date: 2011-04-11
forum: Server Platforms
---

### Post by stealth. on 2011-04-11
First post yay!

I've written a script to update your IP with Namecheap in python

Create the file /home/your_user_name/update_dns

Use nano, gedit, etc.. and add the following

```

# -*- coding: utf-8 -*- 

__import__("urllib2").urlopen("http://dynamicdns.park-your-domain.com/update?host=%s&domain=%s&password=%s" % ("@", "YOURDOMAIN", "YOURPASSWORD"))[FONT=Verdana]
[/FONT]
```[FONT=Verdana]

Add it to crontab (crontab -e)

[/FONT]```
* */1 * * * python /home/your_user_name/update_dns

```Thats it, it should be updating every hour. 

Correct me if anything is wrong.

---

