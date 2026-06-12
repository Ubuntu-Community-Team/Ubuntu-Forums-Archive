---
title: "Issues with apache and custom Gitlab-CE.conf"
date: 2018-09-22
forum: Server Platforms
---

### Post by warmango on 2018-09-22
So here is my issue
I am following this guide [https://www.cheonghyun.com/installing-gitlab-on-existing-apache-server-for-ubuntu/](https://www.cheonghyun.com/installing-gitlab-on-existing-apache-server-for-ubuntu/), 
But I am stuck at the very end of step 3, and here is terminal output that should be relevean


journal -xe ```

-- Unit apache2.service has begun starting up.
Sep 22 16:31:34 codemerith apachectl[18275]: apache2: Syntax error on line 225 of /etc/apache2/apache2.conf: Syntax error on line 1 of /e
Sep 22 16:31:34 codemerith apachectl[18275]: Action 'start' failed.
Sep 22 16:31:34 codemerith apachectl[18275]: The Apache error log may have more information.
Sep 22 16:31:34 codemerith systemd[1]: apache2.service: Control process exited, code=exited status=1
Sep 22 16:31:34 codemerith systemd[1]: apache2.service: Failed with result 'exit-code'.
Sep 22 16:31:34 codemerith systemd[1]: Failed to start The Apache HTTP Server.
-- Subject: Unit apache2.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
--
-- Unit apache2.service has failed.
--
-- The result is RESULT.
```

Config files
```
/etc/apache2/sites-enabled/gitlab.conf > http://paste.ubuntu.com/p/3mHyr2hkmv/
/etc/apache2/apache2.conf > http://paste.ubuntu.com/p/ZQpnZRbVQP/
```

---

