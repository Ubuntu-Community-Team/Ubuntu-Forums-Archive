---
title: "ubuntu 9 with double cron action"
date: 2009-06-12
forum: Server Platforms
---

### Post by alfredolo on 2009-06-12
Hello,
I have a server with ubuntu 9 and a problem. 
Here is my cron :

crontab -e -u utente

*/2 * * * *    php /home/utente/trigger.php

now if i do a simple :

ps aux | grep trigger

i get :

1003     21499 21495  0 21:54 ?        00:00:00 /bin/sh -c php /home/utente/trigger.php
1003     21501 21499  0 21:54 ?        00:00:00 php /home/utente/trigger.php

It is executed 2 times ? How can i fix it ?
Thank you for help
Alfred

---

### Post by gombadi on 2009-06-12
First line is running sh with a process ID of 21499 and a parent process ID of 21495.

Second line is running php, your script, with a process ID of 21501 and a parent process ID of 21499.

Your command is only running once but has a parent.Nothing to fix as it is normal.


There is a ptree command in the repositories that shows the process tree or you can use -
```

ps fauwx

```

---

### Post by alfredolo on 2009-06-12
Thank you very much !

Any idea on how to see a single line with a linux command ?
like : 1003     21501 21499  0 21:54 ?        00:00:00 php /home/utente/trigger.php
and no others

I need it to check if there is a single script running every time the script start.. 
Thank you !
Alfredo

---

### Post by gombadi on 2009-06-12
> 
Any idea on how to see a single line with a linux command ?
like : 1003 21501 21499 0 21:54 ? 00:00:00 php /home/utente/trigger.php
and no others


As with Linux there are many ways depending on what you want :-)

You could use 
```

ps aux | grep trigger | grep -v bin/sh

```

What information are you wanting from the one line? Just the fact that there is only one or something in the line?

If you are just wanting a count then
```

ps aux | grep -c trigger

```

will provide a number "2". Change your php code to be happy with "2" and work from there. Just a thought :-)

---

### Post by alfredolo on 2009-06-12
The -v option in perfect :D

Thank you very much for your help !
Alfred

---

