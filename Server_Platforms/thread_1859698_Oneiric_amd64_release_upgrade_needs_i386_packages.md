---
title: "Oneiric amd64 release upgrade needs i386 packages?"
date: 2011-10-14
forum: Server Platforms
---

### Post by lurker_mike on 2011-10-14
I have a local apt mirror using apt-get.  I have updated my mirror.list on the apt mirror and run it to fetch the Oneiric updates (~53GB).  

When attempting to upgrade an 11.04 server amd64 installation, do-release-upgrade fails with the following error:

```

Error during update 

A problem occurred during the update. This is usually some sort of 
network problem, please check your network connection and retry. 

W:Failed to fetch 
http://.../ubuntu/dists/oneiric/main/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, W:Failed to fetch 
http://.../ubuntu/dists/oneiric/restricted/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, W:Failed to fetch 
http://.../ubuntu/dists/oneiric/universe/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, W:Failed to fetch 
http://.../ubuntu/dists/oneiric/multiverse/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, W:Failed to fetch 
http://.../ubuntu/dists/oneiric-updates/main/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, W:Failed to fetch 
http://.../ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, W:Failed to fetch 
http://.../ubuntu/dists/oneiric-updates/universe/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, W:Failed to fetch 
http://.../ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages 
404 Not Found [IP: ... 80] 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. 


Restoring original system state

Aborting

```Here is the /etc/apt/mirror.list on the apt mirror:

```

############# config ##################
#
set base_path    /nfs/apt-mirror
set var_path     $base_path/var
set mirror_path  $base_path/mirror
set skel_path    $base_path/skel
set cleanscript  $var_path/clean.sh
set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############

deb http://mirrors.us.kernel.org/ubuntu maverick main restricted universe multiverse
deb http://mirrors.us.kernel.org/ubuntu maverick-security main restricted universe multiverse
deb http://mirrors.us.kernel.org/ubuntu maverick-updates main restricted universe multiverse

deb-src http://mirrors.us.kernel.org/ubuntu maverick main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu maverick-security main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu maverick-updates main restricted universe multiverse

##### natty

deb http://mirrors.us.kernel.org/ubuntu natty main restricted universe multiverse
deb http://mirrors.us.kernel.org/ubuntu natty-security main restricted universe multiverse
deb http://mirrors.us.kernel.org/ubuntu natty-updates main restricted universe multiverse

deb-src http://mirrors.us.kernel.org/ubuntu natty main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu natty-security main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu natty-updates main restricted universe multiverse

##### oneiric

deb http://mirrors.us.kernel.org/ubuntu oneiric main restricted universe multiverse
deb http://mirrors.us.kernel.org/ubuntu oneiric-security main restricted universe multiverse
deb http://mirrors.us.kernel.org/ubuntu oneiric-updates main restricted universe multiverse

deb-src http://mirrors.us.kernel.org/ubuntu oneiric main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu oneiric-security main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu oneiric-updates main restricted universe multiverse

clean http://mirrors.us.kernel.org/ubuntu

```Why does Oneiric need i386 files to upgrade an amd64 installation?

What is the correct way to fix this?

---

### Post by Space_Balls on 2011-10-14
With Oneiric they switched to a multi-arch repository. This deprecates the lib32 packages, but you will need both repositories in your sources.list. I've also had to switch my own repository from amd64 only to amd64+i386.

You will need to mirror both the i386 and amd64 repositories on your apt-mirror.

---

### Post by lurker_mike on 2011-10-14
> **Space_Balls said:**
> With Oneiric they switched to a multi-arch repository. This deprecates the lib32 packages, but you will need both repositories in your sources.list. I've also had to switch my own repository from amd64 only to amd64+i386.

You will need to mirror both the i386 and amd64 repositories on your apt-mirror.

Thanks, SB.  I modified my mirror.list for Oneiric thusly:

```

set defaultarch  amd64

##### oneiric

deb http://mirrors.us.kernel.org/ubuntu oneiric main restricted universe multiverse
deb-i386 http://mirrors.us.kernel.org/ubuntu oneiric main restricted universe multiverse

deb http://mirrors.us.kernel.org/ubuntu oneiric-security main restricted universe multiverse
deb-i386 http://mirrors.us.kernel.org/ubuntu oneiric-security main restricted universe multiverse

deb http://mirrors.us.kernel.org/ubuntu oneiric-updates main restricted universe multiverse
deb-i386 http://mirrors.us.kernel.org/ubuntu oneiric-updates main restricted universe multiverse

deb-src http://mirrors.us.kernel.org/ubuntu oneiric main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu oneiric-security main restricted universe multiverse
deb-src http://mirrors.us.kernel.org/ubuntu oneiric-updates main restricted universe multiverse

```I started up apt-mirror and it looks like the i386 packages are ~17GB.  

Will post again after the mirror completes and I run do-release-upgrade again.

---

### Post by lurker_mike on 2011-10-14
After the i386 files finished downloading, I re-ran do-release-upgrade which promptly crashed (an actual Python error from the script).  I poked around the log files then went ahead and ran it again, and the second time it seemed to work without problems.

Upgrade successful!

---

### Post by limaxray on 2011-10-17
I had the same problem initially setting up my mirror and was wondering why this was.  Thank you for the explanation.

On a related note, how did you get the client machine to upgrade from your local mirror?  In the past, I've had the entries in sources.list point to my local mirror and the upgrade would pull from the mirror as expected.

This time, the upgrade commented out the entirety of sources.list and used the default mirror instead.  Is there something I'm missing?

---

### Post by lurker_mike on 2011-10-17
> **limaxray said:**
> I had the same problem initially setting up my mirror and was wondering why this was.  Thank you for the explanation.

On a related note, how did you get the client machine to upgrade from your local mirror?  In the past, I've had the entries in sources.list point to my local mirror and the upgrade would pull from the mirror as expected.

This time, the upgrade commented out the entirety of sources.list and used the default mirror instead.  Is there something I'm missing?

When I ran do-release-upgrade, one of the first questions it asked was this:

```

Updating repository information
WARNING: Failed to read mirror file

No valid mirror found 

While scanning your repository information no mirror entry for the 
upgrade was found. This can happen if you run a internal mirror or if 
the mirror information is out of date. 

Do you want to rewrite your 'sources.list' file anyway? If you choose 
'Yes' here it will update all 'natty' to 'oneiric' entries. 
If you select 'No' the upgrade will cancel. 

Continue [yN]

```I answered Yes to this question and everything just worked.

---

