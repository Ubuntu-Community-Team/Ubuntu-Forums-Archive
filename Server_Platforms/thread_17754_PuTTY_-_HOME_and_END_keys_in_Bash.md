---
title: "PuTTY - HOME and END keys in Bash"
date: 2005-03-02
forum: Server Platforms
---

### Post by Rottweiler on 2005-03-02
I frequently admin my Ubuntu server boxes via SSH using PuTTY on Windows.

But on Ubuntu at the Bash command line the 'Home' and 'End' don't do anything except throw an escape sequence on the screen.

Thing is ...
- The Home and End keys work normally in 'vi' in Ubuntu.
- The Home and End keys work normally in bash on RH/FC boxes.
     ... so I'm inclined not to blame it on PuTTY.

I have it set to 'xterm' on both ends (this is the default on PuTTY, Ubuntu, and RH/FC).

Anyone know how to troubleshoot or fix this?

---

### Post by Rottweiler on 2005-03-02
Well, found the answer five minutes later.

Noticed it was working on my Hoary play box. Eventually found these lines on Warty in /etc/inputrc:
 ```
# allow the use of the Home/End keys
# "\e[1~": beginning-of-line
# "\e[4~": end-of-line
``` Uncomment the two lines and all is well.

---

### Post by mdr on 2005-03-08
ta rotty for the fix.
run into that problem myself last week - most frustrating but too lazy to find a fix!
 =D>

---

