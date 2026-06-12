---
title: "fluxbox loosing network connection after reboot"
date: 2008-03-07
forum: System76 Support
---

### Post by P0CKETS on 2008-03-07
I rather like using fluxbox instead of gnome. I have done some configuration changes in the fluxbox startup, menu and styles files.I have also done some changes in the bashrc and hostname. Other than that I have not changed any thing. Oh and made fluxbox  my default session windows manager. The problem is that when I shutdown my laptop and reboot it, starting a session in fluxbox without going into gnome first, I cant get a network connection. If I change sessions to gnome first than go into fluxbox it works. What can cause this and/or how can I make it so when that my network is detected in fluxbox at startup. Also  the ```
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host- The Box/0/numlock_on": ` ' is an invalid character in key/directory names
``` is still occuring when I press the cap locks key in gnome. Another  thing I have been trying to do is to get GTK+ built, I just mention all this cause I  do not know what can and can not affect things.

---

### Post by jdb on 2008-03-07
I had similar problems with Xubuntu (xfce4 desktop).

In Hardy Heron I no longer have any problems so maybe it will help you too.
The final version should be out in April.

Before that I could always get the network to come up by running:

sudo dpkg-reconfigure network-manager

I'm not sure what that did, but a minute or so after I ran it the network would come up.
I don't know if it will help with fluxbox or not.

jdb

---

### Post by osx424242 on 2008-03-09
> **P0CKETS said:**
> Also  the ```
Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host- The Box/0/numlock_on": ` ' is an invalid character in key/directory names
``` is still occuring when I press the cap locks key in gnome.

You said in the previous thread that you changed your hostname (presumably " The Box" which includes a leading space)  to a name without spaces.  However, since that didn't fix this problem, there must still be a file somewhere that references the old hostname.  Did you try running the 'find' command that I suggested?  Can you try running it again, and post the output here?  If you're not comfortable posting the output, at least try:
```
find ~ -type f -exec grep -il "The Box" '{}' \;
```
and look at each of those files, on your own, to see which ones might be causing the problem.  You'll probably need to either remove the offending file :), escape the spaces, or put quotes around the entire path/filename.

Standard recommendations apply, of course: back up all files or directories before making changes, just in case.

---

### Post by osx424242 on 2008-03-09
Okay I did a little more research this morning (this is an interesting problem!).
First of all, you're not the only one here who's seen it: [http://ubuntuforums.org/showthread.php?t=407017](http://ubuntuforums.org/showthread.php?t=407017)
The fix recommended there was also to just rename your hostname.  Since you did that but it didn't fix the issue, I'd also consider renaming or removing that directory.  Take a look at what all is in ~/.gconf/desktop/gnome/peripherals/keyboard/host-\ The\ Box/
I just have an empty file and a directory ('0') with one file, with one XML entry in it (the numlock_on entry).

Second, I believe that this bug has been reported and fix.  Actually, it was fixed for non-ASCII characters, but hopefully the fix also checked for spaces: [https://bugs.launchpad.net/gnome-control-center/+bug/110567](https://bugs.launchpad.net/gnome-control-center/+bug/110567)   You could always just wait for Hardy and see if that fixes it ;)

---

