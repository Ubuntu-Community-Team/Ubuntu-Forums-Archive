---
title: "ACL permission inheritance behavior on folder copy"
date: 2010-09-13
forum: Server Platforms
---

### Post by kakulacis on 2010-09-13
Hello!

I have difficulties to understand ACL permission behavior, particularly on folder copy/creation using default ACL-s. Below I have given an example of problem.

Folder on which other folder will be copied/created:

```
# file: data/public/
# owner: root
# group: root
user::rwx
group::r-x
group::public_write:[COLOR="Red"]rwx[/COLOR]
group::public_read:r--
mask::rwx
other::---
default:user::rwx
default:group::r-x
default:group::public_write:rwx
default:group::public_read:r--
default:mask::rwx
default:other::---
```

When I create new folder permissions are inherited as follows:

```
# file: data/public/tst6/
# owner: tjutjunnik
# group: tjutjunnik
user::rwx
group::r-x
group::public_write:[COLOR="Red"]rwx[/COLOR]
group::public_read:r--
mask::rwx
other::---
default:user::rwx
default:group::r-x
default:group::public_write:rwx
default:group::public_read:r--
default:mask::rwx
default:other::---
```

But when I copy a folder with following permissions:

```
# file: data/public/lalala
# owner: tjutjunnik
# group: tjutjunnik
user::rwx
group::r-x
group::public_write:[COLOR="Red"]rwx[/COLOR]
group::public_read:r--
mask::rwx
other::---
default:user::rwx
default:group::r-x
default:group::public_write:rwx
default:group::public_read:r--
default:mask::rwx
default:other::---
```

on the same folder (/data/public) I have no more write permissions on public_write group

```
# file: data/public/tatata/
# owner: tjutjunnik
# group: tjutjunnik
user::rwx
group::r-x
group::public_write:[COLOR="Red"]rwx[/COLOR] #effective:[COLOR="Red"]r-x[/COLOR]
group::public_read:r--
mask::r-x
other::---
default:user::rwx
default:group::r-x
default:group::public_write:rwx
default:group::public_read:r--
default:mask::rwx
default:other::---

```

How can I achieve same behavior as with creating new folder? As you can see group mask changes from rwx to r-x and that&#8217;s why effective permission on group public_write becomes r-x. What&#8217;s the reason and how can I avoid it?

---

### Post by kakulacis on 2010-09-13
One additional question... How can i configure system so user with rwx on particular file/folder could change permissions on it? Is it possible?

---

### Post by kakulacis on 2010-09-14
Anyone? :O

---

### Post by barinov2000 on 2010-09-14
same problem here

