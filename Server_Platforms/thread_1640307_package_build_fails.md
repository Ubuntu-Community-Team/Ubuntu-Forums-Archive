---
title: "package build fails"
date: 2010-12-07
forum: Server Platforms
---

### Post by bluethundr on 2010-12-07
I successfully built some debs yesterday that modified openssh to
allow you to store your public keys in an LDAP directory. However when
I tried to run the build again on the same machine that succeeded
previously (ubuntu 10.10 server) even tho none of the contents of the
debian folder were changed the build fails...

```

gcc -o ssh ssh.o readconf.o clientloop.o sshtty.o sshconnect.o
sshconnect1.o sshconnect2.o mux.o roaming_common.o roaming_client.o
-L. -Lopenbsd-compat/ -Wl,-Bsymbolic-functions -fstack-protector-all
-Wl,--as-needed -lssh -lopenbsd-compat -lresolv -lcrypto -ldl -lutil
-lz  -lcrypt
gcc -o scp scp.o progressmeter.o bufaux.o -L. -Lopenbsd-compat/
-Wl,-Bsymbolic-functions -fstack-protector-all -Wl,--as-needed -lssh
-lopenbsd-compat -lresolv -lcrypto -ldl -lutil -lz  -lcrypt
gcc -o sftp progressmeter.o sftp.o sftp-client.o sftp-common.o
sftp-glob.o -L. -Lopenbsd-compat/ -Wl,-Bsymbolic-functions
-fstack-protector-all -Wl,--as-needed -lssh -lopenbsd-compat -lresolv
-lcrypto -ldl -lutil -lz  -lcrypt
gcc -o sshd sshd.o auth-rhosts.o auth-passwd.o auth-rsa.o
auth-rh-rsa.o sshpty.o sshlogin.o servconf.o serverloop.o auth.o
auth1.o auth2.o auth-options.o session.o auth-chall.o auth2-chall.o
groupaccess.o auth-skey.o auth-bsdauth.o auth2-hostbased.o
auth2-kbdint.o auth2-none.o auth2-passwd.o auth2-pubkey.o
auth2-jpake.o monitor_mm.o monitor.o monitor_wrap.o kexdhs.o kexgexs.o
auth-krb5.o auth2-gss.o gss-serv.o gss-serv-krb5.o loginrec.o
auth-pam.o auth-shadow.o auth-sia.o md5crypt.o audit.o audit-bsm.o
platform.o sftp-server.o sftp-common.o roaming_common.o roaming_serv.o
-L. -Lopenbsd-compat/ -Wl,-Bsymbolic-functions -fstack-protector-all
-Wl,--as-needed -lssh -lopenbsd-compat  -lresolv -lcrypto -ldl -lutil
-lz  -lcrypt
gcc -o ssh-keygen ssh-keygen.o -L. -Lopenbsd-compat/
-Wl,-Bsymbolic-functions -fstack-protector-all -Wl,--as-needed -lssh
-lopenbsd-compat -lresolv -lcrypto -ldl -lutil -lz  -lcrypt
make[2]: Leaving directory
`/home/bluethundr/openssh-lpk/openssh-5.6p1/build-udeb'
/usr/bin/make -C contrib gnome-ssh-askpass2 CC='gcc -O2 -g -Wall
-Wl,--as-needed'
make[2]: Entering directory `/home/bluethundr/openssh-lpk/openssh-5.6p1/contrib'
gcc -O2 -g -Wall -Wl,--as-needed `pkg-config --cflags gtk+-2.0` \
               gnome-ssh-askpass2.c -o gnome-ssh-askpass2 \
               `pkg-config --libs gtk+-2.0 x11`
make[2]: Leaving directory `/home/bluethundr/openssh-lpk/openssh-5.6p1/contrib'
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/bluethundr/openssh-lpk/openssh-5.6p1'
  debian/rules override_dh_auto_test
make[1]: Entering directory `/home/bluethundr/openssh-lpk/openssh-5.6p1'
make[1]: Warning: File `debian/rules' has modification time 3.4e+05 s
in the future
/usr/bin/make -C debian/tests
make[2]: Entering directory
`/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tests'
gcc -fPIC -c getpid.c -o getpid.o
gcc -shared -o getpid.so getpid.o
chmod +x keygen-test
./keygen-test
make[2]: Leaving directory
`/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tests'
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/bluethundr/openssh-lpk/openssh-5.6p1'
make: warning:  Clock skew detected.  Your build may be incomplete.
 fakeroot debian/rules binary
