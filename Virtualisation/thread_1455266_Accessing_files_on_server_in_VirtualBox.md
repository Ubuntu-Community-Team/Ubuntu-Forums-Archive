---
title: "Accessing files on server in VirtualBox"
date: 2010-04-15
forum: Virtualisation
---

### Post by DedMoroz on 2010-04-15
I hope I can make this as clear as possible...

*comp 1* Windows XP with files on it

*comp 2* Ubuntu Lucid System
           -> Virtual Box
              -> Win XP installed

Computer 1 is sharing its hard drive. Computers are networked and computer 2 can see and access the shared folders on computer 1.

From within my VirtualBox XP install, I need to access files on computer 1, but Im unable to see anything.

In comp 2 (my ubuntu system), I can see the other XP and files and I make sure they are connected, but in VB, I cant see them. I try to "share folders" icon at the bottom of VB, but the networked folders are not even listed as an option.

Any suggestions to get this connected? Thanks and much appreciated!

---

### Post by elemental11 on 2010-04-15
Can you access the internet, you might try changing the network adapter settings and make sure you can actually access the network. Try pinging your other computer from Virtual Box XP

---

### Post by DedMoroz on 2010-04-15
I got it! I just had to set the correct bridge adapter in the VB settings. Bingo. Now Im able to see the network i need.

---

