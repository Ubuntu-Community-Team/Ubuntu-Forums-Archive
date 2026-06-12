---
title: "cURL Error Number 22: The requested URL returned error: 404"
date: 2011-10-28
forum: Server Platforms
---

### Post by tsubakaran on 2011-10-28
I run LAMP server in Ubuntu Server, I tied to do auto post using Robo3 - plugins and get error

cURL Error Number 22: The requested URL returned error: 404

Can anybody help to resolve this issue?

---

### Post by tsubakaran on 2011-10-28
I tested with simple php code by creating a test php file, test.php

<?php phpinfo() ?>, 

I got the details;

cURL support	enabled
cURL Information	7.21.3
Age	3
etc.

I could not understand some parts how this error comes???:confused:

---

### Post by vasile002 on 2011-10-29
the 404 error you got means that whatever file you are trying to get using curl it can't find it.

---

### Post by tsubakaran on 2011-10-29
yes, I understood, thanks for your response.

---

