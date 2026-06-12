---
title: "display cpu model in conky"
date: 2011-07-16
forum: The Cafe
---

### Post by sectshun8 on 2011-07-16
Been messing around quite a bit with my conky this morning but am having an issue regarding the CPU.

I'm running an Intel Atom N270 CPU... well when i use this line in conky:
```
${execi 1000 cat /proc/cpuinfo | grep 'model name' | cut -c 13-40}
```

It works sure, but it shows it twice. In conky, so it says:

Intel(TM) Atom(TM) CPU N270
Intel(TM) Atom(TM) CPU N270

I do notice there is a CPU 0 and a CPU 1... but how can I adjust the above code so that the processor model is only displayed once?

---

### Post by mips on 2011-07-16
Try

```
${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'| uniq}
```


or

```
${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'| uniq | cut -c 1-26}
```

to cut off the clock speed.

---

### Post by Bandit on 2011-07-16
Easiest way is to just manually put it in conky like text or if you really want to display it without pulling multiple lines out is just use concatenate to number the lines then just pull that one line our and adjust your character selection to get what you need. Like this for me.

```
cat -n /proc/cpuinfo | grep '57' | cut -c 20-40

```

Edit:  MIPS has the correct way just posted.. I have the incorrect lazy way.. :D

---

### Post by sectshun8 on 2011-07-16
Thanks to both of you... both ways work. :)

---

### Post by Bandit on 2011-07-16
> **sectshun8 said:**
> Thanks to both of you... both ways work. :)

Not a problem :)
I forgot all about using uniq to keep from having multiple lines of the same info displaying. Havent had my morning coffee yet.. hehe

cat /proc/cpuinfo | grep 'model name' | cut -c 14-42 | uniq

---

