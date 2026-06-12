---
title: "R Request"
date: 2005-07-15
forum: Requests
---

### Post by larry on 2005-07-15
Hi,
Would it be possible to have the latest R ([http://cran.r-project.org/](http://cran.r-project.org/) , [http://www.itp.phys.ethz.ch/econophysics/R/](http://www.itp.phys.ethz.ch/econophysics/R/) and [http://cran.r-project.org/src/contrib/Views/Finance.html](http://cran.r-project.org/src/contrib/Views/Finance.html)) builds uploaded to the backports?
I think this would be appreciated by anyone working in statistics and finance.
They can also be installed from source (only partial solution I have found so far), but I wonder what happens to them when one upgrades R to the next release included in Ubuntu.
You would not like to have to take care manually of many packages.
Regards
Larry

---

### Post by divemaster on 2005-07-27
I just wanted to tell that there are more persons longing for this too be available for Ubuntu.

---

### Post by lparsons on 2005-08-11
[QUOTE=larry]Would it be possible to have the latest R ([http://cran.r-project.org/](http://cran.r-project.org/) , [http://www.itp.phys.ethz.ch/econophysics/R/](http://www.itp.phys.ethz.ch/econophysics/R/) and [http://cran.r-project.org/src/contrib/Views/Finance.html](http://cran.r-project.org/src/contrib/Views/Finance.html)) builds uploaded to the backports?[/QUOTE]
 Absolutly.  I need to run Bioconducotr packages and they require R 2.1.0 or later.  Ubuntu only has 2.0.1.  Anyone find a good workaround, or at least have some decent insturctions for keeping things stright with a manual compile?  Thanks.

---

### Post by larry on 2005-08-12
Unbelievable! I am not the only one concerned about the latest release of R-cran.
Let us hope that our requested package is uploaded soon.
R has strong links with Debian, so it should not be that hard to have those packages available for ubuntu.

---

### Post by JA_CH on 2005-08-14
Hi all,

I had a similar problem with R 2.0... I wanted to try out the R-GUI R Commander, 
[http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/](http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/)
but it requires R 2.1

So, to make a long story short, I made it work - but in a quick and dirty way:

WARNING: This is not a stable solution - for sure there is a reason why R 2.1 is compiled against a newer version of libc6. But at least for me it works. 

1) Download packages
r-base-core_2.1.1-0sarge1_i386.deb
r-recommended_2.1.1-0sarge1_all.deb

(I also needed this one)
r-base-dev_2.1.1-0sarge1_all.deb

from:

[http://cran.r-project.org/](http://cran.r-project.org/) 
(goto Linux/debian/stable/)

2) These packages are built against a newer version of libc6, so make a leap  of faith and install them with the option --force-depends

sudo dpkg -i --force-depends r-base-core_2.1.1-0sarge1_i386.deb

Your package manager will complain about broken packages, but as soon as ubuntu upgrades, you can remove the installed packages and reinstall R...

This was however only the start of the problems when installing R commander, I also needed to install a couple of source packages in order to install r-base-dev_2.1.1-0sarge1_all.deb... After this I had to download manually mvtnorm_0.7-1.tar.gz and install it with 
sudo R CMD INSTALL /home/xxx/mvtnorm_0.7-1.tar.gz

Hmm - I think that was all, if you are having problems installing R commander, drop a line and maybe I can help. Now it works, atleast, and it looks quite nice. 

J

---

### Post by Nazulatatunkce on 2005-08-16
Hi there, new to ubuntu and not well versed in linux, but believe in Open Source.  I have been going back and forth wit ubuntu and debian after abandoning SUSE.  I have been trying to get r onto ubuntu, but run into these same problems.  thanks for the input.

bob

---

### Post by cinnabar on 2005-08-21
I would also like to add my request for the 2.1 version of R to be placed into backports.  Most of the libraries I need to use require this version.  I hate to say it but I may have to move to a different distro if this isn't adressed soon.  Thanks.

---

### Post by Manny C on 2005-08-22
Me too! 

Need updated R very much! :)

---

### Post by lpc on 2005-08-29
Just to make this request stronger  :)  I am new to Ubuntu and trying to get  R to work hasn't been fun so far :(

---

### Post by skrat on 2005-09-19
That would be really great!

---

### Post by jasplund on 2005-09-19
[QUOTE=JA_CH]Hi all,

I had a similar problem with R 2.0... I wanted to try out the R-GUI R Commander, 
[http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/](http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/)
but it requires R 2.1

So, to make a long story short, I made it work - but in a quick and dirty way:

WARNING: This is not a stable solution - for sure there is a reason why R 2.1 is compiled against a newer version of libc6. But at least for me it works. 

1) Download packages
r-base-core_2.1.1-0sarge1_i386.deb
r-recommended_2.1.1-0sarge1_all.deb

