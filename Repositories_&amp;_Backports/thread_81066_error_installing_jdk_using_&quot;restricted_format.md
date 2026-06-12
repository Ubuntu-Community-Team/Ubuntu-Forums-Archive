---
title: "error installing jdk using &quot;restricted formats&quot; instructions"
date: 2005-10-23
forum: Repositories &amp; Backports
---

### Post by maxxfell on 2005-10-23
I'm trying to install j2sdk for my son--he wants to learn Java programming but I guess he doesn't feel like working with Linux!

I followed the directions in the "Restricted Formats" document on the Wiki, and during the "make-jpkg" step I get this error

mkdir: cannot create directory `/etc/.java': Permission denied

followed by many other missing directory and permission denied messages.  

How bad is this?

I did subsequently run the dpkg line without further comment.  But did get an error message when trying to compile a simple Java program to test the installation.  So now I'm flailing about trying to find sources for that subsequent error.
(In case it isn't clear already, I shold say that I'm a Linux newbie and know nothing, but nothing, about Java.)

Thanks for any help.
M

---

### Post by Jenda on 2005-10-23
Well, although I didn't fully understand your problem, anything that gives you a "permission denied" error aught to be run as root. Repeat the command with "sudo " before it. That should help. If not, you can just make the directories manually (but I think sudo SHOULD help):```
sudo mkdir /etc/.java
```

---

### Post by maxxfell on 2005-10-23
Hmm. When I try that, I get this:

> You are real root -- unfortunately, some Java distributions have
install scripts that directly manipulate /etc, and may cause some
inconsistencies on your system. Instead, you should become a
non-root user and run:

fakeroot make-jpkg jdk-1_5_0_05-linux-i586.bin

which will allow no damage to be done to your system files and
still permit the Java distribution to successfully extract.

Aborting.

I'll take that to imply that perhaps the Java did install correctly the first time, even if Ubuntu didn't let it install the way it wanted to be installed.  I'll investigate the compiler some more.

Thanks,
M

---

