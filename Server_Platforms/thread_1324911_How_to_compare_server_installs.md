---
title: "How to compare server installs"
date: 2009-11-13
forum: Server Platforms
---

### Post by wallcrawler78 on 2009-11-13
I have an issue where an installed software will work on one server but not on the other.


If the two servers OS is installed from the same media, how can i compare the installs?  Is there a tool for comparing and displaying entire file systems?  Perhaps comparing what was loaded as part of the install?  

The two servers were installed by separate people.

I am guessing that it would be one of these methods but, not sure what would be the best way.

1.  File system Compare
2.  Package Manager Compare
3.  Other? (dconf with some type of Dif command perhaps?)

Any suggestions are much appreciated.

---

### Post by Ilalmi on 2009-11-13
I would start with using dpkg to list all installed packages and then diff to compare the results:
```
dpkg -l > somefile
diff somefile1 somefile2
```
After that I would compare the /etc directories of the two servers. You can use diff to do that, too:
```
diff -r dir1 dir2
```

---

