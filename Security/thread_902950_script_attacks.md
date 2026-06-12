---
title: "script attacks"
date: 2008-08-27
forum: Security
---

### Post by ub007 on 2008-08-27
Hi,


When i search for a post/thread on this web site immediately after my first query,the site asks me to wait for a few seconds before performing a new search.I assume this feature is to minimize the potency of a script attack.
Could anyone share their ideas on how such a mechanism to induce a delay can be implemented?
I'm trying to develop a security system to protect against HTTP script attacks.

Thanks in adavnce
Cheers
David

---

### Post by cdenley on 2008-08-28
> **ub007 said:**
> Hi,


When i search for a post/thread on this web site immediately after my first query,the site asks me to wait for a few seconds before performing a new search.I assume this feature is to minimize the potency of a script attack.
Could anyone share their ideas on how such a mechanism to induce a delay can be implemented?
I'm trying to develop a security system to protect against HTTP script attacks.

Thanks in adavnce
Cheers
David

Something like this?
[PHP]
<?php
session_start();
$last=$_SESSION['last'];
$time=time();
if($time-$last<30)
    print "You must wait another ".(30-($time-$last))." seconds";
else {
    print "success";
    $_SESSION['last']=$time;
}
?>
[/PHP]

---

