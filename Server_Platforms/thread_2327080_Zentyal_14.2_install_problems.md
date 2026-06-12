---
title: "Zentyal 14.2 install problems"
date: 2016-06-07
forum: Server Platforms
---

### Post by lars17 on 2016-06-07
Hi Guys. 

I'm trying to install Zentyal on my Ubuntu server, but its missing packages. and without it i cannot install the webui.

```
sudo apt-get install zentyal[ Sudo ] password for halfe :
Reading package lists ... Done
Creates list of dependency
Reading state information ... Done
Some packages could not be installed . This may mean that you have requested
an impossible condition or , if you use the unstable version of Debian ,
that certain core packages have not yet been created or moved out of the " Incoming " for
distribution.
The following information may help to resolve the issue :


The following packages have unmet dependency :
 zentyal : Depends : zentyal -core but will not be installed
           Depends : zentyal software but will not be installed
E: Unable to correct problems , some broken packages are held back .
```

So ok. i need Zentyal-core and Zentyal Software (that is dependent on core)
i'm trying this

```
sudo apt-get install zentyal-core
Reading package lists ... Done
Creates list of dependency
Reading state information ... Done
Some packages could not be installed . This may mean that you have requested
an impossible condition or , if you use the unstable version of Debian ,
that certain core packages have not yet been created or moved out of the " Incoming " for
distribution.
The following information may help to resolve the issue :


The following packages have unmet dependency :
 zentyal -core : Depends : libclone-fast-perl but should not be installed
E: Unable to correct problems , some broken packages are held back .

```

Not working. I need libclone-fast-perl.
with extensive searching i found out that it was part of
```
deb http://us.archive.ubuntu.com/ubuntu trusty main universe
```
so i added it ran update. and tried to install libclone-fast-perl
```

sudo apt-get install libclone-fast-perl
Reading package lists ... Done
Creates list of dependency
Reading state information ... Done
Some packages could not be installed . This may mean that you have requested
an impossible condition or , if you use the unstable version of Debian ,
that certain core packages have not yet been created or moved out of the " Incoming " for
distribution.
The following information may help to resolve the issue :


The following packages have unmet dependency :
 libclone - fast- perl : Depends : perlapi - 5.18.1
E: Unable to correct problems , some broken packages are held back .

```

I'm back to that i need perlapi-5.18.1 that i found out that is part of perl-base.
But this is here i'm lost. Perl-base is installed and updated but it still fails
what am i doing wrong here?

---

### Post by mastablasta on 2016-06-08
sicne they had osme changes in zentyal, this might help a bit: [SIZE=2]https://www.digitalocean.com/community/tutorials/how-to-install-zentyal-on-ubuntu-14-04
[/SIZE]

if this is a fresh install it might be easier to simply donwload zentyal image and install from that.

---

