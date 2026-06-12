---
title: "lxc list output format"
date: 2016-08-17
forum: Virtualisation
---

### Post by votsalo on 2016-08-17
I wish that the output of "lxc list" and similar commands would not have the dash-lines between rows and columns:
```
+--------+---------+---------------------+------+------------+-----------+
|  NAME  |  STATE  |        IPV4         | IPV6 |    TYPE    | SNAPSHOTS |
+--------+---------+---------------------+------+------------+-----------+
| apa    | RUNNING | 10.187.79.25 (eth0) |      | PERSISTENT | 0         |
+--------+---------+---------------------+------+------------+-----------+
| flow   | RUNNING | 10.187.79.28 (eth0) |      | PERSISTENT | 0         |
+--------+---------+---------------------+------+------------+-----------+
```

They make the output take up more rows and more columns than it otherwise would.
Other linux programs don't use this format: df, ps, zfs list, ...
I imagine that the reason for the lines is to separate the rows better when they wrap, but I don't find it very usable when the lines wrap.  I make my terminal wide and I also customize the command so it shows fewer columns.  For the default 6-column output, the extra lines take up an extra 14 characters per row.
I wish there were an option to disable the row/column separators.

---

### Post by votsalo on 2016-08-31
This is also a problem for scripts.  Let's say I want to write a script  that does something with each container (e.g. backup the container).
To get the names of the containers, I have to do something like:
> lxc list -c n | grep -v -- -- | sed 's/|//g' | tail -n +2

Also, it would be nice to have an option to list only the running containers.

---

