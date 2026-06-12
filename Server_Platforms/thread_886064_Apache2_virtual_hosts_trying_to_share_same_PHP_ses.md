---
title: "Apache2 virtual hosts trying to share same PHP sessions"
date: 2008-08-10
forum: Server Platforms
---

### Post by KrisWillis on 2008-08-10
We have a dedicated server managed by our hosting company which was recently migrated from a FreeBSD/PHP4/MySQL4 box to an Ubuntu/PHP5/MySQL5 box.

It appears that all of the accounts on the new server, assumed to be created as virtual hosts, are all trying to share the same PHP session files. For example, I have created a basic script as follows:

```
<?php
session_start();
$_SESSION['test'] = "test";
echo $_SESSION['test'];
?>
```

Now, the first virtual host I execute the script on returns 'test' as it should, but each subsequent execution on a different virtual host returns an error like so:

> Warning: session_start() [function.session-start]: open(/tmp/sess_3373fb7c1f4650a35d7f417419bbfd6b, O_RDWR) failed: Permission denied (13) in /home/f/o/foo/public_html/test.php on line 2

Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /home/f/o/foo/public_html/test.php:2) in /home/f/o/foo/public_html/test.php on line 2

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /home/f/o/foo/public_html/test.php:2) in /home/f/o/foo/public_html/test.php on line 2

Obviously the path to test.php is different on each virtual host, but the path to the session file (/tmp/sess_3373fb7c1f4650a35d7f417419bbfd6b) is the same.

Running ls -la /tmp points out that /tmp/sess_3373fb7c1f4650a35d7f417419bbfd6b has a uid that belongs to the first virtual host that executed the script.

My hosting company can't find anything wrong, and are telling me that my scripts are trying to access sessions created by other accounts, but my test script is just trying to create a session, not pick up a session previously created by another account, as you can see above.

Does anyone have any ideas of what I could suggest to my hosting company, or where I might be looking to solve this problem?

Many thanks.

---