(I also needed this one)
r-base-dev_2.1.1-0sarge1_all.deb

from:

[http://cran.r-project.org/](http://cran.r-project.org/) 
(goto Linux/debian/stable/)

2) These packages are built against a newer version of libc6, so make a leap  of faith and install them with the option --force-depends

sudo dpkg -i --force-depends r-base-core_2.1.1-0sarge1_i386.deb

Your package manager will complain about broken packages, but as soon as ubuntu upgrades, you can remove the installed packages and reinstall R...

This was however only the start of the problems when installing R commander, I also needed to install a couple of source packages in order to install r-base-dev_2.1.1-0sarge1_all.deb... After this I had to download manually mvtnorm_0.7-1.tar.gz and install it with 
sudo R CMD INSTALL /home/xxx/mvtnorm_0.7-1.tar.gz

Hmm - I think that was all, if you are having problems installing R commander, drop a line and maybe I can help. Now it works, atleast, and it looks quite nice. 

J[/QUOTE]

R-commander is in the Breezy-repositories as well as R 2.1. I have installed them. I haven't yet managed to start rcmdr though

---

### Post by killring on 2005-10-02
Hi folks,

I'm not real familiar with Ubunto, but I saw this thread on the R-help list. I'm running Mepis, and I think Ubunto is also built on a Debian base? If that's the case it is quite straightforward to get R, ESS, Rcmdr et al. installed from the repositories using Synaptic, or Apt-get. There's a page on the Mepis Wiki that might be helpful to you folks.

[http://www.mepislovers-wiki.org/index.php?title=R_installation_tips](http://www.mepislovers-wiki.org/index.php?title=R_installation_tips)

My apologies for not knowing better how Ubunto is set up, but I'm guessing the Mepis info might apply to you too...

Good Luck!

kr

---

### Post by pmilin@ptt.yu on 2005-12-27
Hi to ALL R-users!
The day before yesterday I started somewhat different approach to the same problem of keeping my R updated. In very brief, I have added new repository to the old list: a mirror of Debian and one of the R-cran. At the same time, I have disabled all Ubuntu repositories. After that, I started Aptitude (you may try Synaptic) and ask for upgradable packages. I accepted only those related to R and not others that might produce conflicts between Ubuntu and Debian versions. Aptitude made necessary adjustments and upgrading. Now, it seem that my R is current, safe and sound. I am still checking if everything is working. Nevertheless, if someone is willing to try this approach and share experience and problems it would benefit to all of us - Ubuntu and R users.


Sincerely,
Petar Milin
Assistant Professor
Department of Psychology
University of Novi Sad
Serbia and Montenegro

---

### Post by piccobello on 2006-09-02
Hi all,
 it would be good to have dapper R backported to breezy, as there
are more than 50 cran packages that require >= 2.2.0

see: [http://www.imsv.unibe.ch/cran/src/contrib/PACKAGES](http://www.imsv.unibe.ch/cran/src/contrib/PACKAGES)

I checked a bit the different dependencies, basically r-base
depends on r-base-core, and all dependencies of the latter

[http://packages.ubuntu.com/dapper/math/r-base-core](http://packages.ubuntu.com/dapper/math/r-base-core)

are satisfied in breezy already, except libreadline5 >= 5.1
in breezy there is 5.0-10. 

to backport libreadline
[http://packages.ubuntu.com/dapper/libs/libreadline5](http://packages.ubuntu.com/dapper/libs/libreadline5)
 one needs to backport readline-common..

I only checked dependencies with explicit constraints (>= vers)
and did not check other (r-cran*) packages
but it seems doable..

thanks all for bringing it up!
I posted this info to the ubuntu-backports mailing list as well

---

