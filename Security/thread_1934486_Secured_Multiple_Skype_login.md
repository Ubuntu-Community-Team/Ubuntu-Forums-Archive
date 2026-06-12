---
title: "Secured Multiple Skype login"
date: 2012-03-02
forum: Security
---

### Post by vankich on 2012-03-02
Hello.

I'd like to ask is there a way to secure the script with usernames and passwords which makes the Multiple Skypes login [from this thread]("http://ubuntuforums.org/showthread.php?p=11724684") possible.

```
#!/bin/bash  
echo Skypeuser1 Password1 | skype --pipelogin 
```

The script works perfectly, but it keeps the login info in plain text. 
I want to secure it somehow. Is there a way?

Thanks!

---

### Post by Ms. Daisy on 2012-03-02
using stty will allow you to enter a password without seeing it on the screen as you type it:

[http://askubuntu.com/questions/46783/is-it-possible-to-pass-passwords-on-a-shell-script](http://askubuntu.com/questions/46783/is-it-possible-to-pass-passwords-on-a-shell-script)

But you want to script the whole thing including passwords, right? Have a look at this:

[http://stackoverflow.com/questions/2144218/how-can-i-hide-a-password-username-used-in-a-bash-script-for-accessing-mysql](http://stackoverflow.com/questions/2144218/how-can-i-hide-a-password-username-used-in-a-bash-script-for-accessing-mysql)

I'll be interested to hear other suggestions.

---

### Post by vankich on 2012-03-05
I don't think the ideas from above suit my needs. Bump, more ideas?

---

### Post by raja.genupula on 2012-03-05
[http://ubuntuforums.org/showthread.php?p=5916873#post5916873](http://ubuntuforums.org/showthread.php?p=5916873#post5916873)

may be this

---

