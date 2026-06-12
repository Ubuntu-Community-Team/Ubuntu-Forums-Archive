---
title: "Problems Trying to Install FreeNX on Warty"
date: 2005-03-01
forum: Ubuntu Backports
---

### Post by ryharv on 2005-03-01
Hello everyone,

After reading the [HOWTO: Can I use FreeNX with Warty?](http://www.ubuntuforums.org/showthread.php?t=1968&page=8&pp=10&highlight=freenx) I'm trying to install FreeNX on Warty.  My sources.list looks like this:

> 
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted


But when I run **apt-get update**, and then **apt-get install freenx**, I get the following error message:

> 
sudo apt-get install freenx
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  freenx: Depends: nxclient (>= 1.4.0-75.2) but it is not going to be installed
E: Broken packages

and trying to install nxclient gives me:
> 
The following packages have unmet dependencies:
  nxclient: Depends: libstdc++2.10-glibc2.2 but it is not installable
E: Broken packages
 

I saw a couple other people post the same error message, but I couldn't decipher any solutions.  Ideas?  Many thanks.

---

### Post by jdong on 2005-03-01
FreeNX depends on packages in Universe. Uncomment the two Universe lines.

---

### Post by ryharv on 2005-03-02
Still having problems.  I got everything to install correctly, but now the Nomachine client cannot connect.  I saw this problem outlined on the other forum on FreeNX but couldn't find an answer that worked.  The Nomachine client tells me:

> NX> 203 NXSSH running with pid: 2204
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.0.200 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
NX> 204 Authentication failed. 

I have set up nxserver with **nxsetup --setup-nomachine-key** but to no avail.

Any ideas appreciated.  Many thanks -- I think I'm close!!

---

