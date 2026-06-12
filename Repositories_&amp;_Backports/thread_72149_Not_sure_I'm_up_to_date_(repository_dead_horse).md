---
title: "Not sure I'm up to date (repository dead horse)"
date: 2005-10-05
forum: Repositories &amp; Backports
---

### Post by grimmson on 2005-10-05
Hello all. I think this one is simple. I followed the advice on repositories and new backports. sudo gedit /etc/apt/sources.list took out mirrormax added ubuntu. Did a  sudo apt-get update. and sudo apt-get install gstreamer0.8-plugins failed.

grimmson@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
grimmson@ubuntu:~$ sudo apt-get install gstreamer0.8-plugins
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-plugins: Depends: gstreamer0.8-a52dec but it is not going to be i nstalled
                        Depends: gstreamer0.8-aa but it is not installable
                        Depends: gstreamer0.8-artsd but it is not installable
                        Depends: gstreamer0.8-caca but it is not installable
                        Depends: gstreamer0.8-festival but it is not installable
                        Depends: gstreamer0.8-jack but it is not installable
                        Depends: gstreamer0.8-mad but it is not going to be inst alled
                        Depends: gstreamer0.8-mikmod but it is not installable
                        Depends: gstreamer0.8-mpeg2dec but it is not going to be  installed
                        Depends: gstreamer0.8-sid but it is not installable
                        Depends: gstreamer0.8-swfdec but it is not going to be i nstalled
E: Broken packages


This means gstreamer0.8-plugins didn't install, correct? It seams some /several media codecs aren't installable? Since I might have messed up sources can someone have a look and let me know whats going wrong. I have 5.04 w all ubuntu updates. Thanks.

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted  ???
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted  ???



deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports and extras
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

---

### Post by grimmson on 2005-10-06
see [http://www.ubuntuforums.org/showthread.php?t=72282](http://www.ubuntuforums.org/showthread.php?t=72282) for media stuff.

---

