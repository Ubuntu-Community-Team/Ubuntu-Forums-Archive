---
title: "Php Mysql Connection problems - blank page no error messages"
date: 2010-06-14
forum: Server Platforms
---

### Post by mattgaunt on 2010-06-14
Heya everyone,

I'm having a few issues with my LAMP setup.

I've never had a problem before, I installed LAMP using Taskel but when I call a page with:

```
<h1>Testing</h1>

<?php

echo '<h1>Newsletter archive</h1>';
echo '<p>Below is a list of previous newsletters sent to subscribers</p>'

$con = mysql_connect("localhost","root", "Password") or die(mysql_error());
```

The browser just displays a blank page (Chrome and Firefox).

If I remove the mysql_connect call everything works ok. phpinfo has a large amount of information about Mysql so it appears as though it knows MySql is there, but just can't communicate with it, any ideas?

Cheers,
Matt

EDIT: Stupid coding typo

---

