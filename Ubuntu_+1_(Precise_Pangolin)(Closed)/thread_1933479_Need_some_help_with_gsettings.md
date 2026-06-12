---
title: "Need some help with gsettings"
date: 2012-02-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by kansasnoob on 2012-02-29
Removing the user-name from indicator-session has changed in Precise. I found it in dconf-editor but I'm havng no luck parsing a CLI option:

[ATTACH]213485[/ATTACH]

But if I run those commands I just get:

```
lance@lance-desktop:~$ gsettings set apps.indicator-session show-real-name-on-panel false
No such schema 'apps.indicator-session'

```

I'm sure it's just a syntax error but I'm stumped :)

---

### Post by Yellow Pasque on 2012-02-29
Use dconf?
```
dconf write /apps/indicator-session/ false
```

---

### Post by kansasnoob on 2012-02-29
> **Temüjin said:**
> Use dconf?
```
dconf write /apps/indicator-session/ false
```

Apperently not:

```
lance@lance-desktop:~$ dconf write /apps/indicator-session/ true

GLib-WARNING **: (/build/buildd/glib2.0-2.31.18/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)
error: dconf key must not end with a slash

Usage:
  dconf write KEY VALUE

Write a new value to a key

Arguments:
  KEY       A key path (starting, but not ending with '/')
  VALUE     The value to write (in GVariant format)

lance@lance-desktop:~$ dconf write /apps/indicator-session/ false

GLib-WARNING **: (/build/buildd/glib2.0-2.31.18/./glib/gerror.c:390):g_error_new_valist: runtime check failed: (domain != 0)
error: dconf key must not end with a slash

Usage:
  dconf write KEY VALUE

Write a new value to a key

Arguments:
  KEY       A key path (starting, but not ending with '/')
  VALUE     The value to write (in GVariant format)

```

---

### Post by mc4man on 2012-02-29
```
gsettings set com.canonical.indicator.session show-real-name-on-panel false

```

You can always get the schema directly from dconf-editor or gsettings list-schemas 
(could add a |grep if desired

---

### Post by Yellow Pasque on 2012-02-29
Sorry, try:
```
dconf write /apps/indicator-session false
```

---

### Post by kansasnoob on 2012-02-29
> **mc4man said:**
> ```
gsettings set com.canonical.indicator.session show-real-name-on-panel false

```

You can always get the schema directly from dconf-editor or gsettings list-schemas 
(could add a |grep if desired

I think that's how it was in Oneiric but no more:

[ATTACH]213499[/ATTACH]

---

### Post by kansasnoob on 2012-02-29
> **Temüjin said:**
> Sorry, try:
```
dconf write /apps/indicator-session false
```

Clearly NOT because you're leaving out a big part of the <path> :)

---

### Post by mc4man on 2012-02-29
> **kansasnoob said:**
> I think that's how it was in Oneiric but no more:

[ATTACH]213499[/ATTACH]

I assure you the command is valid & the setting(s) are there.
You are looking in the wrong place in dconf-editor - it's under "apps" (apps > indicator-session

 gsettings list-schemas |grep indicator

gsettings list-recursively |grep indicator.session

or

gsettings list-recursively com.canonical.indicator.session

---

### Post by kansasnoob on 2012-02-29
> **mc4man said:**
> I assure you the command is valid & the setting(s) are there.
You are looking in the wrong place in dconf-editor - it's under "apps" (apps > indicator-session

 gsettings list-schemas |grep indicator

gsettings list-recursively |grep indicator.session

or

gsettings list-recursively com.canonical.indicator.session

OK, it works. But compare the before and after, before being in my OP and now:

[ATTACH]213502[/ATTACH]

I'd consider that a bug. I'll study a bit and decide what to do :D

---

### Post by mc4man on 2012-02-29
Please highlight "indicator-session" in the "apps" dropdown

---

### Post by kansasnoob on 2012-02-29
Bug report filed:

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/943532](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/943532)

I hope I did OK :)

---

### Post by kansasnoob on 2012-02-29
> **mc4man said:**
> Please highlight "indicator-session" in the "apps" dropdown

It is highlighted :confused:

See my next post, I goofed.

---

### Post by kansasnoob on 2012-02-29
Oops (this is Oneiric):

[ATTACH]213507[/ATTACH]

---

### Post by mc4man on 2012-02-29
I guess it would be reasonable to expect the dconf-editor path to be the same as the gsettings.
Whether it just hasn't been gotten to yet or some other reason I guess we'll see. 
(the indicator.sessions isn't the only gconf-editor > apps schemas that don't use apps.<whatever> in gsettings

The only thing in your report I don't quite 'get' is why you think "creates a NEW path ", -  nothings being created anew, they just aren't the same (but both 'Do' the same

---

### Post by kansasnoob on 2012-02-29
> **mc4man said:**
> I guess it would be reasonable to expect the dconf-editor path to be the same as the gsettings.
Whether it just hasn't been gotten to yet or some other reason I guess we'll see. 
(the indicator.sessions isn't the only gconf-editor > apps schemas that don't use apps.<whatever> in gsettings

The only thing in your report I don't quite 'get' is why you think "creates a NEW path ", -  nothings being created anew, they just aren't the same (but both 'Do' the same

Well, it displays a new path in dconf-editor. That seems odd to me. I'll bet we see much more of this as gconf is deprecated over the next few cycles :)

---

