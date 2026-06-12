---
title: "crontab not working?"
date: 2009-12-12
forum: Server Platforms
---

### Post by maclenin on 2009-12-12
I am trying set up a cron job, using crontab -e ....

I run...

```
$ crontab -e
```

...then enter the following general parameters into the text editor...

```
* * * * * /home/server/script.sh
```

...then save the file and receive the following...

```
no crontab for server - using an empty one
crontab: installing new crontab
$
```

...and the script never runs!

Any thoughts?

---

### Post by sprouty on 2009-12-12
does the script have execute option
chmod +x /home/server/script.sh

also probably best to put ouput to a logfile so you can see the error message:
* * * * * /home/server/script.sh >>/home/server/scriptlog 2>&1

then see what the logfile says

---

### Post by Muttley99 on 2009-12-12
I has similar problems to this also; do the above logfile: Also, try being explicit in your command, some crontabs require this;
***** /home/server/sh script.sh

Some also need the user specified i.e.

***** root /home/server/sh script.sh

I think also that if you use crontab -e you are using the crontab for the user your logged in as!

to apply a specific user crontab was something like;

crontab -e -u root

good luck!

---

### Post by maclenin on 2009-12-12
**sprouty** and **Muttley99**!

re: chmod - I "chmoded +x" the script file when I created it - doesn't that mean it will execute from wherever it's placed? I can execute the file via right-click "Execute" - but the crontab -e method will not execute the script.

re: logfile - I'll give that a whirl.

re: user - I tried the same with sudo crontab -e - still no luck!

Thanks for the comments, I'll post back what the log reveals....

---

### Post by maclenin on 2009-12-12
The script log file is empty....

---

### Post by erict43 on 2009-12-12
Try:
```
 
* * * * * /bin/bash /home/server/script.sh

```

---

### Post by maclenin on 2009-12-12
No activity....

---

### Post by erict43 on 2009-12-12
Did you put PATH settings inside your script?
 
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by Muttley99 on 2009-12-12
> **erict43 said:**
> Try:
```
 
* * * * * /bin/bash /home/server/script.sh

```

Oh yes! i forgot about that. Also try adding the path to bash in the title of the crontab along with the other standard inputs.
i.e. at the start of the file add;

[HTML]SHELL=/bin/bash[/HTML]

---

### Post by maclenin on 2009-12-12
From that same page:


"The above commands are stored in a crontab file belonging to your user account and executed with your level of permissions."

I do NOT have /etc/cron.allow....

"In the case where neither file exists, the default on current Ubuntu (and Debian, but not some other Linux and UNIX systems) is to allow all users to run jobs with crontab."

I have added SHELL=/bin/bash to the script....

Should the 1st script event run IMMEDIATELY after the crontab file saved?

---

### Post by maclenin on 2009-12-12
Also:

SHELL=/bin/bash added to script.

/bin/bash added to crontab.

To no effect....

---

### Post by maclenin on 2009-12-12
...behold, the original script, which WILL run by right-click, but WILL NOT run via crontab -e:

```
#!/bin/bash

traceroute testurl.com >> traceroute.txt
```

---

### Post by erict43 on 2009-12-12
You should probably post your script, that might help troubleshoot.

---

### Post by Muttley99 on 2009-12-12
I'm here lying in bed waiting for someone to answer my thread! :?

I hate to state the obvious, cron is running?

[HTML]ps-ew[/HTML]

---

### Post by maclenin on 2009-12-12
the essentials of the script are posted...


```
#!/bin/bash

traceroute testurl.com >> traceroute.txt
```


...and I believe cron is, indeed, running....

Should the "first run" of the script execute immediately after crontab -e is set up?

---

### Post by erict43 on 2009-12-13
Try putting this in the first line of your crontab file.  It might not know where to find the traceroute utility.
```
 
PATH=/usr/sbin:/usr/bin:/sbin:/bin

```

---

### Post by maclenin on 2009-12-13
So... I did a little experimenting within the terminal, trying to execute the script from different directories using the PATH to the script to run it "remotely" - to no avail (at least in the way I was going about it). Then I tried running the script from within the script directory, in this way (mimicking the way the path was defined in crontab -e)...
```
:~/script$ /path/to/script/script.sh
```
...and it ran from the terminal...so...

... I added a "cd" to the "PATH" to the script (to point crontab -e to the "proper" directory"), without changing crontab -e...

**script**...
```
#!/bin/bash

cd /path/to/script
script
```
**crontab -e**...
```
* * * * * /path/to/script/script.sh
```
...and...Success!

My takeaway was that I needed to re-define the PATH to the script for crontab (as I had done, manually, during my terminal test) - to "redirect" the system's default /etc/crontab settings....

Thanks for the guidance!

---

