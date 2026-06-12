---
title: "How to switch time to DST"
date: 2011-11-09
forum: Server Platforms
---

### Post by Z.K. on 2011-11-09
My Ubuntu text only server did not lose an hour that way it should.  How do I setup Daylight Savings Time on my Ubuntu 10.04 server.

---

### Post by papibe on 2011-11-09
Is your server updated frequently?

Do you have the package tzdata installed? You can check it like this:
```
apt-cache policy tzdata
```
The result should be something like this:
```
tzdata:
  Installed: 2011n-0ubuntu0.10.04
  Candidate: 2011n-0ubuntu0.10.04
  Version table:
 *** 2011n-0ubuntu0.10.04 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Packages
        100 /var/lib/dpkg/status
     2010i-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ lucid/main Packages

```
If it's not installed, do as follows:
```
sudo apt-get update
sudo apt-get install tzdata
```
Hope it helps. Tell us how it goes.
Regards.

---

### Post by Jonathan L on 2011-11-10
> **Z.K. said:**
> My Ubuntu text only server did not lose an hour that way it should.  How do I setup Daylight Savings Time on my Ubuntu 10.04 server.

Hi ZK

It's also possible you have all the software but it's not configured for the right timezone.

The default timezone for your server is controlled by the file /etc/timezone, which is a one-line text file containing the name of the timezone.  For example:
```
Europe/London
```The timezones available on your computer are the files in /usr/share/zoneinfo

Just in case you're unaware: in Unix the clock is simply a count of seconds since the beginning of 1970.  We only use the timezone information to convert it to human form and print it out, we never actually change the clocks unless they're wrong.  It is also possible for individual processes to change their own timezones with the environment variable TZ.

Hope that helps.

Kind regards,
Jonathan.

---

