---
title: "Removing repository"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Curtis6767 on 2012-03-31
Because I've been having so much trouble with my audio, I decided to look at OutRec, which was recommended on another thread. I added the repository:

sudo add-apt-repository ppa:techm3/outrec

I would now like to delete this because each time I do an update, I just error messages, and I don't want to use Outrec anyway because that would not solve my audio problems.

These are the error messages I get:

"W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead."

Some of the above may or may not be specific to OutRec, but I included them just to be safe.

I'd like to now remove the repository so my computer no longer searches for updates for OutRec.

In case it makes a difference, I am now using 12.04 LTS Beta.

Thanks

---

### Post by Bucky Ball on 2012-03-31
> **Curtis6767 said:**
> 

In case it makes a difference, I am now using 12.04 LTS Beta.

Thanks

Yes, it does make a difference and I have asked mods to move this thread to the appropriate forum. 12.04 LTS is not released yet; expect breakages and glitches. ;)

Not sure if Unity has 'software sources' but find that and untick the OutRec repos to stop them attempting to get updated. 

As for the precise repo errors ... as I said, expect some glitches on a beta release. Hopefully that can be fixed (or will be in a future update).

I would be updating daily at this point, when you can.

---

### Post by howefield on 2012-03-31
Thread moved to "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by codemaniac on 2012-03-31
Just comment out the added repos in **/etc/apt/sources.list ** .

---

### Post by dino99 on 2012-03-31
sudo apt-get install ppa-purge

sudo ppa-purge ppa:techm3/outrec

