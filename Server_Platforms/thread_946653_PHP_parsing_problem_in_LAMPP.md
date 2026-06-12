---
title: "PHP parsing problem in LAMPP"
date: 2008-10-13
forum: Server Platforms
---

### Post by Epifrin on 2008-10-13
The \n and \t tags that are used to indicate a new line and a tab insertion are not parsed correctly on my local server. Any ideas? Thanks in advance.

---

### Post by lykwydchykyn on 2008-10-13
Can you give an example of some code where it's not working right?

---

### Post by Epifrin on 2008-10-13
> **lykwydchykyn said:**
> Can you give an example of some code where it's not working right?

<?php

       echo "hello world! \nHello again!";

?>

It displays the above string on one line instead of two.

---

### Post by lykwydchykyn on 2008-10-13
This is correct behavior.  If you look at the source for the page, you'll see that there is a new line there.  But when the HTML is rendered, the newline is ignored. 

Make a simple .html file like this:
```

This
is
a 
test

```

You'll find that when that is opened in a browser, all the words are on one line.  

If you want a line break, you'll need to use html tags, like <br> or <p>.

---

