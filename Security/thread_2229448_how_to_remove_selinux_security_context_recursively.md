---
title: "how to remove selinux security context recursively"
date: 2014-06-13
forum: Security
---

### Post by David_Craven on 2014-06-13
```
drwxr-xr-x. 1 david david 236K Sep 13  2013 16498.jpg
```
Ever seen a dot just behind the familiar file permissions and wondered what that means? It means the file has a selinux security context. I personally am not a friend of that and have had a lot of trouble on systems with it. I have searched for a long while and finally found [this]("http://ubuntuforums.org/showthread.php?t=1315684") post, which helped a little. But the code provided over there finds a lot of files that do not actually have a security context and takes a long time. So I updated the line into a little for loop one-liner that worked way better. Just wanted to share it with people who might need it, so here it is:

```
for i in "$(ls -AlRd ${PWD}/* |awk -F '' '$11 == "."' |rev |cut -d' ' -f1 |rev)"; do echo ${i}; setfattr -h -x security.selinux ${i}; done
```

This removes any selinux security contexts on files inside the folder you are in (but not including that folder itself).
I know it is a bad practice to use the output of ls, but I didn't really know how to find affected files in an other way.

---

### Post by coffeecat on 2014-06-13
*Thread moved to **Security Discussions**.*

You posted in the Tutorials section, but this does not meet the [criteria for Tutorials.]("http://ubuntuforums.org/showthread.php?t=2143602")  However, it should be of interest to those who follow discussions in this section, so it is better off here.

---

