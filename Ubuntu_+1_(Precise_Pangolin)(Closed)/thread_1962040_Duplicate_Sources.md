---
title: "Duplicate Sources"
date: 2012-04-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-04-20
G'Day; I keep getting this error when i update or upgrade or open Synaptic

code:

W: Duplicate sources.list entry [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-i386_Packages)

Any help would be greatly appreciated

Regards Miykel

---

### Post by dino99 on 2012-04-20
hm, mixing amd64 & i386 :( get raidy for troubles :lolflag:

clean the room:

/etc/apt/sources.list
/etc/apt/sources.list.d/

---

### Post by Miykel on 2012-04-20
G'Day Dino99; Thanks for the reply;

Quote:
clean the room:

/etc/apt/sources.list
/etc/apt/sources.list.d/ 	

Tried to run these commands but got  "access denied" return
Regards Miykel

---

### Post by jefsview on 2012-04-20
gksu "text editor-of-choice-here" /etc/apt/sources.list

type in your root password

and edit the entries accordingly.

(don't use the quotation marks)

-- Jeff

---

### Post by Miykel on 2012-04-20
G'Day guys and thanks for the replies, I installed pcmanfm, seemed like the most popular,
and run the commands as per jeffs post, below is the output;

File;

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120413)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120413)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta amd64 (20120413)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
 >     deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
 >      deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 

the last two entries marked  >  appear to be the only entries which relate to the problem but I removed one, then the other, then both and it made no difference, I notice the entries did not include the i386 or amd64 end (???)
Any Ideas
Regards Miykel

---

### Post by alphacrucis2 on 2012-04-20
> **Miykel said:**
> G'Day Dino99; Thanks for the reply;

Quote:
clean the room:

/etc/apt/sources.list
/etc/apt/sources.list.d/ 	

Tried to run these commands but got  "access denied" return
Regards Miykel

Those aren't commands. The first is a file that apt uses to specify it's sources. The other one is a directory where apt looks for files for other repos like ppa's. The apt-add-repository command will store files related to the added repository/ppa in the /etc/apt/sources.list.d/ directory.  Dino was advising you to clean out the duplicate. Keep the one that is correct for you arch. ie you don't want both 32 and 64 bit for the same thing.

---

### Post by alphacrucis2 on 2012-04-20
Did you rerun ```
sudo apt-get update
``` after making the changes? Also look at the files under /etc/apt/sources.list.d/. Do a ls -l on that and report back.

---

### Post by Miykel on 2012-04-20
Thanks so much for your patients guys;

I opened both the list and list.d files and deleted both;

    deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
 >      deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 

tried deleting one first but still had the same conflict so I deleted both and that seemed to fix it, although I hope the amd 64 one wasn't needed.

Here is the result of  ls -l;

  miykel@miykel-H61M-USB3-B3:~$ ls -l
total 52
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Desktop
drwxr-xr-x 11 miykel miykel 4096 Apr 18 06:01 Documents
drwxr-xr-x  6 miykel miykel 4096 Apr 20 22:02 Downloads
-rw-r--r--  1 miykel miykel  179 Apr 14 19:46 examples.desktop
drwxrwxr-x  2 miykel miykel 4096 Apr 19 19:35 Kernel 
drwxr-xr-x  6 miykel miykel 4096 Apr 14 20:52 Music
drwx------ 27 miykel miykel 4096 Apr 19 17:09 Note Book
drwxrwxr-x  2 miykel miykel 4096 Apr 21 12:54 Notes
drwxr-xr-x  6 miykel miykel 4096 Apr 17 19:28 Pictures
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Public
drwx------ 11 miykel miykel 4096 Apr 20 16:58 Storage
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Templates
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Videos
miykel@miykel-H61M-USB3-B3:~$ 

Regards Miykel

---

### Post by alphacrucis2 on 2012-04-21
> **Miykel said:**
> Thanks so much for your patients guys;

I opened both the list and list.d files and deleted both;

    deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 
 >      deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main 

tried deleting one first but still had the same conflict so I deleted both and that seemed to fix it, although I hope the amd 64 one wasn't needed.

Here is the result of  ls -l;

  miykel@miykel-H61M-USB3-B3:~$ ls -l
total 52
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Desktop
drwxr-xr-x 11 miykel miykel 4096 Apr 18 06:01 Documents
drwxr-xr-x  6 miykel miykel 4096 Apr 20 22:02 Downloads
-rw-r--r--  1 miykel miykel  179 Apr 14 19:46 examples.desktop
drwxrwxr-x  2 miykel miykel 4096 Apr 19 19:35 Kernel 
drwxr-xr-x  6 miykel miykel 4096 Apr 14 20:52 Music
drwx------ 27 miykel miykel 4096 Apr 19 17:09 Note Book
drwxrwxr-x  2 miykel miykel 4096 Apr 21 12:54 Notes
drwxr-xr-x  6 miykel miykel 4096 Apr 17 19:28 Pictures
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Public
drwx------ 11 miykel miykel 4096 Apr 20 16:58 Storage
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Templates
drwxr-xr-x  2 miykel miykel 4096 Apr 14 19:53 Videos
miykel@miykel-H61M-USB3-B3:~$ 

Regards Miykel

