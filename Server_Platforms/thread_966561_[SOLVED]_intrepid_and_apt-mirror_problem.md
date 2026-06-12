---
title: "[SOLVED] intrepid and apt-mirror problem"
date: 2008-11-01
forum: Server Platforms
---

### Post by tedius on 2008-11-01
I'm playing around with my own local mirror using apt-mirror.

I've got the hardy repository working without a hitch. But I've now tried to mirror the intrepid repository and I'm getting the following error.

```

user@Host:/etc/apt$ sudo apt-mirror /etc/apt/mirror-ibex.list
Downloading 33 index files using 20 threads...
Begin time: Tue Oct 21 22:02:27 2008
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Tue Oct 21 22:04:04 2008

Proceed indexes: [Psh: cannot open uk.achive.ubuntu.com/ubuntu//dists/intrepid/main/binary-i386/Packages.gz: No such file
apt-mirror: can't open index in proceed_index_gz at /usr/bin/apt-mirror line 382.

```

Where my mirror-ibex.list file is as follows.

```

############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# if you change the base path you must create the directories below with write privlages
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path    $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
set nthreads    20
set _tilde 0
#
############# end config ##############

deb http://uk.achive.ubuntu.com/ubuntu intrepid main
deb http://uk.achive.ubuntu.com/ubuntu intrepid restricted
deb http://uk.achive.ubuntu.com/ubuntu intrepid universe
deb http://uk.achive.ubuntu.com/ubuntu intrepid multiverse

# Updates
deb http://uk.achive.ubuntu.com/ubuntu intrepid-updates main
deb http://uk.achive.ubuntu.com/ubuntu intrepid-updates restricted
deb http://uk.achive.ubuntu.com/ubuntu intrepid-updates universe
deb http://uk.achive.ubuntu.com/ubuntu intrepid-updates multiverse

# Security
deb http://uk.achive.ubuntu.com/ubuntu intrepid-security main
deb http://uk.achive.ubuntu.com/ubuntu intrepid-security restricted
deb http://uk.achive.ubuntu.com/ubuntu intrepid-security universe
deb http://uk.achive.ubuntu.com/ubuntu intrepid-security multiverse

clean http://uk.archive.ubuntu.com/ubuntu

```

Does anyone know what the problem is and how I can fix it?

Thanks

---

### Post by aos101 on 2008-11-02
You've entered uk.achive.ubuntu.com - I think that should be a**r**chive not achive.

---

### Post by tedius on 2008-11-27
You are correct.  I did indeed spell it wrong, and that was the problem.

Thanks

---

