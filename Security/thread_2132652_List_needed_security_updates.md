---
title: "List needed security updates"
date: 2013-04-05
forum: Security
---

### Post by flickerfly on 2013-04-05
I used to be able to run this command to get updates to tell customers why they should pay me more money to help secure their servers on a regular basis.
```
$ sudo apt-get upgrade -s| grep ^Inst |grep Security
```
Sure it's a bit hacky, but it does the trick and I can quickly count them by piping it to wc -l.

The problem is security updates are no longer specified as far as I can tell in that list or even by a specific repository so I can't just grep that list anymore. It looks like the repositories were merged. (Is that documented somewhere so I can read up on it?)

How do I list the security updates needed on ubuntu server 12.04?

Note: I'd like to accomplish this without making changes to the file system so setting up a separate sources.list in /etc somewhere is undesirable.

---

### Post by flickerfly on 2013-04-05
sarnold and rbasak in #ubuntu-server helped me come up with this solution. I'd rather not create a file, but one it /tmp is almost like not creating it anyway. The data in the file isn't important and won't impact system activity in any way so I'm okay with it.

```
grep security /etc/apt/sources.list > /tmp/security.list
sudo apt-get upgrade -oDir::Etc::Sourcelist=/tmp/security.list -s
```

---

