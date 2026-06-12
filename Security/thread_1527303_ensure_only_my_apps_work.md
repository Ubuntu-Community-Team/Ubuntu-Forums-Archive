---
title: "ensure only my apps work"
date: 2010-07-09
forum: Security
---

### Post by sj1410 on 2010-07-09
Hi,

I have a very typical requirement. 

I have a ubuntu box and i want to ensure that only the applications, scripts, programs that i have installed should run on it, anybody else copying or installing something on it should not be able to execute. 

In other words i want to digitally sign the box or something and store that signage key in the boot loader. 

i googled a lot but could not find an appropriate solutions. i would appreciate it if somebody could help me.

---

### Post by OpSecShellshock on 2010-07-09
As long as you're the only user it should already be that way. The same should be true if you're the only user with admin privileges. No one else's applications can run because no one else can install any applications or make system changes.

---

### Post by The Cog on 2010-07-09
It's going to be hard stopping other users writing and then running their own scripts. In fact, I suspect it can't really be done. It is more normal just to confine users to writing only in their own home directories which they can use as their own playgrounds.

---

### Post by bodhi.zazen on 2010-07-09
> **sj1410 said:**
> Hi,

I have a very typical requirement. 

I have a ubuntu box and i want to ensure that only the applications, scripts, programs that i have installed should run on it, anybody else copying or installing something on it should not be able to execute. 

In other words i want to digitally sign the box or something and store that signage key in the boot loader. 

i googled a lot but could not find an appropriate solutions. i would appreciate it if somebody could help me.

You will need to make separate partitions for as much as possible. Then mount /home /var /tmp /boot (and as many partitions as possible) with the noexec option (in fstab).

You can then use apparmor to limit users further. You will need to make a shell for them, I call it jailbash

```
ln /bin/bash /usr/local/bin/jailbash
```

Then make an apparmor profile for jailbash and list only approved applications for exec.

---

### Post by Rubicon_82 on 2010-07-09
> **bodhi.zazen said:**
> You will need to make separate partitions for as much as possible. Then mount /home /var /tmp /boot (and as many partitions as possible) with the noexec option (in fstab).


I agree that it is a good idea to mount user-writeable areas with the 'noexec' option.  However, doing this to the whole /var directory tree will probably break dpkg (and, by extension, apt, aptitude, synaptic etc.).  This is due to the package configuration scripts that dpkg keeps in '/var/lib/dpkg/info'.  There may also be other packages that keep executable files somewhere under /var

With /var, you have two options as I see it:
A)  Mount /var with the 'noexec' option, then symlink /var/lib/dpkg/info to a different, executable partition.

B)  Leave /var as part of the root partition, and symlink the following user-writeable directories to a non-executable partition:
    /var/tmp
    /var/crash
    /var/mail  (as the user could potentially make their mailbox file executable).

EDIT: C)  As the root user is the only one who should ever need access to dpkg, you could still have /var mounted 'noexec'.  However, before altering your package configuration, you'd need to remount /var with the 'exec' option.
```

# mount /var -o remount,exec

```

---

### Post by bodhi.zazen on 2010-07-09
I was going to say, no, when needed, as root, you remount /tmp and /var , but then I read "C" .

So, I think you get the idea, when needed, as root you can remount various partitions as needed.

It will take some tweaking, but it should go a long ways.

---

### Post by sj1410 on 2010-07-10
i found DigSig (Digital Signature in the Kernel) project:

[http://disec.sourceforge.net/](http://disec.sourceforge.net/)

Unfortunately, it is no longer maintained.

---

### Post by unspawn on 2010-07-10
> **sj1410 said:**
> i want to ensure that only the applications, scripts, programs that i have installed should run on it, anybody else copying or installing something on it should not be able to execute.
With respect to running applications: the GRSecurity kernel patch includes TPE (Trusted Path Execution) and the TOMOYO kernel patch provides path-based MAC. Note that *restricting* access is only half of the game. If you don't *log and audit* user movement then you don't have a clue and you can't anticipate or adjust things. Basically then you've lost before you started.

---

### Post by d3v1150m471c on 2010-07-10
we might be able to better answer the question if we knew why you don't want someone else's code running on your machine. Are you the only dude on your pc...ever? is this parental censoring? are you afraid hackers will invade your machine? these things are important to meeting the problem with a specific solution. otherwise we'll keep fumbling with 9 million ideas that don't really solve your problem.

> 
i want to ensure that only the applications, scripts, programs that i have installed should run on it, anybody else copying or installing something on it should not be able to execute.


Setting user permissions to your home folder might do the trick but i'd wait here for someone to tell you if doing that will totally screw your linux machine. Otherwise, without the correct permissions, and without your password... they wouldn't be "chmod'ing" anything.

---

### Post by The Cog on 2010-07-10
Here is a noob question about apparmour:

If you allow running /usr/bin/python, users can write and run their own python programs (same for perl, java or any other interpreter). I am assuming that noexec makes no difference because the interpreter is the executable, not the script /  class file.

If you were to use apparmour to ban /usr/bin/python for example, would this prevent using executable python scripts such as those in /usr/bin, such as gwibber?

---

### Post by d3v1150m471c on 2010-07-10
if it cannot execute then yeah.

---

