---
title: "proftpd time stamp off by an hour"
date: 2011-07-05
forum: Server Platforms
---

### Post by iconoclast hero on 2011-07-05
For some reason, the proftpd timestamp in xferlog is an hour behind.  When I execute date from the prompt, I get the correct time and this little tutorial is not easy to figure out:

[http://www.proftpd.org/docs/howto/Timestamps.html](http://www.proftpd.org/docs/howto/Timestamps.html)

Any ideas?

---

### Post by Toz on 2011-07-05
You're right, the tutorial is confusing. Here is what I would try. Based on what the tutorial says and some extra googling.....
From the manual: > The best way to deal with this issue, which is especially prominent on systems running glibc-2.3 or later, is to set the TZ environment variable explicitly, before starting proftpd. This can be done in an init script for proftpd, for example. 

According to: [http://pragneshkaria.com/2011/04/21/set-timezone-on-ubuntu-linux-server/]("http://pragneshkaria.com/2011/04/21/set-timezone-on-ubuntu-linux-server/") the timezone in ubuntu can be set via: ```
export TZ=’<your_timezone>’
```

To get your configured timezone, at a command window, type:```
cat /etc/timezone
``` (I get: America/Toronto)

Therefore, the command for me would be:```
export TZ=’America/Toronto’
```

Open the /etc/init.d/proftpd file, and after the line:
> # Start the proftpd FTP daemon., enter:
```
export TZ=’America/Toronto’
```(or whatever your timezone is)

Then restart the proftpd service and see if it works.
```
sudo service proftpd restart
```

If that doesn't work, I would also edit the **/etc/proftpd.conf** file and add ```
TimesGMT off 
```
to the top of the file.

---

### Post by iconoclast hero on 2011-07-05
Thanks...  One of my friends is using the server now, so once he gets done with this directory I'll have to give this a try.

---

### Post by iconoclast hero on 2011-07-05
Nope...  Tried that and still off by an hour (as if it is on standard time as opposed to DST).

I'm TZ='America/New_York' btw

---

### Post by Toz on 2011-07-05
Then try adding to the beginning of your /etc/proftpd.conf file:
```
TimesGMT off
SetEnv TZ America/New_York
```

Restart proftpd.

---

### Post by iconoclast hero on 2011-07-07
solved.  thank you for the help!

---

