---
title: "cron manager app?"
date: 2005-11-01
forum: Server Platforms
---

### Post by wrynn on 2005-11-01
does anyone know of an app that can watch all my cron jobs and if one of them fails it will report the error and maybe attempt to restart it? thanks.

---

### Post by wylfing on 2005-11-01
Doesn't cron mail you about all its actions anyway?

I think you can get cron to mail you only about problems by appending [FONT="Courier New"][COLOR="DimGray"]>/dev/null[/COLOR][/FONT] at the end of your commands (instead of the common [FONT="Courier New"][COLOR="DimGray"]>/dev/null 2>&1[/COLOR][/FONT]).

---

