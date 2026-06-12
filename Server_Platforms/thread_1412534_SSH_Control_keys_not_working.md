---
title: "SSH Control keys not working"
date: 2010-02-21
forum: Server Platforms
---

### Post by danharibo on 2010-02-21
I am SSHing into an Ubuntu server machine, and for some reason, none of the arrow keys work (The just insert the key code, which is useless since I can't use the command history, or even edit previously entered commands). and the Tab key does not autocomplete, it just tabs. 

I have no idea why it's doing this, and would appreciate any help in fixing the issue

---

### Post by joberly on 2010-02-21
What's the client software you are using?

---

### Post by danharibo on 2010-02-21
PuTTY 0.60

---

### Post by stlsaint on 2010-02-22
sounds like a client application issue. Try re-installing putty or test another app to make sure its not hardware related.

---

### Post by johnsanders on 2010-02-22
I don't mean to hijack this post, but I'm having the same problem.  I'm SSH'ing via Putty to my Ubuntu 9.10 server.  Logged in as my user, I have the same problem with the arrow keys sending escape commands.  However, if I ***'sudo su'*** to root, it all works as expected. Up and down arrows are my command history, and left/right move the cursor left/right to edit the command line.  I'm assuming this is a profile issue, as opposed to a Putty issue.  I'd imagine @danharibo is having a similar issue.

So my question is, and I really hope this helps @danharibo too, how do I duplicate the profile settings from my root account to my user account?  I'm confused as to which files contain my profile settings.

EDIT: I have copied over root's version of .profile and .bashrc to my home directory.  No difference in how the arrow keys work though.  I'm really missing something here.  Any help is appreciated.

Thanks,
John

---

### Post by nborders on 2010-03-25
OK, the guy who helped me with this told me my payment was to respond, so fools like me who found this thread could find the solution.

You can all thank Irving!

Anyway, what looks to have created this problem with arrow keys and even the tab not filling out the path or file names was my account default shell was not set to /bin/bash.  

I set it, logged in again and presto!

[http://linuxwave.blogspot.com/2009/03/changing-default-shell-in-ubuntu.html](http://linuxwave.blogspot.com/2009/03/changing-default-shell-in-ubuntu.html)

~n

---

### Post by androidyou on 2011-02-13
the shell is wrong, just run "/bin/bash"

[http://androidyou.blogspot.com/2011/02/linux-putty-ssh-arrow-key-not-working.html](http://androidyou.blogspot.com/2011/02/linux-putty-ssh-arrow-key-not-working.html)

---

### Post by deinerson1 on 2013-01-23
Thank you :) This boosted my late night command-line-fu.

> the shell is wrong, just run "/bin/bash"

[http://androidyou.blogspot.com/2011/...t-working.html](http://androidyou.blogspot.com/2011/...t-working.html)

---

### Post by Toz on 2013-01-23
This thread is over a year old. Closing.

---

