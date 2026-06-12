---
title: "Problem with apt-get (mplayer, specifically)"
date: 2005-10-27
forum: Repositories &amp; Backports
---

### Post by embrodak on 2005-10-27
HI! I've been trying to install mplayer-586 (as I have a P4, that's what I read I should download) and it's not working. :( 

Here is what I type in:

# apt-get install mplayer-586

and it errors, saying:

The following packages have unmet dependencies:
  mplayer-586: Depends: libdirectfb-0.9-20 but it is not going to be installed

I've installed libdirectfb-0.9-22 (9-20 is outdated, apparently, according to my computer).  I was wondering if there are some basic repositories I'm missing and if not what  I should do. I really need to watch this movie (Garden State), and totem isn't working. 

Thanks!

~*~Embrodak~*~

---

### Post by Beggar on 2005-10-27
First off trust me, you dont need to see Garden State.

Could you post the output from ```
cat /etc/apt/sources.list
```

and just out of curiostiy, you ran ```
 sudo apt-get install mplayer-586
``` right?

---

### Post by embrodak on 2005-10-27
I ran apt-get as root, so basically, yeah, I just typed in the command I showed in my earlier post...

/etc/apt/sources.list :


## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

~*~*~*~*~

Thanks again!

---

