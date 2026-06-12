---
title: "start syncthing as service"
date: 2016-09-24
forum: Ubuntu/Debian BASED
---

### Post by marchello_lippi2 on 2016-09-24
Hi all,

I'm able to start syncthing manually on my raspberry pi using```
/usr/bin/syncthing
```


I'd like to start it as I do it usually in my ubuntu 
```
sudo service syncthing start
```

But it says
```
$ sudo /usr/sbin/service syncthing start
syncthing: unrecognized service
```

```
[INDENT]$ cat /etc/*-release
PRETTY_NAME="Raspbian GNU/Linux 7 (wheezy)"
NAME="Raspbian GNU/Linux"
VERSION_ID="7"
VERSION="7 (wheezy)"
ID=raspbian
ID_LIKE=debian
ANSI_COLOR="1;31"
HOME_URL="http://www.raspbian.org/"
SUPPORT_URL="http://www.raspbian.org/RaspbianForums"
BUG_REPORT_URL="http://www.raspbian.org/RaspbianBugs"

[/INDENT]
```

Please advise.
Thanks ahead.

---

### Post by marchello_lippi2 on 2016-09-24
Looking into this howto for now
[https://www.cuonic.com/posts/how-to-start-syncthing-on-debian-boot](https://www.cuonic.com/posts/how-to-start-syncthing-on-debian-boot)

---

### Post by ian-weisser on 2016-09-25
On your pi, does syncthing have a sysvinit script in /etc/init.d ?
That's what the 'service' command looks for.
See 'man service'

---

### Post by marchello_lippi2 on 2016-09-26
[SIZE=1][FONT=arial] 						 							[B]ian-weisser, 
that's it, it works for me already.
[/B]
[/FONT][/SIZE]

---

