---
title: "UbuntuOne background service?"
date: 2010-06-02
forum: Ubuntu One (CLOSED)
---

### Post by piedro on 2010-06-02
Hello!  

Reading all the threads I've found I still haven't found any answer to the following beginners question: 

I can start the ubuntuone service with the "me-menue" (though it's not really syncing for me yet...) but when I close the preferences menue again the ubuntuone client seems to stop. 

Should the client not somehow run in the background? 
(With Karmic I had a panel-applet for that but I can't find it anymore!) 

Same with evolution: Shouldn't the evolution client somehow run in the background to make the indicator for incoming mail useful? 

Doesn't work for me ... have to keep the full evolution program running, can't find any evolution-background-service!  

thx for help, 
piedro

---

### Post by duanedesign on 2010-06-02
The syncdaemon handles the file syncing. To see if its running use this command in a terminal:

```
ps aux | grep ubu
```

You should see:

>  /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon

The Contacts are synced by a CouchDB database. You can check that by running

```
ps aux | grep beam
```

and for evolution I believe it is the evolution-data-server.

```
ps aux | grep ubu
```

---

### Post by piedro on 2010-06-04
thx duanedesign! 

I can see now that the ubuntuone-client is running, the ubuntuone service had problems so that solved this part. 

Different with evolution: 

I want the evolution service to run in the background because the indicator-applet doesn't show the status on mail-accounts when evolution is not running. Pretty useless! 

By the way: Is this a bug or can it be configured somehow? 

So my workaround would be to have the evolution-mail-client (I don't know what service this might be ...) run in the background for the indicator applet to use it for showing the correct mail status. 

Any better suggestions, ideas or help? 

thx, 
piedro

---

### Post by vinx on 2010-06-04
What I see in the log-file ~/.cache/desktop-couch/desktop-couchdb.stdout.1 and on [https://couchdb.one.ubuntu.com/](https://couchdb.one.ubuntu.com/) is that the couchdb-server is offline.

So no contacts in evolution since a few days.

---

### Post by laoshi on 2010-06-04
Thanks for the commands, duanedesign.
```
flemming@laoshi:~$ ps aux | grep ubu
flemming  3087  2.9  1.5  68628 47320 ?        SLl  13:48   5:33 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-syncdaemon
flemming  3761  0.1  0.7  36188 21872 ?        SL   14:06   0:18 /usr/bin/python /usr/lib/ubuntuone-client/ubuntuone-login
flemming  9553  0.0  0.0   3328   816 pts/0    S+   16:58   0:00 grep ubu

```
What exactly do the numbers signify? And the question mark?

---

### Post by laoshi on 2010-06-08
OK - I found the answer where I ought to have looked in the first instance: ```
man ps
```
PID %CPU-usage %MEM-usage VSZ RSS TTY STAT TIME COMMAND

---

