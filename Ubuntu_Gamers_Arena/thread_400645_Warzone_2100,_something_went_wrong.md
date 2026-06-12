---
title: "Warzone 2100, something went wrong"
date: 2007-04-03
forum: Ubuntu Gamers Arena
---

### Post by Clay_Banger on 2007-04-03
i followed the instructions in the how-tos section on installing Warzone 2100.

everything was going fine, i had 2 change:
tar jxvf warzone-2.0.5.tar.bz2
cd warzone-2.0.5

to
tar jxvf warzone2100-2.0.5.tar.bz2
cd warzone2100-2.0.5

but that was all good. i then typed:
./configure

and it spat this out at me:
```
michaelc@backwards:~/Desktop/warzone2100-2.0.5$ ./configure
bash: ./configure: No such file or directory
```

what did i do wrong?

---

### Post by hikaricore on 2007-04-03
I'm having trouble downloading the source at the moment, but if you don't need the absolute latest, warzone2100 2.0.4 is up for grabs here:

[http://www.getdeb.net/comment.php?rel_id=322](http://www.getdeb.net/comment.php?rel_id=322)

**edit** Ok I found the problem, either AI missed a step or the group releasing warzone2100 source changed their compile process a bit.

You'll need to run:

```
./autogen.sh
```

Then continue with:

```
./configure
```

---

### Post by Clay_Banger on 2007-04-03
thx, that worked. BUT i did have 2 install autoconf via aptitude and the version of automake on aptitude wasnt new enough so i had 2 compile one of the newer versions.

so before running ./autogen.sh:
```
sudo aptitude install autoconf
```

go to [ftp://ftp.gnu.org/pub/gnu/automake/]("ftp://ftp.gnu.org/pub/gnu/automake/")

and download the lastest .tar.bz2 to the desktop
extract it to the desktop

in the terminal:
```
cd automake-1.9/ 
./configure
make
make install
```

then change to the warzone2100 folder and use:

```
./autogen
```

and continue on with the how-to

also i noticed that just typing "warzone" in to the terminal wouldnt run it, you needed to type "warzone2100"

---

### Post by Perfect Storm on 2007-04-04
Seems they changed it. Going to look the howto through.

Thanks for reporting back :)

---

### Post by Perfect Storm on 2007-04-04
Fixed! (and fixed other changes like they change their files from warzone to warzone2100), check the howto to make a new launcher.

You don't need to compile automake1.9, I used the one in the repo. 
Instead of ./autogen do sh autogen.sh

---

### Post by Clay_Banger on 2007-04-04
> **Artificial Intelligence said:**
> You don't need to compile automake1.9, I used the one in the repo. 
Instead of ./autogen do sh autogen.sh

oh... i forgot to have a look in there..

> Seems they changed it. Going to look the howto through.

Thanks for reporting back :)

No problem!

---

