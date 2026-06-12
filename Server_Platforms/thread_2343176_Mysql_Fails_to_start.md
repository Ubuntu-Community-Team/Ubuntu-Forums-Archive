---
title: "Mysql Fails to start"
date: 2016-11-14
forum: Server Platforms
---

### Post by malwin1234 on 2016-11-14
Hey, my mysql service wont start.

On running mysql.service these issues are shown:


-- Subject: Unit mysql.service has failed
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit mysql.service has failed.
--
-- The result is failed.
Nov 14 04:45:02 abyss systemd[1]: mysql.service: Unit entered failed state.
Nov 14 04:45:02 abyss systemd[1]: mysql.service: Failed with result 'exit-code'.
Nov 14 04:45:02 abyss sudo[11661]: pam_unix(sudo:session): session closed for user root
Nov 14 04:45:02 abyss systemd[1]: mysql.service: Service hold-off time over, scheduling restart.
Nov 14 04:45:02 abyss systemd[1]: Stopped MySQL Community Server.
-- Subject: Unit mysql.service has finished shutting down
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit mysql.service has finished shutting down.
Nov 14 04:45:02 abyss systemd[1]: Starting MySQL Community Server...
-- Subject: Unit mysql.service has begun start-up
-- Defined-By: systemd
-- Support: [http://lists.freedesktop.org/mailman/listinfo/systemd-devel](http://lists.freedesktop.org/mailman/listinfo/systemd-devel)
--
-- Unit mysql.service has begun starting up.
Nov 14 04:45:05 abyss systemd[1]: mysql.service: Main process exited, code=exited, status=1/FAILURE

pls help me

---

