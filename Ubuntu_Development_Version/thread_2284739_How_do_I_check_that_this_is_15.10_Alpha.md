---
title: "How do I check that this is 15.10 Alpha?"
date: 2015-07-01
forum: Ubuntu Development Version
---

### Post by sam-c on 2015-07-01
How do I check that this is 15.10 Alpha? and not older Beta
Thanks
Uncle Sam:frown:

---

### Post by PaulW2U on 2015-07-01
Hi sam-c, if you're running Ubuntu 15.10 as opposed one of the Ubuntu flavours then you're running the current development version. Ubuntu didn't release an alpha 1 and won't release an alpha 2 or beta 1.

You can find the release schedule at [https://wiki.ubuntu.com/WilyWerewolf/ReleaseSchedule](https://wiki.ubuntu.com/WilyWerewolf/ReleaseSchedule).

In any case an alpha or beta is only a snapshot of development so far on the day that it's released. As soon as you update then you're no longer really running whatever alpha or beta you installed.

---

### Post by grahammechanical on 2015-07-01
Anyway, Alpha comes before Beta. Therefore, Alpha 1 would be older than Beta 2.

With Ubuntu we can download a daily built image. We can do the same with all the other members of the Ubuntu family of distributions as well. It is just that the developers of the other family members like the idea of marking progress with a "milestone" such as Alpha 1; Alpha 2 , and so on.

Regards.

---

### Post by PaulW2U on 2015-07-02
off-topic posts moved to [http://ubuntuforums.org/showthread.php?t=2284972](http://ubuntuforums.org/showthread.php?t=2284972)

---

### Post by craig10x on 2015-07-03
Just curious, but what kernel is 15.10 currently running?

---

### Post by howefield on 2015-07-03
> **sam-c said:**
> How do I check that this is 15.10 Alpha? and not older Beta

```
 cat /etc/lsb-release
```

will confirm if you are on the development release. As long as you've kept up with updates - it doesn't get any fresher. :)

> **craig10x said:**
> Just curious, but what kernel is 15.10 currently running?

3.19.0-22 on this fully updated Wily.

---

### Post by craig10x on 2015-07-03
Thanks, howefield :D
I was curious because i may download a daily build and take a look to see how it is coming along ;)

---

### Post by flocculant on 2015-07-07
I've just been updated from 4.0.0-1 to 4.0.0-4 here. Have had '4' for a while now.

---

