---
title: "locales in server"
date: 2006-06-11
forum: Server Platforms
---

### Post by denni on 2006-06-11
- the system is amd64 dapper server
 - the problem is to get Icelandic keyboard to work properly, all the Icelandic special letters are missing.  Have been doing ```
dpkg-reconfigure locales, dpkg-reconfigure localeconf, dpkg-reconfigure localepurge and dpkg-reconfigure console-data
```
- here is the /etc/enviroment
> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="is_IS.UTF-8"
LANGUAGE="is_IS:is:en_GB:en"
### BEGIN DEBCONF SECTION FOR localeconf
# Do not edit within this region if you want your changes to be preserved
# by debconf.  Instead, make changes before the "### BEGIN DEBCONF SECTION
# FOR localeconf" line, and/or after the "### END DEBCONF SECTION FOR
# localeconf" line.
LANG=is_IS.UTF-8
### END DEBCONF SECTION FOR localeconf

language-pack-is is installed, did chose Icelandic, when installing.

any ideas ????

---

