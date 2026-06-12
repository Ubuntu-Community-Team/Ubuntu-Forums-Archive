---
title: "Setup help"
date: 2006-09-28
forum: Server Platforms
---

### Post by MrFeetio on 2006-09-28
i am a student at a private school, and i am going to be redoing the schools network( i am network committee chair), i no nothing about servers, but i use ubuntu as my main OS. So im going to list a few question and i hope this great community can help.

ill start by telling you what we have(to my knowledge)
We have comcast highspeed Internet, Network rack, with a switch on it(20 or so eth ports), a server running linux(ubuntu?), Wireless router(linksys with modded firmware), atleast 12 computers and varuis other things.

what we need
we need to be able to support all the Operating systems, OSx, Windows, Ubuntu, Gentoo, and all the other operating systems student/staff decide to use.

We need a "Master My Documents"(Shared folder for all students and staff) and a folder for the office(just staff).
What the above says to me is some form of authentication server

we need for dhcp, wireless,and wired to work

we are on a small budget and cant spend to much more ,but if need be we can collect what we need somewhere

---

### Post by pppetter on 2006-09-30
Hi there!

The first thing i'd like to tell you is that if you're gonna go throu with this, it's gonna take some(I mean alot) time, since you need to learn pretty much new stuff...

Some questions then..Is there any type of problem with your current setup or any other specific reason to change your current environment(or redoing it...)?

---

### Post by MrFeetio on 2006-10-01
no i guess i asked to much, we mainly just want to be able to make certain direcotories on the server to have different permissions, so a office committee member could access office files but nonoffice committe members couldnt, same thing to be said with the Judical Committee, School Meeting Chair, and any thing else that would need to to private.

My goal is to have it so when someone trys to access a folder with special permeisions the get a prompt for a password

whatever the solution is it needs to work on all operating systems

---

### Post by Iowan on 2006-10-01
Sounds like quite a project - you have faculty support (advisor)?
Diving directly into network administration (especially the security side of things), doesn't sound like a task for a beginner.  That said, you'll certainly learn a lot during the experience. Hopefully you can set up a lab-type system before exposing critical files to the more "playful" element who may wish to "take a peek" at files they shouldn't.

Samba will probably be able to provide support for most (if not all) the OS's you mentioned.  (It can also provide authentication - May need LDAP and/or Winbind, but that's as much as I know about it.) 

Good luck with your project!!!

---

