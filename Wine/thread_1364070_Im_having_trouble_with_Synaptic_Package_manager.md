---
title: "Im having trouble with Synaptic Package manager"
date: 2009-12-25
forum: Wine
---

### Post by Walkingtree5 on 2009-12-25
E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

.....is the error i'm getting everytime I open SPM, I think it was because I ended up installing wine twice accidentally, anyways could anyone help? It would be greatly appreciated.

---

### Post by bapoumba on 2009-12-25
Please post your sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by Walkingtree5 on 2009-12-25
I would but I have no clue how to do that, could you give me a quick step by step instruction where to paste that command in? I tried "Alt-F2" and pasted it in there but for some reason the box just vanished, even though I told it to run in a terminal.

Btw thanks for the quick response.

---

### Post by bapoumba on 2009-12-25
Sorry :)
Open a terminal > Accessories > Terminal and run the command. Then paste the output here.

---

### Post by Elfy on 2009-12-25
I'll just butt in here a mo .. 

you need the output of a different file, same method in a terminal 

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
```

---

### Post by Walkingtree5 on 2009-12-25
I think I did something wrong because I dont see how the info I found could be of any use, I went to Applications>accessories>Terminal  and ended up with this...
-----------------------------------------------------------------------------------------------------

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

Sorry but as you can tell I have only had linux for a day....So this is kind of all new to me.

---

### Post by Elfy on 2009-12-25
> E: Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.listThat's because it is all new to you :)

you'll see that all the lines in the file you have proved start with with # or deb (and deb-src) anything else will give you an error.

Just so you know # means it will be ignored - so in effect the only lines the system will use are those starting with deb  - now the error you have mught make more sense - Type 'n' is not known on line 2 

However - if you look in post #5 you'll see you need to be looking at a slightly different file.

---

### Post by bapoumba on 2009-12-25
> **forestpiskie said:**
> I'll just butt in here a mo .. 

you need the output of a different file, same method in a terminal 

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
```
Oh sorry :)

Walkingtree5 please do as forestpiskie suggested.

---

### Post by Walkingtree5 on 2009-12-25
Ok this is what came up when I entered that command in the terminal:

# deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) karmic main
n

---

### Post by Elfy on 2009-12-25
So then - the second line has an 'n'

Open the file as root for editing

```
gksudo gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-karmic.list
```

That assumes you are using ubuntu

The file will open, go to the second line and delete the n

Close the file and then in a terminal

```
sudo apt-get update
```

You should not get any error now.

---

