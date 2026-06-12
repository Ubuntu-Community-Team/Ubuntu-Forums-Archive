---
title: "Install java?"
date: 2005-09-08
forum: Ubuntu Backports
---

### Post by jc87 on 2005-09-08
I tryed to install Java , with the command sudo apt-get install sun-j2re1.5 , but i dont find the package .

Here is my repositories (they were all updated winth apt-get update) :

deb [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://pt.archive.ubuntu.com/ubuntu](http://pt.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

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

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

Anyone knows what may be causing this? 

PS. I placed the topic on this section , because i think java is a backport repositorie.

---

### Post by xkamuyo on 2005-09-08
put this lines yours sources.list

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras universe multiverse

---

### Post by 11hjpphty76lkjj on 2005-09-19
I added the two lines to my /etc/apt/souces.list did an apt-get update still unable to locate the java install file.  I search in synpatic for sun, java, j2 and can't find anything.  Ideas?

Thanks!

Aaron  ](*,)

---

### Post by 11hjpphty76lkjj on 2005-09-19
Okay I followed the steps here:

[http://nickselby.com/articles/print.htm?a=1806](http://nickselby.com/articles/print.htm?a=1806)

added: deb [ftp://ftp.tux.org/java/debian/](ftp://ftp.tux.org/java/debian/) sarge non-free to the /etc/apt/sources.list

and now I'm able to find the package, but I can't install it because of this error:
  
j2re1.4: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is to be installed

libc6 IS installed with the version 2.3.2.ds1-20ubuntu14
but I guess java wants libc version 2.3.2.ds1-21

I tried re-installing libc6, no good, I was going to remove it and re-install the 2.3.2.ds1-21 version, but the only version I can find is the 2.3.2.ds1-21

So I was  :D  until I get the error now I'm  ](*,)    :?   ](*,)  and for good measure  ](*,) 

Help?

FYI using Hoary.

Aaron

---

