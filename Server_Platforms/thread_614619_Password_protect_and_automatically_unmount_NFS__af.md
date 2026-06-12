---
title: "Password protect and automatically unmount NFS  after timeout?"
date: 2007-11-16
forum: Server Platforms
---

### Post by zoubidoo on 2007-11-16
Hello,

For security reasons, I'd like to 
  1) require a password when mounting a particular NFS share
  2) automatically unmount the share  after a certain period of inactivity (5 minutes or so).

Does anyone have any suggestions on how to do this?

Cheers,
Z.

---

### Post by kidders on 2007-11-17
Hi there,

> **zoubidoo said:**
> 1) require a password when mounting a particular NFS shareThat can't be done, really. To be honest, I'm not sure why doing so would improve security anyhow.

> **zoubidoo said:**
> 2) automatically unmount the share  after a certain period of inactivity (5 minutes or so)In theory, you *could* do this, but since security is your reason for wanting to, it's worth mentioning that defeating the measure would be trivial.

One way of doing it might be to watch the output of "lsof" for 5-minute periods during which nothing on the share is open.

---

### Post by zoubidoo on 2007-11-18
Thanks for the reply.  

For security reasons, it makes sense not to allow access to information unless it's needed (principle of least privilege).  

If you imagine a desktop that is usually used by one person in an office environment.  Automatic screen-locking is not wanted as it's a pain to have to log in constantly and would be hard to enforce.  However, there is an NFS share that is confidential and used only occasionally.  So it should be inaccessible by default and access should involve authentication.

It doesn't seem such an unusual setting and I was checking no-one has considered this scenario before.

Yes lsof might be useful for snooping, all the more reason to have the share inaccessible by default.

---

### Post by kidders on 2007-11-18
Hey again,

I think you may have misunderstood my comment about lsof ... I was describing a way of finding a good time to automatically unmount a filesystem.

In any case, access to files is best controlled using filesystem permissions & ownership, really. To be honest, encouraging users to log out or lock their screens when they're away from their PCs is pretty fundamental, imo. In practical terms, there's very little difference between telling people to close sensitive files they're not actually using, and locking their screens. You see, even if you *could* introduce redundant authentication into getting access to an NFS share, simply opening a terminal window and typing "cd /path/to/nfs/share" (let alone opening a remote file) would defeat any attempt to automatically dismount it while the user was gone.

I'm also a little puzzled by your remark that constantly having to unlock screens would be irritating. Wouldn't a redundant authentication process essentially amount to the same thing?

I'd like to try to help if I can, but I'm not too clear on what you'd like to achieve.

---

### Post by zoubidoo on 2007-11-19
Sorry, I misunderstood your lsof comment, kidders.

Hmm.  I don't really agree that the security should come from the screen lock.  It's a bit like saying "you don't need a safe in your house because there's a lock on your front door".  Good protection has both.  And I think it's unrealistic to expect to never share a workstation with a colleague.

The principle of least privilege and specifically privilege bracketing[(Wikipedia)]("http://en.wikipedia.org/wiki/Privilege_bracketing") loosely speaking says no access unless explicitly requested.  NFS shares are up from boot to shutdown which doesn't fit with this security principle.  Ideally NFS would solve the problem but if it can I can't see how.  Would it be fair to say that's just the way NFS works?

Additional file protection seems to require another layer on top.  Here's what I have found so far:

1.  Password protect (encrypt) folders.
There seem to be a few other posts on the topic but I can't make out whether there is anything working yet.
[https://blueprints.launchpad.net/ubuntu/+spec/password-protected-folders](https://blueprints.launchpad.net/ubuntu/+spec/password-protected-folders)
[https://wiki.ubuntu.com/IdeaPool#head-8ff388134feaa9880a40f39f220a11f3329e5334](https://wiki.ubuntu.com/IdeaPool#head-8ff388134feaa9880a40f39f220a11f3329e5334)
[http://life.lapin-blanc.net/blog/keyes/2007/08/09/conceal-encrypted-folder-manager](http://life.lapin-blanc.net/blog/keyes/2007/08/09/conceal-encrypted-folder-manager)

2. Create a virtual encrypted disk that resides on the NFS share.
This would involve mounting the nfs share at boot then when required mount the encrypted image that resides on the share.
[http://www.truecrypt.org](http://www.truecrypt.org)
[http://www.linuxmonitor.net/blog/2007/03/howto-encrypt-cddvds-in-ubuntu.html](http://www.linuxmonitor.net/blog/2007/03/howto-encrypt-cddvds-in-ubuntu.html)

Of course, if NFS can achieve the same. that'd be my first choice :-)

Cheers,
Z.

---

### Post by zoubidoo on 2007-11-19
NFS ACLs sound promising, but it seems they are not supported in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=428512](http://ubuntuforums.org/showthread.php?t=428512)

---

### Post by kidders on 2007-11-19
> **zoubidoo said:**
> don't really agree that the security should come from the screen lock.  It's a bit like saying "you don't need a safe in your house because there's a lock on your front door".Lol. There is a point of diminishing returns, I think. An unlocked screen exposes a huge variety of things to unauthorised use, such as web browsers (including any stored site passwords or active sessions), all mounted filesystems (whether local or remote), the data in any open files (eg spreadsheets), and so on. The idea that each and every one of these should be independently locked with passwords & aggressive inactivity timeouts is obviously crazy, and in practice, would not improve security in any way. Surely you'll accept that my earlier suggestion that habitually locking screens is good security policy is hard to dispute.

Additionally, it's important to remember that Linux makes no distinction between local and remote filesystems, so the fact that the files you want to protect happen to be stored remotely is essentially irrelevant. Their security should be approached just as though they were stored locally.

Unfortunately, filesystem encryption (at least for your purposes) is a red herring. As a security measure, it's _only_ suitable for offline protection ... ie the computer storing the encrypted data normally has to be off at the time of an attempted break-in.

The principle of least privilege you referred to describes the idea that a web server, for example, requires root privileges to start up, but typically drops them once they are no longer required. It also applies to filesystem access control, and is the basis for common warnings about commands such as "chmod 777 *".

Anyhow, I'm afraid it looks like NFS doesn't offer what you're looking for. :-( Sorry I haven't been able to be more constructive.

**Edit:**

Something just occurred to me ...

You might find it useful to deny all your users access to all sensitive files. That way, they would have to use sudo (or similar) to acquire the access privileges of another user, before being allowed to open them. It's just a thought ... it might not be terribly useful.

---

