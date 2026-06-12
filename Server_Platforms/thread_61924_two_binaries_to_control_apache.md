---
title: "two binaries to control apache?"
date: 2005-09-02
forum: Server Platforms
---

### Post by omair.majid on 2005-09-02
I just started using apache2 to build a server. What I came across seems pretty wierd. There are, like, 2 files to control apache
/etc/init.d/apche2 and /usr/sbin/apache2ctl
Can someone explain the difference in these two? I can start /stop apache2 using both.

Thanks

---

### Post by heimo on 2005-09-02
/etc/init.d/apache2 is an init script, bash shell script to control starting / stopping Apache (mainly during boot) and apache2ctl is the actual binary to control Apache (apache2 calls apache2ctl).


EDIT: Oh... :) Just to correct myself - apache2ctl is not binary either, it's shell script which calls /usr/sbin/apache2, which is the actual binary. I believe the difference in these two shell scripts is just that init.d is more like distribution / init script and apache2ctl comes with apache. You can use both - apache2ctl is useful to do apache2ctl configtest (tests syntax of configuration).

---

