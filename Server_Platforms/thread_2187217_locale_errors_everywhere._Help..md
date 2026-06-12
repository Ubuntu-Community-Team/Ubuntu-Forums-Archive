---
title: "locale errors everywhere. Help."
date: 2013-11-11
forum: Server Platforms
---

### Post by jelmew on 2013-11-11
[COLOR=#000000][FONT=verdana]Hi all. Yesterday I did set up a linux headless server, but after doing so, something seems to have messed up. I have this error when I try to open a man page:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]man: can't set the locale; make sure $LC_* and $LANG are correct[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]locale reports: LANG=en_US.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LANGUAGE=en_US:en[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_CTYPE="en_US.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_NUMERIC=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_TIME=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_COLLATE="en_US.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_MONETARY=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_MESSAGES="en_US.UTF-8"[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_PAPER=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_NAME=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_ADDRESS=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_TELEPHONE=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_MEASUREMENT=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_IDENTIFICATION=nl_NL.UTF-8[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]LC_ALL=[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sudo dpkg-reconfigure locales gives:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]perl: warning: Setting locale failed.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]perl: warning: Please check that your locale settings:[/FONT][/COLOR]
LANGUAGE = "en_US:en",

LC_ALL = (unset),

LC_PAPER = "nl_NL.UTF-8",

LC_ADDRESS = "nl_NL.UTF-8",

LC_MONETARY = "nl_NL.UTF-8",

LC_NUMERIC = "nl_NL.UTF-8",

LC_TELEPHONE = "nl_NL.UTF-8",

LC_IDENTIFICATION = "nl_NL.UTF-8",

LC_MEASUREMENT = "nl_NL.UTF-8",

LC_all = "en_US.UTF-8",

LC_TIME = "nl_NL.UTF-8",

LC_NAME = "nl_NL.UTF-8",

LANG = "en_US.UTF-8"

are supported and installed on your system.
[COLOR=#000000][FONT=verdana]perl: warning: Falling back to the standard locale ("C").[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]locale: Cannot set LC_ALL to default locale: No such file or directory[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Generating locales...[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_AG.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_AU.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_BW.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_CA.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_DK.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_GB.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_HK.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_IE.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_IN.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_NG.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_NZ.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_PH.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_SG.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_US.ISO-8859-1... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_US.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_ZA.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_ZM.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]en_ZW.UTF-8... up-to-date[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Generation complete.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]More errors, I'm not sure where they are coming from.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Anyone who can help me? I've searched the internet all over, and I can just not find a solution. So yes, I did try the search function.

Greetings,
Jelmer[/FONT][/COLOR]

---

### Post by nebileix on 2013-11-12
could u show the output of ```
cat /etc/default/locale
```

---

### Post by jelmew on 2013-11-14
LANG=en_US.UTF-8
LANGUAGE="en_US:en"

---

### Post by nebileix on 2013-11-14
try ```
sudo locale-gen nl_NL.UTF-8
```

---

