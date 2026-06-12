---
title: "chroot 'ed user shell"
date: 2011-01-19
forum: Server Platforms
---

### Post by I2v8an on 2011-01-19
Hi all,

I am trying to set up chroot'ed user shells, but I so far I've had little luck with anything that works.
My goal here is to setup multiple user accounts with ssh access that will never be aware of any activity or file structure outside of their own home directories AND still have bash as a shell.

I have been google'ing around for a while now and I can't seem to find a solution that works for me. (It seems like 2005 was the last time anyone worked on this)

A push in the right direction would be greatly appreciated,
Thanks!

---

### Post by James78 on 2011-01-20
Does this help?
[http://blogs.techrepublic.com.com/opensource/?p=229](http://blogs.techrepublic.com.com/opensource/?p=229)

Remember that Chrooting with SSH sorta requires all the binaries and command line tools to be in the same chroot copy, so it can get really messy. That's why it's simply recommended you don't give any users SSH access to begin with; sorta makes your server vulnerable to attacks from the inside.

---

### Post by I2v8an on 2011-01-20
Yes, I did read that post, thanks!
I am currently trying to sort out the directory permissions xD to get it to work

For this particular problem, however, I am thinking of building a chroot environment.  I have read a few posts like [http://www.howtoforge.com/chrooted_ssh_howto_debian_p2](http://www.howtoforge.com/chrooted_ssh_howto_debian_p2), but I haven't had too much luck getting it work.
I am pretty familiar with working my way around an environment created with debootstrap though, which is what I'm using right now.  I just wonder if there might be a way that doesn't require the larger footprint of a whole operating system and possibly a bit more constrictive.

As far as security is concerned I'm working with a virtual machine built specifically to test this application, so no worries there.

---

