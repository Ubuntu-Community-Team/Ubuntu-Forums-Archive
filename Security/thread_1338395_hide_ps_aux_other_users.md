---
title: "hide ps aux other users"
date: 2009-11-26
forum: Security
---

### Post by ThanosKLP on 2009-11-26
hey. how can i hide other users processes from ps aux on a normal user?

---

### Post by scorp123 on 2009-11-26
You mean just the output? You could use e.g. "grep" and just filter the one user you want, e.g.
```
ps -efH | grep ^root
```

Or the other way round: You want to see all processes but not root's:
```
ps -efH | grep -v ^root
```

That part that says "***^user***" is a so called *regular expression*. It means **"if the line begins with the word ... "** ... So in the first example I tell "**grep**" that I want to see the output of **"ps"** if it begins with the word *"root"* ... And in the other example I invert the **"grep"** filter and tell it the opposite: to show all lines that do ***not*** begin with "root" ...

Is this what you want?

Your posting could also be understood as you requesting a method by which a user may not see the full output of a "**ps**" command ... And that's not possible I think. Different than on Windows, on Linux processes cannot hide and cannot "disappear" and become "invisible".

If you don't want normal users to see something security-relevant (e.g. a command that requires a password in its options) then you have to solve it differently, e.g. pipe the password from a file, or something like that.

---

### Post by ThanosKLP on 2009-11-26
i want normal users to see only their processes at ps aux / top / htop

---

### Post by scorp123 on 2009-11-26
> **ThanosKLP said:**
> i want normal users to see only their processes at ps aux / top / htop

With a normal Linux this will not be possible. To truly implement that you'd have to use some extra security mechanism such as e.g. GRsecurity. It gets complicated ...  I guess it would be easier to give each user their own para-virtualised Linux instance e.g. via KVM or XEN? With this they'd be "alone" on "their own" Linux instance. And thanks to KVM or XEN the performance hit wouldn't be too big.

So if you really really want to implement this anyway you'll have to do some reading about GRsecurity and what not:

[http://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html](http://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html)

[http://www.linuxquestions.org/questions/linux-server-73/restrict-ps-to-show-only-user-own-processes-on-debian-etch.-644131/](http://www.linuxquestions.org/questions/linux-server-73/restrict-ps-to-show-only-user-own-processes-on-debian-etch.-644131/)

[http://forums.grsecurity.net/viewtopic.php?f=1&t=1490&st=0&sk=t&sd=a&start=30](http://forums.grsecurity.net/viewtopic.php?f=1&t=1490&st=0&sk=t&sd=a&start=30)

[http://www.tuxmachines.org/node/8676](http://www.tuxmachines.org/node/8676)


Once you have "GRSecurity" in place you can then use the methods described here (the **"gradm"** command) and restrict processes:

[http://www.devshed.com/c/a/Security/Unix-Host-Security-Hacks-11-20/3/](http://www.devshed.com/c/a/Security/Unix-Host-Security-Hacks-11-20/3/)

I am not quite sure how you'd do that with ps, top and htop .. but I guess you'd have to start somewhere and try it out.

---

