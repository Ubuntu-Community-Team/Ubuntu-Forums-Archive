---
title: "Sharing script to create virtualhost"
date: 2014-01-22
forum: Ubuntu Application Development
---

### Post by Elvis_Morales on 2014-01-22
I would like to spread the word for this very useful tool, Its about a little script I found my self for OSX and I forked and modified to be used on Ubuntu, This has been tested in Ubuntu 13.10 and Apache 2.4.6, on other distros must work too. Please check it out and spread the word all around the community about this useful script. And if you are a coder, you are more than welcome to enhance it more to make it better!

[https://github.com/elvismdev/virtualhost.sh](https://github.com/elvismdev/virtualhost.sh)

---

### Post by TheFu on 2014-01-23
Welcome to the forums!

Fantastic that you are sharing, especially as your very first post!

What does it do?  Something about virtualization, but which technology, what are the dependencies, how is it different from other scripts?  Why doesn't it work with 12.04 - after all, enterprises will avoid non-LTS releases.  I won't run a VM host machine on anything but Debian stable or Ubuntu Server LTS (still have a few hosts on 10.04).

Is there a tagline for the script that COMPLETELY explains it in 1 phrase?
Perhaps "Easily creates virtualbox VMs on an Ubuntu 13.xx host."

Or am I completely missing the point?

---

### Post by pp-dean-2u on 2014-01-30
> **TheFu said:**
> Welcome to the forums!

Fantastic that you are sharing, especially as your very first post!

What does it do?  Something about virtualization, but which technology, what are the dependencies, how is it different from other scripts?  Why doesn't it work with 12.04 - after all, enterprises will avoid non-LTS releases.  I won't run a VM host machine on anything but Debian stable or Ubuntu Server LTS (still have a few hosts on 10.04).

Is there a tagline for the script that COMPLETELY explains it in 1 phrase?
Perhaps "Easily creates virtualbox VMs on an Ubuntu 13.xx host."

Or am I completely missing the point?

It creates virtualhosts in Apache2 and sets up the directory for it in the correct place.
Its nothing to do with virtualbox from what I can see by reading the script.
I'm going to test this on 12.04 and see what has to be done to make it work. I think there are differences in the syntax that apache uses for the Virtualhosts but these should be easy enough to detect and allow for.

---

