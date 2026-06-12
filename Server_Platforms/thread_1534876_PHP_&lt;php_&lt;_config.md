---
title: "PHP &lt;?php &lt;? config"
date: 2010-07-20
forum: Server Platforms
---

### Post by kamaji792 on 2010-07-20
I have an issue with some PHP files.

Some have the PHP code markers <?php ... ?>

But some have <? ... ?>

It looks like my server does not recognise the second.

How do I configure this?  Is it an Apache thing or a PHP thing?

Thanks in advance for any help

---

### Post by kamaji792 on 2010-07-20
OK So as is often the case, having posted a request for information, I have found the answer.

It is in the 'php.ini' file.
```

short_open_tag=On

```

---

