---
title: "X2GO update failed with unmet dependencies"
date: 2023-06-21
forum: Server Platforms
---

### Post by traceymccabe2 on 2023-06-21
I hope someone on here can help me with this as I searched for hours and I cannot find a solution.

About 2 weeks ago I noticed updates started failing on my Ubuntu 20.04.6 LTS server.  Upon investigation I found the X2GO update was failing and stopping all updates with the following messages:
```
The following packages have unmet dependencies:
 libx2go-log-perl : Depends: x2goserver-common (>= 4.1.0.4-0~1975~ubuntu20.04.1) but 4.1.0.3-5 is installed
 libx2go-server-db-perl : Depends: x2goserver-common (>= 4.1.0.4-0~1975~ubuntu20.04.1) but 4.1.0.3-5 is installed
 libx2go-server-perl : Depends: libx2go-log-perl (< 4.1.0.3-5.1~) but 4.1.0.4-0~1975~ubuntu20.04.1 is installed
                       Depends: libx2go-server-db-perl (< 4.1.0.3-5.1~) but 4.1.0.4-0~1975~ubuntu20.04.1 is installed
 x2golxdebindings : Depends: x2goserver (>= 3.0.99.6-0~) but it is not installed
 x2goserver-extensions : Depends: x2goserver (< 4.1.0.3-5.1~) but it is not installed
                         Depends: x2goserver (>= 4.1.0.3-5) but it is not installed
 x2goserver-fmbindings : Depends: x2goserver (< 4.1.0.3-5.1~) but it is not installed
                         Depends: x2goserver (>= 4.1.0.3-5) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
```

I ran apt --fix-broken install which seemed to fix everything as I had no errors after updating all packages and rebooting, however x2goserver failed to start and I couldn't find any logs as to why.