and here (since 2008 :roll: ): [http://ubuntuforums.org/showthread.php?t=691127](http://ubuntuforums.org/showthread.php?t=691127)

---

### Post by kakulacis on 2010-09-15
The main problem now is group mask which changes on copy from rwx to r-x and that’s why effective permission on group public_write becomes r-x. Luckily that on samba share this is somehow avoided, but anyway i would like to know at least theoretical information why this is happening.

---

### Post by barinov2000 on 2010-09-15
good explanation here.
the article is from 2008 but not much changed since then
[http://www.mattb.net.nz/blog/2007/07/09/posixnfsv4-acl-inheritance-problems/](http://www.mattb.net.nz/blog/2007/07/09/posixnfsv4-acl-inheritance-problems/)

same problems in Mac world: [http://webcache.googleusercontent.com/search?q=cache:lSr3rKXpPiwJ:hintsforums.macworld.com/archive/index.php/t-68358.html+acl+permissions+copied+inherited&cd=7&hl=en&ct=clnk](http://webcache.googleusercontent.com/search?q=cache:lSr3rKXpPiwJ:hintsforums.macworld.com/archive/index.php/t-68358.html+acl+permissions+copied+inherited&cd=7&hl=en&ct=clnk)
but Apple fixed it in Tiger Server. Tiger is based on Darwin, Darwin is based on a flavor of NetBSD.. and most of the stuff they use is based under the hood is based on open source. 

Long story short, Apple made ACL inheritance work for copying directories. How did they do it? Can it be reproduced in Linux?

---

### Post by kakulacis on 2010-09-15
Thanks! At least a little relief, that I'm not a single fish in the sea :)
I'm quite sure that solution is somewhere out there, only right key words are needed for google... :razz:

---

### Post by kakulacis on 2010-09-15
It looks like umask needs to be changed from default 0022 to 0002. But still i haven't got a clue why everything is working without changing umask when creating new directory, but issue raises when copying directories.
Some experienced user could explain me this behavior.

---

### Post by koenn on 2010-09-15
> **kakulacis said:**
> It looks like umask needs to be changed from default 0022 to 0002. But still i haven't got a clue why everything is working without changing umask when creating new directory, but issue raises when copying directories.
Some experienced user could explain me this behavior.
when you copy a directory, you copy with it the permissions set on the original directory. These may affect the resulting ACL and thus the effective permissions of the copied folder.
When you newly create a dir, you start with 0 permissions and inherit from the parent. 
I think.

---

### Post by barinov2000 on 2010-09-15
> **koenn said:**
> when you copy a directory, you copy with it the permissions set on the original directory. These may affect the resulting ACL and thus the effective permissions of the copied folder.
When you newly create a dir, you start with 0 permissions and inherit from the parent. 
I think.
The inability to enforce ACL on anything that's copied into the directory kinda defeats the purpose of ACL's "inherit and do it recursively" setting, doesn't it? I remember it was a problem on OS X Panther, but then in Tiger it was fixed. Apple found a way.

---

### Post by kakulacis on 2010-09-16
Koenn, your statement is not right...
If You would have red my topic carefully you would notice, that I'm copying directory which already have needed permissions set on it, but after copy operation mask changes...

---

### Post by koenn on 2010-09-16
> **barinov2000 said:**
> The inability to enforce ACL on anything that's copied into the directory kinda defeats the purpose of ACL's "inherit and do it recursively" setting, doesn't it? I remember it was a problem on OS X Panther, but then in Tiger it was fixed. Apple found a way.
I was just trying to provide a plausible explanation as to what causes this effect, as kakulacis asked.
I'm not saying it's desirable, or expected behavior, or logical, or whatever. It might just be a bug, or an judgment call or trade-off on the part of the developers. 


Eg, compare to the effect of copy/move on windows 2000 and 2003 (I don't know if it's also the case for 2008 e.a.), where the effect of ACL inheritance depends on whether you move/copy to the same partition or to a different one. [http://support.microsoft.com/kb/310316](http://support.microsoft.com/kb/310316) : "when you move an object to a different folder on the same volume ... _the original permissions are retained_"

---

### Post by koenn on 2010-09-16
> **kakulacis said:**
> Koenn, your statement is not right...
If You would have red my topic carefully you would notice, that I'm copying directory which already have needed permissions set on it, but after copy operation mask changes...
according to an article refered to earlier in this thread:
[http://www.mattb.net.nz/blog/2007/07/09/posixnfsv4-acl-inheritance-problems/](http://www.mattb.net.nz/blog/2007/07/09/posixnfsv4-acl-inheritance-problems/)

"However any file that is copied into the hierarchy without the &#8216;group&#8217; write bit set ... will actually remove the write bit from the ACL mask invalidating the ACL and [result in an effective permission without the w]"

so, the mask change is triggered by the permissions on the file you copied. I'm  assuming it's likewise for directories. 

So, where am I wrong here ?

---

### Post by barinov2000 on 2010-10-16
No one said you're wrong. What is wrong is exactly this "copying..will actually remove the write bit from the ACL mask invalidating the ACL".. ACL should ideally remain valid, shouldn't it? Anything you put into a directory ecplicitly shared by a group should be accessible by the group, whether you copy it or create it there. ACL should be enforced. But right now it works like a secondary supplement for standard POSIX permissions.

Please vote for this idea: [http://brainstorm.ubuntu.com/idea/22974/](http://brainstorm.ubuntu.com/idea/22974/)

---

### Post by koenn on 2010-10-16
> **barinov2000 said:**
> No one said you're wrong. 
some one did say "koen, your explanation is not right"  
:)

---

### Post by kakulacis on 2010-10-20
> **koenn said:**
> I was just trying to provide a plausible explanation as to what causes this effect, as kakulacis asked.
I'm not saying it's desirable, or expected behavior, or logical, or whatever. It might just be a bug, or an judgment call or trade-off on the part of the developers. 


Eg, compare to the effect of copy/move on windows 2000 and 2003 (I don't know if it's also the case for 2008 e.a.), where the effect of ACL inheritance depends on whether you move/copy to the same partition or to a different one. [http://support.microsoft.com/kb/310316](http://support.microsoft.com/kb/310316) : "when you move an object to a different folder on the same volume ... _the original permissions are retained_"


I should say, that your explanation is not fully descriptive because [COLOR="Red"]I'm copying directory which already have needed permissions set on it[/COLOR], but mask changes anyway because of incorrect UMASK which is not problem in SAMBA.

Now i have a similar problem... Everything is working on SAMBA except permissions are not inherited from destination directory on move operation when moving files within the same filesystem... It's not what i expect as windows user :) Can i resolve this somehow?

---

