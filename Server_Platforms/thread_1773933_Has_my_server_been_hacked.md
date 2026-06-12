---
title: "Has my server been hacked?"
date: 2011-06-02
forum: Server Platforms
---

### Post by piratesmvp04 on 2011-06-02
Hi everyone, I'm new to these forums and relatively new to Ubuntu. I recently turned an old pentium II Dell desktop into an server by installing Ubuntu Server 11.04. I've only installed Samba for file-sharing with our Windows computers and Jabber 2 for chatting in our home network. The last thing I did before today was creating a new Samba folder for my sister. I then turned off the monitor and left myself logged in.

Today, I turned on the monitor just to see how things were going and I saw a series of entries that I did not enter. I've reentered exactly what I saw on the screen (I'll use 'username' for my username and 'server' for the domain of my server):

username@server:~$
username@server:~$
Display all 1370 possibilities? (y or n)
username@server:~$ .
-bash: .: filename argument required
.: usage: . filename [arguments]
username@server:~$ sudo chown -R jabber:jabber /usr/local/usr/jabberd/log
[sudo] password for username:
Sorry, try again.
[sudo] password for username:
oSorry, try again.
[sudo] password for username:
Sorry, try again.
sudo: 3 incorrect password attempts
username@server:~$

It seems to me that someone was trying to change the ownership of the jabber log file but did not know my password. I do not remember executing this command to change ownership of that file. I do know that I have little siblings that push keys on the keyboard for fun sometimes, but I don't think they could have randomly generated that command. Is it possible that someone from the outside is trying to hack my server? And is it a good idea to always log off when I leave the server unattended?

Thanks.

---

### Post by arrrghhh on 2011-06-02
> **piratesmvp04 said:**
> It seems to me that someone was trying to change the ownership of the jabber log file but did not know my password. I do not remember executing this command to change ownership of that file. I do know that I have little siblings that push keys on the keyboard for fun sometimes, but I don't think they could have randomly generated that command. Is it possible that someone from the outside is trying to hack my server? And is it a good idea to always log off when I leave the server unattended?

That is very odd indeed.

However, you didn't mention SSH or any externally facing services - do you have anything enabled on the server that would have any ports open/listening to the outside world?

Also, if someone did manage to get ssh'd into your server, the lines they typed would **not** show up on the main terminal like that... They would be in a different session.  That was almost definitely typed into the console...

In addition, if someone was trying to hack your server... they wouldn't be changing the ownership of a log file.  Just a hunch ;).

---

### Post by piratesmvp04 on 2011-06-02
Thanks for your reply. I have not set up SSH yet so everything has to be done at the console I would assume. I just remembered that I did install BIND but was unable to configure it to have my windows pcs access the server without typing the ip address. Other than that, I'm not sure. What could I do to ensure there are no open ports?

---

### Post by arrrghhh on 2011-06-02
> **piratesmvp04 said:**
> Thanks for your reply. I have not set up SSH yet so everything has to be done at the console I would assume. I just remembered that I did install BIND but was unable to configure it to have my windows pcs access the server without typing the ip address. Other than that, I'm not sure. What could I do to ensure there are no open ports?