make: Warning: File `debian/rules' has modification time 3.4e+05 s in the future
dh binary --with apport
  dh_testroot
  dh_prep
       rm -f debian/openssh-client.substvars
       rm -f debian/openssh-client.*.debhelper
       rm -rf debian/openssh-client/
       rm -f debian/openssh-server.substvars
       rm -f debian/openssh-server.*.debhelper
       rm -rf debian/openssh-server/
       rm -f debian/ssh.substvars
       rm -f debian/ssh.*.debhelper
       rm -rf debian/ssh/
       rm -f debian/ssh-krb5.substvars
       rm -f debian/ssh-krb5.*.debhelper
       rm -rf debian/ssh-krb5/
       rm -f debian/ssh-askpass-gnome.substvars
       rm -f debian/ssh-askpass-gnome.*.debhelper
       rm -rf debian/ssh-askpass-gnome/
       rm -f debian/openssh-lpk.substvars
       rm -f debian/openssh-lpk.*.debhelper
       rm -rf debian/openssh-lpk/
       rm -f debian/openssh-client-udeb.substvars
       rm -f debian/openssh-client-udeb.*.debhelper
       rm -rf debian/openssh-client-udeb/
       rm -f debian/openssh-server-udeb.substvars
       rm -f debian/openssh-server-udeb.*.debhelper
       rm -rf debian/openssh-server-udeb/
  dh_installdirs
       install -d debian/openssh-client
       install -d debian/openssh-client/usr/share/lintian/overrides
       install -d debian/openssh-server
       install -d debian/openssh-server/etc/init
debian/openssh-server/etc/init.d debian/openssh-server/etc/default
debian/openssh-server/etc/network/if-up.d
debian/openssh-server/etc/ufw/applications.d
debian/openssh-server/usr/lib/openssh debian/openssh-server/usr/sbin
debian/openssh-server/usr/share/lintian/overrides
debian/openssh-server/usr/share/man/man5
debian/openssh-server/usr/share/man/man8
       install -d debian/ssh
       install -d debian/ssh/usr/share/lintian/overrides
       install -d debian/ssh-krb5
       install -d debian/ssh-askpass-gnome
       install -d debian/ssh-askpass-gnome/usr/lib/openssh
debian/ssh-askpass-gnome/usr/share/man/man1
debian/ssh-askpass-gnome/usr/share/pixmaps
       install -d debian/openssh-lpk
       install -d debian/openssh-client-udeb
       install -d debian/openssh-client-udeb/usr/bin
       install -d debian/openssh-server-udeb
       install -d debian/openssh-server-udeb/usr/bin
debian/openssh-server-udeb/usr/sbin
debian/openssh-server-udeb/var/run/sshd
  debian/rules override_dh_auto_install
make[1]: Entering directory `/home/bluethundr/openssh-lpk/openssh-5.6p1'
make[1]: Warning: File `debian/rules' has modification time 3.4e+05 s
in the future
/usr/bin/make -C build-deb DESTDIR=`pwd`/debian/tmp install-nokeys
make[2]: Entering directory
`/home/bluethundr/openssh-lpk/openssh-5.6p1/build-deb'
if test ! -z ""; then \
               /usr/bin/perl ../fixprogs ssh_prng_cmds ; \
       fi
(cd openbsd-compat && /usr/bin/make)
make[3]: Entering directory
`/home/bluethundr/openssh-lpk/openssh-5.6p1/build-deb/openbsd-compat'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory
`/home/bluethundr/openssh-lpk/openssh-5.6p1/build-deb/openbsd-compat'
../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin
../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/sbin
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/sbin
../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man
../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1
../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man5
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man5
../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man8
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man8
../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/lib/openssh
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/lib
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/lib/openssh
(umask 022 ; ../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/var/run/sshd)
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/var
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/var/run
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/var/run/sshd
/usr/bin/install -c -m 0755  ssh
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/ssh
/usr/bin/install -c -m 0755  scp
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/scp
/usr/bin/install -c -m 0755  ssh-add
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/ssh-add
/usr/bin/install -c -m 0755  ssh-agent
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/ssh-agent
/usr/bin/install -c -m 0755  ssh-keygen
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/ssh-keygen
/usr/bin/install -c -m 0755  ssh-keyscan
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/ssh-keyscan
/usr/bin/install -c -m 0755  sshd
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/sbin/sshd
if test ! -z "" ; then \
               /usr/bin/install -c -m 0755  ssh-rand-helper
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/lib/openssh/ssh-rand-helper
; \
       fi
/usr/bin/install -c -m 4711  ssh-keysign
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/lib/openssh/ssh-keysign
/usr/bin/install -c -m 0755  ssh-pkcs11-helper
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/lib/openssh/ssh-pkcs11-helper
/usr/bin/install -c -m 0755  sftp
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/sftp
/usr/bin/install -c -m 0755  sftp-server
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/lib/openssh/sftp-server
/usr/bin/install -c -m 644 ssh.1.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/ssh.1
/usr/bin/install -c -m 644 scp.1.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/scp.1
/usr/bin/install -c -m 644 ssh-add.1.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/ssh-add.1
/usr/bin/install -c -m 644 ssh-agent.1.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/ssh-agent.1
/usr/bin/install -c -m 644 ssh-keygen.1.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/ssh-keygen.1
/usr/bin/install -c -m 644 ssh-keyscan.1.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/ssh-keyscan.1
/usr/bin/install -c -m 644 moduli.5.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man5/moduli.5
/usr/bin/install -c -m 644 sshd_config.5.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man5/sshd_config.5
/usr/bin/install -c -m 644 ssh_config.5.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man5/ssh_config.5
/usr/bin/install -c -m 644 sshd.8.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man8/sshd.8
if [ ! -z "" ]; then \
               /usr/bin/install -c -m 644 ssh-rand-helper.8.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man8/ssh-rand-helper.8
