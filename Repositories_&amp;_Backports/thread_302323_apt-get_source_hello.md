---
title: "apt-get source hello"
date: 2006-11-18
forum: Repositories &amp; Backports
---

### Post by skierkegaard on 2006-11-18
I am trying to do a packaging example from:
[http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html)

When I run the command apt-get source hello:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_source_Sources - open (2 No such file or directory)

Any ideas?

---

### Post by cantormath on 2006-11-18
did you sudo apt-get ........

---

### Post by Ramses de Norre on 2006-11-18
He shouldn't when using source, are you sure you've got the deb-src repo's correctly in your menu.lst?

---

### Post by skierkegaard on 2006-11-18
Not sure what you mean with menu.lst... You don't mean /etc/apt/sources.list do you?  If you did, this is it:


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by LaserJock on 2006-11-18
I see that all your deb-src lines are for dapper and your deb lines are for edgy. I'm guessing you want them to be the same. Then make sure to do a sudo apt-get update

-LaserJock

---

### Post by skierkegaard on 2006-11-19
That was it, many thanks LaserJock

---

