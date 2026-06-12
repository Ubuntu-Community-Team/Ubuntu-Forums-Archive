---
title: "BUG? dapper-updates repository corrupts dev dependencies"
date: 2006-09-01
forum: Repositories &amp; Backports
---

### Post by tsiMental on 2006-09-01
There seems to be a problem with the dapper-updates repository / dapper packages.

Today I tried to install the kde-develop package. I ran into a series of dependency problems, caused by me having automatically upgraded to the dapper-updates packages when they were released.

The error messages were telling me that I couldn't install some of the packages that kde-develop were dependent on, with no info on why.

So I searched for the package in question. All of these were 'dev' packages. When I tried to install it manually. I found the dev package required an equalant non-dev package with a version exactly like the version of the dev package.

Since these packages where installed by dapper-updates and there were no equivalent 'dev' packages in the dapper-updates repository, I had to do a complete downgrade of the system, to match the 'dapper' versions.

Is there an easier fix for this problem or do I have to remove the 'dapper-updates' repository from my sources.list?

Shouldn't new packages be backwards compatible, so that these kind of problemes does not appear? Shouldn't these packages depend on another package with at least a sertain version, instead of exactly a specific version?

Btw: here is my sources.list:```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://no.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://no.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://no.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://no.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/plf dapper free non-free
deb-src http://packages.freecontrib.org/plf dapper free non-free                                               
                                                                                                                                          
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://www.getautomatix.com/apt kubuntu main
```

---

### Post by PabloH on 2006-09-29
Same thing here. I am having to use all kinds of force sillyness and it wants me to uninstall the whole world just to get libgtk2.0-dev installed. 

Some related threads:

[http://ubuntuforums.org/showthread.php?t=234089](http://ubuntuforums.org/showthread.php?t=234089)

[http://ubuntuforums.org/showthread.php?t=226190](http://ubuntuforums.org/showthread.php?t=226190)

---

