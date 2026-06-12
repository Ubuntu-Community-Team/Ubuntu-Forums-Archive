---
title: "output of tail via php is losing colours and displaying [31:"
date: 2012-11-20
forum: Server Platforms
---

### Post by SlugSlug on 2012-11-20
Hi am trying to display the output of a log via apache


```
<?php echo shell_exec('tail -10 /path/log/file.log'); ?>
```now in bash this displays colours but via web I get the text vi shows which is kind of like colour codes..
eg

```
[36;1
```

---

### Post by pkadeel on 2012-11-20
because a web page needs html tags or css to do the coloring

---

### Post by SlugSlug on 2012-11-20
It looks like I need some form of ansi output for php. 

Does anyone know of this?

---

