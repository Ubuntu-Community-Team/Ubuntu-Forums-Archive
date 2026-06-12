---
title: "sudo vs su"
date: 2006-04-29
forum: The Cafe
---

### Post by DigitalDuality on 2006-04-29
I recently have been jumping desktops and distros left and right.  After trying out Kubuntu, ubuntu, xubuntu, breezy and dapper.. playing with XGL/compiz.. i decided i've actually played enough with a distro that was much easier for me then any of the previous times i've ever played with it in the past..and move on to something else.

Now i used fedra/redhat in the past but i never knew what i was doing.  I never committed to using it as an OS, so here i sit on an FC5 box.  Everything running smoothly.. restricted formats, drivers, codecs, fonts and all.  

I remember redhat was the distro of choice in my linux courses in college and i remember distinctly using Su.

But what i'd like to know.. is what are the benefits of su and sudo? what's the down falls of each?  I'm learning quickly i like debian's package management alot better, and in terms of ease.. sudo. But what underlying things am i missing?

Is one more secure than the other? Sudo is an option in FC5..but i have to setup my user name for it or some such crap.. i dunno.

Just curious about people's take on the matter

---

### Post by Kethinov on 2006-04-29
Advocates of replacing the root account with a single or set of sudo-enabled accounts argue that it is better security practice because it makes it impossible to login as the root user in both a terminal and graphical sense directly. If you need to do things as root, you need to explicitly say so with a password authorization, or sudo su as a regular user in the terminal and start launching rooted apps with it.

I personally prefer it done this way, and Mac OS X does this as well. It looks like sudo is taking over the world. Most of the popular UNIX based operating systems are defaulting to it now.

---

### Post by aysiu on 2006-04-29
[This](https://wiki.ubuntu.com/RootSudo#head-6cfb89699f99dbeee57c81c64945454d6ded2fac) explains the pros and cons of both models.

---

