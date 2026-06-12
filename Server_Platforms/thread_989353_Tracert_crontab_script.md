---
title: "Tracert crontab script"
date: 2008-11-21
forum: Server Platforms
---

### Post by yield999 on 2008-11-21
Hi Everyone,

I am curently building a script to do some tracert to verify if our web hits goes by the 10MB link and not our T1...

To do so I have devided to use tracert this way :

> > /usr/local/nagios/var/tracert.log
date >> /usr/local/nagios/var/tracert.log

sudo /usr/sbin/traceroute EXTERNAL_IP >> /usr/local/nagios/var/tracert.log

sleep 10


var=`egrep EXTERNAL_IP.xx? /usr/local/nagios/var/tracert.log | cut -d" " -f4 | cut -d"." -f4`

if [[( $var = 11 )]]
then
mail -s 'We are using the 10 MB link everything is ok' [email]user@domain.com[/email] < /usr/local/nagios/var/route_ok.msg
fi

if [[( $var = 12 )]]
then
mail -s 'Crap ! the 10 MB Link is Down... RUN !' [email]user@domain.com[/email] < /usr/local/nagios/var/route_bad.msg
fi


So my problem is that tracert need to be run as root and if I try to add this script in another user crontab file, the script does not run... 

What should I do ?

P.S: Replace the term EXTERNAL_IP by a IP address... :)

---

### Post by Vegan on 2008-11-21
Is the script permission for executable set?


:guitar:

---

### Post by yield999 on 2008-11-21
Yes and the script run fine if I do > ./tracert.sh    <--- name of my script while log as root....

---

### Post by unutbu on 2008-11-21
Have you tried putting
```

17 *	* * *	root    /absolute/path/to/tracert.sh
```

in /etc/crontab ?
(Change the path to tracert.sh, of course).

---

### Post by hictio on 2008-11-21
> **unutbu said:**
> Have you tried putting
```

17 *	* * *	root    /absolute/path/to/tracert.sh
```

in /etc/crontab ?
(Change the path to tracert.sh, of course).

++
Another one, add the full path to the interpreter you are using, be it bash or sh, before the full path to the script itself:

```

17 *	* * *	root    /bin/sh /absolute/path/to/tracert.sh

```

---

### Post by yield999 on 2008-11-21
The problem was the interpreter....
It is now fixed.... Thanks guy's... Even if I  figure out before I read your reply... lol

---

