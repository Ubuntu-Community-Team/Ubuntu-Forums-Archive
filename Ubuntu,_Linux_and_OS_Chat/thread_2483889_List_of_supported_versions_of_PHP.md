---
title: "List of supported versions of PHP"
date: 2023-02-12
forum: Ubuntu, Linux and OS Chat
---

### Post by blagoyar on 2023-02-12
How to find out which version of Ubuntu supports the maximum version of PHP?


For example [Debian]("https://wiki.debian.org/PHP#How_PHP_is_packaged_in_Debian")

---

### Post by TheFu on 2023-02-12
You can setup mini-environments to have multiple versions of php on the same system.  So, basically, that means you can have any number of php releases installed.
[https://serverfault.com/questions/153391/running-multiple-versions-of-php-on-ubuntu](https://serverfault.com/questions/153391/running-multiple-versions-of-php-on-ubuntu) has an answer for how to run different php versions for different websites under apache.

As for "supported", there's only 1 per main release at a time. Use "apt search" to get that information.

On 22.04, the supported php is 8.1.x
On 20.04, the supported php is 7.4.x
On 18.04, the supported php is 7.2.x

Use this command to see what's in the repos:
```
$ apt search php |egrep '^php[0-9]'
```

Of course, if you add other repos/PPAs, then other versions can be in the list.  But then "supported by whom" becomes the question.

---

### Post by DuckHook on 2023-02-12
Welcome to the forums, blagoyar

What do you mean by "maximum"? If you mean "the latest" then TheFu has answered you. But if you mean the most users, or the largest installed base, or that which supports the most apps, or something else entirely, then the answer will be different.

---

### Post by blagoyar on 2023-02-13
> **DuckHook said:**
> Welcome to the forums, blagoyar

What do you mean by "maximum"? If you mean "the latest" then TheFu has answered you. But if you mean the most users, or the largest installed base, or that which supports the most apps, or something else entirely, then the answer will be different.

> **TheFu said:**
> 
On 22.04, the supported php is 8.1.x

 Yes, this was interested.That is, the most supported version of PHP in a certain version of the OS.

---