Look at this howto : [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by Mr. Picklesworth on 2012-03-31
[s]Why the techy directions?
Open Software Sources (from Software Centre), and the offending PPA will be listed under the Other Software tab.[/s]

Edit:
Yeah, what dino99 said!

Also, if you aren't concerned about leftover packages that were installed from the PPA (or you just want to disable the repository instead of removing it), go to Software Center and open Software Sources. All the PPAs you have added will be listed in the Other Software tab.

---

### Post by zika on 2012-03-31
> **Mr. Picklesworth said:**
> Why the techy directions?
Open Software Sources (from Software Centre), and the offending PPA will be listed under the Other Software tab.
But (if I may & if I'm not wrong) these are two different advices. First (ppa-purge) restores packages upgraded from that PPA to state without PPA. Other (Software Sources) only turns PPA off but leaves packages upgraded from that PPA on machine...

---

### Post by Mr. Picklesworth on 2012-03-31
> **zika said:**
> But (if I may & if I'm not wrong) these are two different advices. First (ppa-purge) restores packages upgraded from that PPA to state without PPA. Other (Software Sources) only turns PPA off but leaves packages upgraded from that PPA on machine...

Ah, yes, of course! You're right. Sorry about the doubt :)

---

### Post by mc4man on 2012-03-31
Well if being specific to this thread instead of generically then there is nothing to purge, remove other than removing the ppa from sources 

When using add-apt-repository it's added for the release run on, in this case precise, there is no 'precise' in that ppa so nothing was or could be added/installed
(that ppa dies after lucid, whether the 1 package in it will run on later releases one would have to try

---

### Post by Curtis6767 on 2012-03-31
This is what I got:

"curtis@ubuntu:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libept1.4.12 libio-string-perl libparse-debianchangelog-perl
  libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libept1.4.12 libio-string-perl libparse-debianchangelog-perl
  libsub-name-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 90 not upgraded.
Need to get 3,052 kB of archives.
After this operation, 9,437 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libboost-iostreams1.46.1 amd64 1.46.1-7ubuntu3 [39.2 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libcwidget3 amd64 0.5.16-3.1ubuntu1 [406 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libept1.4.12 amd64 1.0.6~exp1ubuntu1 [129 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main aptitude amd64 0.6.6-1ubuntu1 [2,371 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libsub-name-perl amd64 0.05-1build2 [9,656 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libio-string-perl all 1.08-2 [12.0 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 3,052 kB in 6s (450 kB/s)                                              
Selecting previously unselected package libboost-iostreams1.46.1.
(Reading database ... 153359 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_amd64.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.6~exp1ubuntu1_amd64.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.6-1ubuntu1_amd64.deb) ...
Selecting previously unselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build2_amd64.deb) ...
Selecting previously unselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously unselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Selecting previously unselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up libept1.4.12 (1.0.6~exp1ubuntu1) ...
Setting up aptitude (0.6.6-1ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build2) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
curtis@ubuntu:~$ sudo ppa-purge ppa:techm3/outrec
Updating packages lists
W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[B]Warning:  apt-get update failed for some reason
PPA to be removed: techm3 outrec
Warning:  Could not find package list for PPA: techm3 outrec"[/B]


What would be the next step in trying to remove this. And, I'm a newb at this.

Also, within the software center I could not find a 'sources' option.

---

### Post by xebian on 2012-03-31
> **Curtis6767 said:**
> This is what I got:

"curtis@ubuntu:~$ sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libept1.4.12 libio-string-perl libparse-debianchangelog-perl
  libsub-name-perl
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
  libhtml-template-perl libxml-simple-perl
The following NEW packages will be installed:
  aptitude libboost-iostreams1.46.1 libclass-accessor-perl libcwidget3
  libept1.4.12 libio-string-perl libparse-debianchangelog-perl
  libsub-name-perl ppa-purge
0 upgraded, 9 newly installed, 0 to remove and 90 not upgraded.
Need to get 3,052 kB of archives.
After this operation, 9,437 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libboost-iostreams1.46.1 amd64 1.46.1-7ubuntu3 [39.2 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libcwidget3 amd64 0.5.16-3.1ubuntu1 [406 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libept1.4.12 amd64 1.0.6~exp1ubuntu1 [129 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main aptitude amd64 0.6.6-1ubuntu1 [2,371 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libsub-name-perl amd64 0.05-1build2 [9,656 B]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libclass-accessor-perl all 0.34-1 [26.0 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libio-string-perl all 1.08-2 [12.0 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libparse-debianchangelog-perl all 1.2.0-1ubuntu1 [54.0 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe ppa-purge all 0.2.8+bzr56 [4,360 B]
Fetched 3,052 kB in 6s (450 kB/s)                                              
Selecting previously unselected package libboost-iostreams1.46.1.
(Reading database ... 153359 files and directories currently installed.)
Unpacking libboost-iostreams1.46.1 (from .../libboost-iostreams1.46.1_1.46.1-7ubuntu3_amd64.deb) ...
Selecting previously unselected package libcwidget3.
Unpacking libcwidget3 (from .../libcwidget3_0.5.16-3.1ubuntu1_amd64.deb) ...
Selecting previously unselected package libept1.4.12.
Unpacking libept1.4.12 (from .../libept1.4.12_1.0.6~exp1ubuntu1_amd64.deb) ...
Selecting previously unselected package aptitude.
Unpacking aptitude (from .../aptitude_0.6.6-1ubuntu1_amd64.deb) ...
Selecting previously unselected package libsub-name-perl.
Unpacking libsub-name-perl (from .../libsub-name-perl_0.05-1build2_amd64.deb) ...
Selecting previously unselected package libclass-accessor-perl.
Unpacking libclass-accessor-perl (from .../libclass-accessor-perl_0.34-1_all.deb) ...
Selecting previously unselected package libio-string-perl.
Unpacking libio-string-perl (from .../libio-string-perl_1.08-2_all.deb) ...
Selecting previously unselected package libparse-debianchangelog-perl.
Unpacking libparse-debianchangelog-perl (from .../libparse-debianchangelog-perl_1.2.0-1ubuntu1_all.deb) ...
Selecting previously unselected package ppa-purge.
Unpacking ppa-purge (from .../ppa-purge_0.2.8+bzr56_all.deb) ...
Processing triggers for man-db ...
Setting up libboost-iostreams1.46.1 (1.46.1-7ubuntu3) ...
Setting up libcwidget3 (0.5.16-3.1ubuntu1) ...
Setting up libept1.4.12 (1.0.6~exp1ubuntu1) ...
Setting up aptitude (0.6.6-1ubuntu1) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode.
Setting up libsub-name-perl (0.05-1build2) ...
Setting up libclass-accessor-perl (0.34-1) ...
Setting up libio-string-perl (1.08-2) ...
Setting up libparse-debianchangelog-perl (1.2.0-1ubuntu1) ...
Setting up ppa-purge (0.2.8+bzr56) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
curtis@ubuntu:~$ sudo ppa-purge ppa:techm3/outrec
Updating packages lists
W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/techm3/outrec/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
[B]Warning:  apt-get update failed for some reason
PPA to be removed: techm3 outrec
Warning:  Could not find package list for PPA: techm3 outrec"[/B]


What would be the next step in trying to remove this. And, I'm a newb at this.

Also, within the software center I could not find a 'sources' option.

If you added this ppa with add-apt-repository

open a terminal and cd /etc/apt/sources.list.d/

There you will see a file(s) that has 'techm3' in it's name.  delete such file and you should be fine.


If you added directly to /etc/apt/sources.list, then edit this file and delete line(s) with the 'techm3' names.

---

### Post by mc4man on 2012-03-31
One way - in terminal
```
software-properties-gtk
```
Click on 'Other' tab, you'll see 2 entries for the ppa, Highlight each one in turn & click 'remove'

Then close out the window & update your sources = 
```
sudo apt-get update
```

(if you open update-manager the same sources window is accessed from 'Settings', in Software-Center click on "Edit" > "Software Sources"

---

### Post by Baldrick_NZ on 2012-03-31
> **Curtis6767 said:**
> 


What would be the next step in trying to remove this. And, I'm a newb at this.

Also, within the software center I could not find a 'sources' option.

Go 'Update Manager' (not software centre), which is easiest found under installed apps using dash; or, using the cog power button (top right of your screen) choose 'Software to update'.

Either way, Update Manager should appear.

At the bottom left of the window, click on 'settings'. This will launch another window called 'Software Sources'.

Navigate to the 'Other Software' Tab, where you'll find a full list of installed PPA's.

Scroll down to the one which mentions 'outrec', and click on it (there should be two. One will be source). 

A pop-up window will then ask for your system password, which is usually the same as your login password. Enter password and then 'authenticate'.

You can then remove both entries by using the 'remove' button.

When finished, click on 'close', and that window should close.

Back to the 'Update Manager' window, click on 'Check', which will reload all the repo's and inform you whether you have any updates and whether there are any errors found in the repo's. 

Welcome aboard!!

---

### Post by Curtis6767 on 2012-03-31
cd/etc/apt/sources.list.d/

got me this: 

@ubuntu:~$ cd/etc/apt/sources.list.d/
bash: cd/etc/apt/sources.list.d/: No such file or directory

But the following did work along with the instructions:

"Click on 'Other' tab, you'll see 2 entries for the ppa, Highlight each one in turn & click 'remove'"


software-properties-gtk
I then ran sudo apt-get update  and no more tech3/outrec, etc.

Thanks for the help on this.

---

### Post by xebian on 2012-03-31
Then mark it as 'solved'.

Of course you get the error below because you are doing it wrong.  It should be cd  <space> /etc/apt/sources.list.d/

> **Curtis6767 said:**
> cd/etc/apt/sources.list.d/

got me this: 

@ubuntu:~$ cd/etc/apt/sources.list.d/
bash: cd/etc/apt/sources.list.d/: No such file or directory

..

Thanks for the help on this.

---

### Post by Bucky Ball on 2012-03-31
> **xebian said:**
> Then mark it as 'solved'.



+1.

```
cd/etc/apt/sources.list.d/
```... didn't work because you didn't copy it exactly (copy and paste is the best, foolproof way). You need to leave a gap, as in:

```
cd /etc/apt/sources.list.d/

```cd = change directories;

/etc/apt/sources.list.d/ = the directory you want to change to. ;)

---

### Post by Curtis6767 on 2012-03-31
copied it and got this: 


curtis@ubuntu:~$ cd /etc/apt/sources.list.d/
[email]curtis@ubuntu:/etc/apt/sources.list[/email].d$

---

### Post by Bucky Ball on 2012-03-31
> **Curtis6767 said:**
> copied it and got this: 


curtis@ubuntu:~$ cd /etc/apt/sources.list.d/
[EMAIL="curtis@ubuntu:/etc/apt/sources.list"]curtis@ubuntu:/etc/apt/sources.list[/EMAIL].d$

Successful. You have changed to the correct directory. Now type:

```
dir
```... (dir = list of what's in the directory) and you will see the repos you have added. This command was not in the original posters instructions and this way is fairly roundabout way of doing things unless you prefer using the terminal (or use it often). You would then need to remove the offending repo from that directory. The GUI option you used more appropriate here. ;)

---

### Post by zika on 2012-04-01
> **mc4man said:**
> Well if being specific to this thread instead of generically then there is nothing to purge, remove other than removing the ppa from sources 

When using add-apt-repository it's added for the release run on, in this case precise, there is no 'precise' in that ppa so nothing was or could be added/installed
(that ppa dies after lucid, whether the 1 package in it will run on later releases one would have to tryI **was **wrong (at the end)... ;)
I did not take a look at the content of that PPA... In this case there is no difference... ;)

---

