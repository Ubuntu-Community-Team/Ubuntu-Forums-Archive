---
title: "Windows security flaw using Ubuntu"
date: 2008-05-28
forum: Security
---

### Post by agreppi on 2008-05-28
This is not a question, but rather a post to confirm something, and see if I'm right with my reasoning.

I always used windows, and recently I came accross Ubuntu, so I decided to give it a try. I installed it using Wubi, used it for a couple of weeks, and finally last weekend installed Ubuntu properly, partitioning the HD.

After installation, I could see that I can access my windows file from Ubuntu.

This makes me think that I could hack a computer, with no need of knowing the password of any windows user in that computer.

That is, if I want to see the contents of a computer with windows installed, not being a user on that computer, I could install Ubuntu on that computer with the Live CD, and voilà! I see all the files in the windows partition, without entering any password!

Am I right?

---

### Post by Monicker on 2008-05-28
You don't even need to install. Just about any linux live cd will give you access to a Windows file system.  That is why any extremely personal/sensitive data should be encrypted, regardless of the operating system.

---

### Post by The Cog on 2008-05-28
That is not a problem particular to Windows. Any operating systen that uses unencrypted disk data can have its data read either by running another OS booted from network, CD or USB, or by having the disk removed and installed as a secondary drive in another computer. Just because the disk happens to have an operating system installed on it doesn't make it unreadable.

And of course you can also write the disk making any changes you want, too. There are lots of "rescue" CDs that specialise in recovery of lost files or passwords.

---

### Post by Dr Small on 2008-05-28
This is the same with any operating system. As long as you can mount a distro on the CDROM, you basically can access the system. Hence, the need for encrypted filesystems, or encrypted files / partitions.

You data is never safe, when unencrypted.

---

### Post by agreppi on 2008-05-28
Thanks all for the reply!

Now that you mention all the encryption issue, is /home partition in Ubuntu encrypted?

If not, which are the tools I can use to encrypt that?

---

