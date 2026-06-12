---
title: "UBUNTU as PDC"
date: 2005-03-18
forum: Server Platforms
---

### Post by Nachtwind on 2005-03-18
First of all I say Hi to everyone here and say also Thanks to the UBUNTU Team for making the best Distro i have ever used =)


Well, now to my small questions, i hope they arent answered yet, but i tried to look for them.

Today we decided within our small community (school internal service) to switch from plain Windows 2000 Lokal 2 User Systems (1 Admin, 1 User with almost same rights due to some people who exploited the trust of one of our admins...) to a far more secure (and interestering) system. 20 Workstations with either Win2k and Ubuntu and one biiig (hehe ;)) Server that runs Ubuntu as PDC.

Now there are some small things I would need to know before getting to work.

I know that i need Samba as the PDC, but i dont know some specific things about it, which i didnt even find in a book about it, so how can i permit certain groups the amount of space each user is allowed to use (for example the group members of teachers may have 100MB, the group members of the pupils has 50MB...) 
I think i have to use "quota" - but i dont know how to define the maximum Inode numbers and cant find something useful for calculation. 
Another thing is - how much space do you think needs to be calculated for Mozilla (Firefox & Thunderbird) for their profiles to make sure that each user has at about 50MB space available...

So, i hope i am not that annoying with my questions, but these are things i couldnt find myself till now...

Nachtwind

---

### Post by fjleal on 2005-03-20
[QUOTE=Nachtwind]
I know that i need Samba as the PDC, but i dont know some specific things about it, which i didnt even find in a book about it, so how can i permit certain groups the amount of space each user is allowed to use (for example the group members of teachers may have 100MB, the group members of the pupils has 50MB...) 
I think i have to use "quota" - but i dont know how to define the maximum Inode numbers and cant find something useful for calculation. 
[/QUOTE]
Hi, Nachtwind. You will need to place your /home in a separate partition. Then enable user and group quotas for that partition. When I had this problem, I did a search for "quota" on [http://www.tlpd.org](http://www.tlpd.org), and followed the articles there.

Hope it helps... ;)

---

### Post by Nachtwind on 2005-03-21
[QUOTE=fjleal]Hi, Nachtwind. You will need to place your /home in a separate partition. Then enable user and group quotas for that partition. When I had this problem, I did a search for "quota" on [http://www.tlpd.org](http://www.tlpd.org), and followed the articles there.

Hope it helps... ;)[/QUOTE]

This link does no longer seem to be valid, but thank you though  :-)

---

### Post by fjleal on 2005-03-21
[QUOTE=Nachtwind]This link does no longer seem to be valid, but thank you though  :-)[/QUOTE]
Sorry, [http://www.tldp.org](http://www.tldp.org)  #-o

---

