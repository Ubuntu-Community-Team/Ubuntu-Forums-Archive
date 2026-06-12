---
title: "PATH variable configuration and security issues."
date: 2011-08-02
forum: Security
---

### Post by arroy_0209 on 2011-08-02
I have got this suggestion regarding configuration of PATH variable to make linux more  secure: "Set your PATH variable with the empty field last so that the current directory is searched last after system directories have been searched completely. (Otherwise it may happen that someone may for example, change the way some command is expected to behave; one may read the password you type and send it somewhere else)  Example: the output of echo$PATH$ should be like this: /bin:/usr/bin:/home/username/bin:  In my case, the command echo $PATH$ gives: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games$  Can anybody please point out if this is desirable or not. I am yet to learn details of these issues so a little bit of explanation will be very helpful.

---

### Post by karlson on 2011-08-02
> **arroy_0209 said:**
> I have got this suggestion regarding configuration of PATH variable to make linux more  secure: "Set your PATH variable with the empty field last so that the current directory is searched last after system directories have been searched completely.
[snip]
Can anybody please point out if this is desirable or not. I am yet to learn details of these issues so a little bit of explanation will be very helpful.

Security 101 teaches all system administrators and other UNIX users that including "." in the PATH is a bad idea.  You have certain abilities in your home directory for setting permissions and ownership that can compromise security.

---

### Post by Lars Noodén on 2011-08-02
> **arroy_0209 said:**
> Can anybody please point out if this is desirable or not. 

Like what Karlson wrote, the current directory should not be in $PATH.  There are a lot of tricks that one can play if "." gets into the $PATH.  The bottom line is that it is a security flaw to allow it.

---

### Post by arroy_0209 on 2011-08-02
Thanks a lot for your replies but can you tell me how to do the modifications you suggest? I mean which file is to be modified and how?

---

### Post by bodhi.zazen on 2011-08-02
Most people set it in ~/.bashrc

For users I exclude the sbin directories as well, no reason they need those tools on their path.

In terms of security, it is a very minor security hole, IMO, as one would already have to have system access in order to leverage the exploit, and if they already have shell access there are many other things they can do.

With that said, I would now allow "." in my path either.

---

