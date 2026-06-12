---
title: "I can connect with putty put name in but password is not working?"
date: 2011-01-22
forum: Server Platforms
---

### Post by Bushcraft Bill on 2011-01-22
I can log in when using the keyboard from the server no problems but when I try and log on from my laptop this morning using putty I can connect type in my user name but when I put in my password it says access denied now I also can not FTP and webmin does not connect to the server but I can get to the web pages no problem with a browser so can this be fixed or do I have to start from scratch again to get me logged in with putty and webmin somehow the password is not working in ssh? I can ping server no problem too...

---

### Post by Bushcraft Bill on 2011-01-22
I can connect to the server with putty but can not log in what could have changed in the last few days since the last time I logged in with putty?

1- can connect with putty but does not let me log in with my password
2- can no longer log in with ftp software
3- I can go to web pages on server with browser
4- can ping server successfully
5- I can log into the server itself with its keybaord no prob
6- webmin does not work think its the password thing too

any idea what I can try to gain back control or will I end up reinstalling server software from scratch?

---

### Post by Bushcraft Bill on 2011-01-22
what could have changed as it was all working before I could use putty on my laptop to log into the server now I cant I just don't understand it...

---

### Post by djeikyb on 2011-01-22
First off, bumping your thread annoys people and doesn't solve your problem. I know it's frustrating waiting hours for a response. Anyway.

(1) How does putty behave when you try to ssh to the server? Does it actually prompt you for a username and password? Does it seem to connect, but just leave a blank screen?

(2) It's been a while since I've used putty, but you should be able to get the equivalent of ssh's verbose logging. I think enabling ssh packet logging will get what I want to see. Follow the link to the manual, turn on the logging, and post or attach it here.
[http://the.earth.li/~sgtatham/putty/0.52/htmldoc/Chapter4.html#4.2](http://the.earth.li/~sgtatham/putty/0.52/htmldoc/Chapter4.html#4.2)

(3) What operating system are you working with? What version is it? Do you keep it updated manually, automatically, or not at all?

---

### Post by Bushcraft Bill on 2011-01-22
1-it behaves perfectly to the server and it prompts me for my username I put that in then it asks me for my password then it says Access Denied and 
gives me the password prompt again I can attempt the password 5 times then putty says server sent shut down command and then putty shuts down....

2-reading

3-server is using ubuntu server 10.04 this one I manually update since I only have the server up periodically. I did not do an update but when things were not working I updated today but nothing changed/did not fix my problem...
 
my laptop is running ubuntu 10.10 this is set to auto update


> **djeikyb said:**
> First off, bumping your thread annoys people and doesn't solve your problem. I know it's frustrating waiting hours for a response. Anyway.

(1) How does putty behave when you try to ssh to the server? Does it actually prompt you for a username and password? Does it seem to connect, but just leave a blank screen?

(2) It's been a while since I've used putty, but you should be able to get the equivalent of ssh's verbose logging. I think enabling ssh packet logging will get what I want to see. Follow the link to the manual, turn on the logging, and post or attach it here.
[http://the.earth.li/~sgtatham/putty/0.52/htmldoc/Chapter4.html#4.2](http://the.earth.li/~sgtatham/putty/0.52/htmldoc/Chapter4.html#4.2)

(3) What operating system are you working with? What version is it? Do you keep it updated manually, automatically, or not at all?

---

### Post by djeikyb on 2011-01-22
Ok. Look forward to the log. Also, I know this is stupid, but you've double checked caps lock, and your laptop doesn't have any funky keymap, right? I only mention this because once it turned out I was accidentally hitting the switch-to-kanji button..

---

### Post by Bushcraft Bill on 2011-01-22
ya I checked all that. no funky keymap. just wondering can the ssh password get changed in any way or curupt? and can I replace the ssh stuff on the server could that work? if I reinstall it would it ask me for a password for ssh or is that just locked in with my server login password...
I cant find a reset ssh password command... I have rebooted both puters a few times now still no worky....


> **djeikyb said:**
> Ok. Look forward to the log. Also, I know this is stupid, but you've double checked caps lock, and your laptop doesn't have any funky keymap, right? I only mention this because once it turned out I was accidentally hitting the switch-to-kanji button..

---

### Post by djeikyb on 2011-01-22
Can you get that putty log with the ssh packet logging enabled? It should have the answers to your problem.

Also, don't take this as me being a jerk, but as a matter of etiquette, don't ever quote posts below your response. It's redundant. If you must quote, only quote the relevant parts. Put the quote first and write your response underneath. This applies to emails too. Scratch that. This applies to emails **especially**.

> A: Because it messes up the order in which people normally read text.
Q: Why is top-posting such a bad thing?
A: Top-posting.
Q: What is the most annoying thing in e-mail?

---

### Post by djeikyb on 2011-01-24
Oh, and no, the ssh password can't be changed because there is no ssh password. SSH is just a program that creates a secure, private tunnel between two computers. The login is based either on your public key or system login. Thus, if you can login to the system with a username and password, you ought to be able to ssh with those same credentials. Of course, that user could be blocked from using ssh, or from logging in via certain ip addresses.

Any luck with those logs?

---

