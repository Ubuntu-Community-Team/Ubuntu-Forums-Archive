---
title: "BASE 1.4.5 patch"
date: 2012-02-21
forum: Security
---

### Post by emiller12345 on 2012-02-21
This is a correction to the BASE package to (hopefully) eliminate the SQL injection vulnerability found on Jan 30, 2012

```
--- base-1.4.5/includes/base_state_common.inc.php.orig    2012-02-08 19:12:28.394256059 -0500
+++ base-1.4.5/includes/base_state_common.inc.php    2012-02-08 20:49:03.134256723 -0500
@@ -126,6 +126,8 @@
    /* Check the exception value list first */
    if ( $exception != "" && in_array($item, $exception) )
       return $item;
+   elseif ( $exception != "" )
+      return "";
 
    if ( $valid_data == "" )
       return $item;

```Any comments welcome

---