; \
       fi
/usr/bin/install -c -m 644 sftp.1.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/sftp.1
/usr/bin/install -c -m 644 sftp-server.8.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man8/sftp-server.8
/usr/bin/install -c -m 644 ssh-keysign.8.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man8/ssh-keysign.8
/usr/bin/install -c -m 644 ssh-pkcs11-helper.8.out
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man8/ssh-pkcs11-helper.8
rm -f /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/slogin
ln -s ./ssh /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/bin/slogin
rm -f /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/slogin.1
ln -s ./ssh.1 /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/usr/local/share/man/man1/slogin.1
if [ ! -d /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/etc/ssh
]; then \
               ../mkinstalldirs
/home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/etc/ssh; \
       fi
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/etc
mkdir /home/bluethundr/openssh-lpk/openssh-5.6p1/debian/tmp/etc/ssh
make[2]: Leaving directory
`/home/bluethundr/openssh-lpk/openssh-5.6p1/build-deb'
make[1]: warning:  Clock skew detected.  Your build may be incomplete.
make[1]: Leaving directory `/home/bluethundr/openssh-lpk/openssh-5.6p1'
  debian/rules override_dh_install
make[1]: Entering directory `/home/bluethundr/openssh-lpk/openssh-5.6p1'
make[1]: Warning: File `debian/rules' has modification time 3.4e+05 s
in the future
rm -f debian/tmp/etc/ssh/sshd_config
dh_install -Nopenssh-client-udeb -Nopenssh-server-udeb --fail-missing
       install -d debian/openssh-client//etc/ssh
       cp -a debian/tmp/etc/ssh/moduli debian/openssh-client//etc/ssh/
       cp -a debian/tmp/etc/ssh/ssh_config debian/openssh-client//etc/ssh/
       install -d debian/openssh-client//usr/bin
       cp -a debian/tmp/usr/bin/scp debian/openssh-client//usr/bin/
cp: cannot stat `debian/tmp/usr/bin/scp': No such file or directory
dh_install: cp -a debian/tmp/usr/bin/scp
debian/openssh-client//usr/bin/ returned exit code 1
make[1]: *** [override_dh_install] Error 2
make[1]: Leaving directory `/home/bluethundr/openssh-lpk/openssh-5.6p1'
make: *** [binary] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
debuild: fatal error at line 1337:
dpkg-buildpackage -rfakeroot -D -us -uc failed

```


I am including an archive of the debian folder that i used to build
the package. If anyone has any insight into what may be causing this
error I would greatly appreciate your sharing what you know.

I am proud of the debs that did work. They are actually quite useful
as they are based on the openssh-5.6p1 implementation which deals with
the recent openssl vulnerability. So even if you don't want the LPK
functionality you can easily install the latest greatest ssh very
easily.

you can read more about LPK here...

[http://code.google.com/p/openssh-lpk/](http://code.google.com/p/openssh-lpk/)

thanks!!

---

### Post by lensman3 on 2010-12-07
The computer time is about 35000 seconds in the future.  35000 is about 1/2 a day.  Try resetting the system clock to the correct time.  Next start from a clean make.  The command should be "make clean" which should get ride of all the .o files and libraries.  Then try a new make.  If you get the same error then clean it again.  

You need to run the touch command on the c/cpp files.  This is tricky because touch doesn't have a directory recursive mode.  It may be easier to reinstall the source.  The error indicates that you have a .o, a lib files, or a config file that has a time stamp in the future and make is says it up to date while the make rules say "no your not".

If you are compiling the source on a disk that is on another machine then the times for the two machines are 35000 seconds apart.  The other machine is saving files using its local clock, while your machine has a different time.  Make expects system times to be less that a second apart.

Hope this helps.

---

### Post by bluethundr on 2010-12-08
> **lensman3 said:**
> The computer time is about 35000 seconds in the future.  35000 is about 1/2 a day.  Try resetting the system clock to the correct time.  Next start from a clean make.  The command should be "make clean" which should get ride of all the .o files and libraries.  Then try a new make.  If you get the same error then clean it again.  

You need to run the touch command on the c/cpp files.  This is tricky because touch doesn't have a directory recursive mode.  It may be easier to reinstall the source.  The error indicates that you have a .o, a lib files, or a config file that has a time stamp in the future and make is says it up to date while the make rules say "no your not".

If you are compiling the source on a disk that is on another machine then the times for the two machines are 35000 seconds apart.  The other machine is saving files using its local clock, while your machine has a different time.  Make expects system times to be less that a second apart.

Hope this helps.


Hi and thanks for your help!! I fixed the date issue but unfortunately this barely moved the needle on this problem.

I put together a web page that details this problem, if anyone has the time to look at it and a clue by four on this issue said clue by four would be immensely appreciated.

[bluethundr's debuild isue]("http://summitnjhome.com/debuild/index.html")

thanks!!!

---

