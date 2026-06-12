---
title: "Password disabled, impossible to authentificate anymore!"
date: 2012-01-26
forum: Security
---

### Post by tomwcd on 2012-01-26
Hello !

OK, so here is a new problem for you guys !

I tried to disable my password to get rid of the inopportune authentication. The problem now is that I still need it for highly important stuff, like updating the system, which I can't do anymore. So, not only a password is still asked, but my former password is not working anymore. So, as a consequence, I lost all the rights on my own computer, on which I'm the only user. Needless to say that my mind is a shelter for irony and sadness at the moment.

I have 117 updates pending, which I can't install.

If anyone as a solution - if I can go back to the old password situation it's totally OK, I just want to be able to use my computer freely ;)

I read a few similar calls for help for which the solutions didn't work for me, so I'm a little lost, that's why I'm posting here.

Thanks in advance for your useful help !

---

### Post by ajgreeny on 2012-01-26
You don't say what you did to disable your password, nor the steps that you tried in order to get your password back, so if it was this page, my apologies; if it was something else, give this a try now.  It should reset your user password, though I don't know if it will overcome your problem of a disabled password completely, as I don't know exactly what you mean by that.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by emiller12345 on 2012-01-26
I found this page on the ubuntu.com site.  I've heard that you can reset your password right from grub, but I've never tried it.
[https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html#reset-password-grub2](https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html#reset-password-grub2)

---

### Post by tomwcd on 2012-01-26
Actually I just found out how to get back to using a password, so sorry about this and thanks for the answers anyway !
I tried to reset the password via the root shell prompt, and i used to have the error:

> Authentication token manipulation error

What it took was to kind of unlock the recovery mode as this link explains:

[http://askubuntu.com/questions/91188/authentication-token-manipulation-error]("http://askubuntu.com/questions/91188/authentication-token-manipulation-error")

So if any newbies like me run into the same problem, the password can be reset like that.

---

