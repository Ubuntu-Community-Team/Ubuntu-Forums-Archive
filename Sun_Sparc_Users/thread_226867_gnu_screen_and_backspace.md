---
title: "gnu screen and backspace"
date: 2006-07-31
forum: Sun Sparc Users
---

### Post by Mindflux on 2006-07-31
I've googled this. It seems to be a relatively common question in the debian community.

I ssh in via PUTTY on a windows box to my friends machine.

bash# screen
bash# apt-g13t (oops hit backspace) get -wuf wuf- (screens visual for there is no more to backspace).  It control-h ^H sends backspace.. fix g13t to get and continue with my line.

backspace works fine in shell, but not screened. or in programs within screen (since screen changes the termcap).

Has anyone fixed this?

---

### Post by x1a4 on 2007-02-26
Hi,

Tell PuTTY that backspace sends ^H.  

Adding this line to _.screenrc_ might also help.  

*bindkey -d -k kb stuff "\010"*

---

