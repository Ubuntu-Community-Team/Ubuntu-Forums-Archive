---
title: "apt-get dist-upgrade errror"
date: 2005-05-27
forum: Repositories &amp; Backports
---

### Post by kozmo on 2005-05-27
When trying to upgrade I get the error:

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Because of this error apt-get will not upgrade some other packages (gstreamer, mplayer. liblame0, and other multimedia files). 

The file **linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb** is in the /var/cache/apt/archives/ directory. I even gave it execute permissions and I still get the same error messages.

Help!
Thanks!

---

### Post by MrTom on 2005-05-27
above that error there should be a more specific output regarding what went wrong?

---

### Post by kozmo on 2005-05-27
[QUOTE=MrTom]above that error there should be a more specific output regarding what went wrong?[/QUOTE]

Here is the entire output:

jimmy@scooter:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gstreamer0.8-lame libavcodeccvs libpostproc0 libxvidcore4 mplayer-386
  transcode
The following packages will be upgraded:
  linux-image-2.6.10-5-386
1 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
6 not fully installed or removed.
Need to get 0B/15.6MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?

Preconfiguring packages ...
(Reading database ... 75788 files and directories currently installed.)
Preparing to replace linux-image-2.6.10-5-386 2.6.10-34 (using .../linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb) ...
The directory /lib/modules/2.6.10-5-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.10-5-386 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb (--unpack):
 trying to overwrite `/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.10-5-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jimmy@scooter:~$

---

### Post by MrTom on 2005-05-27
ok looks like you have installed ndiswrapper (never had to use it thankfully, so this is somewhat guesswork) and the same file is in both packages.

Try removing the ndiswrapper package. then dist-upgrade. If your wifi card doesn't work reinstall ndiswrapper.

On the other hand you could force dpkg to overwrite the ndiswrapper module by doing a 'dpkg --force overwrite -i kernel.deb' 

i like option 1 just because its better to let apt sort itself out.

---

### Post by kozmo on 2005-05-27
[QUOTE=MrTom]ok looks like you have installed ndiswrapper (never had to use it thankfully, so this is somewhat guesswork) and the same file is in both packages.

Try removing the ndiswrapper package. then dist-upgrade. If your wifi card doesn't work reinstall ndiswrapper.

On the other hand you could force dpkg to overwrite the ndiswrapper module by doing a 'dpkg --force overwrite -i kernel.deb' 

i like option 1 just because its better to let apt sort itself out.[/QUOTE]

I removed the ndiswrapper-modules and the linux-image was able to be upgraded -- thanks!

But now it still will not upgrade the multimedia files:

[B]jimmy@scooter:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gstreamer0.8-lame libavcodeccvs libpostproc0 libxvidcore4 mplayer-386
  transcode
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
jimmy@scooter:~$ [/B]

Any suggestions on why it will not upgrade these packages?

---

### Post by Xian on 2005-05-27
[QUOTE=kozmo]But now it still will not upgrade the multimedia files:

[B]jimmy@scooter:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  gstreamer0.8-lame libavcodeccvs libpostproc0 libxvidcore4 mplayer-386
  transcode
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
jimmy@scooter:~$ [/B]

Any suggestions on why it will not upgrade these packages?[/QUOTE]
If you will try to install those packages individually, APT will list for you the upgrade issues that are present. 

For example,
```
sudo apt-get install gstreamer0.8-lame
```

---

### Post by kozmo on 2005-05-28
[QUOTE=Xian]If you will try to install those packages individually, APT will list for you the upgrade issues that are present. 

For example,
```
sudo apt-get install gstreamer0.8-lame
```[/QUOTE]

When I run: sudo apt-get install gstreamer0.8-lame

I get:

gstreamer0.8-lame: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

Do I need to downgrade libc6 in order to install gstreamer0.8-lame? This doesn't make any sense.

I really need to resolve these issues, right now I cannot get any sound from flash in firefox -- only video. I tried a fix for this from another thread but that is not working.

Thanks for all the help thus far!

---

### Post by Xian on 2005-05-28
[QUOTE=kozmo]I really need to resolve these issues, right now I cannot get any sound from flash in firefox -- only video. I tried a fix for this from another thread but that is not working.[/QUOTE]
As those packages are from a repo that I do not use and don't want to test, I can't help you relsolve those conflicts other than to say that you do have the option in APT to downgrade any packages that are needed, provided there are not more dep issues that appear (see below).

If it is just the firefox problem then I'd suggest reading this thread, as I also encounted this on my box and the solution fixed it promptly: [Multiple Sounds](http://www.ubuntuforums.org/showthread.php?t=32063)

Or you could just open Synaptic and install the polypaudio package.

```
$ sudo aptitude install <pkgname>=<version>
```

---

### Post by kozmo on 2005-05-30
[QUOTE=Xian]As those packages are from a repo that I do not use and don't want to test, I can't help you relsolve those conflicts other than to say that you do have the option in APT to downgrade any packages that are needed, provided there are not more dep issues that appear (see below).

If it is just the firefox problem then I'd suggest reading this thread, as I also encounted this on my box and the solution fixed it promptly: [Multiple Sounds](http://www.ubuntuforums.org/showthread.php?t=32063)

Or you could just open Synaptic and install the polypaudio package.

```
$ sudo aptitude install <pkgname>=<version>
```[/QUOTE]

Thanks, that thread did fix my audio problem with Firefox!

I downgraded all the conflicting packages,  removed the testing repo, reinstalled the original packages -- all is fine now.

I don't understand why the [Ubuntu Guide](http://ubuntuguide.org/#extrarepositories) suggest to add the debian-marillat repo if it isn't stable/secure.

---

