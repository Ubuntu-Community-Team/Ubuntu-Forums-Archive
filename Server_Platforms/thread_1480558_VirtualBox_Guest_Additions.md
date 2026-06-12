---
title: "VirtualBox Guest Additions"
date: 2010-05-11
forum: Server Platforms
---

### Post by Cuco3 on 2010-05-11
I'm trying to install the Guest Additions for a VM running a guest Lucid Lynx Server. The problem I'm encountering is this:

[IMG]http://uppix.net/9/c/c/fcd2706a89a80cf6aea0d8da72f6f.png[/IMG]

The vboxadd-install.log for vbox says it "couldn't find the sources of your current Linux kernel" and to "Specify KERN_DIR=<directory> and run Make again."

---

### Post by Cuco3 on 2010-05-11
Well, except the part about "X Windows", I was able to get it to install by updating my linux kernels (you have to specifically update these by installing them by name; they'll be listed as "kept back" because they require to you restart the computer). Once I restarted, I was able to install. If you still have trouble, try reading this thread:

[http://forums.virtualbox.org/viewtopic.php?f=3&t=28955](http://forums.virtualbox.org/viewtopic.php?f=3&t=28955)

My next question: _**Is there a way to get Guest Additions that allow copying+pasting to a guest Ubuntu Server???**_

---

### Post by arrrghhh on 2010-05-11
So are you copying from the guest or pasting to the guest?  I would assume that pasting to the guest would already be transparent, but copying from the guest may be a different issue.  If the guest additions don't enable that, you could use something like [ix](http://ix.io/).

---

### Post by Cuco3 on 2010-05-12
Thanks for the response.

Yeah, I'm trying to paste to the Guest (Ubuntu Server) machine, but it still won't work.

Does someone know if this is possible or not?

---

### Post by arrrghhh on 2010-05-12
You're using shift+insert, right?

---

