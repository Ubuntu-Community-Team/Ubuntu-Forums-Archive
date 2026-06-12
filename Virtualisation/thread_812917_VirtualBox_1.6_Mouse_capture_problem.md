---
title: "VirtualBox 1.6 Mouse capture problem"
date: 2008-05-30
forum: Virtualisation
---

### Post by Tim0miT on 2008-05-30
i have looked everywhere for a solution to my problem

i have recently installed my XP on virtualBox 1.6 in Ubuntu 8.04 install

now my problem is that the mouse i have does not get captured by the windows install

when i click in the window i get the capture information and i click the capture button but my mouse does not get captured

other people have had this problem but i can not find any sign of a fix??


i had my XP installed in Virtualbox 1.5.6 in Ubunu 7.10 working perfectly 

VirtualBox 1.5.6 does not run on Ubuntu 8.04


ok, so anyone got any ideas as what i can do to get the mouse to capture??

---

### Post by drakeskywing on 2008-05-30
Just wondering, i am having the same issue, though my keyboard is captured fine, though as you said the mouse capturing isnt working. I found some people saying on other forums that the only solution is to try and go back on 1.5.4, though i think that seems ever so slightly dramatic so  i want to try and see if there is another way.

---

### Post by garyedwardjohnston on 2008-05-30
OMG I'm really beginning to hate updates.

---

### Post by Tim0miT on 2008-06-01
> **drakeskywing said:**
> Just wondering, i am having the same issue, though my keyboard is captured fine, though as you said the mouse capturing isnt working. I found some people saying on other forums that the only solution is to try and go back on 1.5.4, though i think that seems ever so slightly dramatic so  i want to try and see if there is another way.

I also ready that and i tried it

sadly 1.5 is not suported on 8.04 as far as i know, well, it didnt work on my machine:(

if you could try it and report back that would be great:popcorn:

---

### Post by Tim0miT on 2008-06-01
ok guys

i have solved the problem

here is what i did:

install windows XP as normal without the use of the mouse, use the keyboard:)

once its all done install the guest additions
this didnt work for me the normal way so i went 
devices > mount CD/DVD-ROM > CD/DVD-ROM images and deleted the .iso for guest editions

then for the devises menu again i selected install guest additions

this time a box popped up in the windows install and i followed the installation 
it prompted me to re-boot which a did

on start up of windows XP a auto capture thingy will appear

click ok or what ever and it should work fine

hope this worked for you guys:guitar::guitar::guitar::guitar:

---

### Post by raplom on 2008-07-24
Tim0miT,

Excellent fix for this, thanks for posting.

---

### Post by Tim0miT on 2008-09-01
thanks, someone final apretiates my method :) lool

---

### Post by raashell on 2008-10-06
Worked for me also-- Thanks Tim

---

### Post by Deadmode on 2008-11-01
Yes worked! Thanks for detailed info.

---

### Post by yangli on 2009-01-06
Thanks, Tim. I have the same problem with XP as guest on Inprepid host. Now I installed the Guess Additions, now everything is fine. 
THANKS~~~~~~~~~~~~

---

### Post by prakharbansal on 2010-03-01
Hey Tim,
It really works.... Thanks a lot buddy...

Regards,
Prakhar

---

