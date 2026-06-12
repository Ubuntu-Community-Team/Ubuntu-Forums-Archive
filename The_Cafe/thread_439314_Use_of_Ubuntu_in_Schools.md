---
title: "Use of Ubuntu in Schools"
date: 2007-05-10
forum: The Cafe
---

### Post by saxofoner on 2007-05-10
My high school is one of those across America that has recently started a laptop program.  All of the students of the last two classes were given Apple laptops, the latter generation receiving Intel Mac Books.  Now of course, students don't want to be restricted to sites and software granted them by the school, so they find loopholes in the security system.  Then it moves on to finding ways to "hack" the apps and make them run.  But there's always a loophole, and good students are punished for, for example, installing Python IDLE to practice programming.  

Anyway, I'm trying to think of a solution, because it's a problem.  

My solution for the internet is have not a blacklist, but a whitelist.  Start with all the obvious things, get them from some source, with, you know, educational sites, search engines, etc.  Then allow students to submit (with their names/IDs) on the school's site, the names of sites they'd like to access.  Then the admin's would click "block" or "deny" and it would happen.  I'm sure there are holes in this, but we can talk about it, at least. 

My question is, would there be an easy way to make an Ubuntu machine totally solid?  So no 9th graders can install anything without permission.  Then the admins could whitelist software in the repos, and force those applications "only" to be used.  NO TERMINAL ACCESS, and no running restricted software.  Is that conceivable?

**So basically, lock application/repo access except for whitelisted software, and have a "request" system for sites, where they could be punished for submitting obviously inappropriate websites, by using their own "white list" system accounts.  **

I like the idea.  See any problems?  If there's any positive response, I'm going to propose this to my school.  Hell, they'd save a lot of money too.  Then the problem is administering these changes to hundreds of laptops...

---

### Post by Steven_Gerrard on 2007-05-10
I guess one problem is to decide which list certain apps and programs belong to. Of course some are given blacks and some are given whites, but there are also many who do a lot of good, but can be used badly as well.

---

### Post by lyceum on 2007-05-10
If you want control, do not give out laptops. Use desktops and an entranet to keep the masses chained down. I hate the idea of "giving" someone something then telling them they cannot use it.

---

### Post by saxofoner on 2007-05-10
Sorry, lyceum, but that would make too much sense.

---

### Post by hsweet on 2007-05-10
One solution is to use Edubuntu or some version of LTSP.  The software running on student's computers is not on their particular machine (laptop or desktop)  

Install all the tools to let them play/learn and let them have at it.

If you want a whitelist, check out Firestarter or some firewall.  As long as you don't have a *-****en proxy-filter in your district it's easy to set that up.

