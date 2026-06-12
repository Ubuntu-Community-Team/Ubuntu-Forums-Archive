---
title: "Apt not correclty downloading Packages file from repo"
date: 2018-12-06
forum: Server Platforms
---

### Post by tlf30 on 2018-12-06
Hello,
I have run into a strange issue, when I run ```
sudo apt update
``` I am getting a 404 on the Packages file. 
```

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages  404  Not Found [IP: 91.189.91.26 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-arm64/Packages  404  Not Found [IP: 91.189.91.26 80]
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic-backports/universe/binary-arm64/Packages  404  Not Found [IP: 91.189.91.26 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/main/binary-arm64/Packages  404  Not Found [IP: 91.189.88.149 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic/main/binary-arm64/Packages  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-security/main/binary-arm64/Packages  404  Not Found [IP: 91.189.88.152 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/binary-arm64/Packages  404  Not Found [IP: 91.189.88.152 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I checked, and that makes sense as the repo only provides the compressed versions, Packages.xz, Packages.gz. As seen here: [http://archive.ubuntu.com/ubuntu/dists/bionic/multiverse/binary-amd64/](http://archive.ubuntu.com/ubuntu/dists/bionic/multiverse/binary-amd64/)
I figured maybe the package file in /var/lib/apt was corrupt so i ran ```
sudo -fr /var/lib/apt/lists/*
``` to clear it out, but the same issue still occurred. This is causing many dependencies for packages I am trying to install to not resolve. 

This is my sources.list file:
```
deb http://archive.ubuntu.com/ubuntu/ bionic main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-security main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ bionic-updates main universe restricted multiverse
deb [arch=amd64] https://download.docker.com/linux/ubuntu/ bionic stable
# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu/ bionic stable
# deb [arch=armhf] https://download.docker.com/linux/ubuntu bionic stable
# deb-src [arch=armhf] https://download.docker.com/linux/ubuntu bionic stable

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```


Currently running 18.04.1 LTS fully updated.

If you have any ideas, I would love some help!

Thank you,
Trevor Flynn

---

### Post by deadflowr on 2018-12-06
Your output is looking for non-existent arm64 packages.
Just run
```
sudo dpkg --remove-architecture arm64
```

Somewhere along the line you've added the arm64 arch to your list of wanted archs.
Probably was added when you added the docker repos.

(Though now docker shows as defaulted to amd64, so it looks like the arm64 repos are not needed anymore.)

---

### Post by tlf30 on 2018-12-06
Ah, I forgot about that. Yes we are doing Jetson TX2 cross compilation on this server. Thus we are grabbing a lot of arm64 packages. 
So then maybe I am looking at the wrong place for my issues. Many packages do not have install candidates
```

sudo apt install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree... Done
E: Unable to locate package ubuntu-restricted-extras

```

```

 sudo apt install libdvdnav4 libdvdread4 gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly libdvd-pkg
Reading package lists... Done
Building dependency tree... Done
Package gstreamer1.0-plugins-bad is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gstreamer1.0-plugins-good gstreamer1.0-gl gstreamer1.0-plugins-base

Package gstreamer1.0-plugins-ugly is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gstreamer1.0-plugins-good

E: Unable to locate package libdvdnav4
E: Unable to locate package libdvdread4
E: Package 'gstreamer1.0-plugins-bad' has no installation candidate
E: Package 'gstreamer1.0-plugins-ugly' has no installation candidate
E: Unable to locate package libdvd-pkg


```

---

### Post by deadflowr on 2018-12-06
You need to configgle about the sources.list file.
There are no arm64 packages in the archive.ubuntu.com main repository, but those do exist over at ports.ubuntu.com repository.
Basically running into the same issue as this:
[https://answers.launchpad.net/ubuntu/+source/apt/+question/661407]("https://answers.launchpad.net/ubuntu/+source/apt/+question/661407")
Comment #4 has the best way to deal with it.

---

### Post by tlf30 on 2018-12-06
That worked great, thank you!
I'm not sure why it did not break sooner, we have not touched the sources.list in over 2 months. But that was the issue. 

Thank you

---

