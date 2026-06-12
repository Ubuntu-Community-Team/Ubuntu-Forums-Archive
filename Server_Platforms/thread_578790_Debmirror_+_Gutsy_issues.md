---
title: "Debmirror + Gutsy issues"
date: 2007-10-17
forum: Server Platforms
---

### Post by kcbnac on 2007-10-17
Attempting to use debmirror, as documented here:
[https://help.ubuntu.com/community/Debmirror](https://help.ubuntu.com/community/Debmirror)

I've successfully been running the above for Feisty for the last several months on my laptop, but for some reason putting the script on my new server & modifying it to gutsy, it seems to error out.
```

user@host:~/scripts$ ./BuildMirror.sh 
Patch binary missing, falling back to --pdiff=none
Mirroring to /home/UbuntuMirror from http://archive.ubuntu.com/ubuntu/
Arches: i386
Dists: gutsy,gutsy-security,gutsy-updates
Sections: main,restricted,universe,multiverse
Will clean up AFTER mirroring.
Pdiff mode: none.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/gutsy/Release... ok
[0%] Getting: dists/gutsy/Release.gpg... ok
[0%] Getting: dists/gutsy-security/Release... ok
[0%] Getting: dists/gutsy-security/Release.gpg... ok
[0%] Getting: dists/gutsy-updates/Release... ok
[0%] Getting: dists/gutsy-updates/Release.gpg... ok
Get Packages and Sources files and other miscellany.
Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (38 MiB).
Downloaded 38 MiB in 5s at 7600.82 kiB/s
Errors:
 Patch binary missing, falling back to --pdiff=none
Everything OK. Moving meta files.
Cleanup mirror.
All done.
user@host:~/scripts$ 


```

The 'Patch binary missing, falling back to --pdiff=none' line seems to be what is causing the problem.

Any ideas?  I'll be giving it a try tomorrow, not sure if the fact that Gutsy isn't "released" yet is having any effect on it.  (Don't see how it would)

Thanks in advance for the help!

---

### Post by kcbnac on 2007-10-23
Did some tweaks.  Here's the code:

```

#### Start script to automate building of Ubuntu mirror #####
## THE NEXT LINE IS NEEDED THE REST OF THE LINES STARTING WITH A # CAN BE DELETED

#!/bin/bash

## Setting variables with explanations.

# Arch=         -a      # Architecture. For Ubuntu can be i386, powerpc or amd64.
# sparc, only starts in dapper, it is only the later models of sparc
#
arch=i386

# Minimum Ubuntu system requires main, restricted
# Section=      -s      # Section (One of the following - main/restricted/universe/multiverse).
#
section=main,restricted,universe,multiverse

# Release=      -d      # Release of the system (Dapper, Edgy, Feisty, Gutsy), and the -updates and -security ( -backports can be added if desired)
#
release=gutsy,gutsy-security,gutsy-updates

# Server=       -h      # Server name, minus the protocol and the path at the end
# CHANGE "*" to equal the mirror you want to create your mirror from. au. in Australia  ca. in Canada.
# This can be found in your own /etc/apt/sources.list file, assuming you have Ubuntu installed.
#
server=us.archive.ubuntu.com


# Dir=          -r      # Path from the main server, so http://my.web.server/$dir, Server dependant
#
inPath=ubuntu

# Proto=        -e      # Protocol to use for transfer (http, ftp, hftp, rsync)
# Choose one - http is most usual the service, and the service must be avaialbe on the server you point at.
#
proto=http

# Outpath=              # Directory to store the mirror in
# Make this a full path to where you want to mirror the material.
#
outPath=/home/UbuntuMirror

# The --nosource option only downloads debs and not deb-srcs
# The --progress option shows files as they are downloaded
# --source \ in the place of --no-source \ if you want sources also.
# Start script
#
debmirror       -a $arch \
                --no-source \
                -m \
                --passive \
                -s $section \
                -h $server \
                -d $release \
                -r $inPath \
                --progress \
                -e $proto \
                --ignore-release-gpg \
                $outPath

#### End script to automate building of Ubuntu mirror ####

```



Here's the results after running the above:

```
user@host:~/scripts$ ./BuildMirror.sh 
Mirroring to /home/UbuntuMirror from http://us.archive.ubuntu.com/ubuntu/
Arches: i386
Dists: gutsy,gutsy-security,gutsy-updates
Sections: main,restricted,universe,multiverse
Passive mode on.
Checking md5sums.
Will clean up AFTER mirroring.
Pdiff mode: use.
Attempting to get lock, this might take 2 minutes before it fails.
Get Release files.
[0%] Getting: dists/gutsy/Release... ok
[0%] Getting: dists/gutsy/Release.gpg... ok
[0%] Getting: dists/gutsy-security/Release... ok
[0%] Getting: dists/gutsy-security/Release.gpg... ok
[0%] Getting: dists/gutsy-updates/Release... ok
[0%] Getting: dists/gutsy-updates/Release.gpg... ok
Get Packages and Sources files and other miscellany.
dists/gutsy-security/main/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-security/main/binary-i386/Packages.gz... ok
dists/gutsy-security/universe/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-security/universe/binary-i386/Packages.gz... ok
dists/gutsy-security/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-security/multiverse/binary-i386/Packages.gz... ok
dists/gutsy-updates/main/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-updates/main/binary-i386/Packages.gz... ok
dists/gutsy-updates/universe/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-updates/universe/binary-i386/Packages.gz... ok
dists/gutsy-updates/multiverse/binary-i386/Packages.gz needs fetch
[100%] Getting: dists/gutsy-updates/multiverse/binary-i386/Packages.gz... ok
Parse Packages and Sources files and add to the file list everything therein.
Download all files that we need to get (38 MiB).
Downloaded 38 MiB in 9s at 4240.66 kiB/s
Everything OK. Moving meta files.
Cleanup mirror.
All done.
user@host::~/scripts$ 
```

Any ideas on why it isn't finding ANY files to download?

---

### Post by ischerry on 2007-10-28
I've experienced the same problem.  Something is definitely broken with the updated version.  I removed the debmirror package, changed my apt sources back to feisty, and installed the feisty version.  Debmirror worked with the feisty version, so I changed back to gutsy, updated, and then debmirror was broken again.

---

### Post by ischerry on 2007-10-28
New finding..  I removed the gutsy version of debmirror, but not the dependencies as I had before.  I manually downloaded the debmirror package used in feisty and installed it, but still had the same result when running the debmirror script.  Apparently, there's a problem with a dependency, not with debmirror itself.

---

### Post by Angeltronix on 2007-11-01
I did have the same problem with debmirror...

As ischerry says, the problem isn't with debmirror, but you might have a missing program called "patch", used for proccess the diff files, or something like that.

So, to fix the problem simply do a:

```
 sudo apt-get install patch
```
and it should work :)

---

### Post by ebrahim on 2007-11-03
My patch package is up to date but the problem persists! :(

---

### Post by ebrahim on 2007-11-03
See these:
[https://bugs.launchpad.net/ubuntu/+source/debmirror/+bug/136634](https://bugs.launchpad.net/ubuntu/+source/debmirror/+bug/136634)
[https://answers.launchpad.net/ubuntu/+source/libcompress-zlib-perl/+question/16651](https://answers.launchpad.net/ubuntu/+source/libcompress-zlib-perl/+question/16651)

---

