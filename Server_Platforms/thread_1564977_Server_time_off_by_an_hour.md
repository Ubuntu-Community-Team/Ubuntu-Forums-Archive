---
title: "Server time off by an hour"
date: 2010-08-31
forum: Server Platforms
---

### Post by xkaliburx on 2010-08-31
Recently moved into amazon's ec2 cloud and noticed our server time was in UTC where we use EST.  I did some looking around, and changed using the following;

*ln -sf /usr/share/zoneinfo/EST localtime*

followed up setting the correct time using the date command with the correct time, then *date* showed;
**Tue Aug 31 09:12:59 EST 2010**

Now, that is correct, but if I do an ntpdate pool.time.org or any other time server, the offset is huge and the date moves back one hour.  Is this a daylight settings or something I am just missing?

Thanks

---

### Post by stlsaint on 2010-08-31
Try here: [UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime#Using%20the%20Command%20Line%20(terminal)")

---

### Post by Bachstelze on 2010-08-31
It is generally good practice to have the system time set to UTC, because it does not fluctuate (no leap years or leap seconds).  If a user wants to use another time zone for his account, he can use the TZ environment variable.

---

