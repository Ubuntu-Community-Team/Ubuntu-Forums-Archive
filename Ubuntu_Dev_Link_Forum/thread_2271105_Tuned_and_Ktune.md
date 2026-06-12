---
title: "Tuned and Ktune"
date: 2015-03-27
forum: Ubuntu Dev Link Forum
---

### Post by Kenneth_Benson on 2015-03-27
I've been looking at the tuned and ktune utilities. For those who have not heard of them, these are a pair of services that tune the kernel on a dynamic basis. Tuned has several profiles that can be chosen
depending on the type of usage the machine is setup for, ie. desktop, laptop, low volume server, high volume server, etc. Ktune adjusts network buffers and disk params depending on active usage. They
 were originally designed for Fedora, however I'm trying to get them to work with the various Ubuntus. Before I go thru the reading/training to do deb packaging, I want to know if anyone is interested
in these two?

---

### Post by v3.xx on 2015-03-27
Yes, I would be interested in desktop and laptop (not using hardware stack).

---

### Post by Kenneth_Benson on 2015-03-30
Alright, I'll get to working on it. Be aware this is my first package project so it might take me a bit to get it right.

---

### Post by Kenneth_Benson on 2015-04-02
After digging further, I've discovered that tuned is a redo plus of ktune. Therefore tuned is what I will be working on and (hopefully) packaging. I need to ask the author if I have his ok to port it to Ubuntu.

---

### Post by Kenneth_Benson on 2015-04-04
Just received an email from the tuned author with permission. I'll get started on the work.

---

### Post by v3.xx on 2015-04-04
Ok

---

### Post by Kenneth_Benson on 2015-04-28
I've got the tuned daemon running on my 14.04.1 Desktop. Being as it's a virtualbox guest there are some things that error until tuned decides not to try that
that anymore; specifically HDPARMs. It does recognize that it's a virtual guest and automatically chose the correct profile. I'm having some minor issues with 
tuned-adm at the moment, but it seems to be going well. As soon as I get those issues fixed, I need to talk to someone about being my mentor to get it 
packaged and uploaded for testing. The upstream author likes what I've done so far as I've kept him posted. As soon as I can (still reading all the 
policy/developer/maintainer manuals :rolleyes: ), I'll get online and start the process.

---

