---
title: "Dash (vs Bash, Zsh etc)"
date: 2014-08-20
forum: Ubuntu, Linux and OS Chat
---

### Post by kiwi9 on 2014-08-20
I use Zsh as my interactive shell but have always written my scripts in Bash for:
 - greater compatibility and
 -  ease of seaching out others solutions when I run into problems.

On discovering that Ubuntu and Debian use Dash as the shell, sh, I did some research.  Dash is more POSIX compliant and faster than Bash.  Faster is always good so what do you have to give up to use sh/Dash instead of Bash?  Not a lot it turns out but it was quite hard to find documentation on it.

I've now rewritten most of my scripts in dash and they are snappier.  While doing that I annotated John McCreesh's excellent Bash Quick Reference Card with the differences between the two.  I've now modified John's card to cover Dash and by contrast the differences and provide links to web based documentation.  If anyone wants it you can find it here:

[Dash Quick Reference Card]("http://dropcanvas.com/knyzd").


Comments and improvements are most welcome.

---

### Post by umrku on 2014-08-21
If your computer is not slow then use bash.

---

### Post by kiwi9 on 2014-08-21
Thanks for the response umrku.

My computer is a 3.4GHz Quad Core i5 so its not slow but changing the scripts to dash has a surprisingly positive effect so I'll beg to differ.  Unlike a file manager like Nautilus or Nemo where I'm happy to wear a little "slowness" on launch for the extra prettiness over PCMan-FM I don't see an upside in waiting for scripts when it isn't needed.

Ubuntu devs went to the trouble of overcoming the incompatibilities in all the init scripts for the same reason.  And then Debian, changed the upstream distribution to get the same benefits.  Funnily my Pi, using Raspbian and booting as slow as grass grows still uses bash. :-)

---

