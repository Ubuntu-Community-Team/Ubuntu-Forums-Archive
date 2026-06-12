---
title: "apt-stack"
date: 2008-03-29
forum: Ubuntu Brainstorm
---

### Post by RyanHLewis on 2008-03-29
Hi,

I have an idea for a change to apt.

Currently it is a really bad plan to try and do something like


apt-get install program1
apt-get install program2

(maybe you try and run these in different terminals)

However the suggested workaround is to do

apt-get install program1 program2


but what if im installing something (say upgrading from fiesty to gutsy) and I want to install vlc so that I can watch a movie while I upgrade?

I suggest that we put all the installations on an 'installation stack' so typing 

apt-get install program1 ... programN

puts the first N items on the stack

later typing apt-get install programN+1 will just but the n+1'th program onto the stack and it too will eventually be installed.

---

### Post by RyanHLewis on 2008-03-29
p.s. when I said stack, I meant queue.

---

### Post by smartboyathome on 2008-03-29
This has been suggested, and programs already can be installed by typing apt-get install program1 program2.

---

