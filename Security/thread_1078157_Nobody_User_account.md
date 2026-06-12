---
title: "Nobody User account"
date: 2009-02-23
forum: Security
---

### Post by matrim33 on 2009-02-23
Hello,

Would there be any security issues with giving user "nobody" and password and shell so that "nobody" can log in through ssh?  The reason I would like to do this is because I am using sshfs to put files from one server (call it "A") into the webroot of another server ("B").  I would like the files I copy to B to be owned by "nobody" as they are exposed to the internet, but to do this with sshfs, I believe I would have to be able to log into B with "nobody."

Are there any security problems with giving "nobody" shell access? Does giving "nobody" shell access defeat its purpose (because nobody is supposed to be limited users)?

Any thoughts on this would be appreciated.

Thanks,
matrim

---

### Post by HermanAB on 2009-02-23
Nobody is commonly used as a limited user.  It is not a good idea to violate that convention, since it may byte you one day when you install something that assumes that nobody is a limited account.

So, rather create another account and call it johndoe, joesixpack or whatever, but not nobody.

Cheers,

Herman

---

### Post by matrim33 on 2009-02-23
Thanks for the reply Herman. I should revise my question: Is it safe to have files in the webroot that are owned by a regular user account (i.e johndoe)? My understanding is that you do not want files owned by root in the webroot because if someone to was to right something to those files somehow (i.e. some script code), it might be possible to run that code as root.  Is this correct? Is this the reason you do not want root to own files in webroot?

If so, is there similar risk for files owned by johndoe?  Or is johndoe ok because it does not have super-user privileges?

Thanks again for your help,
matrim

---

### Post by cdenley on 2009-02-23
There is nothing wrong with your web scripts being owned by root. In fact, it is preferred. It doesn't make it more likely to be run as root. Web scripts will always be run as www-data, regardless who owns them. You should be more worried about who has filesystem permissions to write to them. Since root is the most difficult account to compromise and the most guarded, it should own your most sensitive files.

If you give johndoe a shell and password, then it will be possible for someone to log in and run commands as johndoe, but he shouldn't have any more permissions than nobody. I would suggest using a restricted shell like scponly, and using a key instead of a password.

---

### Post by WatchingThePain on 2009-02-23
Hi,

I think you are meant to have a johndoe account then get root from that because then a password needs to be typed in. Also the root password gets sent one packet at a time.

---

### Post by matrim33 on 2009-02-24
Thanks for all the comments. 

cdenley, what you say makes sense to me - I think I will go ahead and create a user that uses a key instead of a password.  Do you know if there are advatages to scponly over sshfs?  It sounds like scponly might be able to do this, but I like sshfs because it allows me to mount a specific directory from computer B on computer A and treat that directory as if it was no different from any other dir on A.  Is there any reason that I should use scponly over sshfs?

Thanks again for all your help.

---

### Post by cdenley on 2009-02-25
> **matrim33 said:**
> Thanks for all the comments. 

cdenley, what you say makes sense to me - I think I will go ahead and create a user that uses a key instead of a password.  Do you know if there are advatages to scponly over sshfs?  It sounds like scponly might be able to do this, but I like sshfs because it allows me to mount a specific directory from computer B on computer A and treat that directory as if it was no different from any other dir on A.  Is there any reason that I should use scponly over sshfs?

Thanks again for all your help.

scponly is a restricted shell for giving users filesystem access without an actual shell like bash. This should prevent them from being able to execute things. I would assume it would work with sshfs, but I never tried it.

---

