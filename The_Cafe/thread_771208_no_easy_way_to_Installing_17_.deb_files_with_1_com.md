---
title: "no easy way to Installing 17 .deb files with 1 command?"
date: 2008-04-27
forum: The Cafe
---

### Post by madjr on 2008-04-27
sorry to post this here

but am trying to install this program on **5 PCs with no internet**:
[http://getdeb.net/release.php?id=2287](http://getdeb.net/release.php?id=2287)

it has **17(seventeen) .deb** files

in fact for the server it will be 18 .debs

i'll be installing from an USB stick.

it's incredibly slow and annoying to type the password for each .deb .....

a command would be so much faster on these slow machines.

i know i seen the command somewhere, but searching doesn't give me any usable results (probably got deleted with the forum update?)... :S

Thanks for any help :)

---

### Post by klange on 2008-04-27
```
sudo dpkg -i *.deb
```
Any specific problem with doing this?

**e**: It appears I am the winner in this race to post "dpkg -i".

---

### Post by FuturePilot on 2008-04-27
Put them all in a directory then cd into that directory
```
cd /path/to/directory
```
Then
```
sudo dpkg -i *.deb
```
Hopefully there's no missing dependencies, but if there is
```
sudo apt-get install -f
```

---

### Post by myusername on 2008-04-27
cant you do sudo dpkg -i package names ?

---

### Post by myusername on 2008-04-27
whoa that was weird

---

### Post by DukeNuke2 on 2008-04-27
if nothing else works, try a little script:

for i in `ls -1 *.deb`; do dpkg -i $i; done

---

### Post by klange on 2008-04-27
> **DukeNuke2 said:**
> if nothing else works, try a little script:

for i in `ls -1 *.deb`; do dpkg -i $i; done
Should just be "for i in *.deb"

---

### Post by DukeNuke2 on 2008-04-27
> **WindowsSucks said:**
> Should just be "for i in *.deb"

there is allways more than one way... maybe yours is nicer but mine works also...

---

### Post by madjr on 2008-04-27
wow, thanks (and thanking all) that was fast.

i heard getdeb.net was working on a "system" to do this, but i see is just a simple command.

they should also have 1 **zip** (or tar) file with everything on it and include the script mentioned above.

---

