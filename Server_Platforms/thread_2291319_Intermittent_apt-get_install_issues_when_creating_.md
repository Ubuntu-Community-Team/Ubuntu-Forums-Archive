---
title: "Intermittent apt-get install issues when creating an AMI using Packer"
date: 2015-08-19
forum: Server Platforms
---

### Post by behrangsa on 2015-08-19
Hi,

I am trying to create an AMI based on `ami-3b054701` in the `ap-southeast-2` region. The Packer config has one simple provisioner:

```
#!/bin/bash -e

info() {
    echo -e "[INFO] $1\n"
}

exec_cmd() {
    echo -e "\n[INFO] $1\n"
    eval $1
}

exec_cmd "apt-get update"

exec_cmd "apt-get -y upgrade"

exec_cmd "apt-get -y install build-essential git zip unzip wget default-jre"
```

This sometimes work with no problem but sometimes fails with this error:


```
    ami: [INFO] apt-get -y install build-essential git zip unzip wget default-jre
    ami:
    ami: Reading package lists... Done
    ami: Building dependency tree
    ami: Reading state information... Done
    ami: Package build-essential is not available, but is referred to by another package.
    ami: This may mean that the package is missing, has been obsoleted, or
    ami: is only available from another source
    ami:
    ami: Package default-jre is not available, but is referred to by another package.
    ami: This may mean that the package is missing, has been obsoleted, or
    ami: is only available from another source
    ami:
    ami: Package zip is not available, but is referred to by another package.
    ami: This may mean that the package is missing, has been obsoleted, or
    ami: is only available from another source
    ami:
    ami: E: Package 'build-essential' has no installation candidate
    ami: E: Package 'zip' has no installation candidate
    ami: E: Package 'default-jre' has no installation candidate
```

I wasted one full day to find a way to avoid this. There was a solution on Stack Exchange but I can't remember its link. And it was more of a hack than a solution. Is there a way to prevent this error from happening intermittently?

---
EDIT: The StackOverflow post I mentioned above is this: [http://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error](http://askubuntu.com/questions/41605/trouble-downloading-packages-list-due-to-a-hash-sum-mismatch-error) 
---
Here's the full output of Packer

```
==> ami: Prevalidating AMI Name...
==> ami: Inspecting the source AMI...
==> ami: Creating temporary keypair: packer 55d33324-e319-bd49-24c5-c06a18b4fe09
==> ami: Launching a source AWS instance...
    ami: Instance ID: i-8b78cd55
==> ami: Waiting for instance (i-8b78cd55) to become ready...
==> ami: Waiting for SSH to become available...
==> ami: Connected to SSH!
==> ami: Provisioning with shell script: scripts/provision.sh
    ami:
    ami: [INFO] apt-get update
    ami:
    ami: Ign http://security.ubuntu.com trusty-security InRelease
    ami: Ign http://archive.ubuntu.com trusty InRelease
    ami: Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
    ami: Ign http://archive.ubuntu.com trusty-updates InRelease
    ami: Get:2 http://security.ubuntu.com trusty-security Release [63.5 kB]
    ami: Hit http://archive.ubuntu.com trusty Release.gpg
    ami: Get:3 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]
    ami: Hit http://archive.ubuntu.com trusty Release
    ami: Get:4 http://archive.ubuntu.com trusty-updates Release [63.5 kB]
    ami: Get:5 http://security.ubuntu.com trusty-security/main amd64 Packages [333 kB]
    ami: Get:6 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8875 B]
    ami: Hit http://archive.ubuntu.com trusty/main amd64 Packages
    ami: Get:7 http://security.ubuntu.com trusty-security/universe amd64 Packages [114 kB]
    ami: Hit http://archive.ubuntu.com trusty/restricted amd64 Packages
    ami: Hit http://archive.ubuntu.com trusty/universe amd64 Packages
    ami: Get:8 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3686 B]
    ami: Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages
    ami: Get:9 http://security.ubuntu.com trusty-security/main Translation-en [181 kB]
    ami: Hit http://archive.ubuntu.com trusty/main Translation-en
    ami: Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
    ami: Hit http://archive.ubuntu.com trusty/multiverse Translation-en
    ami: Hit http://security.ubuntu.com trusty-security/restricted Translation-en
    ami: Hit http://archive.ubuntu.com trusty/restricted Translation-en
    ami: Get:10 http://security.ubuntu.com trusty-security/universe Translation-en [66.6 kB]
    ami: Hit http://archive.ubuntu.com trusty/universe Translation-en
    ami: Get:11 http://archive.ubuntu.com trusty-updates/main amd64 Packages [605 kB]
    ami: Get:12 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.3 kB]
    ami: Get:13 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [308 kB]
    ami: Get:14 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.9 kB]
    ami: Get:15 http://archive.ubuntu.com trusty-updates/main Translation-en [292 kB]
    ami: Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
    ami: Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
    ami: Get:16 http://archive.ubuntu.com trusty-updates/universe Translation-en [163 kB]
    ami: Fetched 2232 kB in 16s (134 kB/s)
    ami: Reading package lists... Done
    ami:
    ami: [INFO] apt-get -y upgrade
    ami:
    ami: Reading package lists... Done
    ami: Building dependency tree
    ami: Reading state information... Done
    ami: Calculating upgrade... Done
    ami: The following packages have been kept back:
    ami: linux-headers-generic linux-headers-virtual linux-image-virtual
    ami: linux-virtual
    ami: 0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
    ami:
    ami: [INFO] apt-get -y install build-essential git zip unzip wget default-jre
    ami:
    ami: Reading package lists... Done
    ami: Building dependency tree
    ami: Reading state information... Done
    ami: Package build-essential is not available, but is referred to by another package.
    ami: This may mean that the package is missing, has been obsoleted, or
    ami: is only available from another source
    ami:
    ami: Package default-jre is not available, but is referred to by another package.
    ami: This may mean that the package is missing, has been obsoleted, or
    ami: is only available from another source
    ami:
    ami: Package zip is not available, but is referred to by another package.
    ami: This may mean that the package is missing, has been obsoleted, or
    ami: is only available from another source
    ami:
    ami: E: Package 'build-essential' has no installation candidate
    ami: E: Package 'zip' has no installation candidate
    ami: E: Package 'default-jre' has no installation candidate
==> ami: Terminating the source AWS instance...
==> ami: No AMIs to cleanup
```

---

