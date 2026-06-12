---
title: "I am major broken packages issues"
date: 2007-07-03
forum: Repositories &amp; Backports
---

### Post by DR_K13 on 2007-07-03
```
sean@nixlappy:~$ sudo apt-get install lm-sensors
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  lm-sensors: Depends: sysvinit (>= 2.85-19) but it is not going to be installed
E: Broken packages
sean@nixlappy:~$ sudo apt-get install sysvinit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sysvinit: PreDepends: initscripts but it is not going to be installed
E: Broken packages
sean@nixlappy:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-15-generic is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
sean@nixlappy:~$ 


```

my source list is up to date and fresh


```
deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```






HELP?

---

### Post by Shazaam on 2007-07-03
Here is an oldy but still a goody that might help...

[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

---

### Post by DR_K13 on 2007-07-03
Thanks for the guide, still no dice, this is interesting

```
Hit http://archive.ubuntu.com dapper-backports/multiverse Sources
Get:9 http://archive.ubuntu.com dapper/universe Sources [1312kB]                
99% [9 Sources gzip 0]            
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/universe Sources
  Sub-process gzip returned an error code (1)
Fetched 176kB in 23s (7409B/s)
Reading package lists... Done
W: GPG error: http://archive.ubuntu.com dapper Release: Unknown error executing gpgv
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv
W: GPG error: http://archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

```

I run apt-get update/upgrade too and still the same errors

---

### Post by bapoumba on 2007-07-04
This is quite strange.
sysvinit has been at a version > 2.85 since hoary.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=sysvinit]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=sysvinit")

Did you edit your sources.list? If so, which repos did you have at the time you got the error?
PLease paste the complete output to:
```
sudo aptitude update
```

---

