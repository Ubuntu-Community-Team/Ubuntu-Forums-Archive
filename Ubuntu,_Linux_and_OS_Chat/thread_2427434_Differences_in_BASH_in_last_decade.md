---
title: "Differences in BASH in last decade"
date: 2019-09-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Grigoriy on 2019-09-22
Hello!
                          I've found onine is pretty decent video  tutorial about BASH. But it's dated around 2010. I think Ubuntu 10.10 or  so... You think I can still learn today by using that old tutorial or  there're changes in BASH in last years that render that course obsolete?

---

### Post by TheFu on 2019-09-23
I mainly use sh (Bourne shell) stuff in bash. It all works as far as I know.

I wouldn't worry much about any older Bash, sed, awk, cut, vim, sort, tutorials. The ideas are the same today as they were in the mid-1990s and it is unlikely the tiny differences will matter, especially when learning. Every once in a while, I'm surprised to learn about some new capability that would have made some scripts a little shorter.   The main time I use bash methods is for math. Nice not to use expr anymore.

Backwards compatibility is hardly ever broken by most Unix programmers, unless they are warped by Windows programming and break the idea. More and more stuff seems to have that problem, but not bash or any of the core text handling tools.

If you **need** the latest version of bash on your systems, I think you are doing it all wrong.  To make cross-platform bash scripts work, I assume everyone is running a 5 yr old version from the release date.  I run 16.04, so I assume the bash is from 2011.  Probably 98% of bash commonly used hasn't changed enough to notice since 2005.

And don't forget to read the bash manpage on YOUR system.  That's the best way to see any new features. Forget using web versions of manpages. Those will almost certainly be for a different version than you have.

Your forum profile says 14.04. I hope that is incorrect. Supporte ended for 14.04 server last April. Desktops tend to lose support a few years earlier.

---

### Post by jeremy31 on 2019-09-23
Moved to Ubuntu, Linux and OS chat

---

### Post by Grigoriy on 2019-09-23
**TheFu,**
Thanks for your reply! I've updated my profile. I use 16.04 Upgraded my system a few months ago mainly to get a native PHP 7 support for my LAMP stack and web site. Had to downgrade Gedit though... The new version of it in 16.04 is so nasty! Though I've found out the hard way that one should use stuff like Notepadqq instead (took me hours to figure out why that loooong line of encryption code wouldn't work in BIND's zone file when I was installing DKIM for mail server).

---

