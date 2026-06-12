---
title: "Where are user mimetype associations saved?"
date: 2016-02-25
forum: Ubuntu Development Version
---

### Post by mc4man on 2016-02-25
In the past any changes from default where written to .local/share/applications/mimeapps.list
That no longer seems the case, anyone know where this is now stored?

---

### Post by mc4man on 2016-02-25
Found - .config/mimeapps.list

---

### Post by Bashing-om on 2016-02-25
mc4man; Hey,

As I live and learn ... looks like the location may also depend on the DE.

Here 14.04 with xfce4:
```

sysop@1404mini:~$ ls -al .config/mimeapps.list
ls: cannot access .config/mimeapps.list: No such file or directory

sysop@1404mini:~$ ls -al .local/share/applications/mimeapps.list
-rw-rw-r-- 1 sysop sysop 1135 Oct 20 19:09 .local/share/applications/mimeapps.list
sysop@1404mini:~$

```

Moved I guess in 16.04 .
 
[INDENT][INDENT]one thing I rest assured of
[INDENT][INDENT][INDENT]most of the time I do not know enough
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mc4man on 2016-02-25
It would appear that at least one app continues to use the .local/share/applications location though it is worthless. Seen here with google-chrome.
So if one sets g-c as default on a file (html,xml, ect.) or sets g-c as default in *it's dialog *the settings are saved to .local.... & of no effect.
Ex. after doing so in g-c - 
> $ cat .local/share/applications/mimeapps.list 

[Default Applications]
text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop


---

### Post by vasa1 on 2016-02-25
[https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.html](https://specifications.freedesktop.org/mime-apps-spec/mime-apps-spec-1.0.html) has this:> File name and location

Users, system administrators, application vendors et distributions can change associations between applications and mimetypes by writing into a file called mimeapps.list.

The lookup order for this file is as follows:
```
$XDG_CONFIG_HOME/$desktop-mimeapps.list	user overrides, desktop-specific (for advanced users)
$XDG_CONFIG_HOME/mimeapps.list	user overrides (recommended location for user configuration GUIs)
$XDG_CONFIG_DIRS/$desktop-mimeapps.list	sysadmin and ISV overrides, desktop-specific
$XDG_CONFIG_DIRS/mimeapps.list	sysadmin and ISV overrides
$XDG_DATA_HOME/applications/$desktop-mimeapps.list	for completeness, deprecated, desktop-specific
$XDG_DATA_HOME/applications/mimeapps.list	for compatibility, deprecated
$XDG_DATA_DIRS/applications/$desktop-mimeapps.list	distribution-provided defaults, desktop-specific
$XDG_DATA_DIRS/applications/mimeapps.list	distribution-provided defaults
```




---

