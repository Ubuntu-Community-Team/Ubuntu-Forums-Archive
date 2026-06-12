---
title: "apt problems R and Virtualbox"
date: 2018-04-05
forum: Virtualisation
---

### Post by emm01 on 2018-04-05
I've been using ubuntu since 2005 and I've noticed that package management
has never been completely "sorted" - just by looking at the amount of problems
people have with running apt with -fix and autoremove etc.

Ive seen some spectacular multi-line "apt-recipes" for supposedly fixing
problems including the inevitable hit the red button and reboot

All this suggests to me that it is poorly understood and in all this time
I havent seen any attempt at a considered and integrated solution.

In fact I would go as far as to say that the non-free operating systems
alternatives have linux beat hands-down in this area.

my own particular problem this time  involves the following scenario

fresh install of ubuntu 14.10 with a kernel upgraded to 4.14.10

what set off the problem was this scenario

1. install virtual box 5.2.8 this pulled in a libcurl3 dependency
1b. download compile and install virtual box extensions for 5.2.8

2. install R fails wanting libcurl4-openssl-dev dependency

3. backout the broken R install which wouldn't compile R modules
because of some obscure dependencies see libcui57 at (7)

4. backout the perfectly working virtualbox install

5. install libcurl4-dev to manually fix the joint dependency requirements

6. reinstall virtualbox 5.2.8

7. install some obscure R dependencies that proved problematical
for R for some reason for example libcui57 and libgfortran

8. Reinstall R 

9. After 8 hours work I now have an R that works perfectly - 
that will download and compile and install R module extensions
and a Virtual Box that works with Virtual Box addons that will
also compile and install and work 

The problem I have now is I can no longer install * ANYTHING *
I certainly dont want to randomly apply apt recipes because
I attempted that at (3) and (4) and I got 2 screens of apt
nonsense about it replacing deleting and downgrading half
my system including many packages you would never have
thought had anything to do with R and Virtualbox and 8 hours
of my time to get back to exactly the same place I was
with the R/libcurl4-openssl-dev dependency sorted.

My problem now is this error message when I attempt to
use apt

##>

$sudo apt install kaffeine

Reading package lists...Done
Building dependency tree
Reading state information...Done
You might want to run 'apt --fix-broken install' to correct these.

The following packages have unmet dependencies.
 kaffeine : Depends: libdvbv5-0 (>= 1.4.0) but it is not going to be installed
 libgfortran-6-dev : Depends: gcc-6-base (= 6.4.0-8ubuntu1) but it is not going to be installed
                     Depends: libgcc-6-dev (= 6.4.0-8ubuntu1) but it is not going to be installed
                     Depends: libgfortran3 (>= 6.4.0-8ubuntu1) but it is not going to be installed
 libicu57 : Breaks: libicu57:i386 (!= 57.1-6) but 57.1-6ubuntu0.2 is to be installed
 libicu57:i386 : Breaks: libicu57 (!= 57.1-6ubuntu0.2) but 57.1-6 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

Obviously the libicu57  and libgfortran is something to do with my R (which works perfectly btw)
however R wouldnt work on my system without me installing for it the libicu57 and libgfortran.

I certainly dont want to type --fix and spend another 8 hours downloading, compiling and putting
packages back again

I also note that the amount of virtualisation that is going is a useful way to avoid the
problems of using apt at all and in future I predict that apt will become even more
inadequate at its job.

In the meantime a simple and quick solution to the above problem would be
greatly appreciated.

Thx.

---

### Post by wildmanne39 on 2018-04-05
While your issue is not directly related to the following perhaps:
> fresh install of ubuntu 14.10 with a kernel upgraded to 4.14.10
14.10 is EOL and the repositories or no longer available including no more security updates.

---

### Post by SeijiSensei on 2018-04-05
You should be relying on releases with long-term support. They are released every other April. 18.04 will be released some time in the next couple of weeks.

---

### Post by emm01 on 2018-04-06
Sorry, typo 

$ lsb_release -a

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

$ uname -a

Linux node1 4.14.10-041410-generic #201712291810 SMP Fri Dec 29 18:11:20 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by emm01 on 2018-04-08
No takers?

I suppose my typo caused a rush to "end of life" (a variation to switch it off and on that fixes everything).

I expected more comment from the GREAT UBUNTU FORUM IN THE SKY

Perhaps the situation really is APT is something that vaguely works but in reality is a broken pile of crap

---

### Post by dragonfly41 on 2018-04-08
Good advice .. which still applies in modern forums ..

[https://en.wikipedia.org/wiki/How_to_Win_Friends_and_Influence_People](https://en.wikipedia.org/wiki/How_to_Win_Friends_and_Influence_People)

---

### Post by SeijiSensei on 2018-04-08
I prefer to use Oracle's own repositories for VirtualBox as explained here: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

### Post by emm01 on 2018-04-08
Just to verify in case it wasnt clear,  all of my virtualbox was taken from Oracle. 

(Getting the right sources is something I've always done even before I had to 
start using linux in 1995)

---

### Post by deadflowr on 2018-04-08
Looking at the packages  in post #1, your system is out-of-date.
Have you refreshed it?
```
sudo apt update
```
you should be pulling in libicu57-57.1-6ubuntu0.3
but your showing it's trying to pull in libicu57-57.1-6ubuntu0.2.

---

### Post by emm01 on 2018-04-08
the official R installer which i downloaded not more than 3 weeks ago failed to
 pull in libicui57 and I couldnt get apt to find and install it those two facts would
seem to support each other. In light of this I went over to the deb packages
and downloaded the first libicui57 that I could find.

Interesting.

---

### Post by emm01 on 2018-04-08
btw: I continually run updates/refreshes for apt
and I'm sure that I now do that before adding anything major such as the Virtualbox and the R

thanks.

---

### Post by monkeybrain20122 on 2018-04-08
I always install the most up to date R from [https://launchpad.net/~marutter/+archive/ubuntu/rrutter](https://launchpad.net/~marutter/+archive/ubuntu/rrutter), never had a problem. Professor Rutter also maintains CRAN's repository and Ubuntu's official packages so this PPA is very trusted. Otherwise you can also find cran's packages in the repo (albeit a bit outdated for the LTS), to be able to install additional packages with install.packages() you need r-base-dev for the headers.

**Edited:** What official "R installer"?? It has no installer for Linux, but repositories and source codes. What are you talking about, are you trying to install R in VB?

---

### Post by slickymaster on 2018-04-09
*Thread moved to **Virtualisation**.*

---

