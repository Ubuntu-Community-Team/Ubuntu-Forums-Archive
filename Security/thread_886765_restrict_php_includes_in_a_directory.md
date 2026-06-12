---
title: "restrict php includes in a directory"
date: 2008-08-11
forum: Security
---

### Post by ethanlifka on 2008-08-11
I am trying to restrict php files from being included on a directory.  I have a tmp directory and I don't want scripts to run inside of it.  I can get to that part fine, but I am still able to include that file and it runs fine.

here is my structure

tmp/phpinfo.php
test.php

  -contents of test.php
   <?php
    include('tmp/phpinfo.php');
   ?>

I would like it to fail or 403 error or something, but still allow for move_uploaded_file from tmp to another directory.

Any help would be great.

---

