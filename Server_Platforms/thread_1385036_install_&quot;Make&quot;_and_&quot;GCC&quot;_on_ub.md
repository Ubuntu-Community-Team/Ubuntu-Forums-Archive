---
title: "install &quot;Make&quot; and &quot;GCC&quot; on ubuntu server 9.04"
date: 2010-01-19
forum: Server Platforms
---

### Post by cataztrophe on 2010-01-19
hi there, i have a big trouble here, i allready installed ubuntu 9.04 server edition, when i install xinit (use ./configure ; make ; make install) i found some error that "make" not installed yet on my syste, then when  wanna insdtall "make" , it said that i must install "GCC" first, then when i wanna install gcc, it said i must install gmp,mpfr and readline. arghh,,,this situation makes me stress,, can anyone help me?

can anyone share link to install "make" and "gcc" completely? so i can use it well? thnx before guys:P:P

---

### Post by regala on 2010-01-19
> **cataztrophe said:**
> hi there, i have a big trouble here, i allready installed ubuntu 9.04 server edition, when i install xinit (use ./configure ; make ; make install) i found some error that "make" not installed yet on my syste, then when  wanna insdtall "make" , it said that i must install "GCC" first, then when i wanna install gcc, it said i must install gmp,mpfr and readline. arghh,,,this situation makes me stress,, can anyone help me?

can anyone share link to install "make" and "gcc" completely? so i can use it well? thnx before guys:P:P

well, on Ubuntu, you almost never install anything from source. In a terminal, type "sudo aptitude install gcc make" enter your password, and you have installed gcc and make

br,

---

### Post by blackened on 2010-01-19
All of those tools come in the build-essential meta-package.

```
sudo apt-get install build-essential
```

---

### Post by cataztrophe on 2010-01-19
@regala
thnx for your suggestion, but i dont have internet connection, so i must install them offline (from source)

@blackened
thnx dude, but how can i run that command if i dont have any connection??

can anyone give solution based on my situation plz.
thnx before!

---

### Post by blackened on 2010-01-19
Put your installation cd into the drive, open a terminal and enter
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by blackened on 2010-01-19
Please don't bump via PM. We all see when subscriptions are updated by looking at the User Control Panel. Bumping is unecessary and rude.

---

### Post by lisati on 2010-01-19
> **blackened said:**
> Please don't bump via PM. We all see when subscriptions are updated by looking at the User Control Panel. Bumping is unecessary and rude.

+1 :)

@cataztrophe: it is usually better to keep discussion on the main thread, so others who come by might benefit from the nuggets shared, or maybe offer new nuggets that help with a solution.

---

### Post by cataztrophe on 2010-01-19
@blackened
thnx for your share.
oops sory..thats my bad, actually im a newbie on this place, please have my sory! :D

@lisati
thnx for your suggestion.
really apreciated it!

---

### Post by Bridgette on 2010-01-26
Hi 
In have a similar problem and with the kk server disk in the drive I do the sudo apt-cdrom add command and it looks for lists and comes back and tells me that it found 2 package indexes and 1 signatures, tells me then to repeat the process for the rest of the disks in your set then says it has skipped some packages as they are non existant (4), if i do the apt-get it just looks at the web and comes up with failed to fetch errors. I just can get it to look at updates, tried loading repos onto a dis and also using the alternate version with the above commands and still nothing, different error messages though, can somone please help
 
Thanks
Bridgette

---

