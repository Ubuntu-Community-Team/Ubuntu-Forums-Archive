---
title: "Crash after resume, probably wireless related"
date: 2009-06-23
forum: System76 Support
---

### Post by perce on 2009-06-23
Hi Tom,

quite often my wireless doesn't work after resume, and I have to switch it on and off AND remove and inserting the module iwl3945 to make it work again. Yesterday I was doing this usual operation after resuming from hibernation, when my laptop froze. Not even Alt-SysRq-b had any effect, so I turned power off. I attach the logs I took immediately after restart. The 
freezing happened on June 22 around 10:59.


Thanks.

---

### Post by Idefix82 on 2009-06-23
It's not very pretty but there is a workaround for such issues, namely to tell the system to stop the misbehaving module _before_ suspending and to load it again after resuming. To do that, create a text file named for example 'config' in /etc/pm/config.d/ and add the line
```
SUSPEND_MODULES="iwl3945"
```
to it. Now try suspending and resuming and see if your wireless card works.

---

### Post by thomasaaron on 2009-06-23
The freeze does look like it happened as you were removing/replacing the module.

The above fix is also definitely the place to start.

---

### Post by perce on 2009-06-23
Thank you to both.

 Will this work for both suspend and hibernate?

---

### Post by Idefix82 on 2009-06-23
> **perce said:**
> Thank you to both.

 Will this work for both suspend and hibernate?

I think it should work for suspend and hibernate but why don't you just try it out and let us know?

---

### Post by perce on 2009-06-25
So far so good, my wireless has never worked so well since we switched to the free driver. I hope it will last.

Thank you very much for your fix, Idefix82

---

### Post by Idefix82 on 2009-06-29
You are very welcome!

---

