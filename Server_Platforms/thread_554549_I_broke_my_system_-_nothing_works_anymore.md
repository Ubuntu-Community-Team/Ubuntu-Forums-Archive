---
title: "I broke my system - nothing works anymore"
date: 2007-09-19
forum: Server Platforms
---

### Post by breakaway on 2007-09-19
Hello,

Was just tinkering about with my system, when some package (belocs-locales-data I think it was) was having a cry about dependencies. apt-get said I should try "apt-get -f install" to fix the problem. And so I did. It said something along the lines of "Be careful, don't delete these unless you know what you are doing." Type "Yes, do as I say!" to continue.

And so I did. It removed a bunch of packages, and now my system is competely broken. Nothing works - ls, clear, wget, ssh, nothing.

Trying to install ssh results in this:

```

 root@testsrv ~ $ apt-get install ssh
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  belocs-locales-bin: Depends: belocs-locales-data but it is not going to be installed
  coreutils: PreDepends: libselinux1 (>= 1.32) but it is not going to be installed
  debianutils: PreDepends: mktemp but it is not going to be installed
  gcc: Depends: gcc-4.1 (>= 4.1.1-2) but it is not going to be installed
  iptables: Depends: libselinux1 (>= 1.32) but it is not going to be installed
  libdevmapper1.02: Depends: libselinux1 (>= 1.30) but it is not going to be installed
                    Depends: libsepol1 (>= 1.12) but it is not going to be installed
  libpam-modules: Depends: libselinux1 (>= 1.30.28) but it is not going to be installed
  ssh: Depends: openssh-client but it is not going to be installed
       Depends: openssh-server but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
```

Running 'apt-get -f install' puts me here: 

```
 root@testsrv ~ $ apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  apt aptitude base-passwd bash belocs-locales-bin binutils bsdutils coreutils cpio cpp cpp-4.1 debconf debconf-i18n debian-archive-keyring debianutils
  diff dmidecode dpkg e2fslibs findutils gcc gnupg gpgv grep groff-base hostname info iptables iputils-ping klogd laptop-detect liba52-0.7.4 libacl1
  libapr1 libartsc0 libasound2 libaspell15 libasyncns0 libatk1.0-0 libattr1 libaudiofile0 libblkid1 libbz2-1.0 libc6 libcaca0 libcap1 libcomerr2 libconsole
  libcucul0 libdb4.2 libdb4.3 libdb4.4 libdc1394-13 libdevmapper1.02 libdirectfb-0.9-25 libdrm2 libdv4 libdvdnav4 libedit2 libesd0 libexpat1 libfribidi0
  libgcc1 libgcrypt11 libgdbm3 libglib2.0-0 libgnutls13 libgpg-error0 libgpmg1 libgsm1 libidn11 libjack0.100.0-0 libjasper-1.701-1 libjpeg62 libkrb53
  liblcms1 libldap2 liblircclient0 liblocale-gettext-perl libltdl3 liblzo1 liblzo2-2 libmad0 libmpcdec3 libncurses5 libncursesw5 libnewt0.52 libogg0
  libopencdk8 libpam-modules libpam0g libpcre3 libpopt0 libraw1394-8 libreadline5 libsasl2-2 libsdl1.2debian-alsa libselinux1 libsepol1 libsigc++-2.0-0c2a
  libslang2 libspeex1 libsqlite3-0 libss2 libssp0 libstdc++6 libsvga1 libsysfs2 libt1-5 libtasn1-3 libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libtheora0 libtwolame0 libungif4g libusb-0.1-4 libuuid1 libvolume-id0 libvorbis0a libvorbisenc2 libwrap0 locales m4 makedev mawk
  perl perl-base perl-modules sysklogd tasksel tasksel-data zlib1g
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) debian-archive-keyring (due to apt) base-passwd bash debianutils (due to bash)
  libncurses5 (due to bash) bsdutils coreutils libacl1 (due to coreutils) libselinux1 (due to coreutils) diff dpkg findutils grep hostname perl-base
0 upgraded, 0 newly installed, 133 to remove and 0 not upgraded.
52 not fully installed or removed.
Need to get 0B of archives.
After unpacking 143MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] Yes, do as I say!
E: Sub-process /usr/sbin/dpkg-preconfigure --apt || true returned an error code (100)
E: Failure running script /usr/sbin/dpkg-preconfigure --apt || true

```

And throws me back to prompt.

Have I totally killed my system? Any way to recover from this? Or do I just cut my losses and format? :D

---

### Post by twistedtwig on 2007-09-19
complete stab in the dark.  Does the Ubuntu CD have a "repair" function on it? can't remember off the top of my head

What stage do you get to when you boot?

Does apt-get work?

cant remember the exact command but theres something like build essential that "might" give you the bits you need?!?!?!?!

---

### Post by cdenley on 2007-09-19
If you're just missing commands like ls, cp, and cat, but it still boots and gives you a command line, then try running
```
sudo apt-get install coreutils ubuntu-standard
```

---

