---
title: "Server 14.04 LTS Crontab Issue"
date: 2014-12-01
forum: Server Platforms
---

### Post by slamanna212 on 2014-12-01
Im trying to get a python IRC bot to launch at startup, the crontab i made works perfectly when i run it in a terminal, it does not work when i put it in a crontab and reboot the server. This crontab worked perfectly in fedora 17, now its not working at all

Crontab:
```
@reboot /usr/bin/screen -d -m /usr/bin/python2.7  /home/TrollOP/willie/willie.py
```

Output from whereis python:
```
python: /usr/bin/python3.4 /usr/bin/python3.4m /usr/bin/python /usr/bin/python2.7 /usr/bin/python2.7-config /etc/python3.4 /etc/python /etc/python2.7 /usr/lib/python3.4 /usr/lib/python2.7 /usr/local/lib/python3.4 /usr/local/lib/python2.7 /usr/include/python2.7 /usr/share/python /usr/share/man/man1/python.1.gz

```

UPDATE #1 (there might be more)
I outputted the log of that crontab to a file and there is one entry, this:
```
Cannot make directory '/var/run/screen': Permission denied 
```

---

### Post by slamanna212 on 2014-12-01
Update: I edited the cron to output the log stuff to a file, and got this:

```
Cannot make directory '/var/run/screen': Permission denied
```

---

### Post by slamanna212 on 2014-12-01
Final Edit: Adding [CODE] sleep 10 && [CODE] right after the @reboot made it sleep 10 seconds to get around that error

---

