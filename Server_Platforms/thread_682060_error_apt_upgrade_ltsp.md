---
title: "error apt upgrade ltsp"
date: 2008-01-29
forum: Server Platforms
---

### Post by angelot on 2008-01-29
I' running ltsp on my gutsy edubuntu-server.
```
$ sudo chroot /opt/ltsp/i386
root@server:/# apt-get update
..no errors
root@server:/# apt-get upgrade
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Reading state information ... Ferdig    
Følgende pakker vil bli oppgradert:
  apt-utils libcairo2 libcomerr2 libcupsys2 libflac8 libpango1.0-0
  libpango1.0-common libpng12-0 libss2 libssl0.9.8 libuuid1 libxfont1
  linux-image-2.6.22-14-386 openssh-client tzdata xserver-xorg-core
  xserver-xorg-video-intel
17 oppgraderte, 0 nylig installerte, 0 å fjerne og 0 ikke oppgradert.
1 pakker ikke fullt installert eller fjernet.
Må hente 0B/28,5MB med arkiver.
Etter utpakking vil 238kB ekstra diskplass bli brukt.
Vil du fortsette [Y/n]? 
Forhåndsoppsetter pakker ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Leser database ... 18747 filer og kataloger er installerte.)
Gjør klar til å bytte ut linux-image-2.6.22-14-386 2.6.22-14.46 (ved bruk av .../linux-image-2.6.22-14-386_2.6.22-14.47_i386.deb) ...
Done.
Pakker ut erstatningen linux-image-2.6.22-14-386 ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.22-14-386.postrm line 320.
dpkg: Advarsel - gammelt post-removal-skript returnerte feilstatus 1
dpkg - prøver i stedet et skript fra den nye pakken ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 320.
dpkg: Feil ved behandling av /var/cache/apt/archives/linux-image-2.6.22-14-386_2.6.22-14.47_i386.deb (--unpack):
 underprosessen nytt post-removal-skript returnerte feilstatus 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 320.
dpkg: feil ved opprydding:
 underprosessen post-removal script returnerte feilstatus 1
Gjør klar til å bytte ut libcomerr2 1.40.2-1ubuntu1 (ved bruk av .../libcomerr2_1.40.2-1ubuntu1.1_i386.deb) ...
Pakker ut erstatningen libcomerr2 ...
Det oppsto feil ved behandling av:
 /var/cache/apt/archives/linux-image-2.6.22-14-386_2.6.22-14.47_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:/#
```
Sorry - some of it is in norwegian....
The silly thing is that I'm not even running linux-image-2.6.22-14-386, I've got the generic kernel image....
I tried installing the 386 on the server and even when I boot with that on server the ltsp wont upgrade.

Any clues?

EDIT:```
root@server:/# uname -a
Linux server 2.6.22-14-generic #1 Tue Dec 18 07:34:24 UTC 2007 i686 GNU/Linux
```

Before I did this I copied /etc/apt/sources.list til /opt/ltsp/i386/etc/apt/sources.list....

---

