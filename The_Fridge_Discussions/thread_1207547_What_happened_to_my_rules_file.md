---
title: "What happened to my rules file?"
date: 2009-07-08
forum: The Fridge Discussions
---

### Post by TheFridge on 2009-07-08
If you’re anything like me, you might have read something about the [plans for debhelper 7 when they were still in the works.]("http://kitenet.net/~joey/blog/entry/cdbs_killer___40__design_phase__41__/") The idea of having a debian/rules file as simple as the following sounded pretty darn cool.

[INDENT]
    #!/usr/bin/make -f
    %:
    dh $@


[/INDENT]Then Debian Sid was unfrozen and Ubuntu Karmic opened for development, and you found a packaging bug you wanted to fix or a package you work on was ready to be merged. Say you needed to run some code manually after a particular debhelper command is run, but the rules file was converted to use some of the new features in debhelper 7. You probably found your self wondering what happened to my rules file!

Well, in this week’s [Packaging Training Session]("https://wiki.ubuntu.com/Packaging/Training/") James Westby (james_w) will be answering just that question in his session, **Debhelper v7: what happened to my rules file?** Come to [#ubuntu-classroom on irc.freenode.net]("http://webchat.freenode.net/?randomnick=1&channels=ubuntu-classroom") at [09th July, 12:00 UTC]("http://www.timeanddate.com/worldclock/fixedtime.html?month=7&day=9&year=2009&hour=12&min=0&sec=0&pl=0") to get the answer and learn how to take advantage of all the cool new stuff in dh 7.

Originally posted by Andrew Starr-Bochicchio (andrewsomething) [here]("http://ubuntupackaging.wordpress.com/2009/07/08/what-happened-to-my-rules-file/") on July 8, 2009 at 12:00 pm



[More...](http://fridge.ubuntu.com/node/1875)

---

### Post by shankhs on 2009-07-09
Where are the logs?

---

### Post by nhandler on 2009-07-10
> **shankhs said:**
> Where are the logs?

Logs for this session are available at [https://wiki.ubuntu.com/Packaging/Training/Logs/2009-07-09]("https://wiki.ubuntu.com/Packaging/Training/Logs/2009-07-09")

---

