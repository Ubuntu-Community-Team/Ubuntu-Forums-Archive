---
title: "mysql_safe 98% CPU usage + huge memory use"
date: 2008-05-19
forum: Server Platforms
---

### Post by Mr.Carramba on 2008-05-19
hi!
I have bad problem, myqsl_safe process eat all cpu power! it bounces from 96-99% even if I'm shore there are no activities right now. and memory usage is 127800 kB!

What is wrong with it? and how can I fix this?

---

### Post by hyper_ch on 2008-05-19
stop mysql and restart it
```

sudo /etc/init.d/mysql restart

```

---

### Post by Mr.Carramba on 2008-05-19
> **hyper_ch said:**
> stop mysql and restart it
```

sudo /etc/init.d/mysql restart

```

but wouldn't this only solve the problem temporarily?
I would like to find out what is the reason for this high cpu usage

---

### Post by hyper_ch on 2008-05-19
it might be a hiccup and the restart of the serve might solve it...

---

### Post by Mr.Carramba on 2008-05-19
> **hyper_ch said:**
> it might be a **hiccup **and the restart of the serve might solve it...

what do you mean **hiccup** ? how can it be prevented from the future? it would be impossible to monitor server in real time

btw. restart solved problem, but  I didn't start mysql as recommended thought mysqld_safe

---

