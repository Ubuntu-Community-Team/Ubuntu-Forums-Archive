---
title: "Adduser command not working!"
date: 2008-01-08
forum: Server Platforms
---

### Post by BigBoned on 2008-01-08
Hi,

I am fairly new with Ubuntu and i must say it is great.

ALTHOUGH, today I did a reformat on one of my harddisks to reinstall Ubuntu. I am running version 7.10 on i386.

When I login to my root account with PuTTy via Secure shell, everything works and it display's the bash command line.

So I try "adduser uname", set the password, information, and it seems to work fine.
Then I will SSH into my Ubuntu computer, attempt to login with my new UserName and password, but it Fails! :(
Right after I type in the password, PuTTy.exe give's me an error saying "Remote host has closed the connection"

It doesnt do this with root but does with ANY user I try to add! :/

What in the world can this be? I even reinstalled it 3 times, fresh, and still no go...

Please Help!!!

Thanks!!](*,)

---

### Post by jflaker on 2008-01-08
You need to be root to add a users  Try appending sudo infront of the command.

---

### Post by BigBoned on 2008-01-08
I am root when I add them. It has no problem adding the user, but it won't let my login via SSH with putty.

---

