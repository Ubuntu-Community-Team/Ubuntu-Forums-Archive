---
title: "Squirrelmail Script File / User Deafult Preferences"
date: 2014-04-07
forum: Server Platforms
---

### Post by lingpanda on 2014-04-07
Attempted to follow this simple script but it resulted in no change. Has anyone done this and what am I doing wrong?

[h=3]An example script[/h]  TODO: Write a better script (in Perl) providing this functionality and include it the SquirrelMail distribution.
 This is a simple shell solution to edit more than one user preference file at once.
 If you, for example, want mails to display as HTML by default and change the font to a custom one by using CSS, create a file containing:
  
```
[INDENT] show_html_default=1
custom_css=sans-10.css

[/INDENT]
```  Save the file as /tmp/default.pref, change to the data directory, and run the following command from the prompt:
  
```
[INDENT] for l in `ls *.pref`; do cat /tmp/default.pref >> $l; done

[/INDENT]
```
I only want to add ```
show_html_default=1
``` from ```
show_html_default=0
```

---

