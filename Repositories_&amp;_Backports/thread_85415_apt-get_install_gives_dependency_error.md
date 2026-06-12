---
title: "apt-get install gives dependency error"
date: 2005-11-02
forum: Repositories &amp; Backports
---

### Post by nick4mony on 2005-11-02
I am getting this error when I try to upgrade the firefox browser.

```
root@willis:~/SystemActions # apt-get install mozilla-firefox
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libperl5.8: Depends: perl-base (= 5.8.4-2ubuntu0.4) but 5.8.4-2 is to be installed
  perl: Depends: perl-base (= 5.8.4-2ubuntu0.4) but 5.8.4-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

and I am unsure why this happened, or how to proceed.

The history of the system is that I 
[list=1]
[*]installed it from a Warty CD, 
[*]added universe to the sources.list file
[*]apt-get install <a whole pile of goodies>
[*]removed universe from the sources.list file (leaving cdrom & security)
[*]attempted above command
[*]also attempted apt-get upgrade
[/list]

Below gives more details.
```

root@willis:~/SystemActions # cat PastAptGet.cmd
apt-get install zonecheck bind9 bind9-doc dlint mtools lilo-doc bison flex manpages-dev gcc-doc stl-manual bash-doc 
xfce4 xfce4-systray xfce4-toys xfce4-trigger-launcher xfprint4 xfcalendar floppyd ruby1.8-examples libdbm-ruby1.8 menu 
a2ps psutils gv groff html2ps wdiff perlmagick mysql-client mysql-common mysql-server build-essential postgresql 
postgresql-client postgresql-doc php4 php4-apd php4-curl php4-mcrypt php4-mysql php4-pgsql php4-ps phpdoc 
libapache2-mod-php4 php4-cgi mozilla-thunderbird-dev apt-doc apt-file apt-howto-en apt-proxy debmirror dlocate 
expect5.31 twm user-mode-linux user-mode-linux-doc uml-utilities umlrun umlrun-uml cvsbook cvsd cvsgraph cvsutils 
cvs chastity-list squidclient squid rootstrap apache2-doc perl-doc doc-linux-html
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions # cat /etc/apt/sources.list
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://mirror.optus.net/ubuntu warty main restricted
deb-src http://mirror.optus.net/ubuntu warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb http://mirror.optus.net/ubuntu warty universe
#deb-src http://mirror.optus.net/ubuntu warty universe

deb http://security.ubuntu.com/ubuntu warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu warty-security main restricted

root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions # apt-get -q update
Hit http://mirror.optus.net warty/main Packages
Hit http://mirror.optus.net warty/main Release
Hit http://mirror.optus.net warty/restricted Packages
Hit http://security.ubuntu.com warty-security/main Packages
Hit http://mirror.optus.net warty/restricted Release
Hit http://mirror.optus.net warty/main Sources
Hit http://mirror.optus.net warty/main Release
Hit http://mirror.optus.net warty/restricted Sources
Hit http://security.ubuntu.com warty-security/main Release
Hit http://mirror.optus.net warty/restricted Release
Hit http://security.ubuntu.com warty-security/restricted Packages
Hit http://security.ubuntu.com warty-security/restricted Release
Hit http://security.ubuntu.com warty-security/main Sources
Hit http://security.ubuntu.com warty-security/main Release
Hit http://security.ubuntu.com warty-security/restricted Sources
Hit http://security.ubuntu.com warty-security/restricted Release
Reading Package Lists...
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions # date -u
Wed Nov  2 18:39:19 UTC 2005
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions #
root@willis:~/SystemActions # apt-get install mozilla-firefox
Reading Package Lists... Done
Building Dependency Tree... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libperl5.8: Depends: perl-base (= 5.8.4-2ubuntu0.4) but 5.8.4-2 is to be installed
  perl: Depends: perl-base (= 5.8.4-2ubuntu0.4) but 5.8.4-2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by tonysathre on 2005-11-02
try synaptic

---

### Post by nick4mony on 2005-11-02
[QUOTE=tonysathre]try synaptic[/QUOTE]

Not if I can help it.  I strongly prefer a command-line solution.  Do others have suggestions?

---

### Post by niko_ on 2005-11-02
did you try: apt-get -f install mozilla-firefox

---

### Post by erik-the-red on 2005-11-02
Do what niko suggests.

Also, if you prefer command-line, use aptitude instead of apt-get.

