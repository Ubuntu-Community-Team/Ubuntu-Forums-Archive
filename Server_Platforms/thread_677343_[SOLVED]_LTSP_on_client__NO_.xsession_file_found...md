---
title: "[SOLVED] LTSP on client : NO .xsession file found..."
date: 2008-01-24
forum: Server Platforms
---

### Post by angelot on 2008-01-24
I've just installed ltsp standalone on my ubuntu server 7.10.

Everything went fine.

I boot the client and I get the login-screen.

Then I try to login as one of my users on the server and I get this errormessage:```
Xsession: Unable to start xsession --- no "/home/myusername/.xsession" file, no "home/myusername/.Xsession" file, no session managers, no windowmanagers, and no terminal emulators found; aborting.
```
I have have no GUI (no xserver) on my server - didn't know that I had to have one to get LTSP up?

I Ctrl-Alt-F1 and try login from a shell. This time I get "login incorrect" using the same username/password.

How can I fix this?

I also tried to update the client from the server:```
myusername@server:/home$ sudo cp /etc/apt/sources.list /opt/ltsp/i386/etc/apt/
myusername@server:/home$ sudo chroot /opt/ltsp/i386/
root@server:/# apt-get update
[to long list - no errors]
The following packages will be upgraded::
  libcairo2 libcomerr2 libcupsys2 libflac8 libpango1.0-0 libpango1.0-common
  libpng12-0 libss2 libssl0.9.8 libuuid1 libxfont1 linux-image-2.6.22-14-386
  openssh-client tzdata xserver-xorg-core
15 upgrades, 0 newly installed, 0 to remove and 0 not upgraded.
6 packages not fully installed or removed.
Must get 0B/28,1MB of archives.
After unpacking 238kB extra diskspace will be used.
Continue [Y/n]? Y
[sorry it's translated from Norwegian - but you get the drift]
Preconfigureing packages ...
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 16352 files and catalogs is installed.)
Preapering to upgrading linux-image-2.6.22-14-386 2.6.22-14.46 (using .../linux-image-2.6.22-14-386_2.6.22-14.47_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-386 ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.22-14-386.postrm line 320.
dpkg: Warning - old post-removal-skript returned errorstatus 1
dpkg - trying script from the new package ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 320.
dpkg: Error prossessing /var/cache/apt/archives/linux-image-2.6.22-14-386_2.6.22-14.47_i386.deb (--unpack):
 subprocess new post-removal-skript returned errorstatus 1
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/ltsp-update-kernels
Cannot open ``/boot/nbi.img-2.6.22-14-386'':File exists
run-parts: /etc/kernel/postrm.d/ltsp-update-kernels exited with return code 1
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/tmp.ci/postrm line 320.
dpkg: error cleaning up:
 subprocess post-removal script returned errorstatus 1
There was an error prosessing:
 /var/cache/apt/archives/linux-image-2.6.22-14-386_2.6.22-14.47_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:/# exit
exit
myusername@server:/home$
```
Any suggestions?

EDIT: [I]I don't have any users in /opt/ltsp/i386/home/ on server and no .xsession file in /home/myusername on server..... 
I also tried "cp /etc/X11/Xsession ~/.Xsession" on server, and now I don't get the errormsg - just a black screen doing nothing. I'm still getting "login incorrect" in a shell on client....[/I]

Angelot

---

### Post by angelot on 2008-01-27
I've just installed edubuntu-server 7.10 and finally ltsp is up and running with no problems :lolflag:

And - yes, edubuntu installs by default GNOME and all the Edubuntu colors...

I belive to get ltsp running you'll have to have a working X-enviroment on the server....

Thanks for all help...

---

### Post by ahmadzainul on 2008-05-16
Same problem here but, I am running Hardy. Anybody can help us? I believe this is old problem.

---