The ls -l just lists the current directory. In the case above you listed your home directory. Sorry I needed to be a bit more specific.

There are two ways to do it.

1. Change the current directory to /etc/apt/sources.list.d/

```
cd /etc/apt/sources.list.d
```

Then

```
ls -l
```

or

2. 

```
ls -l /etc/apt/sources.list.d
```

---

### Post by Miykel on 2012-04-21
Here's the result of the ls-l as per;

[email]miykel@miykel-H61M-USB3-B3:/etc/apt/sources.list[/email].d$ ls -l
total 72
-rw-r--r-- 1 root root 132 Apr 20 06:44 diesch-testing-precise.list
-rw-r--r-- 1 root root 132 Apr 20 06:44 diesch-testing-precise.list.save
-rw-r--r-- 1 root root 132 Apr 20 06:44 eugenesan-java-precise.list
-rw-r--r-- 1 root root 132 Apr 20 06:44 eugenesan-java-precise.list.save
-rw-r--r-- 1 root root 175 Apr 20 06:44 google-earth.list
-rw-r--r-- 1 root root 175 Apr 20 06:44 google-earth.list.save
-rw-r--r-- 1 root root 144 Apr 20 06:44 nilarimogard-webupd8-precise.list
-rw-r--r-- 1 root root 144 Apr 20 06:44 nilarimogard-webupd8-precise.list.save
-rw-r--r-- 1 root root 130 Apr 20 06:44 pitivi-stable-precise.list
-rw-r--r-- 1 root root 130 Apr 20 06:44 pitivi-stable-precise.list.save
-rw-r--r-- 1 root root 130 Apr 20 06:44 rsachetto-ppa-precise.list
-rw-r--r-- 1 root root 130 Apr 20 06:44 rsachetto-ppa-precise.list.save
-rw-r--r-- 1 root root 152 Apr 20 06:44 ubuntu-mozilla-daily-ppa-precise.list
-rw-r--r-- 1 root root 152 Apr 20 06:44 ubuntu-mozilla-daily-ppa-precise.list.save
-rw-r--r-- 1 root root  74 Apr 21 13:07 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root 150 Apr 20 06:44 ubuntu-x-swat-x-updates-precise.list~
-rw-r--r-- 1 root root 136 Apr 20 06:44 webupd8team-java-precise.list
-rw-r--r-- 1 root root 136 Apr 20 06:44 webupd8team-java-precise.list.save
[email]miykel@miykel-H61M-USB3-B3:/etc/apt/sources.list[/email].d$ 


Regards Miykel

---

### Post by alphacrucis2 on 2012-04-21
> **Miykel said:**
> Here's the result of the ls-l as per;

[email]miykel@miykel-H61M-USB3-B3:/etc/apt/sources.list[/email].d$ ls -l
total 72
-rw-r--r-- 1 root root 132 Apr 20 06:44 diesch-testing-precise.list
-rw-r--r-- 1 root root 132 Apr 20 06:44 diesch-testing-precise.list.save
-rw-r--r-- 1 root root 132 Apr 20 06:44 eugenesan-java-precise.list
-rw-r--r-- 1 root root 132 Apr 20 06:44 eugenesan-java-precise.list.save
-rw-r--r-- 1 root root 175 Apr 20 06:44 google-earth.list
-rw-r--r-- 1 root root 175 Apr 20 06:44 google-earth.list.save
-rw-r--r-- 1 root root 144 Apr 20 06:44 nilarimogard-webupd8-precise.list
-rw-r--r-- 1 root root 144 Apr 20 06:44 nilarimogard-webupd8-precise.list.save
-rw-r--r-- 1 root root 130 Apr 20 06:44 pitivi-stable-precise.list
-rw-r--r-- 1 root root 130 Apr 20 06:44 pitivi-stable-precise.list.save
-rw-r--r-- 1 root root 130 Apr 20 06:44 rsachetto-ppa-precise.list
-rw-r--r-- 1 root root 130 Apr 20 06:44 rsachetto-ppa-precise.list.save
-rw-r--r-- 1 root root 152 Apr 20 06:44 ubuntu-mozilla-daily-ppa-precise.list
-rw-r--r-- 1 root root 152 Apr 20 06:44 ubuntu-mozilla-daily-ppa-precise.list.save
-rw-r--r-- 1 root root  74 Apr 21 13:07 ubuntu-x-swat-x-updates-precise.list
-rw-r--r-- 1 root root 150 Apr 20 06:44 ubuntu-x-swat-x-updates-precise.list~
-rw-r--r-- 1 root root 136 Apr 20 06:44 webupd8team-java-precise.list
-rw-r--r-- 1 root root 136 Apr 20 06:44 webupd8team-java-precise.list.save
[email]miykel@miykel-H61M-USB3-B3:/etc/apt/sources.list[/email].d$ 


Regards Miykel

Ok. It looks like you may have had the x-swat ppa in sources.list file as well as having a .list file for the x-swat ppa in /etc/apt/sources.list.d. It should only be in one or the other. Not both. Since you edited the sources.list file to remove the offending lines you should be ok now.

---

### Post by Miykel on 2012-04-21
Thanks again for all your help, all seems to be good now, another lesson learned.  LOL.
Regards Miykel   ):P

---

