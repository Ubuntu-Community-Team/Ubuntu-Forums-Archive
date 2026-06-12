---
title: "subprocess paste was killed by signal (Broken pipe)"
date: 2017-11-26
forum: Windows
---

### Post by molnar-tibor on 2017-11-26
i have an issue with my Ubuntu 16.04 LTS build. When trying to perform an apt update && apt upgrade i get dependency errors with some pearl packages. running apt-get -f install gives the following errors:


```
Unpacking perl-modules-5.22 (5.22.1-9ubuntu0.2) over (5.22.1-9) ...
dpkg: error processing archive /var/cache/apt/archives/perl-modules-5.22_5.22.1-9ubuntu0.2_all.deb (--unpack):
 unable to stat './usr/share/perl/5.22.1/pod' (which I was about to install): Permission denied
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../libperl5.22_5.22.1-9ubuntu0.2_amd64.deb ...
Unpacking libperl5.22:amd64 (5.22.1-9ubuntu0.2) over (5.22.1-9) ...
dpkg: error processing archive /var/cache/apt/archives/libperl5.22_5.22.1-9ubuntu0.2_amd64.deb (--unpack):
 unable to stat './usr/lib/x86_64-linux-gnu/perl/5.22.1/sys' (which I was about to install): Permission denied
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.7.5-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/perl-modules-5.22_5.22.1-9ubuntu0.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

i tried uninstalling the affected packages, but was not able to due to multiple dependencies. interestingly i don't remember doing anything unusual like editing config files or so prior to this error. the only thing i did was to add a backport repository to the apt sources file, which looks like this:
```
deb http://archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu xenial-backports main restricted universe multiverse
```
also i don't remeber building packages out of the official repos on the machine

any idea for help? i already searched the similar threats but to no avail:
[https://askubuntu.com/questions/383079/subprocess-paste-was-killed-by-signal-broken-pipe](https://askubuntu.com/questions/383079/subprocess-paste-was-killed-by-signal-broken-pipe)
[https://askubuntu.com/questions/441047/dpkg-deb-error-subprocess-paste-was-killed-by-signal-broken-pipe-nginx](https://askubuntu.com/questions/441047/dpkg-deb-error-subprocess-paste-was-killed-by-signal-broken-pipe-nginx)
[https://ubuntuforums.org/showthread.php?t=2252823&highlight=subprocess+paste+killed+signal+%28Broken+pipe%29](https://ubuntuforums.org/showthread.php?t=2252823&highlight=subprocess+paste+killed+signal+%28Broken+pipe%29)

---

### Post by Impavidus on 2017-11-27
The message about the broken pipe is just the result of another error given the line above. By itself, it doesn't tell a lot. This however is puzzling:```
unable to stat './usr/share/perl/5.22.1/pod' (which I was about to install): Permission denied
...
unable to stat './usr/lib/x86_64-linux-gnu/perl/5.22.1/sys' (which I was about to install): Permission denied
```Every user should have read and execute permissions on those directories and their (grand-) parent directories. Something strange is going on here. I'm using a more recent version of Ubuntu, so I've got some different version numbers, but things should be roughly the same.

What do you get from```
ls -l /usr/share/perl/
ls -ld /usr/share/perl/5.22.1/pod
ls -l /usr/lib/x86_64-linux-gnu/perl/
ls -ld /usr/lib/x86_64-linux-gnu/perl/5.22.1/sys
```

---

### Post by molnar-tibor on 2017-11-27
well this is interesting. it seems i cannot even access those directories as root... on the other hand i am not sure if those directories with denied permission are even existing

```
# ls -l /usr/share/perl/
total 0
lrwxrwxrwx 1 root root   6 Mar 13  2016 5.22 -> 5.22.1
drwxr-xr-x 0 root root 512 Nov 26 21:57 5.22.1

# ls -ld /usr/share/perl/5.22.1/pod
ls: cannot access '/usr/share/perl/5.22.1/pod': Permission denied

# ls -l /usr/lib/x86_64-linux-gnu/perl/
total 0
lrwxrwxrwx 1 root root   6 Mar 13  2016 5.22 -> 5.22.1
drwxr-xr-x 0 root root 512 Nov 26 21:57 5.22.1
drwxr-xr-x 0 root root 512 Dec 21  2016 cross-config-5.22.1
drwxr-xr-x 0 root root 512 Dec 21  2016 debian-config-data-5.22.1

