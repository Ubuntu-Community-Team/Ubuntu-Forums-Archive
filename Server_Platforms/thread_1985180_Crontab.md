---
title: "Crontab"
date: 2012-05-23
forum: Server Platforms
---

### Post by jerim79 on 2012-05-23
I have a simple little script for running unison. /usr/bin/sync.sh:

[INDENT][I]#!/bin/bash
unison -auto -silent /PriStorage ssh://KNTCLFS002//PriStorage[/I][/INDENT]

It works great from the command line:

[INDENT]*sh /usr/bin/sync.sh *
[/INDENT]

I am having issues running this from a cronjob. I have tried adding this line to /etc/cron.d/sync and crontab -e:

*[INDENT]2 * * * * root sh /usr/bin/sync.sh [/INDENT]*

Nothing seems to work. Any help will be greatly appreciated.

---

### Post by LHammonds on 2012-05-23
This is [how I manage my crontab schedule]("http://ubuntuforums.org/showpost.php?p=11953618&postcount=11").

---

### Post by hawkmage on 2012-05-23
9 time out of 10 when you can run a script at a prompt and it fails in cron the issue is caused by the fact that cron has a very basic PATH defined.  Try using the full path to the unison command in your script.

---

### Post by SeijiSensei on 2012-05-23
Also get rid of the .sh extension, as Debian/Ubuntu sometimes will fail to run scripts with that extension, especially if it's in /etc/cron.*.

---

