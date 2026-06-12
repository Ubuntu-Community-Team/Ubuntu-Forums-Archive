---
title: "Home server help"
date: 2011-01-16
forum: Server Platforms
---

### Post by thatt'onekidmichael on 2011-01-16
hey guys. so i want to start a home server in which i can log on to the same account form 2 or three different machines running ubuntu server. is it possible and if so, how? :D

thanks in advance

---

### Post by cbarron on 2011-01-16
what kind of "account" are you talking about? There are lots of options depending on what you want to do. SSH is the easiest and safest way. post more info please.

---

### Post by thatt'onekidmichael on 2011-01-16
> **cbarron said:**
> what kind of "account" are you talking about? There are lots of options depending on what you want to do. SSH is the easiest and safest way. post more info please.


I mean the same user account. like at my school for instance, same files same preferences different computer

---

### Post by corrytonapple on 2011-01-16
Sounds to me like he wants to have one main server that has the OS, user account, and all that.  Then have some machines net-boot to that machine's OS, thus logging in to the computers account.  I would also like to hear about this.

---

### Post by thatt'onekidmichael on 2011-01-16
exactly. i want to try this at home and if it is a success. i'l do it at my church. we have problem with out files being on multiple computers

---

### Post by cbarron on 2011-01-16
> **thatt'onekidmichael said:**
> I mean the same user account. like at my school for instance, same files same preferences different computer
those "computers" are actually terminals which log in to the server and use its OS and such....that is a new area for me and have just started messing with it......but I would start looking for how to set up terminals in ubuntu server. Sorry Im not of much more help.

---

### Post by cbarron on 2011-01-16
> **thatt'onekidmichael said:**
> exactly. i want to try this at home and if it is a success. i'l do it at my church. we have problem with out files being on multiple computers
File sharing is a wonderful thing...or if you can just create a short cut to the drive the files are on, it works too. The problem you are having at your church really depends on the OS of the computers.

---

### Post by corrytonapple on 2011-01-16
I have an idea.  It may or may not work, so do not go forth with it unless an expert here proves it.  You could wire from the server to the computers, but I do not know how that would work.  Another idea:  You could hook all the machines to a router like normally, but find out how to net-boot with the machines you are wanting to boot by internal IP.  
As for mixed up files on different machines, just do the same thing as you would with a data partition and two OSes.  Make it so all machines on the network can see the file server, and then have the machines save and read from that network HDD (Hard Drive).
Just a thought....

---

### Post by thatt'onekidmichael on 2011-01-16
yeah but his is cooler. lol i found something that might do it:
[http://netboot.sourceforge.net/english/index.shtml](http://netboot.sourceforge.net/english/index.shtml)

check it out

---

### Post by cbarron on 2011-01-16
> **thatt'onekidmichael said:**
> yeah but his is cooler. lol i found something that might do it:
[http://netboot.sourceforge.net/english/index.shtml](http://netboot.sourceforge.net/english/index.shtml)

check it out
That IS the true terminal client computer....................that is the best way to do what you want but there are other was also.

---

### Post by slooksterpsv on 2011-01-16
I've done something somewhat like it before, it was somewhat of a pain, but here's what I had to do, specifics of how to do it vary (considering all the computers you log into are Ubuntu, and the main server faces the internet):

1. Setup a server (easy, could use a VM for security)
2. Setup an LDAP Server
3. Use PAM Authentication
4. Setup an NFS share that would be used as a mount for your /home/<username> folder
5. Point to automatically mount the /home/<userfolder> 
---Easy part done---

---Hard Part, varies cause it can be difficult---
6. Setup the client computers to check authentication against PAM for an LDAP server (said LDAP Server setup in easy part).
7. Have client computers mount NFS share to a common location in FSTAB (it was easier to do it that way instead of initiating the connection each time of login)
... umm... I know there's more than that, and I think I may have messed up, maybe the #5 is on the clients... It was a bit ago.

Not sure if that's what you're looking for, you can also setup Samba authentication for Domain joining type effect. But again, you'd have to manually configure all computers you use to point to the server, can get messy, but is fun =D

---