Attempted to reinstall x2go and I get the below errors which are similar to above:
```
tracey@dServer:~$ sudo apt-get install x2goserver x2goserver-xsession x2golxdebindings
[sudo] password for tracey:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 x2goserver : Depends: x2goserver-x2gokdrive (< 4.1.0.5-0~1987~ubuntu20.04.1.1~) but it is not going to be installed
              Depends: x2goserver-x2gokdrive (>= 4.1.0.5-0~1987~ubuntu20.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


I then removed the following repositories from the sources.list.d directory:
```
-rw-r--r-- 1 root root 124 May 16 12:18 x2go-ubuntu-stable-focal.list
-rw-r--r-- 1 root root 124 May 16 12:18 x2go-ubuntu-stable-focal.list.save
```


After an apt update I tried again to install again and got the following errors with more unmet dependencies:
```
tracey@dServer:/etc/apt/sources.list.d$ sudo apt install x2goserver
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 x2goserver : Depends: libx2go-server-perl (< 4.1.0.3-5.1~) but 4.1.0.5-0~1987~ubuntu20.04.1 is to be installed
              Depends: x2goserver-common (< 4.1.0.3-5.1~) but 4.1.0.5-0~1987~ubuntu20.04.1 is to be installed
              Depends: x2goserver-x2goagent (< 4.1.0.3-5.1~) but 4.1.0.5-0~1987~ubuntu20.04.1 is to be installed
              Recommends: x2goserver-extensions (< 4.1.0.3-5.1~) but it is not going to be installed
              Recommends: x2goserver-extensions (>= 4.1.0.3-5) but it is not going to be installed
              Recommends: x2goserver-fmbindings (< 4.1.0.3-5.1~) but it is not going to be installed
              Recommends: x2goserver-fmbindings (>= 4.1.0.3-5) but it is not going to be installed
              Recommends: x2goserver-printing (< 4.1.0.3-5.1~) but it is not going to be installed
              Recommends: x2goserver-printing (>= 4.1.0.3-5) but it is not going to be installed
              Recommends: x2goserver-xsession (< 4.1.0.3-5.1~) but it is not going to be installed
              Recommends: x2goserver-xsession (>= 4.1.0.3-5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```


I added the x2go repository (sudo add-apt-repository ppa:x2go/stable), updated apt and tried again with these now familiar errors:
```
tracey@dServer:/etc/apt/sources.list.d$ sudo apt install x2goserver
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 x2goserver : Depends: x2goserver-x2gokdrive (< 4.1.0.5-0~1987~ubuntu20.04.1.1~) but it is not going to be installed
              Depends: x2goserver-x2gokdrive (>= 4.1.0.5-0~1987~ubuntu20.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

When I try to manually start the service it tell me it is masked and wont start:
```
tracey@dServer:/etc/apt/sources.list.d$ sudo service x2goserver start
Failed to start x2goserver.service: Unit x2goserver.service is masked.
```

Any suggestions on what I can do to get x2go to install and start would be appreciated?

Thanks
Mr. Tracey McCabe

---

### Post by slickymaster on 2023-06-21
*Thread moved to **Server Platforms**.*

---

### Post by TheFu on 2023-06-21
Interesting.
To install the x2go PPA and server, use:
```
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goserver x2goserver-xsession
```

To install the x2go PPA and client, use:
```
sudo add-apt-repository ppa:x2go/stable
sudo apt-get update
sudo apt-get install x2goclient

```
I'm not seeing any issues.

The "x2go server" has Linux Mint 21.1 (22.04-based) and the x2go client is using 20.04 with fvwm.
I'm using the PPA for both systems.  I also have ssh-keys setup and checked the "Try auto login (via SSH Agent or default ssh keys) and I set the Connect to be WAN with 4k-png for compression.  Works great.

The first thing I'd ask is have you purged any prior x2go installs, added the stable PPA and already setup ssh connections between the 2 systems?  If ssh is already working, especially using ssh-keys, then you'll have removed much of the places where issues can happen.

---

### Post by traceymccabe2 on 2023-06-21
I appreciate the reply and suggestion TheFu, I should have thought of purging it. 

 However I did purge the x2goserver, x2goserver-xsessions, and x2goserverlxdebindings, then rebooted and tried to reinstall in and it still fails with the same error:

[INDENT]tracey@dServer:~$ sudo apt install x2goserver x2goserver-xsession x2golxdebindings
[sudo] password for tracey:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 x2goserver : Depends: x2goserver-x2gokdrive (< 4.1.0.5-0~1987~ubuntu20.04.1.1~) but it is not going to be installed
              Depends: x2goserver-x2gokdrive (>= 4.1.0.5-0~1987~ubuntu20.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
[/INDENT]
 
So I still cannot get it to install or start.

---

### Post by MAFoElffen on 2023-06-21
In Ubuntu 18.04 LTS, you 'had" to use the PPA, because that was where they were available for Bionic... But since 20.04 LTS, the x2go packages were added to the default Ubuntu Universe Repo (Focal through current)... 
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt-cache show x2go*
Package: x2goclient
Architecture: amd64
Version: 4.1.2.2-2build1
Priority: extra
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 2364
Depends: libc6 (>= 2.15), libcups2 (>= 1.4.0), libgcc-s1 (>= 3.3.1), libldap-2.5-0 (>= 2.5.4), libqt5core5a (>= 5.15.1), libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2), libqt5network5 (>= 5.14.1), libqt5svg5 (>= 5.6.0~beta), libqt5widgets5 (>= 5.15.1), libqt5x11extras5 (>= 5.6.0), libssh-4 (>= 0.8.0), libstdc++6 (>= 5.2), libx11-6, libxpm4, openssh-client, nxproxy
Recommends: openssh-server, rdesktop | freerdp-x11
Suggests: pinentry-x2go
Conflicts: x2goclient-gtk
Replaces: x2goclient-gtk
Filename: pool/universe/x/x2goclient/x2goclient_4.1.2.2-2build1_amd64.deb
Size: 1125300
MD5sum: ebfc38bfb2b7951e21ba66d08af8f1fe
SHA1: 56f9a0acdcaa21ef4523d16d71846516ba0de337
SHA256: 11818f8c31f7c001f04255cc27108e4c478f3124f770de41396b7d7cf7c28fae
SHA512: ae9c220ddc682576a29ef8fe35f50bff0f2156ce0904dce0eac9c35bd7a0b6a224d377042c011ba72ce21dcfba0f322d4a7cc335a0e43a2706bf5a50b988423e
Homepage: https://wiki.x2go.org/
Description-en: X2Go Client application (Qt5)
 X2Go is a serverbased computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 X2Go Client is a graphical client (Qt5) for the X2Go system.
 You can use it to connect to running sessions and start new sessions.
Description-md5: 382c392ada5d061dcc91d9fd62249894

Package: x2goserver
Architecture: amd64
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 420
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: bc, libfile-basedir-perl, libfile-which-perl, libswitch-perl, libtry-tiny-perl, libx2go-server-perl (<< 4.1.0.3-5.1~), libx2go-server-perl (>= 4.1.0.3-5), lsb-base, lsof, net-tools, openssh-client, openssh-server, perl, psmisc, pwgen, x2goserver-common (<< 4.1.0.3-5.1~), x2goserver-common (>= 4.1.0.3-5), x2goserver-x2goagent (<< 4.1.0.3-5.1~), x2goserver-x2goagent (>= 4.1.0.3-5), xauth, xkb-data, debconf (>= 0.5) | debconf-2.0
Recommends: fontconfig, sshfs, x11-apps, x11-session-utils, x11-utils, x11-xfs-utils, x11-xkb-utils, x11-xserver-utils, x2goserver-extensions (<< 4.1.0.3-5.1~), x2goserver-extensions (>= 4.1.0.3-5), x2goserver-fmbindings (<< 4.1.0.3-5.1~), x2goserver-fmbindings (>= 4.1.0.3-5), x2goserver-printing (<< 4.1.0.3-5.1~), x2goserver-printing (>= 4.1.0.3-5), x2goserver-xsession (<< 4.1.0.3-5.1~), x2goserver-xsession (>= 4.1.0.3-5), xfonts-base, xinit
Suggests: pulseaudio-utils, rdesktop
Breaks: x2godesktopsharing (<< 3.1.1.2-0~), x2goserver-compat (<< 4.0.1.99~), x2goserver-home, x2goserver-one, x2goserver-pyhoca (<< 4.0.1.99~)
Replaces: x2goserver-compat, x2goserver-home, x2goserver-one, x2goserver-pyhoca
Filename: pool/universe/x/x2goserver/x2goserver_4.1.0.3-5_amd64.deb
Size: 74380
MD5sum: 19449a9d2465c418ad4fcf61825c1d3f
SHA1: 6a9aa4dbc951bff4fda1f66c36219adb5c87c379
SHA256: 7ae3364577711155a655c431462f392c775e5e12e9e70ae67f64fb090d695d76
SHA512: 3fd8ceebc6dfc80347abd518f92dddfae5ee2ed5dbb498d3c8844e9d3ee2e8b7e628e4d4c3131600087eaed11a4b1509cd18e9b6fbc47efd9dc4c9c8836eaf2a
Homepage: http://wiki.x2go.org
Description-en: X2Go Server
 X2Go is a server based computing environment with
   - session resuming
   - low bandwidth support
   - session brokerage support
   - client-side mass storage mounting support
   - client-side printing support
   - audio support
   - authentication by smartcard and USB stick
 .
 This package contains the main daemon and tools for X2Go server-side
 session administrations.
Description-md5: 45d00ad020b6d29e0eaf5898993e6fd9

Package: x2goserver-common
Architecture: all
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Source: x2goserver
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 52
Depends: adduser
Breaks: x2goserver (<< 4.1.0.0-0~)
Replaces: x2goserver (<< 4.1.0.0-0~)
Filename: pool/universe/x/x2goserver/x2goserver-common_4.1.0.3-5_all.deb
Size: 10888
MD5sum: 1d5ff048fb3497f06886a05e5036dd27
SHA1: 74ba894388422a82f4716f918c479f4d6bce014e
SHA256: f5c5f3630ebce1e361a061ec20e13ddc3fc15f01760c2a036dab848841de3031
SHA512: 18e24a5f0fd7d754f574976dfdfc97c4d0c4c3acbabcacb27a7111f6c90a9d94f8f58e99fb1cfbaa7db77a13a0f6641d27e05874de4b1754809304d6e78d2040
Homepage: http://wiki.x2go.org
Description-en: X2Go Server (common files)
 X2Go is a server based computing environment with
   - session resuming
   - low bandwidth support
   - session brokerage support
   - client-side mass storage mounting support
   - client-side printing support
   - audio support
   - authentication by smartcard and USB stick
 .
 This package contains common files needed by the X2Go Server
 and the X2Go::Server Perl API.
Description-md5: d7d00e49d7e3fdc9a13fbd37adc2c53c

Package: x2gobroker-common
Architecture: all
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Source: x2gobroker
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 107
Breaks: python-x2gobroker (<< 0.0.4.0~)
Replaces: python-x2gobroker (<< 0.0.4.0~)
Filename: pool/universe/x/x2gobroker/x2gobroker-common_0.0.4.3-2_all.deb
Size: 25734
MD5sum: af7e51deeb8c5394bf083cbd12a819b1
SHA1: 67c67e6d5e1085e8a34c5b1138dad4ae94df27e2
SHA256: 0401d4ddbd069af13eb17ea32bf85014d0a72770311df0d5cc6abce062f23f54
SHA512: 1db2a8c9ea42cf9e89eaa325be79f52e8d4c77adc4867bddb520815d167b2089916ce0f45dd9ae3eda83b4f919994b784d3e1064379b4350830f476cc4d74109
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (common files)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This package contains x2gobroker common files.
Description-md5: 212f333f82fadfa738073081f1c3a042

Package: x2gobroker
Architecture: all
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 132
Depends: python3, python3-setproctitle, python3-tornado, python3-wsgilog, python3-x2gobroker (>= 0.0.4.3-2), python3-x2gobroker (<< 0.0.4.3-2.1~)
Suggests: apache2 | httpd
Filename: pool/universe/x/x2gobroker/x2gobroker_0.0.4.3-2_all.deb
Size: 33428
MD5sum: 4a8b301ae12213cda59f4a8480335f7f
SHA1: aa63ddad0d935ca5e07dfb5b6a35cca41585b957
SHA256: 4e057ed373458381df7e9f13971602e153eb0a7bc532d1856534fbd7f5fe056c
SHA512: 92382bb5d45c3233c62cda404b9e29a4a11833c56e48fa4503b49b77772eb9d356e0e865cd73430102baa1fc3b4d4cb0d5e83a8da1661b73d313df6a081e0e85
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (executable)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This package contains the x2gobroker executable.
Description-md5: 5c2106a824e3d63e1f47c7aa76f46dbe

Package: x2gobroker-agent
Architecture: amd64
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Source: x2gobroker
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 122
Depends: libc6 (>= 2.34), python3, python3-setproctitle, python3-paramiko, perl, adduser, libfile-which-perl
Suggests: x2goserver (>= 4.0.1.16-0~)
Filename: pool/universe/x/x2gobroker/x2gobroker-agent_0.0.4.3-2_amd64.deb
Size: 28016
MD5sum: 21fec2aef1a2ba4d7188eb2cd1f558a6
SHA1: 6f623128e034878f252af6b96ad13665fbf7ece8
SHA256: 1ea955105ed1f1b31e72a857e55a040c72b969c0d32661a9632211f27fd336da
SHA512: 7cb1beb813b3157326d928b4afced9d31152d19972554ea75c0a502fee85e247c3e8ee50dc7df7aab43e0d6bd42e2688d1f9dbfca659f5a4151af208f75fa635
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (remote agent)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This package contains a setuid agent command that extends X2Go Session Broker
 functionality. It has to be installed on X2Go Servers that shall be
 controlled via a session broker.
 .
 The broker agent provides means to the X2Go Session Broker for controlling
 the X2Go Server it is installed on (e.g. suspend/terminate sessions, deploy
 SSH login keys, detect server load, detect running/suspended sessions
 of connecting users, etc.).
 .
 WARNING: This package installs a setuid wrapper
 (/usr/lib/x2go/broker/x2gobroker-agent) on your system. This setuid wrapper
 aims to be a secure replacement for the deprecated suidperl executable that
 was removed from Perl (>= 5.12).
 .
 This wrapper is only able to execute the Perl script
 /usr/lib/x2go/broker/x2gobroker-agent.pl. For running properly,
 x2gobroker-agent.pl needs setuid root privileges.
 .
 If you hesitate to install this package, study the code of the named wrapper
 and the named Perl script beforehand. Note that the X2Go session broker will
 lack functionality, but it will work without this x2gobroker-agent component
 installed on your to-be-managed X2Go servers.
Description-md5: bc3987a1115c36bc0cfe4795b6deab6c

Package: x2gobroker-authservice
Architecture: all
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Source: x2gobroker
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 118
Depends: adduser, lsb-base, python3, python3-setproctitle, python3-pampy, python3-x2gobroker (>= 0.0.4.3-2), python3-x2gobroker (<< 0.0.4.3-2.1~)
Suggests: x2gobroker-daemon
Filename: pool/universe/x/x2gobroker/x2gobroker-authservice_0.0.4.3-2_all.deb
Size: 21870
MD5sum: 9570b1c29b1a5c79fd4bf711a66b3b2b
SHA1: f6d82c7f9b36dc0489a2f1046cded44477556a75
SHA256: fb6db63263e0cb044e61a6b87487d8684b0df52cfcc820136f23faa060b5b5a0
SHA512: 94da0b108147fae4af209cbc342df471f12e9858d969463e94de025610a3f42f592d7d4eefed4dbabb278d015489e7d624b11822f49ff2a8ee276c9576b1c5ba
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (PAM authentication service)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This package contains the authentication service
 against the PAM system.
Description-md5: 6d3f615b878ca9380a8a15ddaba03f47

Package: x2gobroker-daemon
Architecture: all
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Source: x2gobroker
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 113
Depends: adduser, lsb-base, x2gobroker (>= 0.0.4.3-2), x2gobroker (<< 0.0.4.3-2.1~)
Recommends: x2gobroker-authservice
Suggests: x2gobroker-loadchecker
Filename: pool/universe/x/x2gobroker/x2gobroker-daemon_0.0.4.3-2_all.deb
Size: 21736
MD5sum: 08619f003aa48ff50156c5ff4198a584
SHA1: 768310acf434370e431f4b8524b0164baccb8abc
SHA256: 5611d930b9b54f12f260e2079d1613adff9c5e397f0d3a14a933013999e094b3
SHA512: fb11587ffbdbc489f3e35924db66cf61e99d949a5ffc17ef10113c22a736ddcd1725fe6ffedb7b52e807a316f30932a7d8c9d59e402c861cc9684f98af8e0057
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (standalone daemon)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This package contains the start-stop script that
 installs the X2Go Session Broker as standalone
 daemon.
Description-md5: f0e09120287b3767829a8a2304bdb300

Package: x2gobroker-loadchecker
Architecture: all
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Source: x2gobroker
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 122
Depends: adduser, lsb-base, python3, python3-setproctitle, python3-x2gobroker (>= 0.0.4.3-2), python3-x2gobroker (<< 0.0.4.3-2.1~)
Suggests: x2gobroker-daemon
Filename: pool/universe/x/x2gobroker/x2gobroker-loadchecker_0.0.4.3-2_all.deb
Size: 23298
MD5sum: b3d00f54d1efd848c58613b0adf1ac5e
SHA1: 1fbddbbd24369da7d4192a03e55ff01bec04cdb5
SHA256: 86fded2660ac4c6595c8144808bdec6920a127eee39d51d2b5bad2288d0874bb
SHA512: 41260e966be1dc39420063b9e1c64c762d1d4742320108455b6bb965d94e0579b7868650c02e20bd7d1a4e1005434c7d1773e534d3b726a7e9ae4ef0f4e27f31
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (load checker service)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This package contains the load checker service required for broker setups
 with dynamic load balancing.
Description-md5: 52e003135ac051d8f6afb2ed6116ef7e

Package: x2gobroker-ssh
Architecture: amd64
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Source: x2gobroker
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 117
Depends: libc6 (>= 2.34), debconf (>= 0.5) | debconf-2.0, adduser, procps, x2gobroker (>= 0.0.4.3-2), x2gobroker (<< 0.0.4.3-2.1~)
Filename: pool/universe/x/x2gobroker/x2gobroker-ssh_0.0.4.3-2_amd64.deb
Size: 28266
MD5sum: 0e6eec2374bfdc84ad0dc4085296ed01
SHA1: d7428997f05bdfaf4a59cf2b2f2e472741a0ab36
SHA256: 0d5e9f8c2e5758f14b7af0e6ca35a3b53ec39bc81ac3d72f0eeaa98655c070ed
SHA512: 6108e25592900d0236f23758cd33459c07b524d702231c4e4b1e5504acbe158d68a4fc058e7f4ae0b3b361244c76f195fd426e20093bdab38da3a705be0fd850
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (SSH broker)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This add-on package provides fully-featured SSH brokerage
 support (with access to broker agents on remote X2Go
 Servers).
Description-md5: 379ea267b84064f4795a20bbdf1600e3

Package: x2gobroker-wsgi
Architecture: all
Version: 0.0.4.3-2
Priority: optional
Section: universe/misc
Source: x2gobroker
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 97
Depends: python3, adduser, x2gobroker (>= 0.0.4.3-2), x2gobroker (<< 0.0.4.3-2.1~)
Recommends: libapache2-mod-wsgi-py3
Filename: pool/universe/x/x2gobroker/x2gobroker-wsgi_0.0.4.3-2_all.deb
Size: 16438
MD5sum: b3ee118e194f3200c45d9c03c2ee8d30
SHA1: d50d4de01636444a1e1a00c4eac7dedf657ad3b7
SHA256: 0e3b09a7bda0b53ef9af04a25327c2b13e2e97766953990754e27f9b162af929
SHA512: db8a9ef14393226239278ad2027dfee91a695c6873609ff30ca398a13215cc4c693257c79a68e76105c50aecf7f300cba0d01ddb68242961cbcc62f1b92df384
Homepage: https://wiki.x2go.org/
Description-en: X2Go Session Broker (WSGI)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - client side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 The session broker is a server tool for X2Go that tells your X2Go Client
 application in a terminal server cluster what servers and session types are
 most appropriate for the user in front of the X2Go terminal.
 .
 A session broker is most useful in load balanced X2Go server farms.
 .
 This package contains an Apache2 configuration that
 installs the X2Go Session Broker as a WSGI application
 into a running Apache2 httpd.
Description-md5: 33390b8d83fb76ec047fab58127be77c

Package: x2godesktopsharing
Architecture: amd64
Version: 3.2.0.0-2build1
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 640
Depends: libc6 (>= 2.14), libgcc-s1 (>= 3.0), libqt5core5a (>= 5.12.2), libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2), libqt5network5 (>= 5.0.2), libqt5widgets5 (>= 5.2.0~alpha1), libstdc++6 (>= 5), x2goserver (>= 4.0.0.0-0~)
Recommends: x2goserver-desktopsharing (>= 4.1.0.3~)
Filename: pool/universe/x/x2godesktopsharing/x2godesktopsharing_3.2.0.0-2build1_amd64.deb
Size: 418716
MD5sum: aab1845cf2d88d9891ea2d67ac363476
SHA1: a77fb3e8c5bb02b526d6ddc799f92d66c9b28633
SHA256: 9804ebc42be49f00dfdec71f648dc627c3e910e6d7153e44a38930f29133117a
SHA512: 4ed2f2edc92b688ed74a69216477be61dfae670973896323c8288841b80963e9e5d77b10886a9f1208bc693c2fd0398f4f871d835687f166b1e0de2f7fc2dbdd
Homepage: https://wiki.x2go.org
Description-en: Share X11 desktops with other users via X2Go
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session brokerage support
    - client side mass storage mounting support
    - audio support
    - authentication by smartcard and USB stick
 .
 X2Go Desktop Sharing is an X2Go add-on tool that allows a user to
 grant other X2Go users access to the current session (shadow session
 support). The current session may be an X2Go session itself or simply
 a local X11 session.
Description-md5: 155522a7f7e2340089b948c3d0e780f9

Package: x2goserver-desktopsharing
Architecture: all
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Source: x2goserver
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 71
Depends: debconf (>= 0.5) | debconf-2.0, x2goserver (>= 4.0.0.0-0~), x2godesktopsharing (>= 3.2.0.0~)
Breaks: x2godesktopsharing (<< 3.2.0.0~)
Replaces: x2godesktopsharing (<< 3.2.0.0~)
Filename: pool/universe/x/x2goserver/x2goserver-desktopsharing_4.1.0.3-5_all.deb
Size: 14420
MD5sum: 2de47c2036c1c40e9fee9d6bc610959e
SHA1: f9ff016aa7ace4687f8b9f06033b26866bf881ea
SHA256: 1750f1e512142950123aed959fa752250637a74883d802108d8267db888daa64
SHA512: f06162679aad0c2743c1a67f94e2e1f282a61303c16656ca633395be11ecf5d96a6c40a8c21d43706794a46bb2f5d6747f571cf8a5e697869cd1dedded5dad9a
Homepage: http://wiki.x2go.org
Description-en: Share X11 desktops with other users via X2Go
 X2Go is a server based computing environment with
   - session resuming
   - low bandwidth support
   - session brokerage support
   - client side mass storage mounting support
   - client-side printing support
   - audio support
   - authentication by smartcard and USB stick
 .
 X2Go Desktop Sharing is an X2Go add-on feature that allows a user to
 grant other X2Go users access to the current session (shadow session
 support). The user's current session may be an X2Go session itself or
 simply a local X11 session.
 .
 This package contains all the integration and configuration logics
 of a system-wide manageable desktop sharing setup.
Description-md5: e495e3809c5ff5d54bd9f4680b22d8c0

Package: x2goserver-x2goagent
Architecture: amd64
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Source: x2goserver
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 69
Depends: nxagent (>= 2:3.5.99.17~)
Suggests: x2goserver
Breaks: x2goagent (<< 2:3.5.99.2~), x2goserver (<< 4.0.1.99~)
Replaces: x2goagent (<< 2:3.5.99.2~), x2goserver (<< 4.0.1.99~)
Filename: pool/universe/x/x2goserver/x2goserver-x2goagent_4.1.0.3-5_amd64.deb
Size: 11048
MD5sum: a95c6d4fc6ed5e6301456669ea693276
SHA1: e79d8e2072ef7d19bfc4c846a8972ead4ebcf34c
SHA256: 38bcb103212a1ffd92fc1330c456a9fe3e567e8bdd4405195dfd4316bf819bb4
SHA512: 32932eb2706f75fdc8d5a55b5aef55dcffeb25ac1d4c2fe9b42591f569b8cfbe93a6ef6f2fc9c7ef4abca30aa73fb228acff3544c238a0d52d5880558da28a39
Homepage: http://wiki.x2go.org
Description-en: X2Go Server's X2Go Agent
 X2Go is a software suite that uses NX technology for remote desktop
 computing.
 .
 NX technology implements a very efficient compression of the X11
 protocol. This increases performance when using X applications over a
 network, especially a slow one.
 .
 X2Go Agent functionality has been completely incorporated into NX
 agent's code base. If the nxagent binary is executed under the name of
 `x2goagent', the X2Go functionalities get activated.
 .
 This package is a wrapper that activates X2Go branding in nxagent.
 Please refer to the nxagent package's description for more information
 on NX.
Description-md5: 64b6fd9e745f943a5d7ec629249168ce

Package: x2goserver-extensions
Architecture: all
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Source: x2goserver
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 67
Depends: x11-xkb-utils, x2goserver (<< 4.1.0.3-5.1~), x2goserver (>= 4.1.0.3-5)
Filename: pool/universe/x/x2goserver/x2goserver-extensions_4.1.0.3-5_all.deb
Size: 9160
MD5sum: 5199f014a1d20826e7eb6ec0808ce6e4
SHA1: c04f26884e2f0951e28dba42afd7369ce8e3daef
SHA256: 571e6f45bd4fe5a1aa3368f5b2f800e0bdbdc5f59f4e3aa5118aedec164da71f
SHA512: 25441d15ab4d74337d7948207992dad3541c375d2535547d0703c6c0ee00de419b1ca8563b0139941df7671dd3d65826df3f3e048b6e30e01fad82d6cd53f09a
Homepage: http://wiki.x2go.org
Description-en: X2Go Server (extension support)
 X2Go is a server based computing environment with
   - session resuming
   - low bandwidth support
   - session brokerage support
   - client-side mass storage mounting support
   - client-side printing support
   - audio support
   - authentication by smartcard and USB stick
 .
 The X2Go Server extension namespace offers contributors to add script
 functionality to X2Go that is not needed/ignored by the legacy X2Go
 client (x2goclient).
Description-md5: a701d0e01c127ed3226342d165a3ca38

Package: x2goserver-fmbindings
Architecture: all
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Source: x2goserver
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 40
Depends: desktop-file-utils, x2goserver (<< 4.1.0.3-5.1~), x2goserver (>= 4.1.0.3-5), xdg-utils
Filename: pool/universe/x/x2goserver/x2goserver-fmbindings_4.1.0.3-5_all.deb
Size: 5676
MD5sum: b6f4669a40b55f98e6ffbdde3688b156
SHA1: 5ca3285cf24f28ac05ddfa0a9da7d1030aa1b3c6
SHA256: 39fad1eb8fa9155ff0b0caaf30ec9466c000b71f5adfff8368e7bea295dbdede
SHA512: 32c53f6e22b6241df63c68ed6139d987113af540005b2637b9056c25be9ac84f48c3032e9b238257fc24024b22d3169be57cb2053a13b50d8ded559da34d3ac8
Homepage: http://wiki.x2go.org
Description-en: X2Go Server (file manager bindings)
 X2Go is a server based computing environment with
   - session resuming
   - low bandwidth support
   - session brokerage support
   - client-side mass storage mounting support
   - client-side printing support
   - audio support
   - authentication by smartcard and USB stick
 .
 x2goserver-fmbindings contains generic MIME type information for X2Go's
 local folder sharing. It can be used with all freedesktop.org compliant
 desktop shells.
 .
 However, this package will be superseded by other, more specific destkop
 binding components, if installed and being used with the corresponding
 desktop shell:
 .
   - under LXDE by x2golxdebindings
   - under GNOMEv2 by x2gognomebindings
   - under MATE by x2gomatebindings
   - under KDE4/5 by plasma-widget-x2go
Description-md5: 325408debc2fe9ce6e3237f9a172c81d

Package: x2goserver-printing
Architecture: all
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Source: x2goserver
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 57
Depends: adduser, x2goserver (<< 4.1.0.3-5.1~), x2goserver (>= 4.1.0.3-5)
Suggests: cups-x2go
Breaks: x2goprint
Replaces: x2goprint
Filename: pool/universe/x/x2goserver/x2goserver-printing_4.1.0.3-5_all.deb
Size: 10484
MD5sum: 2735a7d63734beece7edc5390a147729
SHA1: 437f358360d16fa338a11d63387583f87cf749db
SHA256: 2c0bc107e83f21b8cd3cd9a6f3c2cec945c5b5189e58e8eecda095de399c961a
SHA512: 590839880a4169c650e4b8202d65784c9884d382d93e844af3c766a94855ae2a4a697400a327254938b33f48cca0d175e7440d73e55f9ff29e60d6a2f2e0578b
Homepage: http://wiki.x2go.org
Description-en: X2Go Server (printing support)
 X2Go is a server based computing environment with
   - session resuming
   - low bandwidth support
   - session brokerage support
   - client-side mass storage mounting support
   - client-side printing support
   - audio support
   - authentication by smartcard and USB stick
 .
 The X2Go Server printing package provides client-side printing support
 for X2Go.
 .
 This package has to be installed on X2Go Servers that shall be able to
 pass X2Go print jobs on to the X2Go client.
 .
 This package co-operates with the cups-x2go CUPS backend. If CUPS server
 and X2Go Server are hosted on different machines, then make sure you
 install this package on the X2Go Server/s (and the cups-x2go package on
 the CUPS server).
Description-md5: f7b009cfadcfa214f2938715c380736e

Package: x2goserver-xsession
Architecture: all
Version: 4.1.0.3-5
Priority: optional
Section: universe/x11
Source: x2goserver
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 54
Depends: dbus, perl:any, x11-common, x2goserver (<< 4.1.0.3-5.1~), x2goserver (>= 4.1.0.3-5)
Filename: pool/universe/x/x2goserver/x2goserver-xsession_4.1.0.3-5_all.deb
Size: 8044
MD5sum: f441b3dd45ad47fdf9f2cd883b93a22b
SHA1: 59024dc12ca05b6885a105b2a677ae0bfbb0c8dd
SHA256: 840f0b2830dd2fc128942fb5f640dc237b8ca2f2831fe37aa36569f4eea01307
SHA512: d659e2e0398ed10827ce652af309daefba09b8b44d940beba4f94f0e614d86c8200e0cc33665ae316185a93ea7a0f89c3ddd8751f38f44dc4fd03c303a850126
Homepage: http://wiki.x2go.org
Description-en: X2Go Server (Xsession runner)
 X2Go is a server based computing environment with
   - session resuming
   - low bandwidth support
   - session brokerage support
   - client-side mass storage mounting support
   - client-side printing support
   - audio support
   - authentication by smartcard and USB stick
 .
 This X2Go Server add-on enables Xsession script handling when starting
 desktop sessions with X2Go.
 .
 Amongst others the parsing of Xsession scripts will enable
 desktop-profiles, ssh-agent startups, gpgagent startups and many more
 Xsession related features on X2Go session login automagically.
Description-md5: e5b4355d735c72460ae04f09acddca28

Package: x2gothinclient-cdmanager
Architecture: amd64
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 66
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: libc6 (>= 2.34), libgcc-s1 (>= 3.3.1), libqt5core5a (>= 5.15.1), libqt5gui5 (>= 5.0.2) | libqt5gui5-gles (>= 5.0.2), libqt5widgets5 (>= 5.15.1), libstdc++6 (>= 5), lsb-base, lsscsi, eject, libfile-path-expand-perl
Breaks: x2gocdmanager (<< 1.5.0.0)
Replaces: x2gocdmanager (<< 1.5.0.0)
Filename: pool/universe/x/x2gothinclient/x2gothinclient-cdmanager_1.5.0.1-7_amd64.deb
Size: 16668
MD5sum: 73bd72ade9ecab2a634b293ee45ffd0a
SHA1: 8fca79156d88f1dabf2e655297f544298202184f
SHA256: c60f85818f62781a83268b20ef15333b08629304b04ca3e329f4051a33782164
SHA512: 8ee4a499f69cfce6a1a9b36be730a96392d0ea9f55da15ebff913bfff351bfc67cba6cac632ba524642ebdf4d3d8fcb01ec4ca30d5da1f607c00e853759ae780
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: clientside daemon enabling automatic CD-Rom mounting
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-cdmanager:
 .
 IMPORTANT: Use this Package only for the x2go Thin Client Environment
 (This package is meant to be installed in a CHROOT environment!!!)
 .
 This package adds a client-side daemon to your X2Go Thin Client that enables
 automatic CD-ROM mounting within Thin Client X2Go sessions.
Description-md5: 86dc6826559fc6107768c2fb1f5f5876

Package: x2gothinclient-chroot
Architecture: all
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 41
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: lsb-base, nfs-common, patch, plymouth, plymouth-themes-all, pulseaudio-x11 | pulseaudio, dbus-x11, dbus-user-session, syslinux, x2gothinclient-displaymanager | x2gothinclient-minidesktop, locales, policykit-1
Recommends: acpid, gnupg-agent, pinentry-x2go, pcscd, pcsc-tools, scdaemon, gpgsm, less, mc, memtest86+, vim, x11-xserver-utils, x2gothinclient-cdmanager, x2gothinclient-usbmount, x2gothinclient-smartcardrules, ntp
Suggests: firmware-linux-nonfree, firmware-bnx2, firmware-ralink, firmware-realtek, intel-microcode, amd64-microcode
Filename: pool/universe/x/x2gothinclient/x2gothinclient-chroot_1.5.0.1-7_all.deb
Size: 7372
MD5sum: 945df742cac005e865b88e0ead47ec6c
SHA1: fa5ce0fa83bb06e4f973bce1f310f7575649daef
SHA256: f80b8004e45e22fd1029dcd0b883934dc9cdf54dd80e29ac84ce8ca3878d1dff
SHA512: 24ebda2bc5bcf445076a9fe3171f6250aac2b3ff2d2c863783f8def304bcf8602b0114b277e8ab05576f730039009cefbde9965316d8e11cafbe5e6f45373b5b
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: Install X2Go Thin Client chroot (metapackage)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-chroot:
 .
 This metapackage installs all X2Go TCE dependencies. This
 package is used in the X2Go Thin Client's chroot.
Description-md5: 71c4ffc841bd25631b54e0ebb2396101

Package: x2gothinclient-displaymanager
Architecture: all
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 79
Provides: x2gothinclient
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: debconf (>= 0.5) | debconf-2.0, lsb-base, psmisc, pinentry-x2go, xauth, xinit, locales, dbus-x11, policykit-1, libfile-path-expand-perl, x2gothinclient-common (>= 1.5.0.1-7), x2gothinclient-common (<< 1.5.0.1-7.1)
Breaks: x2gothinclient (<< 1.5.0.0), x2gothinshutdown
Replaces: x2gothinclient (<< 1.5.0.0), x2gothinshutdown
Filename: pool/universe/x/x2gothinclient/x2gothinclient-displaymanager_1.5.0.1-7_all.deb
Size: 14236
MD5sum: 43a655cf47303d1751571e65325071e4
SHA1: fe1c9c47fbe038689cc2b7dbf93ad43db8690b82
SHA256: 4c16c85612a10255dee24429bde840008c90ee722e585221ce1917868e6d8fb1
SHA512: 8fee6a6b3281e333fd65efcc993ab314884216724329be92b2d60cdd64b985e2e01ee2a38a405b58aced81ea2618faeeb329a7cee63e2146a110ae5c03c78efd
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: login daemon starting x2goclient in displaymanager mode
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-displaymanager:
 .
 IMPORTANT: Use this Package only for the X2Go Thin Client Environment
 (This package is meant to be installed in a CHROOT environment!!!)
 .
 This package starts X2Go Client in fullscreen mode---without window
 decorations, without menu and toolbar and optionally with enabled
 session broker support.
 .
 This package ships the core X2Go Thin Client daemon that guards over
 X2Go Client functionality.
 .
 X2Go Client in thin-client-mode will behave like xdm, kdm or gdm.
Description-md5: 2c1234c76aa18c9833366fdae564cfa1

Package: x2gothinclient-minidesktop
Architecture: all
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 76
Provides: lightdm-greeter
Pre-Depends: x2goclient
Depends: dconf-gsettings-backend | gsettings-backend, mate-desktop-environment-core, mate-icon-theme, mate-themes, mate-backgrounds, mate-media-pulse | hello, mate-settings-daemon-pulse | hello, murrine-themes, nuvola-icon-theme | hicolor-icon-theme, firefox-esr | firefox | chromium | x-www-browser, libglib2.0-bin, pavucontrol, pinentry-x2go, pulseaudio, xauth, xinit, x2gothinclient-common (>= 1.5.0.1-7), x2gothinclient-common (<< 1.5.0.1-7.1), lightdm
Recommends: alsa-tools
Conflicts: x2gothinclient
Breaks: x2gothinclient-minidesktop-mate
Replaces: x2gothinclient-minidesktop-mate
Filename: pool/universe/x/x2gothinclient/x2gothinclient-minidesktop_1.5.0.1-7_all.deb
Size: 9636
MD5sum: 12c92b32438b90b581ebc746cad057da
SHA1: 9ed00a6c72270e00206c1da7d8bd0bd6bd74dbd0
SHA256: 00880dd5d531cbb4c3af043ec63838405595b742d3597d8453db00668b8effa0
SHA512: fb18098cd8cbee096ddb77e572bbbaecb719f1548a568787bdafc0d47ad2a846db476e8c4fb97698d73696edd8cec511d59b91088864d632437a41845cd5a4fb
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: Minimal desktop for X2Go Thin Client chroot (based on MATE)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-minidesktop:
 ---------------------------
 This metapackage provides a minimal desktop (based on MATE) as the
 TCE's workspace area. From there you can launch X2Go Sessions, but
 you also have a set of basic applications that run on the thinclient
 CPU (e.g. Firefox (ESR) with Flash).
Description-md5: 9470ab90ac785b01691e22d73d7f3ae6

Package: x2gothinclient-usbmount
Architecture: all
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 38
Depends: udev, cryptsetup, libfile-path-expand-perl
Breaks: x2gousbmount (<< 1.5.0.0)
Replaces: x2gousbmount (<< 1.5.0.0)
Filename: pool/universe/x/x2gothinclient/x2gothinclient-usbmount_1.5.0.1-7_all.deb
Size: 9572
MD5sum: 6fbb0bf7c48ae79f8c706687facdd0b5
SHA1: 6950709d146213ddc04b7fbf5663e84fdfbf9d3e
SHA256: a72ff64dd370c2404a26aebaaca9b8dd3e151f571c2ea654acd7bcbb8040a84e
SHA512: 65b92f6889257eb300d00b4be2eb4b73a9b4f0bf70c703e8f93b58b3a5564a8fd8c8e67239f4685ba59906e3ae9373ebd609435fa9511264779440b3b0e92bf1
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: clientside usb mass-storage device mounting
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-usbmount:
 .
 IMPORTANT: Use this Package only for the x2go Thin Client Environment
 (This package is meant to be installed in a CHROOT environment!!!)
 .
 This package adds client-side USB mass storage device mounting using
 UDEV rules to your X2Go Thin Client.
Description-md5: dc28c9418afe3d1adfe2387498f5b308

Package: x2gothinclient-smartcardrules
Architecture: all
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 30
Depends: udev
Breaks: x2gosmartcardrules (<< 1.5.0.0)
Replaces: x2gosmartcardrules (<< 1.5.0.0)
Filename: pool/universe/x/x2gothinclient/x2gothinclient-smartcardrules_1.5.0.1-7_all.deb
Size: 6260
MD5sum: 08ff47c06824ac9a13fefe6cf669f012
SHA1: 4b83a6bb16c166e4b056f1eeb9f71673965ed3b8
SHA256: 919b27513bde6144f9323ad876baffcac944a9e685709cc6ef12b7a05382aa6e
SHA512: 55e52b5a35a095622e415809d28988b515a84d86e6f5c71bfc2f76e4fca1db4db5b1b5fd093f7de0936110222fbda0fdd5bc735e7dbaac7512c0417cc61d20e7
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: UDEV rules for smartcard readers
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-smartcardrules:
 .
 IMPORTANT: Use this Package only for the x2go Thin Client Environment
 (This package is meant to be installed in a CHROOT environment!!!)
 .
 This package provides UDEV rules for smartcard readers (devices that
 serve the purpose of ID-card based authentication).
Description-md5: bb3500f8b68d2f07c5972812dc7801c6

Package: x2gothinclient-common
Architecture: all
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 36
Depends: adduser, x2goclient (>= 4.0.1.2-0~)
Breaks: x2gothinclient (<< 1.5.0.0)
Replaces: x2gothinclient (<< 1.5.0.0)
Filename: pool/universe/x/x2gothinclient/x2gothinclient-common_1.5.0.1-7_all.deb
Size: 7034
MD5sum: d31978c3000f83cbb54cccd6930076e8
SHA1: 46315cace53e17ada24ea59af233618c438af372
SHA256: 20237abdf21b6305b9d8f0f3fcd5cad262821c7ef827c7226fe08e65d1e25ffe
SHA512: 982df6880c088da3773dc2d56a673f1622909be189a941146ce8f2e8fa0ddc0618eb2eca1d343dcebc837c47ab21f3a505ae1311fca9425248b6a4f0b37c3093
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: X2Go thin client environment (common files)
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-common:
 .
 Common files for X2Go TCE (display manager / mini desktop).
Description-md5: e4d7d0d00e375805931e395e86976f72

Package: x2gothinclient-management
Architecture: all
Version: 1.5.0.1-7
Priority: optional
Section: universe/admin
Source: x2gothinclient
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Remote Maintainers <debian-remote@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 139
Depends: debootstrap
Recommends: atftpd | tftpd | tftpd-hpa, syslinux, pxelinux, syslinux-themes-debian-squeeze, nfs-kernel-server
Suggests: dhcp3-server | dnsmasq | isc-dhcp-server
Breaks: x2gothinclientmanagement (<< 1.5.0.0)
Replaces: x2gothinclientmanagement (<< 1.5.0.0)
Filename: pool/universe/x/x2gothinclient/x2gothinclient-management_1.5.0.1-7_all.deb
Size: 39894
MD5sum: 595c8935aff67b54f22ecced66e99b67
SHA1: 7d75b7370a1f26c24d808851076af3b588c0e758
SHA256: 7c19f9191eb8a5d4b7529d6b97ebee61c7752cd3eed6659f26f1c09e5b798b42
SHA512: 31bc3786cf596a369ac89bbbd75733ef1c5768bafb2069ccee46ba0d70c37d640b19aaa3b4e212ac9cb707e1897714579046b6b63361a60436bea544e4910f65
Homepage: https://code.x2go.org/releases/source/x2gothinclient
Description-en: Management tools for X2Go Thin Client chroot server
 X2Go is a server based computing environment with
    - session resuming
    - low bandwidth support
    - session broker support
    - client-side mass storage mounting support
    - client-side printing support
    - audio support
    - authentication by smartcard and USB stick
 .
 x2gothinclient-management:
 .
 IMPORTANT: Install this package on the chroot server that
 provides X2Go Thin Client images over PXE/Etherboot.
 .
 For chroot servers it is recommended to use a very separate machine (not
 your main server on your network) that only serves this purpose.
Description-md5: c8084ed584ad391947cba3d9a878708d

```
Is there a lot of difference in the versions, that it should still be installed and updated from the PPA? Just curious. I know you seem to use x2go a whole lot, so you would be the person to ask.

---

### Post by TheFu on 2023-06-21
traceymccabe2, those aren't the commands I used and they aren't the commands the x2go website says to use. I posted the exact commands and tested them on my systems here.


MAFoElffen,
With the PPA, you'll have the same versions between different systems. 
20:04: ```

ii  x2goclient                             4.1.2.2-1
```

22.04: 
```
ii  x2goserver                                 4.1.0.3-5
ii  x2goclient                                 4.1.2.2-2build1
```

Don't know if I use x2go THAT much. It is only used when I'm away from home, typically traveling.  Most of the time, I'll use an ssh-tunnel for my needs rather than a full remote desktop, but if I'm in a foreign country where I don't trust the borders or internet to be free from monitoring, I'll leave all my data at home and use x2go for typical desktop stuff.

When I'm traveling for fun, I usually just take an 8in tablet and wifi-only phone. Both connect to my self-hosted VPN, which is fast and stable.  I haven't needed to travel for work in about 5 yrs.

But I can understand why some people feel they need a full remote desktop.

---

### Post by traceymccabe2 on 2023-06-21
TheFu, The only difference in the commands I used is I shortened apt-get to apt and I added x2golxdebindings.  Just to be sure, I removed x2golxdebindings and I still get the same errors.  I think an update installed a newer version of a library that x2go doesn't like for some reason.  

I even tried to install x2goserver-x2gokdrive which the error message is saying the x2goserver depends on and I get a message saying that " x2goserver-x2gokdrive : Depends: xserver-x2gokdrive but it is not installable".  

Do you know where I can look to see why it isn't installable?  What log to I check for the reason of the failure?

---

### Post by MAFoElffen on 2023-06-21
Okay...

In both your posts showing the output of the errors, the problem (to me) is this:
```

The following packages have unmet dependencies:
x2goserver : Depends: x2goserver-x2gokdrive (< 4.1.0.5-0~1987~ubuntu20.04.1.1~) but it is not going to be installed
Depends: x2goserver-x2gokdrive (>= 4.1.0.5-0~1987~ubuntu20.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
Usually, if you get an error like that, you would do this with the package that it says it is having a problem with
```

apt list x2goserver-x2gokdrive --installed

```
So you can see the package and version that is installed. Then I go to the repo or in this case, the PPA and check out what is there, to see if the versioon that is needed can be installed explictly...

Look at this--> RE: [https://launchpad.net/~x2go/+archive/ubuntu/stable/+packages?batch=75&memo=75&start=75](https://launchpad.net/~x2go/+archive/ubuntu/stable/+packages?batch=75&memo=75&start=75)

See the versions that are built for what releases Ubuntu? Do you see x2goserver-x2gokdrive there for Focal? I don't. I see it built for Jammy through Mantic...

---

### Post by traceymccabe2 on 2023-06-22
MoFoElffen, Thanks for the reply.

I issued the apt list command with all-versions and installed options and it showed the following:[INDENT]tracey@dServer:~$ sudo apt list x2goserver-x2gokdrive
Listing... Done
[COLOR=#00ff00]x2goserver-x2gokdrive[/COLOR]/focal 4.1.0.5-0~1987~ubuntu20.04.1 amd64
tracey@dServer:~$ sudo apt --all-versions list x2goserver-x2gokdrive
Listing... Done
[COLOR=#00ff00]x2goserver-x2gokdrive[/COLOR]/focal 4.1.0.5-0~1987~ubuntu20.04.1 amd64

tracey@dServer:~$ sudo apt --installed list x2goserver-x2gokdrive
Listing... Done
[/INDENT]

From this I am determining that version 4.1.0.5-0~1987~ubuntu20.04.1 of x2goserver-x2gokdrive is  available in the repository and isn't currently installed on my  system.  Is that a correct assumption?

Any suggestions on what is next?  I still cannot install it and I don't know why.

---

### Post by TheFu on 2023-06-22
If you use the PPA, then x2go packages should come from the PPA, if available there.
When I see 
```
E: Unable to correct problems, you have held broken packages.
```
as an error and **sudo apt-get -f install** doesn't correct it, then I look for manually installed .deb files that are conflicting with the OS packages and holding OS packages back.  BTW, I patch weekly my systems, so my systems are up to date, as of last Saturday.

```
$ dpkg -l |grep libx2go
ii  libx2go-config-perl                        4.1.0.3-5                                         all          Perl X2Go::Config package
ii  libx2go-log-perl                           4.1.0.3-5                                         all          Perl X2Go::Log package
ii  libx2go-server-db-perl                     4.1.0.3-5                                         amd64        Perl X2Go::Server:DB package
ii  libx2go-server-perl                        4.1.0.3-5                                         all          Perl X2Go::Server package
ii  libx2go-utils-perl                         4.1.0.3-5                                         all          Perl X2Go::Utils package
```
and
```
$ dpkg -l |grep x2goserver
ii  x2goserver                                 4.1.0.3-5                                         amd64        X2Go Server
ii  x2goserver-common                          4.1.0.3-5                                         all          X2Go Server (common files)
ii  x2goserver-extensions                      4.1.0.3-5                                         all          X2Go Server (extension support)
ii  x2goserver-fmbindings                      4.1.0.3-5                                         all          X2Go Server (file manager bindings)
ii  x2goserver-printing                        4.1.0.3-5                                         all          X2Go Server (printing support)
ii  x2goserver-x2goagent                       4.1.0.3-5                                         amd64        X2Go Server's X2Go Agent
ii  x2goserver-xsession                        4.1.0.3-5                                         all          X2Go Server (Xsession runner)
```

dpkg is safe to use to pull information. No risk at all as I've used it. I don't have *x2goserver-x2gokdrive* installed, so it isn't required for a working x2go install.

If it were me, I'd purge all x2go stuff, ensure that my system is fully patched without any warnings or errors, then try again using the exact commands provide.  No extras.  Since I had zero issues, there's probably something mixed up with the dependencies on your system.  My 20.04 and 22.04 installs were both fresh, not upgrades. Upgrades from release to release can leave cruft behind.

---

### Post by MAFoElffen on 2023-06-22
+1 --- Agreed.

I don't see where x2goserver-x2gokdrive is even installed, unless installed manually.

Please post the results of this, **within CODE Tags**:
```

apt-cache show x2goserver-x2gokdrive

```
I think what we are going to see is that that package is labeled as "Priority: optional"...

I am wondering about the sources you installed from... Because the package name is different than what I find(???) From the PPA TheFu posted, and from Ubuntu Universe.

The reason I posted "**within CODE Tags**" in bold, is that you have been posting your raw output in your posts, without them. Please post your output within Code Tags. That can do done two ways. By either posting from the "Go Advanced" post menu, where you would select the "#" Icon, which will insert Code Tags for you, which you would then paste your output within them... Or manually type them like this:

[noparse][CODE}
     Paste your
    code
    here...
[/CODE][/noparse]

Posted commands and raw output sometimes does strange and odd things to the Forum's software, so doing that is a Forum Policy. I know, as a past Moderator, that I would re-format someone's post the first time, and warn/inform them... Just trying to keep you out of troubles with the Moderators here. Just a learning curve.

---

### Post by violet-beauregarde on 2023-06-23
Aside from your other problems, if the service is masked, just unmask it:


```

sudo systemctl unmask x2goserver

```

---

