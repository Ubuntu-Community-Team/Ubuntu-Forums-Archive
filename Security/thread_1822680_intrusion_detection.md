---
title: "intrusion detection"
date: 2011-08-10
forum: Security
---

### Post by macminiuser on 2011-08-10
Hi all
Hey I have a question.Is there anything i can install on ubuntu 
that will popup and tell me when someone is trying to screw with my home network? I was just curious
Thx Jim

---

### Post by Lars Noodén on 2011-08-11
You might want to take a look at Snort.

---

### Post by bodhi.zazen on 2011-08-11
> **macminiuser said:**
> Hi all
Hey I have a question.Is there anything i can install on ubuntu 
that will popup and tell me when someone is trying to screw with my home network? I was just curious
Thx Jim

What do you want exactly in such a popup ? If you are connected to the internet, someone is trying to crack you.

The question is what to do about it. Read the security sticky ;)

Some people try to block IP addresses, but it does not help much as the attacks are scripted and ip addresses are easy enough to change or spoof.

---

### Post by nastynate1219 on 2011-09-04
I just downloaded it from the software center I wanted to know how do I use it and configure it.


I looked at bodhi.zazen thread at: [http://ubuntuforums.org/showthread.php?t=919472&highlight=ossec+hids](http://ubuntuforums.org/showthread.php?t=919472&highlight=ossec+hids)

But know offense I think that info is outdated because certain links don't work and at the time, the audience that it was intended for probably used older versions of ubuntu

I am using 11.04  

so what's up can anybody help??????

---

### Post by bodhi.zazen on 2011-09-05
> **nastynate1219 said:**
> I just downloaded it from the software center I wanted to know how do I use it and configure it.


I looked at bodhi.zazen thread at: [http://ubuntuforums.org/showthread.php?t=919472&highlight=ossec+hids](http://ubuntuforums.org/showthread.php?t=919472&highlight=ossec+hids)

But know offense I think that info is outdated because certain links don't work and at the time, the audience that it was intended for probably used older versions of ubuntu

I am using 11.04  

so what's up can anybody help??????

If you found a dead link or links, send me a PM and I will try to update them.

What problem did you have when you tried to install OSSEC ?

---

### Post by nastynate1219 on 2011-09-05
nate@nate-R530-R730-R540:~$ tar xzvf ossec-hids-1.6.tar.gz
tar (child): ossec-hids-1.6.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

---

### Post by bodhi.zazen on 2011-09-05
Well you are not in the proper directory. Where did you download the tar ball to ? ~/Desktop ? ~/Downloads ???

---

### Post by nastynate1219 on 2011-09-05
I went to terminal and type in the code command you had in that one thread from 2008

Ossec hids command code to install in terminal and i am using a laptop was that thread intended for desktop users????

---

### Post by bodhi.zazen on 2011-09-05
> **nastynate1219 said:**
> I went to terminal and type in the code command you had in that one thread from 2008

Ossec hids command code to install in terminal and i am using a laptop was that thread intended for desktop users????

I suggest you are going to struggle with this task as :

1. You do not know your way around the terminal.

2. You do not seem to know where you downloaded the tar ball to.

3. You did not answer my question.

It has nothing to do with when the tutorial was written if you do not yet have the experience.

Start with the security sticky , then take a look at this :

[http://linuxcommand.org/](http://linuxcommand.org/)
I suggest you relax , learn the basics, and then come back to this task.

---

### Post by nastynate1219 on 2011-09-05
I apologize for my lack of experience in operating ubuntu. I wasnt with ubuntu in the begininng of 04, frankly I thought microsoft would shut it down.
 
I just convert a week ago, Ive been using microsoft all my life and now i jumped into a whole new culture by itself with its own language and stlye 
 
so please cut me some slack
 
i thank you for the info 
i will read the info from [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) along with the snort manual that I somehow managed to obtain 
 
once i am done I will come back  and answer your question so you can answer my question
 
I need to know this stuff, so this conversation isnt over.
 
OH!!!!!! what security sticky are you talking about???? so I can read that too?????:D

---

### Post by bodhi.zazen on 2011-09-05
> **nastynate1219 said:**
> I apologize for my lack of experience in operating ubuntu. I wasnt with ubuntu in the begininng of 04, frankly I thought microsoft would shut it down.
 
I just convert a week ago, Ive been using microsoft all my life and now i jumped into a whole new culture by itself with its own language and stlye 
 
so please cut me some slack
 
i thank you for the info 
i will read the info from [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) along with the snort manual that I somehow managed to obtain 
 
once i am done I will come back  and answer your question so you can answer my question
 
I need to know this stuff, so this conversation isnt over.
 
OH!!!!!! what security sticky are you talking about???? so I can read that too?????:D

The sticky at the top of these fourms 

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

You really do not need snort or OSSEC for peace of mind. Both these tools are moderately advanced which is why you will need to gain some experience with the basics first.

---

### Post by cariboo on 2011-09-06
> **nastynate1219 said:**
> I apologize for my lack of experience in operating ubuntu. I wasnt with ubuntu in the begininng of 04, frankly I thought microsoft would shut it down.
 
I just convert a week ago, Ive been using microsoft all my life and now i jumped into a whole new culture by itself with its own language and stlye 
 
so please cut me some slack
 
i thank you for the info 
i will read the info from [http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php) along with the snort manual that I somehow managed to obtain 
 
once i am done I will come back  and answer your question so you can answer my question
 
I need to know this stuff, so this conversation isnt over.
 
OH!!!!!! what security sticky are you talking about???? so I can read that too?????:D

Scroll to the top of the security discussion page, there are several links to bodhi_zazen's tutorials.

---