The tricky balance in schools is to allow enough freedom for students to be able to experiment without them buggering up systems that take you hours to repair. (I've been there).

---

### Post by hessiess on 2007-05-10
not alowing students to install the softwere thay need would make the laptops fit for the crusher. this is why i never yse my schools network, theres hardly any usfal softwere, and a complete inabilaty to do anything about it.

---

### Post by Polygon on 2007-05-11
depends what you mean by "using ubuntu in schools"

if you mean having ubuntu on laptops that like college kids bring to their classes and can do whatever on...w ell since its their laptop there should really be no restrictions (except for net access maybe, like blocking bittorent as some colleges do)

but if your talking about elementry/middle/high schools, and for desktop computers that are in the library/computer labs / classrooms, its really not that hard. My school uses Mac OS X computers and what they do is really simple (not that simple but it works)

they have the system administrators create an account for every single person in the school (students and teachers alike)

then they basically set up a mac os x computer exactly to their liking, as in all the settings that they want are enabled, all of the installed programs are there, everything. Then they make an image of that hard disk and burn it to every single computer in the school so every single computer is identical

then they create some groups, one for "admins", one for "teachers" and one for "students", and set the permissions of all the programs so that one group or multiple groups can use them, and others cant

and since these accounts are on a central server, you can go on any computer in the school and login, get all of your files that are on your desktop / home folder (since they are all saved on the server), and do whatever, since each computer ahs the exact same stuff installed. and students cant screw up the computers as all of the utilities (like disk utility, console) are locked since you dont have permission  and you cant use them.

A similiar setup for linux or ubuntu would be almost the exact same thing. Except i have no idea how you would set up a network where the home folders for accounts are located on a central server (i assume there is a way however).

I think this differs from a "thin client" setup as these computers are real computers and have their own hard drives and everything, its just that the home folders are on the server, but the individual computers still run all the programs and everything. Thin clients are where the server does EVERYTHING and the computer is basically some ram and a ethernet card.

---

### Post by macogw on 2007-05-11
> **Polygon said:**
> depends what you mean by "using ubuntu in schools"

if you mean having ubuntu on laptops that like college kids bring to their classes and can do whatever on...w ell since its their laptop there should really be no restrictions (except for net access maybe, like blocking bittorent as some colleges do)

but if your talking about elementry/middle/high schools, and for desktop computers that are in the library/computer labs / classrooms, its really not that hard. My school uses Mac OS X computers and what they do is really simple (not that simple but it works)

they have the system administrators create an account for every single person in the school (students and teachers alike)

then they basically set up a mac os x computer exactly to their liking, as in all the settings that they want are enabled, all of the installed programs are there, everything. Then they make an image of that hard disk and burn it to every single computer in the school so every single computer is identical

then they create some groups, one for "admins", one for "teachers" and one for "students", and set the permissions of all the programs so that one group or multiple groups can use them, and others cant

and since these accounts are on a central server, you can go on any computer in the school and login, get all of your files that are on your desktop / home folder (since they are all saved on the server), and do whatever, since each computer ahs the exact same stuff installed. and students cant screw up the computers as all of the utilities (like disk utility, console) are locked since you dont have permission  and you cant use them.

A similiar setup for linux or ubuntu would be almost the exact same thing. Except i have no idea how you would set up a network where the home folders for accounts are located on a central server (i assume there is a way however).

I think this differs from a "thin client" setup as these computers are real computers and have their own hard drives and everything, its just that the home folders are on the server, but the individual computers still run all the programs and everything. Thin clients are where the server does EVERYTHING and the computer is basically some ram and a ethernet card.
That doesn't make a lot of sense.  At first you're describing having every account on an installed OS on every machine.  Then if you saved stuff, it'd be on that specific machine.  Maybe they're somehow setup to mount /home from a server, though I've no idea how you could do that.  Edubuntu's LTSP does the thing where they're dumb terminals and everything is server-based.  It makes the most sense.  Dumb terminals cost a lot less than real computers.

---

### Post by aysiu on 2007-05-11
> **macogw said:**
> Maybe they're somehow setup to mount /home from a server, though I've no idea how you could do that. According to [this page](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html), it can be done: > NFS Advantages

• Local workstations use less disk space because commonly used data can be stored on a single machine and still remain accessible to others over the network.

• There is no need for users to have separate home directories on every network machine. Home directories could be set up on the NFS server and made available throughout the network.

• Storage devices such as floppy disks, CDROM drives, and Zip® drives can be used by other machines on the network. This may reduce the number of removable media drives throughout the network.

---

### Post by pirothezero on 2007-05-11
Whats the point of giving all the students of 11th and 12th a laptop again? What good does it do? what does it motivate? Why did a community/school board decide to do that? 

How big is the school/those two classes ? They should have gotten System 76s for a fourth of the cost., not an advocate here but seems like someone didn't think through it clearly on getting a big lot of apple laptops I only hope they got one hell of a deal on it. Though if it was a school in my community I don't know how I would react knowing it went to buy something deemed moderately hip catering to the current generations materialistic persona.

To answer the NFS question:

Here at UT in Austin our in our CS department, each student/faculty/grad student stuff has a home directory to their username and thats on a server on campus, we are able to cycle up in the directories to see each persons user name but obviously no one has access to the contents of the folder. Personally I think this system is awesome because it allows people to log in remotely and get their stuff or go into the computer labs. 

So why laptops and why not a computer lab with remote access? I seem to miss the point of giving people under the age of 18 laptops for a reason they themselves don't want to admit to using it for.

---

### Post by macogw on 2007-05-11
pirothezero, good question.  It sounds like a waste of money to me.  My HS had laptops, but that was for when all of the desktops in the library were in use.

---

### Post by H.E. Pennypacker on 2007-05-11
I hope my tax money is not going towards this.  I don't work difficult hours so that 9th graders can get fancy laptops (don't take any offense).

---

### Post by caveman56 on 2007-05-17
We have a couple of local schools in the area that are doing just that.  They want all their students, 9 thru 12 to have tablet laptops to take notes and use as books in some of their classrooms.  Seems like a waste of money to me to require the students to have a laptop that most of them seem to drop and break, when they can have a full lab of computers at the school and use a pen and paper to write on.

---

