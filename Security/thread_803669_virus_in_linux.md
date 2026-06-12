---
title: "virus in linux"
date: 2008-05-22
forum: Security
---

### Post by itd on 2008-05-22
Ok, first of all, when it comes to linux, i am almost a total noob.
For a report i have to write about viruses in linux. That is not realy a problem because there are enough sources on the internet.
The thing is, that for additional points i have to write a virus for linux (I do not know what my professor was thinking when he gave that task). Nothing fancy, just something, that can be at least called a virus. There is almost nothing on the internet about that. Can somebody at least show me the way or give me a hint how to do that? The system, i should test the virus, has installed Ubuntu 6.10 . But there is a chance that i have to run the virus on my computer, which has installed Kubuntu 7.10.
Thanks in advance and sorry if i didn't write some words correct, english is not my first language.

---

### Post by eragon100 on 2008-05-22
This frigging' idiot would have you make a virus and run it on your own computer!? :confused:

---

### Post by yaztromo on 2008-05-22
I think he might be happy with some kind of time bomb shell script run from cron that deletes a load of stuff.

You could also try and program something in python/C that sits in memory and flashes up an annoying message now and again (had lots of Amiga viruses like that).

You're going to need an installation you don't mind destroying of course :D

Also have a look at this: [http://www.milw0rm.com/papers/188](http://www.milw0rm.com/papers/188)

---

### Post by amingv on 2008-05-22
You can run it in a VM so you don't have to wreck your pc.
If it was me, I'd keep it simple; I guess I'd do something that corrupts menu.lst and renders the system unbootable (at least, as simple as unbootable can get), plus you can have a backup and recover easily.

However, I'd be sure they see me log in as root, give it executable permissions and deliberately running it so that they don't get the idea this can happen trivially. :)

PD. Your teacher really needs to get into some better exercises... I can see a couple fascinated window cr4k3rz poping out from this.

---

### Post by ASULutzy on 2008-05-22
Will this "virus" be something that runs as root, or as a regular user?

Because if it runs as root you could have it do any extravagant thing you want, but if it's as a regular user it's not doing anything other than maybe attaching itself to things in your /home/$USER folder.

---

### Post by itd on 2008-05-23
> **eragon100 said:**
> This frigging' idiot would have you make a virus and run it on your own computer!? :confused:

Do you really think i didn't think about that??
The virus is supposed to run on a virtual instalation (my professor gave me that advice, i just have to find out, how to do that :) ), or on the school computer( I don't really care about those computers :lolflag:). 
Thanks for the replies. However, the definition in the project description says: "You can add also this functionallity: write a virus (if the virus for spreading uses the web, test it on a closed     network". 
It will propably run as regular user (If it would run as root, it would be simple, just write an c program, that runs some commands to mess with the boot files and afterwards goes to any PC connected via the same local network).

thanks to yaztromo, I think, this webpage you posted, could give me some information and ideas, how to do that.

---

### Post by ASULutzy on 2008-05-23
Well, if it doesn't run as root, it's not going to do anything other than do stuff to files in the /home/$USER directory

---

