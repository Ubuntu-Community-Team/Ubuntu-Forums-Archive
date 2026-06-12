---
title: "Release upgrade from Precise to Trusty with apt-mirror"
date: 2014-05-25
forum: Server Platforms
---

### Post by clement.analogue on 2014-05-25
Hi,

I run a local repository with apt-mirror. I want to use the latter in order to perform a release upgrade from Precise to Trusty. I modified the repository list to have the Trusty packages on the local server. It runs on Precise. I don't know if it's relevant (but I don't think so).

Here a simplified configuration file:
```
% cat mirror.list
############# config ##################
#
set base_path    /home/www/mirror
#
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set var_path     $base_path/var
set cleanscript $var_path/clean.sh
set defaultarch  amd64
set postmirror_script $var_path/postmirror.sh
set run_postmirror 1
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://archive.ubuntu.com/ubuntu precise main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu trusty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu trusty-proposed main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu precise main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb http://archive.ubuntu.com/ubuntu precise-updates main/debian-installer restricted/debian-installer universe/debian-installer
deb http://archive.ubuntu.com/ubuntu precise-backports main/debian-installer
deb http://archive.ubuntu.com/ubuntu precise-security main/debian-installer restricted/debian-installer universe/debian-installer
deb http://archive.ubuntu.com/ubuntu precise-proposed main/debian-installer restricted/debian-installer universe/debian-installer

deb http://archive.ubuntu.com/ubuntu trusty main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer
deb http://archive.ubuntu.com/ubuntu trusty-updates main/debian-installer restricted/debian-installer universe/debian-installer
deb http://archive.ubuntu.com/ubuntu trusty-backports main/debian-installer
deb http://archive.ubuntu.com/ubuntu trusty-security main/debian-installer restricted/debian-installer universe/debian-installer
deb http://archive.ubuntu.com/ubuntu trusty-proposed main/debian-installer restricted/debian-installer universe/debian-installer

deb http://archive.canonical.com/ubuntu precise partner

deb http://archive.canonical.com/ubuntu trusty partner

clean http://archive.ubuntu.com/ubuntu
clean http://archive.canonical.com/ubuntu
```

I tried the release upgrade:
```
% do-release-upgrade -d

...

Fetched 3,238 kB in 0s (0 B/s)                                                                                                              
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information

No valid mirror found 

While scanning your repository information no mirror entry for the 
upgrade was found. This can happen if you run an internal mirror or 
if the mirror information is out of date. 

Do you want to rewrite your 'sources.list' file anyway? If you choose 
'Yes' here it will update all 'precise' to 'trusty' entries. 
If you select 'No' the upgrade will cancel. 

Continue [yN]
```

I'm not sure I should answer yes. Especially because the proposed answer is no, probably for a reason. I think a release upgrade do more than replace precise by trusty on the source.list.

Do you know if I can jsut answer yes without expecting trouble? Or is there a way to set up apt-mirror for release upgrade?

Thank you.

---

