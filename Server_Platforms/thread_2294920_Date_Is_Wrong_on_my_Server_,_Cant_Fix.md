---
title: "Date Is Wrong on my Server , Cant Fix"
date: 2015-09-14
forum: Server Platforms
---

### Post by slamanna212 on 2015-09-14
My Server is running Ubuntu Server 14.04.3. Its a dedicated server rented from a Host in NC

Its showing UTC time as EST, my time. I have installed NTP and even manually forced a sync but its showing UTC as my time

Example: My time zone is US Eastern, current time is 12:01PM , thats what its showing for UTC time

What can i do to fix this?

EDIT: I didnt give ntd time to sync, its fine now

---

### Post by darkod on 2015-09-14
The way I understand it, ntp is more if you want that server to serve time to other machines in the network. I have seen plenty of virtual servers with correct time and never needed to install ntp on them.

The timezone can be decided sometimes automatically included in the image used to deploy the server, or the location, etc. If sometimes you want to change the timezone, do:
```
sudo dpkg-reconfigure tzdata
```

That is the package for timezones. In general the time should be correct regardless whether you have ntp.

---

