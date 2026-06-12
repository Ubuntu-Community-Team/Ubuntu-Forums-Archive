---
title: "xfce4-session segfault, suspend and hibernate not working"
date: 2013-05-08
forum: Ubuntu Development Version
---

### Post by fowlslegs on 2013-05-08
Hello everyone! I am experiencing some critical bugs during a critical time (finals week) and could really appreciate some life-saving help. I have posted about it at [https://bugzilla.xfce.org/show_bug.cgi?id=10068](https://bugzilla.xfce.org/show_bug.cgi?id=10068), but have yet to receive a response from a xfce developer.

---

### Post by fowlslegs on 2013-05-08
I just added some important information to the bug report. Please check it out if you can. Photo also available here at [tinypic.com/view.php?pic=2lp4iu&s=5]("http://tinypic.com/view.php?pic=2lp4iu&s=5") if more convenient.

---

### Post by fowlslegs on 2013-05-09
The xfce-session segfault was due to xfce bug #9709:
[URL="http://git.xfce.org/xfce/xfce4-session/commit/?id=ab391138cacc62ab184a338e237c4430356b41f9"]
http://git.xfce.org/xfce/xfce4-session/commit/?id=ab391138cacc62ab184a338e237c4430356b41f9[/URL].

There is a patch which fixed it for me:
[URL="http://git.xfce.org/xfce/xfce4-session/commit/?id=ab391138cacc62ab184a338e237c4430356b41f9"]
http://git.xfce.org/xfce/xfce4-session/commit/?id=ab391138cacc62ab184a338e237c4430356b41f9[/URL].

Suspend and hibernate are still not working from action button item on my xfce panel. I also tried to run the command `pmi action suspend` and received the following:


Sorry, command-not-found has crashed! Please file a bug report at:
[https://bugs.launchpad.net/command-not-found/+filebug](https://bugs.launchpad.net/command-not-found/+filebug)
Please include the following information with the report:


command-not-found version: 0.3
Python version: 3.3.1 final 0
Distributor ID:	Ubuntu
Description:	Ubuntu Saucy Salamander (development branch)
Release:	13.10
Codename:	saucy
Exception information:


unsupported locale setting
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/util.py", line 24, in crash_guard
    callback()
  File "/usr/lib/command-not-found", line 69, in main
    enable_i18n()
  File "/usr/lib/command-not-found", line 40, in enable_i18n
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python3.3/locale.py", line 541, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

---

### Post by matt_symes on 2013-05-09
As your using Saucy: thread moved to **Ubuntu +1**.

You're taking a gamble using Saucy during your finals week.

EDIT:

pmi is not installed by default.

```
matthew-S206:/home/matthew/thunar_dbus % bash
matthew@matthew-S206:~/thunar_dbus$ pmi
The program 'pmi' is currently not installed. You can install it by typing:
sudo apt-get install powermanagement-interface
matthew@matthew-S206:~/thunar_dbus$ exit
exit
matthew-S206:/home/matthew/thunar_dbus % 
```

Looks like you may have a locale problem as well.

> locale.Error: unsupported locale setting

---

### Post by fowlslegs on 2013-05-09
> **matt_symes said:**
> [COLOR=#000000]You're taking a gamble using Saucy during your finals week.[/COLOR]

I know I meant to upgrade to Raring but skipped that Ubuntu altogether and now can't downgrade without a clean reinstall.

> **matt_symes said:**
> Looks like you may have a locale problem as well.

Don't locale settings just manage language settings and package installation? Could this be a Saucy bug.

---

### Post by fowlslegs on 2013-05-09
Thought I should add that my laptop does suspend when I close the lid.

---

### Post by slickymaster on 2013-05-10
> **fowlslegs said:**
> Don't locale settings just manage language settings and package installation?

Locales customize programs to your language and country. When you installed Ubuntu, you answered some simple questions such as specifying your country and language. Ubuntu used the answers to those questions, in part, to choose a suitable locale for your installation.

---

### Post by fowlslegs on 2013-05-10
Solved locale problem by editing ```
/etc/default/locale
```. The problem was xfce4-power-manager wasn't able to launch because of incomplete locale settings. Strange that Ubuntu changed this file itself during upgrade as I never touched it.

Before

```
LANG="en_US.UTF-8"

```

After:

```
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE=en_US.UTF-8
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES=en_US.UTF-8
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"


```

---

