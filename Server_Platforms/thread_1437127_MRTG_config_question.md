---
title: "MRTG config question"
date: 2010-03-23
forum: Server Platforms
---

### Post by jsprev on 2010-03-23
Just installed Ubuntu 9.10 and installed MRTG.  During configuration, however, I ran in to a snag.  I was following this procedure:

[http://linuxbasement.com/content/mrtg-ubuntu-server](http://linuxbasement.com/content/mrtg-ubuntu-server)

Sounded reasonable enough but when I ran this line I received an error:
indexmaker --output=/var/www/mrtg/index.html /etc/mrtg/mrtg.cfg
[COLOR=Red]use of uninitialized value $first in hash element at /usr/bin/indexmaker line 353
[COLOR=Black]
So, I look in indexmaker and see this:

[352] my $first = $order[0];
[353] my $host = $$rcfg{host}{$first};

Anyone know what I need to do?  I'm new to all this so if I'm missing something simple please let me know.

Thanks

[/COLOR][/COLOR]

---

### Post by jsprev on 2010-03-23
Would any more info help?

---

### Post by terazen on 2010-03-24
It looks like that is a script that creates your index page if I'm guessing correctly.  Check your html directory where mrtg is putting it's files and if they are all there then you can just manually create the index page.  I manually created my index.html and also edited the file cfgmaker made.

Cfgmaker will index every active port on a switch and some of them are ip phones and printers that I really didn't care to have monitored.

Basically you should run cfgmaker (creates config file), edit the config file (remove stuff you don't care about monitoring), run that ENV command from the guide (creates html files using the config file), add the ENV command to crontab or cron.d/mrtg to update html files every 5 minutes, check file permissions in web directory, and create index.html in the web directory.

---

### Post by jsprev on 2010-03-31
Thanks!  Will check it out.  Good tips.  Sorry I didn't reply earlier - I was out of the office.
 
> **terazen said:**
> It looks like that is a script that creates your index page if I'm guessing correctly. Check your html directory where mrtg is putting it's files and if they are all there then you can just manually create the index page. I manually created my index.html and also edited the file cfgmaker made.
 
Cfgmaker will index every active port on a switch and some of them are ip phones and printers that I really didn't care to have monitored.
 
Basically you should run cfgmaker (creates config file), edit the config file (remove stuff you don't care about monitoring), run that ENV command from the guide (creates html files using the config file), add the ENV command to crontab or cron.d/mrtg to update html files every 5 minutes, check file permissions in web directory, and create index.html in the web directory.

---

