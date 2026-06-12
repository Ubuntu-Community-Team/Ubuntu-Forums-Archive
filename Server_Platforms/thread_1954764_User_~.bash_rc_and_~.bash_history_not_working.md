---
title: "User ~/.bash_rc and ~/.bash_history not working"
date: 2012-04-08
forum: Server Platforms
---

### Post by hughr2005 on 2012-04-08
Hi All,

I have a server running with various services. When I log in over ssh, ~/.bash_rc doesn't execute. Additionally, ~/.bash_history doesn't register any of my commands. I remember that when my user was made, I had to mkdir my own home directory. Is there somewhere I have to register what my home directory is? Shouldn't that have been done automatically? Any other ideas?

Thanks in advance.

---

### Post by CharlesA on 2012-04-08
It depends on how you created the user.

Post the output of:

```
ls -al ~
```

---

### Post by roelforg on 2012-04-08
Try .bashrc (no underscore)
or .bash_profile

---

### Post by hughr2005 on 2012-04-08
output is:

total 164
drwxr-xr-x  9 hugh root   4096 2012-04-08 21:05 .
drwxr-xr-x 11 root root   4096 2012-04-08 17:10 ..
-rw-r--r--  1 hugh hugh      0 2012-04-08 02:34 .bash_history
-rw-r--r--  1 root root    675 2012-04-06 19:00 .profile
drwxr-xr-x 15 hugh hugh   4096 2012-04-08 17:27 public_html
drwxr-xr-x  3 root root   4096 2012-04-07 00:53 .ssh
-rw-r--r--  1 hugh hugh      0 2012-04-07 00:52 .sudo_as_admin_successful
-rw-------  1 hugh hugh   6184 2012-04-08 04:21 .viminfo

.bash_history is only there because I ran 'touch ~/.bash_history'

---

### Post by hughr2005 on 2012-04-08
also, ~/.bash_rc isn't there because I had just deleted it before I ran that command, I was about to write it again

---

### Post by hughr2005 on 2012-04-08
do you reckon it has anything to do with the fact that when I press the up key it types ^[[A instead of displaying my previous command? this works when I'm acting as root, or as any other user on the same system.

---

### Post by Hack.The.Pow. on 2012-04-08
are you sure that your actually using a bash prompt and not some other type of prompt?

---

### Post by Doug S on 2012-04-08
For this:> Additionally, ~/.bash_history doesn't register any of my commands.I've noticed that my commands don't get into ./bash_history until I log out from my SSH session. Once I log out, all the commands from that session get added to .bash_history. (perhaps you knew this already and I am not adding value.)

---

### Post by CharlesA on 2012-04-08
> **Doug S said:**
> For this:I've noticed that my commands don't get into ./bash_history until I log out from my SSH session. Once I log out, all the commands from that session get added to .bash_history. (perhaps you knew this already and I am not adding value.)
Yep.

Typing "history" however should show your commands.

As for having that symbol appear when you press the up arrow - are you using the number pad or arrow keys?

---

### Post by roelforg on 2012-04-08
> **CharlesA said:**
> Yep.

Typing "history" however should show your commands.

As for having that symbol appear when you press the up arrow - are you using the number pad or arrow keys?

Wrong user, permission problems?

Why is it .bash_rc at your pc and not working but .bashrc at mine where it does work?
EDIT: i was a little rude, but at least just try it.

---

### Post by hughr2005 on 2012-04-08
Doug S: I wasn't aware of that actually, I'll take that into account. I presumed that was involved in how the 'up' arrow key function worked.

CharlesA: the ```
history
``` command doesn't work. The output is ```
$ history
-sh: history: not found
```. Does the -sh mean I'm not using bash?

roelforg: as far as I know the user permissions are set correctly. I'll try .bashrc, thanks :)

---

### Post by Doug S on 2012-04-08
> . Does the -sh mean I'm not using bash?
Yes, I think so. and as of a few versions ago, sh links to dash instead of bash. As a test, within my ssh session I entered```
sh
history
```and got```
doug@test-smy:~$ sh
$ history
sh: 1: history: not found
$ exit
doug@test-smy:~$

```So I think you are running dash.
You can check your link:```
doug@test-smy:~$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 Mar 29 10:40 /bin/sh -> dash
```
Note: I do not know why your sessions would be running sh (mapped to dash) instead of bash.
 
by the way, if I run dash, then I get the up arrow troubles:```
doug@test-smy:~$ dash
$ history
dash: 1: history: not found
$ ^[[A

```

---

### Post by hughr2005 on 2012-04-08
ooh, changing to bash got the up arrow working. How do I set it to use bash by default instead of sh?

---

### Post by hughr2005 on 2012-04-08
History works as well, this is great. The problem was that I was using sh instead of bash. I used chsh to change my default shell. It works now :) Thanks for your help everyone! I'll mark this thread as solved.

---

### Post by roelforg on 2012-04-08
> **hughr2005 said:**
> History works as well, this is great. The problem was that I was using sh instead of bash. I used chsh to change my default shell. It works now :) Thanks for your help everyone! I'll mark this thread as solved.

Sidenote:
Your shell is spec'd in /etc/passwd and can be changed by hand, chsh, usermod

---