---

### Post by nick4mony on 2005-11-03
[QUOTE=erik-the-red]Do what niko suggests.

Also, if you prefer command-line, use aptitude instead of apt-get.[/QUOTE]
Adding the -f switch, as niko says, has no effect, I think that's because I'm not specifying packages that will fix the problem.

However, I will try aptitude, and if not, I'll try it with the -f switch.

---

### Post by aysiu on 2005-11-03
I don't know if this helps, but isn't *mozilla-firefox* now a dummy package that just refers to plain old *firefox*?

---

### Post by nick4mony on 2005-11-06
I tried a plain apt-get -f install (no packages) and got a different error.

```
root@willis:~ # apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  perl-base
The following packages will be upgraded:
  perl-base
1 upgraded, 0 newly installed, 0 to remove and 154 not upgraded.
3 not fully installed or removed.
Need to get 0B/728kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue? [Y/n] Y

Preconfiguring packages ...
(Reading database ... 84602 files and directories currently installed.)
Preparing to replace perl-base 5.8.4-2 (using .../perl-base_5.8.4-2ubuntu0.4_i386.deb) ...
Unpacking replacement perl-base ...
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.4-2ubuntu0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/perl/5.8', which is also in package liblockfile-simple-perl
Errors were encountered while processing:
 /var/cache/apt/archives/perl-base_5.8.4-2ubuntu0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


root@willis:~ # apt-get -f install perl-base liblockfile-simple-perl-
(gives similar error)

```

I found aptitude a bit confusing.  What do you suggest next?

---

### Post by nick4mony on 2005-11-06
I have solved the second problem ([font=courier] dpkg: error processing /var/cache/apt/archives/perl-base_5.8.4-2ubuntu0.4_i386.deb (--unpack):
 trying to overwrite `/usr/lib/perl/5.8', which is also in package liblockfile-simple-perl[/font])

It seems that apt-get (and aptitude) is too smart for it's own good, at times.

I did it like this:
```
root@willis:~ # dpkg -r liblockfile-simple-perl debmirror
(Reading database ... 84601 files and directories currently installed.)
Removing debmirror ...
Removing liblockfile-simple-perl ...
```
Then I went on to solve the first problem (wrong perl-base version)
```
root@willis:~ # apt-get install perl-base
Reading Package Lists... Done
Building Dependency Tree... Done
The following packages will be upgraded:
  perl-base
1 upgraded, 0 newly installed, 0 to remove and 154 not upgraded.
3 not fully installed or removed.
Need to get 0B/728kB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 84584 files and directories currently installed.)
Preparing to replace perl-base 5.8.4-2 (using .../perl-base_5.8.4-2ubuntu0.4_i386.deb) ...
Unpacking replacement perl-base ...
Setting up perl-base (5.8.4-2ubuntu0.4) ...
Setting up libperl5.8 (5.8.4-2ubuntu0.4) ...

Setting up perl-modules (5.8.4-2ubuntu0.4) ...
Setting up perl (5.8.4-2ubuntu0.4) ...
```
then I put the packages back (paranoid: one at a time) ...
```
root@willis:~ # apt-get install liblockfile-simple-perl
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  liblockfile-simple-perl
0 upgraded, 1 newly installed, 0 to remove and 154 not upgraded.
Need to get 0B/20.7kB of archives.
After unpacking 135kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package liblockfile-simple-perl.
(Reading database ... 84584 files and directories currently installed.)
Unpacking liblockfile-simple-perl (from .../liblockfile-simple-perl_0.2.5-4_all.deb) ...
Setting up liblockfile-simple-perl (0.2.5-4) ...
root@willis:~ # apt-get install debmirror
Reading Package Lists... Done
Building Dependency Tree... Done
The following NEW packages will be installed:
  debmirror
0 upgraded, 1 newly installed, 0 to remove and 154 not upgraded.
Need to get 0B/18.2kB of archives.
After unpacking 86.0kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package debmirror.
(Reading database ... 84597 files and directories currently installed.)
Unpacking debmirror (from .../debmirror_20040427_all.deb) ...
Setting up debmirror (20040427) ...
```

---

### Post by Bwyan on 2007-11-28
Thanks allot nick4mony.

This got rid of a similar problem I had with my Debian server.
The package names were a little different, but removing a package the way you showed, solved my problem.

Best regards,
Bwyan.

---

