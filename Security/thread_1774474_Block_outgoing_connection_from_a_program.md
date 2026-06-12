---
title: "Block outgoing connection from a program"
date: 2011-06-03
forum: Security
---

### Post by insecure hyena on 2011-06-03
Hi guys, I open this thread after an unsuccessful long search over the Web. Essentially what I want is to block the outgoing connection of a program. All I know about this program is its name and so I don't have any information regarding the ports it utilizes or the address it may contact.

P.S: sorry for my bad English and if the thread is bad located in the forum or if it is duplicated.

---

### Post by bodhi.zazen on 2011-06-03
Linux does not really have an application level firewall the way windows does.

What program are you wanting to restrict ?

---

### Post by insecure hyena on 2011-06-03
Firstly thank you for the fast and clear response :).
The application that I want to restrict is a programming tool that connect automatically to the internet whenever it starts.
However as I said the only thing I know about it it's his name.

---

### Post by Lars Noodén on 2011-06-03
apparmor looks like it can block network connections.  If so, then you can set up a profile for that application.

---

### Post by insecure hyena on 2011-06-04
Ok thanks I'm really a novice and I didn't know this apparmor feature. However I tried to create a profile for the application by simply specify deny network. The result is that the application don't start. Should I specify also all the things that are permitted? There's a way to specify only the things denied?

P.S: thanks again to everybody

---

### Post by insecure hyena on 2011-06-04
Up!!! Guys I need help!!! C'mon I only want that a program should not connect to the internet, It's such a basic thing!!! It's like a common firewall!!!

---

### Post by Lars Noodén on 2011-06-04
> **insecure hyena said:**
> Up!!! Guys I need help!!! C'mon I only want that a program should not connect to the internet, It's such a basic thing!!! It's like a common firewall!!!

Common != useful.  It's easy enough to circumvent that kind of restriction by renaming the executable.  

Guess a) If you do *not* have a SMP (symmetric multiprocessing) kernel then you can try looking at the **--cmd-owner** option in the 'owner' module of [iptables](http://linux.die.net/man/8/iptables).

Guess b) Otherwise, you can try making an [apparmor](http://manpages.ubuntu.com/manpages/natty/en/man5/apparmor.d.5.html) profile that blocks net access for that one program.  Look for 'domain' and 'protocol'

---

### Post by insecure hyena on 2011-06-05
Thanks for the fast response :). I tried to create an apparmor profile by specifying to deny network access to the program that I want to lock down but it seems that I must specify not only what to deny but also what to permit and that's really annoying. In fact if I specify only to deny network access the program simply doesn't start.

---

### Post by bodhi.zazen on 2011-06-05
> **insecure hyena said:**
> Thanks for the fast response :). I tried to create an apparmor profile by specifying to deny network access to the program that I want to lock down but it seems that I must specify not only what to deny but also what to permit and that's really annoying. In fact if I specify only to deny network access the program simply doesn't start.

Yes you will have to write an appaprmor profile for your application =)

---

### Post by insecure hyena on 2011-06-05
So that's the only method...really annoying :(...
However thanks to everyone, I'll leave this thread open just to have other comments regarding this argument...maybe someone has a simpler solution.
But ehy, thanks again to everyone!!! ;)

---

