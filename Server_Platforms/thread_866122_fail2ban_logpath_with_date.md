---
title: "fail2ban logpath with date"
date: 2008-07-21
forum: Server Platforms
---

### Post by cdenley on 2008-07-21
I need to configure fail2ban to monitor logs created daily with the date in the log's filename.
For example: "LOG20080721.log"
Is this possible?

---

### Post by cariboo on 2008-07-21
Have a look here:

[http://www.howtoforge.com/fail2ban_debian_etch](http://www.howtoforge.com/fail2ban_debian_etch)

It is for debian, but it will work in Ubuntu too.

Jim

---

### Post by cdenley on 2008-07-22
I guess I could use "LOG*.log" for the logpath. This doesn't seem to work for me, though, because the logs are large, stored for a long time, and accessed over the network. When I started fail2ban, I let it run for a few minutes, and I assume it was still reading the logs. If I could configure it to read only the log for the current day, it might work.

---

### Post by cariboo on 2008-07-22
You can edit the logpath in each section to whatever log file you want. Unfortunately their is not global logging option so it would have to be changed for each individual section. You could set it up using the day date string, I'm not exactly sure of the synatax as I haven't used it for a while but you could try something like:

```
logpath=/var/lob/fail2ban_%d%m%y.log
```

this would give you a log file name of fail2ban_220708.log

Jim

---

### Post by cdenley on 2008-07-22
> **cariboo907 said:**
> You can edit the logpath in each section to whatever log file you want. Unfortunately their is not global logging option so it would have to be changed for each individual section. You could set it up using the day date string, I'm not exactly sure of the synatax as I haven't used it for a while but you could try something like:

```
logpath=/var/lob/fail2ban_%d%m%y.log
```

this would give you a log file name of fail2ban_220708.log

Jim

Exactly what I'm looking for, but it doesn't seem to work.
```

 * Restarting authentication failure monitor fail2ban
Traceback (most recent call last):
  File "/usr/bin/fail2ban-client", line 401, in <module>
    if client.start(sys.argv):
  File "/usr/bin/fail2ban-client", line 370, in start
    return self.__processCommand(args)
  File "/usr/bin/fail2ban-client", line 180, in __processCommand
    ret = self.__readConfig()
  File "/usr/bin/fail2ban-client", line 375, in __readConfig
    ret = self.__configurator.getOptions()
  File "/usr/share/fail2ban/client/configurator.py", line 65, in getOptions
    return self.__jails.getOptions(jail)
  File "/usr/share/fail2ban/client/jailsreader.py", line 64, in getOptions
    ret = jail.getOptions()
  File "/usr/share/fail2ban/client/jailreader.py", line 70, in getOptions
    self.__opts = ConfigReader.getOptions(self, self.__name, opts)
  File "/usr/share/fail2ban/client/configreader.py", line 84, in getOptions
    v = self.get(sec, option[1])
  File "/usr/lib/python2.5/ConfigParser.py", line 525, in get
    return self._interpolate(section, option, value, d)
  File "/usr/lib/python2.5/ConfigParser.py", line 593, in _interpolate
    self._interpolate_some(option, L, rawval, section, vars, 1)
  File "/usr/lib/python2.5/ConfigParser.py", line 634, in _interpolate_some
    "'%%' must be followed by '%%' or '(', found: %r" % (rest,))
ConfigParser.InterpolationSyntaxError: '%' must be followed by '%' or '(', found: '%y%m%d.LOG'
                                                                         [fail]

```

---

### Post by cdenley on 2008-07-22
Also, is it possible for it to read logs where the time is logged on the previous line. Something like...
```

log entry made at 07/22/2008 10:08:49
Authentication failed from IP xxx.xxx.xxx.xxx
log entry made at 07/22/2008 10:08:52
Authentication failed from IP xxx.xxx.xxx.xxx
log entry made at 07/22/2008 10:08:56
Authentication failed from IP xxx.xxx.xxx.xxx

```

---

