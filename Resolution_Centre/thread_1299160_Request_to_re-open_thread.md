---
title: "Request to re-open thread"
date: 2009-10-23
forum: Resolution Centre
---

### Post by saulgoode on 2009-10-23
The closing post of [this thread](http://ubuntuforums.org/showthread.php?p=8137087#post8137087) contains misinformation and the thread should be re-opened so that correct information can be provided.

Ubuntu by default does not prevent logging in as root. It prevents *password authentication* of root logins. Other authentication methods are available such as PAM (Pluggable Authentication Modules), SSH keys, and 'sudo -i' -- all of which permit "logging in as root" even though root's password may not be required.

---

### Post by bodhi.zazen on 2009-10-23
That thread has gotten a bit off topic.

The OP question was : 

> So... what IS the root password in Ubuntu?

Although your information is accurate, it is somewhat off topic. IMO that discussion in that thread has been both off topic and in the case of several posts inaccurate. Surprisingly this has caused heated debates.

As such, the information you are providing is a bit offtopic and (somewhat) obscure. The OP is not asking about ssh logins or ssh security or methods of logging in as root, the OP is asking about the root password. Your information is accurate, but off topic as , by default ssh-server is not installed and one would need to make a key for the root account and then upload it to the server. 

So to be clear with you, by default, one can not log into the root account via ssh either. You of course can install and configure ssh such that one can log into the root account without setting a root password, I agree with you there, but not by default.

As such, IMO the information posted by [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941") is correct and there really is nothing to add.

In other words, I think the thread has run it's course and it is time to move on.

---

### Post by saulgoode on 2009-10-24
> **bodhi.zazen said:**
> As such, IMO the information posted by [[COLOR=#d40000]**aysiu**[/COLOR]]("http://ubuntuforums.org/member.php?u=21941") is correct and there really is nothing to add.
The information posted by aysiu is not correct. Even discounting SSH or PAM authenticated logins (which I agree are not enabled by default), whenever one performs 'sudo -i' in Ubuntu, they have indeed logged in as root -- */etc/profile* and */root/.profile* get executed; and after the user exits, */root/.bash_logout* gets executed (if present). The login is authenticated by 'sudo', but it is no less a root login than if the authentication uses */etc/passwd*. 

I don't really care if the thread remains closed or not, but it would seem a disservice to both the Ubuntu community and to aysiu to leave the "straight facts" presented in that closing post uncorrected.

---

### Post by bodhi.zazen on 2009-10-24
I am afraid we will have to agree to disagree on this issue. I have looked at aysiu's post several times now and, IMO it is accurate.

---

