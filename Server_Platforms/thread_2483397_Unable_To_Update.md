---
title: "Unable To Update"
date: 2023-01-29
forum: Server Platforms
---

### Post by hezy2 on 2023-01-29
Hi,
cannot update the system. Screenshot added. Thank you

---

### Post by oldfred on 2023-01-29
I cannot read that screen and I do not think others will.
Better to post terminal output in code tags. And only post part containing error messages.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

What did you do before, update, add ppa, manually edit sources or something else?

---

### Post by MAFoElffen on 2023-01-29
Network connection problem. No route reach...

Try this and post the results
```

traceroute il.archive.ubuntu.com
pnig -c 4 www.google.com
ping -c 4 8.8.8.8


```

---

### Post by hezy2 on 2023-01-29
Hi,
in addition to your reply see screenshot. Thanks,
Hrzy

---

### Post by MAFoElffen on 2023-01-30
You have ICMP and DNS resolation...  You have a direct route to it...

I don't see the problem.

Can you try to update again? Maybe the repo was temporarily down... You can see it now.

---

### Post by hezy2 on 2023-01-31
Hi,
same errors. Can it be because of webmin installation?

---

### Post by MAFoElffen on 2023-01-31
Webmin uses a firewall (usually)... But  you were able to do a traceroute to, so no. I think not. Can you ping to il.archive.ubuntu.com?

---

### Post by hezy2 on 2023-02-01
Yes.  It's actually updating now. Hope there will not be problems.  Thanks a lot for the help

---

