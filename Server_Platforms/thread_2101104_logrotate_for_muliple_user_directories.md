---
title: "logrotate for muliple user directories"
date: 2013-01-03
forum: Server Platforms
---

### Post by usaims on 2013-01-03
Hi ):P,

I'm using logrotate to rotate apache logs for a web hosting company. When the user log rotates, the rotated log does not retain the permission of that file. I have thousands of home directories, each directory owned by the unique user. I want the users to access there rotated log but they can't because it's own by root. Below is my logrotate file:

/home/*/Sites/*/logs/*.log {
    size 5M
    rotate 4
    missingok
    notifempty
    copytruncate
    dateext
    compress
}

Any help would be greatly appreciated:D

---

### Post by volkswagner on 2013-01-03
> **usaims said:**
> Hi ):P,

I'm using logrotate to rotate apache logs for a web hosting company. When the user log rotates, the rotated log does not retain the permission of that file. I have thousands of home directories, each directory owned by the unique user. I want the users to access there rotated log but they can't because it's own by root. Below is my logrotate file:

/home/*/Sites/*/logs/*.log {
    size 5M
    rotate 4
    missingok
    notifempty
    copytruncate
    dateext
    compress
}

Any help would be greatly appreciated:D

I have only one user and have added the following to my lograte file.

```
create 640 username www-data
```

I'm not sure if you can sript the username entry or use a wildcard.

Hope this gets the ball rolling.

---

