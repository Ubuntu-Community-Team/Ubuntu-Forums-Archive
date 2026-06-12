---
title: "mysql, editline, and vim"
date: 2009-09-13
forum: Server Platforms
---

### Post by ahmedre on 2009-09-13
hi,
i saw the post here ([http://ubuntuforums.org/showthread.php?t=1147183](http://ubuntuforums.org/showthread.php?t=1147183)) discussing vim keybindings under mysql (that it is now using editline rather than readline).

however, an .editrc file is not working for me - i made a simple .editrc file in my home directory with just

bind -v

and mysql still uses standard emacs keybindings.  i saw a post online here:
[http://wjd.nu/notes/2009](http://wjd.nu/notes/2009)

and so i tried this strategy of using strace to see which configuration files are being looked for - however, i could see mysql trying to .mysql_history, .mysql_history.TMP, etc, but could not see any reference to it trying to open editrc nor .editrc nor anything of interest inside of /etc either.

any ideas?  i am currently on karmic so i guess i am running whatever the latest is.

thanks!

---