There's several security assessment tools you can use, there's probably some more in-depth ones but [http://www.grc.com/](http://www.grc.com/) has this 'ShieldsUp!' service that will scan your IP for open ports.

Also, there's no need for BIND - I just configure the clients hosts files.  Obviously you have to touch each client machine, but for my environment this made more sense than running a local DNS server ;).

---

### Post by piratesmvp04 on 2011-06-02
> **arrrghhh said:**
> There's several security assessment tools you can use, there's probably some more in-depth ones but [http://www.grc.com/](http://www.grc.com/) has this 'ShieldsUp!' service that will scan your IP for open ports.

Also, there's no need for BIND - I just configure the clients hosts files.  Obviously you have to touch each client machine, but for my environment this made more sense than running a local DNS server ;).
Cool, thanks for the help! I'll check out ShieldsUp! and uninstall the Bind package.

---

### Post by arrrghhh on 2011-06-03
> **piratesmvp04 said:**
> Cool, thanks for the help! I'll check out ShieldsUp! and uninstall the Bind package.

Ah, there was [another thread](http://ubuntuforums.org/showthread.php?t=1770845&page=3) that I remember someone mentioning [OpenVAS](http://www.openvas.org/).  Looks pretty impressive, a quite thorough security scan.

---

### Post by tapi0n on 2011-06-03
This may be a silly thing, but seeing how the commands were displayed on the screen wouldn't that suggest that whoever entered it was physically there?

---

### Post by spynappels on 2011-06-03
> **tapi0n said:**
> This may be a silly thing, but seeing how the commands were displayed on the screen wouldn't that suggest that whoever entered it was physically there?

Not silly at all. The answer would be yes. A remote connection using SSH (which the OP has not installed yet, so I'm talking in generalities here) would open a new terminal and not be seen on the screen.

I cannot actually think of any occasion where this would not be the case except where the remote connection uses VNC or Teamviewer or something, and the OP specifically said he is using Server Edition, so I don't think that could even be the case.

Closet Linux Geek in the house maybe?

---

### Post by piratesmvp04 on 2011-06-03
> **arrrghhh said:**
> Ah, there was [another thread](http://ubuntuforums.org/showthread.php?t=1770845&page=3) that I remember someone mentioning [OpenVAS](http://www.openvas.org/).  Looks pretty impressive, a quite thorough security scan.
Thanks!

[quote="tapi0n"]This may be a silly thing, but seeing how the commands were displayed on the screen wouldn't that suggest that whoever entered it was physically there?[/quote]
lol, yeah but I don't know who, plus I wrote the password on a notepad next to the server, so whoever did this was pretty dumb.

---

### Post by tapi0n on 2011-06-03
> **spynappels said:**
> 
I cannot actually think of any occasion where this would not be the case except where the remote connection uses **VNC or Teamviewer** or something, and the OP specifically said he is using Server Edition, so I don't think that could even be the case.
[B]
Closet Linux Geek in the house maybe?[/B]

I was thinking the exact same. And linux geeks in the house can easily be taken care of by opening some windows (get it, har har)

> plus I wrote the **password on a notepad next to the server**, so whoever did this was pretty dumb

tut tut, that's like the last thing you should do imho

---

### Post by piratesmvp04 on 2011-06-03
> **tapi0n said:**
> tut tut, that's like the last thing you should do imho
Yeah probably. But the rest of my family won't remember the password if I don't write it down. ;)

---

### Post by arrrghhh on 2011-06-03
> **piratesmvp04 said:**
> Yeah probably. But the rest of my family won't remember the password if I don't write it down. ;)

What do they need to know the password for?

Not to be rude, but seriously.  So long as they can access the services that the server provides, who in your house (other than you) actually needs to login to the beast?

No one in my household has the root password to the server, yet happily utilize the services running on it daily :D.

---

### Post by tapi0n on 2011-06-03
> **arrrghhh said:**
> What do they need to know the password for?

Not to be rude, but seriously.  So long as they can access the services that the server provides, who in your house (other than you) actually needs to login to the beast?

No one in my household has the root password to the server, yet happily utilize the services running on it daily :D.

totally agree on this. And even if you plan to keep the password on a piece of paper (which isn't per se  bad) keep it far from the physical server, and don't make any reference to what it could be used for.

> login to the beastI'm gonna rename my machine to this. Sounded so awesome and pure epic when reading it aloud. "Hold on guys, I'm going to log in on the beast". nice ^^

---

### Post by piratesmvp04 on 2011-06-03
> **arrrghhh said:**
> What do they need to know the password for?

Not to be rude, but seriously.  So long as they can access the services that the server provides, who in your house (other than you) actually needs to login to the beast?

No one in my household has the root password to the server, yet happily utilize the services running on it daily :D.

Well, I'll be moving out for college in a few months, so theyll be the ones managing it when I'm gone.

---

### Post by arrrghhh on 2011-06-03
> **piratesmvp04 said:**
> Well, I'll be moving out for college in a few months, so theyll be the ones managing it when I'm gone.

Ah... fair enough.  Hopefully there's someone capable of doing so... I know if I left my server no one would admin it.  I'd still have to fix things myself thru ssh :p.

---

### Post by piratesmvp04 on 2011-06-03
> **arrrghhh said:**
> Ah... fair enough.  Hopefully there's someone capable of doing so... I know if I left my server no one would admin it.  I'd still have to fix things myself thru ssh :p.

Haha, I know. I've considered installing SSH, but I dont want to increase the risk of hacking since I'm the only one in the family with enough knowledge to try to fix it could. I'm trying to teach my brother how to manage the server by having him install ubuntu server on virtualbox, so we'll see how that goes.

---

### Post by lfacchinelli on 2011-06-03
> **piratesmvp04 said:**
> 

username@server:~$
username@server:~$
Display all 1370 possibilities? (y or n)
username@server:~$ .
-bash: .: filename argument required
.: usage: . filename [arguments]
username@server:~$ sudo chown -R jabber:jabber /usr/local/usr/jabberd/log
[sudo] password for username:
Sorry, try again.
[sudo] password for username:
oSorry, try again.
[sudo] password for username:
Sorry, try again.
sudo: 3 incorrect password attempts
username@server:~$

It seems to me that someone was trying to change the ownership of the jabber log file but did not know my password. I do not remember executing this command to change ownership of that file. I do know that I have little siblings that push keys on the keyboard for fun sometimes, but I don't think they could have randomly generated that command. Is it possible that someone from the outside is trying to hack my server? And is it a good idea to always log off when I leave the server unattended?

Thanks.

Hi piratesmvp04
Yeah, always log off, no mather if you're away for 2 min or 20 hours. always LOG OFF
secondly, it's weird, if someone hacks you, why they want to change jabber's log owner?
Otherwhise, no SSH service, so ....
Probably one of your siblings push up key (yeah, keyboard) several times and bash's history shows that comand (probably when you installed jabber execute that command and dont remember)

Just for recomendation, change default SSH port when you install it.. it's a silly thing but scanports always try against defaults ports

---

### Post by piratesmvp04 on 2011-06-03
> **lfacchinelli said:**
> Hi piratesmvp04
Yeah, always log off, no mather if you're away for 2 min or 20 hours. always LOG OFF
secondly, it's weird, if someone hacks you, why they want to change jabber's log owner?
Otherwhise, no SSH service, so ....
Probably one of your siblings push up key (yeah, keyboard) several times and bash's history shows that comand (probably when you installed jabber execute that command and dont remember)

Just for recomendation, change default SSH port when you install it.. it's a silly thing but scanports always try against defaults ports

Thanks for the tips!

---

