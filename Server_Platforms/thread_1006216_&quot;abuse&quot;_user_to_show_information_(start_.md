---
title: "&quot;abuse&quot; user to show information (start a script)"
date: 2008-12-09
forum: Server Platforms
---

### Post by stiV on 2008-12-09
hello!

I would need a secure (!) way to enable a user (lets user "info") to start a script (for the moment a bash script, may be a perlscript some time that also takes some time to run and asks questions) - just as he logs in.

So instead of giving the user a normal shell, the shell would be the script itself, for the moment only printing some system information.

The "user" can be used via console or ssh, logs in with eg. "info:info" and gets the ouput - nothing else.

At the moment i still get the ubuntu message...
Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
Could not chdir to home directory /dev/null: Not a directory

anyway to do this properly and in a way that even if the script hangs the user can't break out?

regards

stefan

---

### Post by cdenley on 2008-12-09
I'm pretty sure if you set the user's shell to be your script, there is no way for the user to get an actual shell unless there is a flaw in your script which allows it. If the user kills the script, he will be logged out. If you want to get rid of "Could not chdir to home directory /dev/null: Not a directory", then change the user's home directory to an actual directory. If you want to get rid of that usual ubuntu message:
[http://ubuntu-tutorials.com/2007/12/09/how-to-enable-or-disable-login-messages/](http://ubuntu-tutorials.com/2007/12/09/how-to-enable-or-disable-login-messages/)

---

