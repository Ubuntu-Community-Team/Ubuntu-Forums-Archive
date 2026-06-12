---
title: "Faillog is empty? Is that a problem?"
date: 2010-10-01
forum: Security
---

### Post by p.s. on 2010-10-01
When I use```
 tail faillog 
```to look at my failed login attempts it shows nothing, just an empty file.

Is that weird, or is that normal? I changed my login password recently and I'm pretty sure I typed the old one and got denied at least once or twice out of habit over the last week or two. Wouldn't that show up in the log?


Also, I just tried to use ```
 tail faillog 
``` again, and it just jumps back to the prompt but instead of looking normal:

pat@leibniz:/var/log$ tail faillog 


it displays like this:

tty1&#65533;H&#65533;Lpat@leibniz:/var/log$ 


Anyone have any ideas?

---

### Post by cariboo on 2010-10-01
You can't read fail log directly. type:

```
faillog -a
``` 

My faillog, just turned over, so all enties are at zero.

For more info on the faillog command type:

```
man faillog
```

---

### Post by p.s. on 2010-10-03
Great, thanks!

---

