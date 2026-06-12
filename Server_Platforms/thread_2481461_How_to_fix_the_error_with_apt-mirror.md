---
title: "How to fix the error with apt-mirror?"
date: 2022-11-30
forum: Server Platforms
---

### Post by autominus on 2022-11-30
Trying to create a local copy of the repository for Ubuntu 22.10.

Here is the file *mirror.list*:

```
    set base_path    /mnt/ExternalSSD/apt-mirror
    #
    set mirror_path  $base_path/mirror
    set skel_path    $base_path/skel
    set var_path     $base_path/var
    set cleanscript $base_path/var/clean.sh
    # set defaultarch  <running host architecture>
    set postmirror_script $base_path/var/postmirror.sh
    # set run_postmirror 0
    set nthreads     10
    set _tilde 0
    #
    ############# end config ##############
    
    eb http://archive.ubuntu.com/ubuntu kinetic main restricted universe multiverse
    deb http://archive.ubuntu.com/ubuntu kinetic-security main restricted universe multiverse
    deb http://archive.ubuntu.com/ubuntu kinetic-updates main restricted universe multiverse
    deb http://archive.ubuntu.com/ubuntu kinetic-proposed main restricted universe multiverse
    deb http://archive.ubuntu.com/ubuntu kinetic-backports main restricted universe multiverse
    
    deb-arm64 http://ports.ubuntu.com/ubuntu kinetic main restricted universe multiverse
    deb-arm64 http://ports.ubuntu.com/ubuntu kinetic-security main restricted universe multiverse
    deb-arm64 http://ports.ubuntu.com/ubuntu kinetic-updates main restricted universe multiverse
    deb-arm64 http://ports.ubuntu.com/ubuntu kinetic-proposed main restricted universe multiverse
    deb-arm64 http://ports.ubuntu.com/ubuntu kinetic-backports main restricted universe multiverse
    
    deb http://ppa.launchpad.net/jonmagon/kdiskmark/ubuntu kinetic main
    deb-arm64 http://ppa.launchpad.net/jonmagon/kdiskmark/ubuntu kinetic main
    
    clean http://archive.ubuntu.com/ubuntu
    clean http://ports.ubuntu.com/ubuntu
    clean http://ppa.launchpad.net/jonmagon/kdiskmark/ubuntu
```



When you run the command *sudo apt-mirror*,  I have the following response:

```
    root@Ubuntu-VM:/mnt/ExternalSSD/apt-mirror# apt-mirror
    Downloading 404 index files using 8 threads...
    Begin time: Wed Nov 30 09:33:11 2022
    [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
    End time: Wed Nov 30 09:35:45 2022
    
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-security/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-security/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-security/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-security/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-updates/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-updates/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-updates/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-updates/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-proposed/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-proposed/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-proposed/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-proposed/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-backports/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-backports/RI would be grateful for help in solving this problem.elease at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-backports/Release at /usr/bin/apt-mirror line 507.
    Failed to open Release file from http://ports.ubuntu.com/ubuntu/dists/kinetic-backports/Release at /usr/bin/apt-mirror line 507.
    Processing translation indexes: [TTTTTTTTTTTT]
    
    Begin time: Wed Nov 30 09:42:45 2022
    [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
    End time: Wed Nov 30 09:42:46 2022
    
    Processing indexes: [PPPPPapt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic/mainI would be grateful for help in solving this problem./binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic/restricted/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic/universe/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic/multiverse/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-security/main/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-security/restricted/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-security/universe/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-security/multiverse/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-updates/main/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-updates/restricted/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-updates/universe/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-updates/multiverse/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-proposed/main/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-proposed/restricted/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-proposed/universe/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-proposed/multiverse/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-backports/main/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-backports/restricted/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-backports/universe/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    apt-mirror: can't open index ports.ubuntu.com/ubuntu//dists/kinetic-backports/multiverse/binary-arm64/Packages in process_index at /usr/bin/apt-mirror line 800.
    PPPPPPP]
```


I would be grateful for help in solving this problem.

---

### Post by LHammonds on 2022-11-30
```
############# end config ##############
eb http://archive.ubuntu.com/ubuntu kinetic main restricted universe multiverse
```
Is the above a typo?  It is messing a "d" at the beginning of this line.

Also, I do not get any response from this URL...which is probably why all the errors are occurring related to it not being there:
```
http://ports.ubuntu.com/ubuntu
```

If I look at the root of that URL, I see an "ubuntu-ports" sub-folder....so maybe the correct URL is **[http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports)** but I have no experience setting up mirrors so I don't know.

LHammonds

---

### Post by autominus on 2022-12-01
You right, this is my mistake. I corrected my mistake in /etc/apt/mirror.list, but I still have the same error "Failed to open Release file...".

---

