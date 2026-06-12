---
title: "laptop-detect error every time"
date: 2005-06-01
forum: Repositories &amp; Backports
---

### Post by kittcankitt on 2005-06-01
I am usually able to search these forums (and google, of course) to get any questions I might have answered but this one has me stumped.

Originally I was trying to install vcdimager and kept getting this error..

kck@sdmf:~$ sudo apt-get install vcdimager
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcdio0 libiso9660-0 libvcdinfo0
The following NEW packages will be installed:
  libcdio0 libiso9660-0 libvcdinfo0 vcdimager
0 upgraded, 4 newly installed, 0 to remove and 53 not upgraded.
Need to get 0B/724kB of archives.
After unpacking 1524kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libcdio0_0.68-2_i386.deb (--unpack):
 unable to open files list file for package `laptop-detect': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/libcdio0_0.68-2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now, ANYTHING I try to install/upgrade gives me the same error.  I am not using a laptop (although from what I've read, laptop-detect does just that...detects whether or not you are) 

I have the latest version of laptop-detect installed and even though I tried re-installing it, I get the same error.  (while re-installing..."unable to open files list for laptop-detect...)

If anyone could help me out on this one I'd probably stop  ](*,) 

Thanks! kck

---

### Post by Mez on 2005-06-01
looks liek you got a corrupt fiel on download

```
sudo apt-get clean
sudo apt-get update
sudo apt-get install vcdimager
```

Should fix it


Info from the man page:
```
       clean  clean  clears out the local repository of retrieved package files. It removes everything but the lock file
              from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When  APT  is  used  as  a  dselect(8)
              method,  clean  is  run  automatically. Those who do not use dselect will likely want to run apt-get clean
              from time to time to free up disk space.

```

---

### Post by kittcankitt on 2005-06-01
Thanks Mez, I already tried that.  You see the thing is it gives me the same error for EVERYTHING I try to install/update now.  They can't all be corrupt?  btw, my apt sources are up to date according to the forum announcements and I haven't added any "unusual" sources so I am really scratching my head...I gave up banging on the wall.  Was getting a headache!  lol  

Anyone else have any ideas?

KCK

---

### Post by kittcankitt on 2005-06-01
Okay, I'm thinking I have to post this in another forum...for some reason I thought this was "apt" related.

I apologize now to the mods if this isn't appropriate but I can not move forward from here and it's really getting frustruating.

Thanks kck

---

### Post by THEspacemonkey on 2005-07-02
[QUOTE=kittcankitt]Okay, I'm thinking I have to post this in another forum...for some reason I thought this was "apt" related.

I apologize now to the mods if this isn't appropriate but I can not move forward from here and it's really getting frustruating.

Thanks kck[/QUOTE]
Let me know if you figured it out, I have the exact same problem, but with the evms package file lists.

I've posted several times, but no answers, and am running out of hope. I even built the evms locally and tried a force install, with the same error. Forum mods (or anyone else) feel free to whack me with a cluestick if there is an answer to this somewhere. ](*,)
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/cdrdao_1%3a1.1.9-3ubuntu2_i386.deb (--unpack):
 unable to open files list file for package `evms': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/cdrdao_1%3a1.1.9-3ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by THEspacemonkey on 2005-07-02
Just as an FYI the answer was to reboot and run a full fsck. After that, everything started working normally.

Now to identify the cause, I suspect it is evms as it fails to cleanly unmount the root filesystem about every 6 boots. With it disabled, I have had no boot issues, either on power or battery  \\:D/

---

