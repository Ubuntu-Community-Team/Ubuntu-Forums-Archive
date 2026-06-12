---
title: "young beginner looking for ways to start"
date: 2009-08-29
forum: The Cafe
---

### Post by billboule on 2009-08-29
Hi !

I´m right now with my cousin from southern Peru, he is 14 and has the dream of being a system administrator... For now, he is helping at the administration in a cybercafe,  running on Windows. I tried to impulse the "free spirit" and we are now writing this post on an "Ubuntu Live". My question is : how should he start? Learning some programming ? Which language?

What would you recommand to him?

Thanks for any ideas,

Billboule

---

### Post by bodyharvester on 2009-08-29
programming language of choice is python to me, easier to learn, theres a good book i learned from, it teaches you how to program your own games, but its a good way to learn the language [http://pythonbook.coffeeghost.net/](http://pythonbook.coffeeghost.net/)

good luck

---

### Post by Copernicus1234 on 2009-08-29
If he wants to be a system administrator for Linux, he needs to know how to write bash scripts, how file permissions work and a lot of other things.

But he might as well start with learning Python. Its a great language and a lot of fun.

---

### Post by madjr on 2009-08-29
A+ and linux+ certification

---

### Post by Frak on 2009-08-29
> **madjr said:**
> A+ and linux+ certification
+1

These have the bare basics of what you need to get started.

---

### Post by koenn on 2009-08-29
> **billboule said:**
> Hi !

I´m right now with my cousin from southern Peru, he is 14 and has the dream of being a system administrator... For now, he is helping at the administration in a cybercafe,  running on Windows. I tried to impulse the "free spirit" and we are now writing this post on an "Ubuntu Live". My question is : how should he start? Learning some programming ? Which language?


Knowing a programming language is not your first priority if you want to be a sysadmin. It does help if you can automate stuff with scripting (bash mostly, maybe python, ... perl used to be popular as well)
but in any case, you"d use it to automate sysadmin tasks, so that's where your priorities are.

knowing how networks work helps, because that's how your servers and whatever's on it, reach the users.

Your main task is to have servers running that provide data or applications to the users (think file servers, web servers/web applications, databases, mail, ... ). you'll also have to know how to install a server OS. You'll have to setup, backup, monitor and secure these servers, applications, data, ... you'll have to manage user accounts. You need to have a decent plan how you can get all of that up and running again in case of a crash or a small to medium-sized disaster. 

It's not something you can easily learn without formal training, but you can start by setting up a home network with several clients (PC's) and several servers, and try to work out a solution for all of the above.

---

### Post by bodyharvester on 2009-08-29
doesnt dragos204 have a server running using a netbook or something? im sure i read that somewhere

---

### Post by jaxxstorm on 2009-08-29
Becoming a Linux sysadmin requires a whole base of skills.

[LIST][*]Bash and other shell scripting[*]File permission control[*]knowledge of services like LDAP, BIND DNS server, Samba, Kerberos and many more[*]Some networking and hardware expertise[*]Virtualization using Xen or VMWare[*]Process and service control
[/LIST]

Any many, many other things!

It's a long, hard road - but starting young always help. I'd recommend moving his main machine to Ubuntu or other user friendly distro and learning simple command line commands like mv, cp, chmod, chown and others. Then start with some bash scripting and some python coding, and from there the sky is the limit. At some point he'll need to move from Ubuntu to another Redhat based distro to become familiar with the way it works, as there are some subtle differences between Ubuntu and Redhat based distros.

Good luck

---

### Post by MaxIBoy on 2009-08-29
> **bodyharvester said:**
> doesnt dragos204 have a server running using a netbook or something? im sure i read that somewhereSomeone SSH'd in and ran a fork bomb. Then he tried to "harden" it and wound up wrecking his permissions. Last I heard he was reinstalling Arch on it.

I've had an Ubuntu home print/backup server running almost continuously for most of a year. My secret: I DON'T GIVE OUT MY IP ADDRESS AND ASK PEOPLE TO SSH INTO IT! Just thought I'd share that.

---

### Post by billboule on 2009-09-02
Thanks guys for all the infos and remarks.... Let´s see how it will work out for him in the next years...

---

### Post by madjr on 2009-09-02
check out the latest fullcircle mag (and other releases), should get him started

[IMG]http://fullcirclemagazine.org/wp-content/uploads/2009/08/fcm28-300x211.jpg[/IMG]

[http://ubuntuforums.org/showthread.php?t=1253541](http://ubuntuforums.org/showthread.php?t=1253541)

---

