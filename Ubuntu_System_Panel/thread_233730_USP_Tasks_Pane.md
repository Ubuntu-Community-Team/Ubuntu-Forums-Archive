---
title: "USP Tasks Pane"
date: 2006-08-10
forum: Ubuntu System Panel
---

### Post by DBO on 2006-08-10
A side project has begun, USP might gain a task pain, but first we, the community, need to give chanders the scripts he needs for the tasks.  I have begun writing several, but I need the help of the community to make sure they work properly.    This thread should be used as a task development area, were scripts are posted and developed until they are ready to hand off to chanders for inclusion.  You are all of course free to write your own tasks.

Tasks use zenity as a frontend, focus on doing common tasks that may not have a unified frontend, a GUI for the task at all, or are simply overcomplicated for most users.  

Currently I am working on two tasks, a task to configure a proper firewall, and a task for setting up and internet connection and browser properly.  I however need at least one dialup user to help me with ppp.  Anyone interested can find me on freenode at #usp or #ubuntu-xgl

Lets get these tasks made so we can get a new pane =)

DBO

---

### Post by Note360 on 2006-08-10
I'll help! What do we need.

(I need to spell check more)

---

### Post by DBO on 2006-08-11
> **Note360 said:**
> I'll helo what do we need

how do you want to help, are you a dialup user or looking to write scripts?

---

### Post by hgibson on 2006-08-11
Hi

I'm back. Thanks to "chanders" for accepting the tasks idea.
Unfortunately I am not that good at "bash" :sad:

However may I suggest some other things regarding "tasks".

We should try to apply "desktop" standards and co-ordinate with [http://tango-project.org](http://tango-project.org) and [http://portland.freedesktop.org](http://portland.freedesktop.org).

_For example:_

All the tasks configuration data should be saved in XML format in a folder in the users home directory. Say **/home/username/.Tasks**> If this is done, then when the task is run again it simply uses this data for configuration and off you go. Easy as pie.

I like "DBO"'s specs, very good comments. If this could be formalised somewhere for all to implement it would be great. Just like the IETF RFC's.

Here's to USP, UCP and the easiest OS to use. :cool: 

Cheers

Hilton.

---

### Post by vonpmg on 2006-08-11
Hi
I sent a message to chanders about my vision of tasks.
I think it could be a GREAT step.
I think hgibson is right in saving all the configuration in ~/.task or something similar.
I don't know if XML or some form of INI file, but it is the idea.
I'll try to talk to DBO about tasks, and help him if possible.
We'll need contributions so we have to make a good spec about what is needed and how the people could help.

---

### Post by Note360 on 2006-08-11
I actually made a UEC (Ubuntu Easy Compiler). It is just starting but is another step in making Ubuntu easy. (Then again most people who are compiling want extreme customizable)

---

