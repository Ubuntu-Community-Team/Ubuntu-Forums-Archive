---
title: "Force System Information to be Displayed"
date: 2012-06-09
forum: Server Platforms
---

### Post by mortrca on 2012-06-09
When logging into my 12.04 x64 server I get:
"System information disabled due to load higher than 2.0"
Rather than the system information that is typically displayed on login. Is it possible to force the information to be displayed on login regardless of the server load?

---

### Post by CharlesA on 2012-06-09
Type:

landscape-sysinfo

---

### Post by mortrca on 2012-06-09
Is it possible to do this automatically on login?

---

### Post by CharlesA on 2012-06-09
> **mortrca said:**
> Is it possible to do this automatically on login?
Not sure. I wasn't able to find much info about that program.

---

### Post by Doug S on 2012-06-09
I think you could edit /usr/share/landscape/landscape-sysinfo.wrapper to do what you want. Perhaps save the original file first, in case you want, or need, to restore it later.

---

### Post by volkswagner on 2012-06-09
> **Doug S said:**
> I think you could edit /usr/share/landscape/landscape-sysinfo.wrapper to do what you want. Perhaps save the original file first, in case you want, or need, to restore it later.

You can likely just add a sleep timer to give the system time to load services, hence allowing CPU cycles to drop.

add:

```
sleep 3
```

Start with 3 seconds to see if that is enough time.

---

### Post by mortrca on 2012-06-09
> **Doug S said:**
> I think you could edit /usr/share/landscape/landscape-sysinfo.wrapper to do what you want. Perhaps save the original file first, in case you want, or need, to restore it later.

Thank you, after making some changes to landscape-sysinfo.wrapper I am getting the desired behaviour.

---

### Post by CharlesA on 2012-06-09
> **mortrca said:**
> Thank you, after making some changes to landscape-sysinfo.wrapper I am getting the desired behaviour.
What changes did you make?

---

### Post by mortrca on 2012-06-09
> **volkswagner said:**
> You can likely just add a sleep timer to give the system time to load services, hence allowing CPU cycles to drop.

add:

```
sleep 3
```Start with 3 seconds to see if that is enough time.

With the programs that I run on the server, the system load doesn't drop below 2.0. However, if the circumstances were different, I would have taken your suggestion.

---

### Post by mortrca on 2012-06-09
> **CharlesA said:**
> What changes did you make?

I removed the if/else structure so the landscape-sysinfo command would be run without first checking the system load.

---

### Post by CharlesA on 2012-06-09
> **mortrca said:**
> I removed the if/else structure so the landscape-sysinfo command would be run without first checking the system load.
Cool. Thanks!

---

### Post by panosssvent19 on 2013-01-04
Can you post the original and the new file configuration????

Have a nice year!!!!!!

---

