---
title: "Malicious Destop User"
date: 2008-12-25
forum: Security
---

### Post by mayagrafix on 2008-12-25
in this thread 

[http://ubuntuforums.org/showthread.php?p=6437073#post6437073](http://ubuntuforums.org/showthread.php?p=6437073#post6437073)

I described how I was suddenly without desktop menu bars. It was fixed with this command line:

xfce4-panel &

My question is: could the initial problem have been caused by a malicious user via the remote desktop?

---

### Post by pytheas22 on 2008-12-25
Sure, anything *could* be caused by malicious behavior.

But if you just experienced a crashing XFCE panel, it's much more likely that it was caused simply by a bug or other instability.

If you're concerned about security, you can read your /var/log/auth.log file to see if there were any suspicious logins to your machine lately.  XFCE probably also has a log where you could perhaps find more information on why the panel crashed, but I'm not positive where the log is (check in your /home/username/.xfce folder), as I haven't used XFCE much.

But really, I wouldn't worry too much about this.  After all, if someone wanted to attack your computer, it would make a lot more sense for them to try to get root access than to crash something that would cause legitimate users to get suspicious.

---

### Post by mayagrafix on 2008-12-25
Thank you Pytheas22. Ill sleep much better tonight.

---

### Post by bodhi.zazen on 2008-12-26
There was a time when in my experience the xfce panel would crash frequently , especially when adding some of the applets.

This has not been an issue recently, I am just saying, why would someone crack into your box just to crash the XFCE panel ? The only reason would be a friend or practical joke ...

---