# ls -ld /usr/lib/x86_64-linux-gnu/perl/5.22.1/sys
ls: cannot access '/usr/lib/x86_64-linux-gnu/perl/5.22.1/sys': Permission denied
```

---

### Post by Impavidus on 2017-11-28
If those directories that give you "permission denied" simply didn't exist, there would be a different error message. But here we see a failure to read the contents of the parent directory. All those directories have zero hard links, or so ls tells us. But directories must always have two hardlinks plus one for each subdirectory. This looks like filesystem damage. Try to run a filesystem check. Use a live disk if necessary.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

Also check the SMART status of your hard drive. A failing hard drive is a possible cause of filesystem damage.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by molnar-tibor on 2017-11-28
i don't think so... i didn't mention (kinda intentionally) that this is not a real ubuntu distro, but Linux Subsystem for Windows. I can imagine that microsoft messed up something during the updates (i am using the insider builds)...

edit: i didn't realize there was a windows subsection on the forum. thanks for moving the thread to the appropriate location!

---

### Post by howefield on 2017-11-28
Moved to the "*Windows*" sub forum.

---

### Post by gregmajor on 2018-02-07
Did you ever find a solution for this? I'm having the exact same issue with WSL.

Greg

---

### Post by molnar-tibor on 2018-02-07
**unfortunately not**

---

### Post by gregmajor on 2018-02-07
Ouch. With perl effectively broken, that leaves our WSL installations pretty borked.

---

### Post by replicant1 on 2018-06-15
I am having the same issue. 

This is the output from trying to upgrade the packages in Bash for Windows

```
 
root@machine:~# sudo apt upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 perl : Depends: perl-modules-5.22 (>= 5.22.1-9ubuntu0.5) but 5.22.1-9 is installed
        Depends: libperl5.22 (= 5.22.1-9ubuntu0.5) but 5.22.1-9 is installed
E: Unmet dependencies. Try using -f.

```

Running apt -f install

```

root@machine:~# sudo apt -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libperl5.22 perl-modules-5.22
The following packages will be upgraded:
  libperl5.22 perl-modules-5.22
2 upgraded, 0 newly installed, 0 to remove and 137 not upgraded.
1 not fully installed or removed.
Need to get 0 B/6,041 kB of archives.
After this operation, 7,168 B disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 25494 files and directories currently installed.)
Preparing to unpack .../perl-modules-5.22_5.22.1-9ubuntu0.5_all.deb ...
Unpacking perl-modules-5.22 (5.22.1-9ubuntu0.5) over (5.22.1-9) ...
dpkg: error processing archive /var/cache/apt/archives/perl-modules-5.22_5.22.1-9ubuntu0.5_all.deb (--unpack):
 unable to stat './usr/share/perl/5.22.1/pod' (which I was about to install): Permission denied
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../libperl5.22_5.22.1-9ubuntu0.5_amd64.deb ...
Unpacking libperl5.22:amd64 (5.22.1-9ubuntu0.5) over (5.22.1-9) ...
dpkg: error processing archive /var/cache/apt/archives/libperl5.22_5.22.1-9ubuntu0.5_amd64.deb (--unpack):
 unable to stat './usr/lib/x86_64-linux-gnu/perl/5.22.1/sys' (which I was about to install): Permission denied
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.7.5-1) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have the same permissions on those directories as molnar-tibor.

Has anyone solved this over the past few months?

---

### Post by replicant1 on 2018-06-15
FYI, there is another thread on github with the same issue: [https://github.com/Microsoft/WSL/issues/2769](https://github.com/Microsoft/WSL/issues/2769)

---

### Post by mahmoud.a on 2018-10-21
Hi, here's my solution to the error message when I tried installing a firmware for my wifi. I am using an HP Mini, Intel Atom processor system with 1gig ram. I was testing "SparkyLinux", which is Debian based and wireless connectivity was not working, as it had been "hardware disabled". This is a bug in some Debian Linux versions.

# sudo rfkill list all

# sudo lsmod | grep -e hp -e wireless

# sudo modprobe -r hp-wmi

# sudo rfkill list all

# sudo echo hp-wireless >> /etc/modules

# sudo gedit /etc/modprobe.d/blacklist.conf 

# sudo lsusb

# sudo lspci -nnk | grep 0280 -A2



Anway, when it came to updating the firmware, I got the error "
[h=2][SIZE=3]*subprocess paste was killed by signal (Broken pipe) 		*[/SIZE][/h]when I used :[SIZE=3]
**# sudo dpkg --install linux-firmware*.deb**[/SIZE]

I was able to solve the problem, and install the firmware using the "--force" option:
[SIZE=3][B]
# sudo dpkg --install --force-overwrite linux-firmware*.deb[/B][/SIZE]

There were a few warnings, but they were just that. I hope this helps.

dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/lib/firmware/s2250.fw', which is also in package firmware-misc-nonfree 20161130-3
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/lib/firmware/s2250_loader.fw', which is also in package firmware-misc-nonfree 20161130-3
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/lib/firmware/ti-connectivity/wl1271-nvs.bin', which is also in package firmware-ti-connectivity 20161130-3
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/lib/firmware/ti-connectivity/wl12xx-nvs.bin', which is also in package firmware-ti-connectivity 20161130-3
Setting up linux-firmware (1.169.3) ...
update-initramfs: Generating /boot/initrd.img-4.9.0-8-686
update-initramfs: Generating /boot/initrd.img-4.9.0-6-686
Processing triggers for man-db (2.7.6.1-2) ...

---

