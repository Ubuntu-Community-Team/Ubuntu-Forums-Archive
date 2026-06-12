---
title: "Firewall based on the user and the programs they wish to use"
date: 2005-11-19
forum: Server Platforms
---

### Post by incon on 2005-11-19
Hello

Setting up a terminal server 

I wish to block apps like you do with zone alarm on windows
I have a port based firewall setup and i want to extend this with rules based on the user and the program they wish to use

Example I want some users to have access to the local network (intranet) only and others I want to allow internet access with only firefox gaim and a few other ramdom apps that a proxy blocked base setup will not work. Also the program must be checksumed so the user cant mod the app to do other things. Some of the users will have full internet access.

How would I go about setting something like this up?

Thanking you in advance
incon

---

### Post by garyng on 2005-11-20
[QUOTE=incon]Hello

Setting up a terminal server 

I wish to block apps like you do with zone alarm on windows
I have a port based firewall setup and i want to extend this with rules based on the user and the program they wish to use

Example I want some users to have access to the local network (intranet) only and others I want to allow internet access with only firefox gaim and a few other ramdom apps that a proxy blocked base setup will not work. Also the program must be checksumed so the user cant mod the app to do other things. Some of the users will have full internet access.

How would I go about setting something like this up?

Thanking you in advance
incon[/QUOTE]

The closest I can think of is this:

[http://www.nufw.org/index.php3?lang=en](http://www.nufw.org/index.php3?lang=en)

But I don't think you can get as fine grain as app level control as that needs corporation from the app(or some kind of control programs at the client that inventory these specific apps).

---

### Post by grendelkhan on 2005-11-20
You could create a user group that contains all the net access people, make that the group on the executables for stuff like firefox and then set the permissions to be 750.

---

### Post by LordHunter317 on 2005-11-20
You can use the owner module and egress filtering, but it's far smarter to prevent users you don't want on the Internet from running the applications in the first place.

---

