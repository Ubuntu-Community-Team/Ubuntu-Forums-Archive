---
title: "Did You try (U)KSM?"
date: 2018-10-25
forum: Ubuntu Development Version
---

### Post by zika on 2018-10-25
```
[COLOR=#000000][FONT=&amp]/bin/echo "1" | /usr/bin/sudo /usr/bin/tee /sys/kernel/mm/ksm/run[/FONT][/COLOR]
```(Not new but usefull.. ;))

---

### Post by dino99 on 2018-10-25
Can you share your experience with these unknown (yet) tools (ksm & cake)? And what  they are for .

---

### Post by #&amp;thj^% on 2018-10-25
> **zika said:**
> ```
[COLOR=#000000][FONT=&amp]/bin/echo "1" | /usr/bin/sudo /usr/bin/tee /sys/kernel/mm/ksm/run[/FONT][/COLOR]
```(Not new but usefull.. ;))
+1 :)
```
/bin/echo "1" | /usr/bin/sudo /usr/bin/tee /sys/kernel/mm/ksm/run
[sudo] password for me: 
1


```

---

### Post by #&amp;thj^% on 2018-10-25
> **dino99 said:**
> Can you share your experience with these unknown (yet) tools (ksm & cake)? And what  they are for .

Not real sure with cake, >>but this: Kernel Samepage Merging (KSM) allows de-depulication of memory in Linux.
Example:
```
ls -1  /sys/kernel/mm/ksm/
full_scans
max_page_sharing
merge_across_nodes
pages_shared
pages_sharing
pages_to_scan
pages_unshared
pages_volatile
run
sleep_millisecs
stable_node_chains
stable_node_chains_prune_millisecs
stable_node_dups
use_zero_pages

```

---

### Post by zika on 2018-10-26
> **dino99 said:**
> Can you share your experience with these unknown (yet) tools (ksm & cake)? And what  they are for .Added info in thread about CAKE. UKMS is an „old“ thing just reminding...

---

