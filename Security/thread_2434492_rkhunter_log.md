---
title: "rkhunter log"
date: 2020-01-06
forum: Security
---

### Post by newb1e98 on 2020-01-06
Hello everyone! I'm gonna attach my rkhunter log here, i'm new into linux and idk if should i worry or not and how to solve those "warnings", maybe somenone can help me :D thank you !

[https://paste.ubuntu.com/p/f43FMPXpPJ/](https://paste.ubuntu.com/p/f43FMPXpPJ/)

---

### Post by yetimon_64 on 2020-01-06
Here are a couple of threads I've been involved in that have some info and discussion of rkhunter ...
[[COLOR=#0000ff]--rkhunter warnings--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2385333"), (2018)[URL="https://ubuntuforums.org/showthread.php?t=2411144"][COLOR=#0000ff]
--rkhunter error--[/COLOR][/URL] (2019) 

Both blue links above may have some information of interest to your issues. There's also some discussion of how useful or otherwise rkhunter is. It has a reputation for giving false positives. It definitely needs researching and knowledge to be of use to anyone.

Having checked over your results, I'd be more interested to see the contents or /var/log/rkhunter.log and searching for the warnings there; you will get better information as to what is going on from there rather than the straight terminal output posted here.

 Opening rkhunter.log in a text editor (read-only) and using the search function will give a better overview of any warnings. That is search for the word "Warning" in the log file.

Regards, yeti.

---

### Post by newb1e98 on 2020-01-07
I don't know how to open the log in a text-editor .. only in terminal..

---

### Post by yetimon_64 on 2020-01-07
Ok, from the terminal enter the next command, I am assuming you're on a stock Ubuntu installation (gnome DE)...
```
gedit /var/log/rkhunter.log
```

The editor will open with the file as read only.

Use the find option in the editor menus to search for the word "Warning".

**Edit:** note the last line of your terminal output posted above ...
> Please check the log file (/var/log/rkhunter.log)

---

### Post by newb1e98 on 2020-01-07
Ok, let's see

[13:52:25]   /usr/bin/lwp-request                            [ Warning ]
[13:52:25] Warning: The command '/usr/bin/lwp-request' has been replaced by a script: /usr/bin/lwp-request: Perl script text executable
Checking for suspicious (large) shared memory segments [ Warning ]
[13:54:09] Warning: The following suspicious (large) shared memory segments have been found:
[13:54:09]          Process: /usr/bin/nautilus-desktop    PID: 2811    Owner: batman    Size: 64MB (configured size allowed: 1,0MB)
[13:54:09]          Process: /usr/bin/nautilus-desktop    PID: 2811    Owner: batman    Size: 16MB (configured size allowed: 1,0MB)
[13:54:09]          Process: /usr/lib/firefox/firefox    PID: 3314    Owner: batman    Size: 3,5MB (configured size allowed: 1,0MB)
[13:54:09]          Process: /usr/lib/firefox/firefox    PID: 3314    Owner: batman    Size: 3,5MB (configured size allowed: 1,0MB)
[13:54:09]          Process: /usr/lib/gnome-terminal/gnome-terminal-server    PID: 3806    Owner: batman    Size: 4,0MB (configured size allowed: 1,0MB)

---

### Post by yetimon_64 on 2020-01-07
That doesn't look bad at all. The first warning is a script replacement and can be whitelisted.

The first link in my first post will show you how to whitelist that file lwp-request and gives more information about rkhunter usage. It would pay you to carefully read both those links above, the second will give you an idea why rkhunter is not always of much use. "rkhunter" is not a new user friendly tool in my opinion. It is of more use to a system admin type person who understands the system than it is for a desktop user.

---

### Post by newb1e98 on 2020-01-10
Thank you!

---

