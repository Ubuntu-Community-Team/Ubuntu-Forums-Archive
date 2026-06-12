---
title: "The Ubuntu security model concerning the browser"
date: 2009-07-23
forum: Security
---

### Post by yeeeev on 2009-07-23
Hello all,

I'm new to this forum, and been using Ubuntu for about a year now (with about 6 months as a primary OS).
I have recently tumbled upon this post:
[http://mihaiv.wordpress.com/2009/07/17/security-issues-with-sudo/](http://mihaiv.wordpress.com/2009/07/17/security-issues-with-sudo/)
What concerns me about the Ubuntu and desktop Linux security standpoint is that the security model is targeted at protecting the system, while protecting the user's data is not less important from a Desktop user's perspective.
One more thing that is clear is that the browser is one of the main attack vectors in the desktop world.
These lead me to think of the following security model for browsing:
* Normal user is part of the sudoers group (same as it is today)
* A new user (Let's call it browse user) will be added and will not be part of sudoers
* The browser will normally run as the browse user (even when run by the normal user) and will have no write access to the normal user's home
* The browse user will contain a hidden directory to which will contain files saved during the browsing session, and will act as a sandbox. Files will be saved according to the path in which the user intended to save them on the "real" path on the normal user's home directory
* Transfer of files from sandbox to the normal home will be done automatically with a simple GUI. It will be done with a separate process running under the normal user. That way the normal user will be able to really save only the files he intended to download.

That will enable browser sandboxing without real trouble from the user's perspective, and without changing the current security model.

Please let me know if such a solution has any apparent security flaws, if I'm missing something, or that the above solution is trivial and stupid :). Any comments, ideas, etc will be appreciated.

Thanks,
Yoav

---

### Post by movieman on 2009-07-23
Not a bad idea...but if some malware manages to exploit a bug which installs an add-on that emails them all your banking logon and credit card details you're still toast.

You'd really want to run the web browser as a separate user and revert the user's configuration to a safe default state every time it starts up.

---

### Post by Rob_H on 2009-07-23
Yeah, not a bad idea. If you're really paranoid, you could set up a small virtual machine with something like VirtualBox and browse from there. You can even have it revert to a snapshot after every session.

But really, I think all of this is overkill. There is virtually no malware out there that targets Linux file systems via the browser.

---

### Post by rookcifer on 2009-07-23
A MAC like AppArmor can already do this, and it's already installed on Ubuntu.  All you have to do is create a profile for Firefox.

---

### Post by bodhi.zazen on 2009-07-23
If you want a few samples for apparmor profiles look here :

[http://bodhizazen.net/aa-profiles](http://bodhizazen.net/aa-profiles)

---

### Post by yeeeev on 2009-07-24
Bodhi,
My problems with AppArmor in that aspect is that a browser can be used to start another process that is usually not network related (such as OOWriter) and therefore typically not confined, and exploit vulnerabilities in it.
Is it possible to have a process inherit confinement from its parent process in AppArmor?

In any case, having AppArmor with no profiles (besides CUPS and dhcpd) by default means that 95% of your target audience will not use it...

Yoav

P.S. Excellent AppArmor tutorial. Thanks!

---

### Post by bodhi.zazen on 2009-07-24
No your perceptions about apparmor are false. If aa is confining firefox , and firefox calls ooo (and you allow it) Open office is confined by the firefox profile, unless you specify otherwise.

As of now aparmor and selinux are the only potential foreseeable solutions to the issues you raise. 

Your assumption is that firefox is somehow cracked or somebody uses social engineering such that firefox downloads a malignant script, This hypothetical step is the real security hole.

---

### Post by yeeeev on 2009-07-24
It's good to know that whatever process FF calls is confined by the same rules.
The scenario that troubles me is not the "social engineering" one, but a zero day exploit that enables a malicious web site to run arbitrary code once browsed to (like the JIT zero day exploit found in FireFox last week).
It is true that AppArmor can solve the issues I raised. Now the only remaining problem is that it is not turned on by default, and profile maintenance is currently a mission that most non-power users will find difficult.
Ideally, the apparmor profile would have been supplied by the package arriving from the repositories and would have been automatically modified in case of an update.

Thanks,
Yoav

---

### Post by bodhi.zazen on 2009-07-24
I agree, which is why I set up a profile "repository" where people can share their profiles.

I think it would help if there were a default profile for bash, similar to jailbash, for users to use to log in (see jdong's repository).

You then log in as a non-privileged user (jailbash is actually permissive for most "normal activities, try it) and a separate admin account with bash.

Also firefox is both one of the bigggest risks, but not a great first application to confine with aa. One reason is ff is quite variable in usage, it is a browser, flash, java script, java, audio, video, etc, etc . The default apparmor profile would be very very permissive if it is to be used for everybody.

I suggest you try my profile and see how it performs for you.

It is also much easier to start with a smaller application to confine and work up to firefox.

---

