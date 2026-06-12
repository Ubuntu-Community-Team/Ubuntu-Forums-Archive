---
title: "Where to start?"
date: 2012-01-26
forum: Security
---

### Post by jpdeaton on 2012-01-26
I am trying to lock down my linux desktop. I've only been using linux a couple months and a lot of the information out there is confusing to me. Theres so much software I don't even know where to'start. Currently I have iptables setup, rkhunter, chkconfig, clamav, tiger plus startup services somewhat configured; I don't know about any of the run levels though. I've read all the tutorials but don't really understand them... theres so much information I really just need to know where to start rather than reading a bunch of tutorials and not understanding the concepts. I really just want to know where I should start. Is there a distro that would be better suited for me other than ubuntu?  Thanks

---

### Post by tubbygweilo on 2012-01-26
Ubuntu is considered quite safe and secure right out of the box and as long as you install code from the repos is should remain so. If sharing your computer with others then as soon as someone else has physical access then to be honest all bets are off.

jpdeaton, can I ask have you noticed anything that would make you think your installation is not right or not secure? If so then keep asking more questions and members of this forum will attempt to offer advice that may well put your mind at rest.

---

### Post by Lars Noodén on 2012-01-26
> **jpdeaton said:**
> I really just want to know where I should start.

If you're talking about a desktop, then one of the more relevant places to start would be with AppArmor:

[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)
[https://wiki.ubuntu.com/DebuggingApparmor](https://wiki.ubuntu.com/DebuggingApparmor)

---

### Post by sudodus on 2012-01-26
It is hard to give anything but very general advice unless you give us more information:

- How are you using your computer (play, communication, work, money ...)?
- What are you afraid of (losing data, someone reading your data, someone making your data corrupt ...)?
- Or are you just interested and want to know more behind the curtains?

Did you read the following link? (but it is not enough for securing a server) 

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by HermanAB on 2012-01-26
Dude, just relax and enjoy your Linux system.  You don't really have to do anything to make it more secure.  

The trick is not to make it LESS secure by installing stuff you don't understand.  So always read up on whatever it is you want to install, before you do so and most importantly, use LOOOOOOONG passwords.

---

### Post by JawsThemeSwimming428 on 2012-01-26
Ubuntu is definitely the best place to start. One of the main advantages is the huge community of people on the forums to help you out.

---

### Post by bodhi.zazen on 2012-01-26
Start with the stickies in the top of this section.

---

### Post by jpdeaton on 2012-01-26
> - How are you using your computer (play, communication, work, money ..It's for personal use

> - What are you afraid of (losing data, someone reading your data, someone making your data corrupt ...)?I'm not really worried about protecting my data as it is all backed up. 

> - Or are you just interested and want to know more behind the curtains? Yea, I am also just interested.  What I really want to learn about is how protect against eavedropping, log attempted logins, and keep my O.S. as minimal as possible, I don't want all these services running related to stuff other than the bare essentials. There is a windows pc (i use wireless) plugged into the router that has a bunch of viruses.

>  Did you read the following link? (but it is not enough for securing a server) 

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)Yea I did, I just don't know where to start because there's so much to learn. I've spent hours searching the forums. I mean there's Ossec, snort, wireshark, apparmor, service run levels, etc; I am trying to take this one step at a time



Also, how would I go about running a custom install script after installing a minimum version of ubuntu?
And finally, would linux arch be a good choice or is it too complicated.


> Ubuntu is considered quite safe and secure right out of the box and as  long as you install code from the repos is should remain so. If sharing  your computer with others then as soon as someone else has physical  access then to be honest all bets are off.

jpdeaton, can I ask have you noticed anything that would make you think  your installation is not right or not secure? If so then keep asking  more questions and members of this forum will attempt to offer advice  that may well put your mind at rest. I think my wireless network is compromised.

---

### Post by sudodus on 2012-01-26
I would suggest that you start by

- making your internet browsing safer by adding NoScript to Firefox

- looking after your wireless network (firewall settings, encryption method and passphrase). A good way is to start a new thread about your fear that it is compromised, for example with the title "I fear my wireless network is compromised". You will almost certainly get good advice from at least one expert in the field, that is helping people at the Ubuntu Forums. Although we are all volunteers, the experts know very much more than I about security.

A (temporary) alternative is to use a wired local network.

---

