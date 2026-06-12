---
title: "Logging in as root??"
date: 2009-10-27
forum: Security
---

### Post by pavsid on 2009-10-27
Hi, i hope someone can help.

I have an Ubuntu Server which i administer via SSH and tonight i stupidly moved myself to another group without keeping the previous group.  As a result i can't run any sudo commands as all i get is "pav is not in the sudoers file. This incident will be reported."

Is there anyway to log in as root so that i can add myself back into the necessary group???

---

### Post by sailthesea on 2009-10-27
These forums forbid discussing this topic , but if you perhaps try elsewhere you will find out (I think I can tell you that)
 Take GREAT care if you use commands in /root

---

### Post by bribera on 2009-10-27
> **sailthesea said:**
> These forums forbid discussing this topic

Really? Is that just an unstated-but-still-enforced policy, or I am I missing something when I read the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")?

---

### Post by sailthesea on 2009-10-27
> **bribera said:**
> Really? Is that just an unstated-but-still-enforced policy, or I am I missing something when I read the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")?

 Pretty much an unwritten rule
 With good reason too;)

---

### Post by bribera on 2009-10-27
I might agree that the *rule* is good, but not writing it down simply sets people up to fail. :(

---

### Post by sailthesea on 2009-10-27
> **bribera said:**
> I might agree that the *rule* is good, but not writing it down simply sets people up to fail. :(

 True 
But writing it down simply sets up people to ask "why?" and try to bend the rules. 
 Good point though:D

---

### Post by cariboo on 2009-10-28
Actually the guidelines aren't in the [Code of Conduct]("http://ubuntuforums.org/index.php?page=policy"), but the are located in a [stickie]("http:///ubuntuforums.org/showthread.php?t=716201") at the top of this forum.

There is nothing that says that you can't tell someone how to enable the root account, as long as you explain the dangers of running as root.

I don't think it will help the op in this case as he is administering his server using ssh, sudo won't work in this case. The only way I can see him being able to repair the problem is by physically accessing the server.

---

### Post by lisati on 2009-10-28
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cariboo on 2009-10-28
lisati beat me to it with his link, but I haven't found any reason to enable the root account that I can't do using **sudo -i**

---

### Post by pavsid on 2009-10-28
> **cariboo907 said:**
> 
I don't think it will help the op in this case as he is administering his server using ssh, sudo won't work in this case. The only way I can see him being able to repair the problem is by physically accessing the server.

Woah, sorry to have caused such a stir!

i was hoping there was another way other than physically accessing the server - i presume if i have to go down this route then i'd boot into recovery mode and edit the sudoers file?

Thanks lisati for the link, but i can't issue any sudo commands as i'm accessing via ssh! Doh!

If i was to ask the same question on 'another forum' do you think i'll get an easyish way to do it without having to physically access the server, or is it near impossible given my situation?

thanks

---

### Post by QLee on 2009-10-28
[QUOTE=pavsid]
I have an Ubuntu Server which i administer via SSH and tonight i stupidly moved myself to another group without keeping the previous group. [/QUOTE]

What exact code did you use to do that?

---

### Post by piankhi on 2009-10-28
> **QLee said:**
> What exact code did you use to do that?

good question :D

---

### Post by wojox on 2009-10-28
> **pavsid said:**
> Woah, sorry to have caused such a stir!

i was hoping there was another way other than physically accessing the server - i presume if i have to go down this route then i'd boot into recovery mode and edit the sudoers file?

Thanks lisati for the link, but i can't issue any sudo commands as i'm accessing via ssh! Doh!

If i was to ask the same question on 'another forum' do you think i'll get an easyish way to do it without having to physically access the server, or is it near impossible given my situation?

thanks

Doesn't matter what forum you go to they will all say the same thing: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by pavsid on 2009-10-28
> **QLee said:**
> What exact code did you use to do that?

i used...

sudo usermod -G group1,group2 pav

where my original group was neither group1 nor group2

Thing is though, i seem to remember still being able to run sudo commands until i rebooted - but can't be sure...

---

### Post by pavsid on 2009-10-28
> **wojox said:**
> Doesn't matter what forum you go to they will all say the same thing: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Thanks for the link wojox, just what i needed...

---

### Post by CharlesA on 2009-10-28
> **pavsid said:**
> i used...

sudo usermod -G group1,group2 pav

where my original group was neither group1 nor group2

Thing is though, i seem to remember still being able to run sudo commands until i rebooted - but can't be sure...

Yeah, I did that a while ago too, totally locked myself out, but at least I had physical access to the machine. Recovery mode is very handy.

---

