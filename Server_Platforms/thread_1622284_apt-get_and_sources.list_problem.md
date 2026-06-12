---
title: "apt-get and sources.list problem"
date: 2010-11-15
forum: Server Platforms
---

### Post by penguin-power on 2010-11-15
hi all!

i googled and searched here for 2 or 3 days but cant find a solution to my problem.  :(

i did a fresh install of ubuntu 10.04.1 and selected (at install)
to install a LAMP and SSH server. (its a vm running in esxi4)

all installed, no errors or issues.

after install, started installing nagios. to compile nagios, i got an error gcc or cc not installed.

so i: "apt-get install -y gcc", but got and error to do with my sources that cant be updated.

* i dont get it, it a new "un-tweaked" installation and almost half of the sources fail.

even tried to "--fix-missing". no go.

can anyone help please? [-o<

to demo the problem, i will use "apt-get update"

```


root@nagios:~/nagios-3.2.3# apt-get update
Get: 1 http://security.ubuntu.com lucid-security Release.gpg [2,232B]
Get: 2 http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB [2,252B]
Get: 3 http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB [2,258B]
99% [2 Translation-en_GB bzip2 0B] [Connecting to ls.archive.ubuntu.com] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_GB
Get: 4 http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB [2,256B]
74% [3 Translation-en_GB bzip2 0B] [Connecting to ls.archive.ubuntu.com] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_GB
49% [4 Translation-en_GB bzip2 0B] [Connecting to ls.archive.ubuntu.com] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_GB
Get: 5 http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB [2,258B]
39% [5 Translation-en_GB bzip2 0B] [Connecting to ls.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_GB
Get: 6 http://security.ubuntu.com lucid-security Release [2,228B]
Err http://security.ubuntu.com lucid-security Release

Get: 7 http://ls.archive.ubuntu.com lucid Release.gpg [2,227B]
Get: 8 http://ls.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [2,247B]
49% [8 Translation-en_GB bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB
Get: 9 http://ls.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,253B]
44% [9 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB
Get: 10 http://ls.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [2,251B]
39% [10 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB
Get: 11 http://ls.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [2,253B]
36% [11 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB
Get: 12 http://ls.archive.ubuntu.com lucid-updates Release.gpg [2,235B]
Get: 13 http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB [2,255B]
38% [13 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_GB
Get: 14 http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB [2,261B]
35% [14 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_GB
Get: 15 http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB [2,259B]
33% [15 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_GB
Get: 16 http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB [2,261B]
31% [16 Translation-en_GB bzip2 0B] [Connecting to ls.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Ign http://ls.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_GB
Get: 17 http://ls.archive.ubuntu.com lucid Release [2,223B]
Ign http://ls.archive.ubuntu.com lucid Release
Get: 18 http://ls.archive.ubuntu.com lucid-updates Release [2,231B]
Ign http://ls.archive.ubuntu.com lucid-updates Release
Get: 19 http://ls.archive.ubuntu.com lucid/main Packages [2,245B]
36% [19 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 20 http://ls.archive.ubuntu.com lucid/restricted Packages [2,251B]
39% [20 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 21 http://ls.archive.ubuntu.com lucid/main Sources [2,239B]
42% [21 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 22 http://ls.archive.ubuntu.com lucid/restricted Sources [2,245B]
45% [22 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 23 http://ls.archive.ubuntu.com lucid/universe Packages [2,249B]
47% [23 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 24 http://ls.archive.ubuntu.com lucid/universe Sources [2,243B]
49% [24 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 25 http://ls.archive.ubuntu.com lucid/multiverse Packages [2,251B]
51% [25 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 26 http://ls.archive.ubuntu.com lucid/multiverse Sources [2,245B]
53% [26 Sources bzip2 0B] [Connecting to ls.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 27 http://ls.archive.ubuntu.com lucid-updates/main Packages [2,253B]
55% [27 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 28 http://ls.archive.ubuntu.com lucid-updates/restricted Packages [2,259B]
56% [28 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 29 http://ls.archive.ubuntu.com lucid-updates/main Sources [2,247B]
58% [29 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 30 http://ls.archive.ubuntu.com lucid-updates/restricted Sources [2,252B]
59% [30 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 31 http://ls.archive.ubuntu.com lucid-updates/universe Packages [2,257B]
61% [31 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 32 http://ls.archive.ubuntu.com lucid-updates/universe Sources [2,251B]
62% [32 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 33 http://ls.archive.ubuntu.com lucid-updates/multiverse Packages [2,259B]
63% [33 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 34 http://ls.archive.ubuntu.com lucid-updates/multiverse Sources [2,253B]
64% [34 Sources bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err http://ls.archive.ubuntu.com lucid-updates/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 76.4kB in 3s (20.8kB/s)
Reading package lists... Done
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: GPG error: http://ls.archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://ls.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://ls.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
root@nagios:~/nagios-3.2.3#



```

---

### Post by wojox on 2010-11-15
Have you tried changing servers?

---

### Post by penguin-power on 2010-11-15
> **wojox said:**
> Have you tried changing servers?

thx for reply, and yes, i did.

i went here:
 [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)

...generated a very basic sources.list:
```


#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 


```

....then i "apt-get update" but got this:

```


root@nagios:~# apt-get update
Get: 1 http://us.archive.ubuntu.com lucid Release.gpg [2,227B]
Get: 2 http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB [2,247B]
Get: 3 http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB [2,253B]
99% [2 Translation-en_GB bzip2 0B]bzip2: (stdin) is not a bzip2 file.      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_GB
66% [3 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_GB
Get: 4 http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB [2,251B]
49% [4 Translation-en_GB bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_GB
Get: 5 http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB [2,253B]
39% [5 Translation-en_GB bzip2 0B] [Connecting to us.archive.ubuntu.com]bzip2: (stdin) is not a bzip2 file.
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_GB
Get: 6 http://us.archive.ubuntu.com lucid Release [2,223B]              
Ign http://us.archive.ubuntu.com lucid Release          
Get: 7 http://us.archive.ubuntu.com lucid/main Packages [2,245B]
42% [7 Packages bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/main Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 8 http://us.archive.ubuntu.com lucid/restricted Packages [2,251B]
49% [8 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/restricted Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 9 http://us.archive.ubuntu.com lucid/universe Packages [2,249B]
55% [9 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/universe Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 10 http://us.archive.ubuntu.com lucid/multiverse Packages [2,251B]
59% [10 Packages bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/multiverse Packages
  Sub-process /bin/bzip2 returned an error code (2)
Get: 11 http://us.archive.ubuntu.com lucid/main Sources [2,239B]
63% [11 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/main Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 12 http://us.archive.ubuntu.com lucid/restricted Sources [2,245B]
66% [12 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/restricted Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 13 http://us.archive.ubuntu.com lucid/universe Sources [2,241B]
69% [13 Sources bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/universe Sources
  Sub-process /bin/bzip2 returned an error code (2)
Get: 14 http://us.archive.ubuntu.com lucid/multiverse Sources [2,245B]
71% [14 Sources bzip2 0B]bzip2: (stdin) is not a bzip2 file.
Err http://us.archive.ubuntu.com lucid/multiverse Sources
  Sub-process /bin/bzip2 returned an error code (2)
Fetched 31.4kB in 1s (31.3kB/s)
W: GPG error: http://us.archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

E: Some index files failed to download, they have been ignored, or old ones used instead.
root@nagios:~# 



```

** thing is, i have a few "ubuntu 10.04.1 lts" servers, one of them is identical, only run backuppc instead of nagios.

tried a "apt-get update" and it does the same!  nothing changed on the server that was working, but same issue exists.

- on my previous post i think apt also complained about "file sizes miss-match" or something. 

- do i need to import keys? if so, how? never done that before.

* any help much appreciated *   :D

---

### Post by drs305 on 2010-11-15
> GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures were invalid: **NODATA 1 NODATA 2**


Try opening Synaptic. Go to Settings, Repositories, Authentication tab.

Note: In this tab, you should be able to select the 'offending' source and just hit the "Import Key File", but I've not tried it. If that doesn't work:
If there is an Ubuntu listing, delete it.
Open a terminal and run "sudo apt-get update".
You will receive a message like this:
> W: GPG error: [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF**[COLOR="DarkRed"]437D05B5[/COLOR]**

Take the last 8 characters of any messages and run this command:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **437D05B5**
```
Repeat for each error.

---

### Post by penguin-power on 2010-11-15
> **drs305 said:**
> Try opening Synaptic. Go to Settings, Repositories, Authentication tab.

Note: In this tab, you should be able to select the 'offending' source and just hit the "Import Key File", but I've not tried it. If that doesn't work:
If there is an Ubuntu listing, delete it.
Open a terminal and run "sudo apt-get update".
You will receive a message like this:

Take the last 8 characters of any messages and run this command:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **437D05B5**
```
Repeat for each error.


mmmm...  would love to give it a try, but from your directions above i presume you are using ubuntu desktop. i'm on ubuntu server. :(

is there any terminal-tool for synaptic? (if not, how then?)

thx again for your time. :)

---

### Post by sikander3786 on 2010-11-15
> **penguin-power said:**
> mmmm...  would love to give it a try, but from your directions above i presume you are using ubuntu desktop. i'm on ubuntu server. :(

is there any terminal-tool for synaptic? (if not, how then?)

thx again for your time. :)
Hi. **drs305** seems away for now so I'm jumping in.

These are the instructions for Ubuntu server using command-line ;-)
> 
Open a terminal and run "sudo apt-get update".
You will receive a message like this:
[quote]
W: GPG error: [http://www.gtlib.gatech.edu](http://www.gtlib.gatech.edu) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF**437D05B5**
Take the last 8 characters of any messages and run this command:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys **437D05B5**
```

Repeat for each error.[/quote]

---

### Post by penguin-power on 2010-11-15
> **sikander3786 said:**
> Hi. **drs305** seems away for now so I'm jumping in.

These are the instructions for Ubuntu server using command-line ;-)

](*,)  works vpn just dropped.....  got no connection anymore..   :(
 
looks like a power fail, phone system offline too.

(does anyone see the irony? --> the above is to create a nagios box....)

---

### Post by tonyyarusso on 2010-11-18
Meanwhile, once you get apt straightened out, you should just install nagios3 from the repositories rather than trying to compile it yourself.

---

