---
title: "apt-get source errors?"
date: 2005-06-12
forum: Repositories &amp; Backports
---

### Post by furtivefelon on 2005-06-12
Hello, i can't get apt-get to work.. it returned the following errors:
jason@jason:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz)  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

anyone know what's wrong? i'm using kubuntu 5.04..

thanks!
Jason

---

### Post by az on 2005-06-12
Perhaps the server went down.  Does it still do that?

---

### Post by furtivefelon on 2005-06-12
well, not when you type sudo apt-get update... but i just uncommented alot of the sources in sources.list, as shown below:
deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe
 deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
------------------------------------------------------------------------------------------------------------------------------

now when i try to get ubuntu-desktop: sudo apt-get install ubuntu-desktop, it gave me the following errors:
jason@jason:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package ubuntu-desktop
-----------------------------------------------------------------------------------------------------------------------------
it should find it no?

thanks!

---

### Post by Xian on 2005-06-12
Did you do a 'apt-get update' after changing your sources.list?

---

### Post by furtivefelon on 2005-06-12
i just did try apt-get update.. then i try to install something simple, like gaim.. but it still failed.. the following is the message:

root@jason:~# apt-get install gaim
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkspell0 libpango1.0-0 libpango1.0-common
Suggested packages:
  gnome-panel evolution-data-server libzephyr3 ttf-thryomanes
The following NEW packages will be installed:
  gaim libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkspell0 libpango1.0-0 libpango1.0-common
0 upgraded, 7 newly installed, 0 to remove and 14 not upgraded.
Need to get 264kB/3203kB of archives.
After unpacking 18.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hoary/main libpango1.0-0 1.8.1-0ubuntu2 [264kB]
Fetched 264kB in 0s (282kB/s)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.8.1-0ubuntu2_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.8.1-0ubuntu2_i386.deb)  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

anyone know what's wrong?

---

### Post by az on 2005-06-12
I have read that the servers are having some troubles, today...

---

### Post by furtivefelon on 2005-06-12
but for some reason the apt-get update works fine.. it shows it had hitted all ca.archive.ubuntu.com sources.. when i try to install gaim, it still gives me the same problem..

---

### Post by dkitty on 2005-06-12
[QUOTE=furtivefelon]MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/QUOTE]

I've seen that error several times today as well. It's been hit and miss though. I could install Wesnoth but not Freeciv. GnomeBaker but not gFTP.

---

### Post by eyequeue on 2005-06-12
[QUOTE=furtivefelon]but for some reason the apt-get update works fine.. it shows it had hitted all ca.archive.ubuntu.com sources.. when i try to install gaim, it still gives me the same problem..[/QUOTE]

ca.archive.ubuntu.com is the same machine as us.archive.ubuntu.com. For some reason, though it is working fine for me here, consistently, many on IRC are reporting that it is still failing for them.

I would suggest editing your /etc/apt/sources.list and changing all .ca.archive to archive, then re-updating, and issue what you want.

Example follows:

 ```

$ sudo  sed -e  's/ca.archive/archive/'  -i  /etc/apt/sources.list
$ # or "sudo gedit /etc/apt/sources.list" and make the changes manually

$ sudo apt-get update

$ sudo apt-get install gaim


``` 
 
Obviously, this is only needed until the archive issues are resolved somehow by the ftpmasters, perhaps an rsync needs doing?

---

