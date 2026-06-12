---
title: "&quot;Error found when loading /home/user/.profile&quot; upon login"
date: 2020-11-25
forum: Ubuntu/Debian BASED
---

### Post by jkjk24601 on 2020-11-25
Hello, I had a really quick question. Right after I log in, there is a prompt with a red "X" that says the following: 

```
Error found when loading /home/user/.profile

awk: read error (is a directory)

As a result the session will not be configured correctly. 
You should fix the problem as soon as feasable.
``` 

I tried using chmod to give +rwx permissions to .profile as I thought that would give permissions to read and write; however, this has not seemed to work. Everything else works fine after I log in, but I didn't know what the severity of this error message was. Would anyone be able to offer some insight on this problem? Thank you all so much!

---

### Post by DuckHook on 2020-11-25
Welcome to the forums, jkjk24601.

Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

The error message is saying that the system cannot read .profile because it is a directory and not a file (as would be expected). Did you tinker with your /home/user directory and change things?

---

### Post by jkjk24601 on 2020-12-12
Yes, sorry for the late reply! After a long overdue hardware upgrade, the error message told me it was missing a file called /etc/llver. I just added a blank file and the system booted up fine.

---

### Post by DuckHook on 2020-12-13
Good to hear that you solved it. However, please note the following:

[LIST=1]
[*]There's no point in asking for help on an Ubuntu forum when you don't use Ubuntu. Your failure to tell us from the start that you are using Linux Lite OS just wastes helpers time by sending us off on wild goose chases.
[*]Ubuntu does not use the file that you refer to. Different distros are set up with different defaults and config files. Therefore, what is needed in another distro such as yours doesn't exist in Ubuntu. In other words, without full disclosure from the outset, it is impossible for anyone to help even if they have the requisite knowledge.
[*]I have moved this thread to its appropriate subforum where it will not confuse Ubuntu users. I have also marked it "solved" for posterity. As a side note, you will likely find the sort of help you need on the [Linux Lite forums]("https://www.linuxliteos.com/forums/") rather than here. I suspect that very few Ubuntu users are familiar with Linux Lite OS.
[*]Last but not least, if you do not intend on replying for a prolonged period, please alert potential helpers ahead of time so that we won't unsubscribe the thread. As part of my housekeeping habits, I unsubscribe a thread after 4 days of inactivity. I only came across this thread again serendipitously.
[/LIST]

---

