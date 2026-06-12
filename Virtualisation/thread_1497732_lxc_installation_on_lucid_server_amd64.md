---
title: "lxc installation on lucid server amd64"
date: 2010-05-31
forum: Virtualisation
---

### Post by .primus on 2010-05-31
hi everyone,

i am running lucid server amd64 and recently tried to set up lxc.

i read through the following during my setup:
[LIST]
[*][http://blog.bodhizazen.net/linux/lxc-linux-containers/]("http://blog.bodhizazen.net/linux/lxc-linux-containers/")
[*][http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/]("http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/")
[*][http://lxc.teegra.net/]("http://lxc.teegra.net/")
[*][http://github.com/phbaer/lxc-tools/blob/master/lxc-ubuntu]("http://github.com/phbaer/lxc-tools/blob/master/lxc-ubuntu")
[*][http://blog.system42.net/2010/05/18/ubuntu-1004-lxc-container-script/]("http://blog.system42.net/2010/05/18/ubuntu-1004-lxc-container-script/")
[/LIST]

the first issue i ran into was that my [FONT="Fixedsys"]/var[/FONT] was on a separate partition (see [https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/566827]("https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/566827") and [http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00261.html]("http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00261.html")). the resolution to this (for me) was to pull the latest lxc from the git repository ([http://lxc.sourceforge.net/]("http://lxc.sourceforge.net/")) and install it.

so i don't know if the problem i am facing now is a result of using the latest code from the git repository, but i cannot seem to log into the container.

if i try to use [FONT="Fixedsys"]sudo lxc-console -n something[/FONT], then i simply get a screen
```

Type <Ctrl+a q> to exit the console

```

additionally, i've set up sshd on the container and when i attempt to ssh to the container's ip address, i get
```

PTY allocation request failed on channel 0

```

if i look at the auth.log in the container, then it appears that the login of the user i am ssh-ing with is successful, but we see
```

May 31 03:34:06 localhost sshd[51]: Server listening on 0.0.0.0 port 22.
May 31 03:34:06 localhost sshd[51]: Server listening on :: port 22.
May 31 03:37:10 localhost sshd[97]: Accepted password for someuser from 192.168.1.31 port 40696 ssh2
May 31 03:37:10 localhost sshd[97]: pam_unix(sshd:session): session opened for user someuser by (uid=0)
May 31 03:37:10 localhost sshd[97]: error: openpty: No such file or directory
May 31 03:37:10 localhost sshd[109]: error: session_pty_req: session 0 alloc failed

```

i came across the following discussion of this issue
[LIST]
[*][http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00240.html]("http://www.mail-archive.com/lxc-users@lists.sourceforge.net/msg00240.html") 
[*][http://platonic.techfiz.info/2008/10/13/pty-allocation-request-failed-on-channel-0/]("http://platonic.techfiz.info/2008/10/13/pty-allocation-request-failed-on-channel-0/")
[/LIST]

but i appear to have the [FONT="Fixedsys"]ptmx[/FONT] device in [FONT="Fixedsys"]/path/to/container/rootfs/dev[/FONT]
```

total 16
drwxr-xr-x  4 root root 4096 2010-05-30 22:46 .
drwxr-xr-x 26 root root 4096 2010-05-31 03:34 ..
crw-------  1 root root 5, 1 2010-05-31 03:34 console
crw-rw-rw-  1 root root 1, 7 2010-05-30 22:46 full
prw-------  1 root root    0 2010-05-30 22:46 initctl
crw-rw-rw-  1 root root 1, 3 2010-05-30 22:46 null
crw-rw-rw-  1 root root 5, 2 2010-05-30 22:46 ptmx
drwxr-xr-x  2 root root 4096 2010-05-30 22:46 pts
crw-rw-rw-  1 root root 1, 8 2010-05-30 22:46 random
drwxrwxrwt  2 root root 4096 2010-05-30 22:46 shm
crw-rw-rw-  1 root root 5, 0 2010-05-30 22:46 tty
crw-rw-rw-  1 root root 4, 0 2010-05-30 22:46 tty0
crw-rw-rw-  1 root root 4, 1 2010-05-30 22:46 tty1
crw-rw-rw-  1 root root 4, 2 2010-05-30 22:46 tty2
crw-rw-rw-  1 root root 4, 3 2010-05-30 22:46 tty3
crw-rw-rw-  1 root root 4, 4 2010-05-30 22:46 tty4
crw-rw-rw-  1 root root 1, 9 2010-05-30 22:46 urandom
crw-rw-rw-  1 root root 1, 5 2010-05-30 22:46 zero

```

i thought maybe there was something preventing me from accessing the container due to the init scripts, but i tried a variety of options and nothing has been successful. currently in my [FONT="Fixedsys"]/path/to/container/rootfs/etc/init[/FONT]
```

total 168
drwxr-xr-x  2 root root 4096 2010-05-31 02:55 .
drwxr-xr-x 52 root root 4096 2010-05-30 23:02 ..
-rw-r--r--  1 root root  518 2010-03-12 22:29 console-setup.conf
-rw-r--r--  1 root root  356 2010-04-02 00:13 control-alt-delete.conf.distrib
-rw-r--r--  1 root root  297 2010-04-15 06:51 cron.conf
-rw-r--r--  1 root root  273 2010-02-24 18:26 dmesg.conf.distrib
-rw-r--r--  1 root root  312 2010-03-10 19:00 hostname.conf
-rw-r--r--  1 root root  557 2010-03-22 17:54 hwclock.conf.distrib
-rw-r--r--  1 root root  444 2010-03-22 17:54 hwclock-save.conf.distrib
-rw-r--r--  1 root root  676 2010-05-30 22:52 lxc.conf
-rw-r--r--  1 root root  367 2010-04-14 04:36 module-init-tools.conf
-rw-r--r--  1 root root  747 2010-04-26 05:53 mountall.conf
-rw-r--r--  1 root root  349 2010-04-26 05:53 mountall-net.conf.distrib
-rw-r--r--  1 root root  261 2010-04-26 05:53 mountall-reboot.conf.distrib
-rw-r--r--  1 root root 1201 2010-04-26 05:53 mountall-shell.conf.distrib
-rw-r--r--  1 root root  427 2010-04-26 05:53 mounted-dev.conf
-rw-r--r--  1 root root 1149 2010-04-26 05:53 mounted-tmp.conf
-rw-r--r--  1 root root  490 2010-04-26 05:53 mounted-varrun.conf
-rw-r--r--  1 root root  332 2010-02-20 04:30 networking.conf
-rw-r--r--  1 root root  493 2010-02-20 04:30 network-interface.conf
-rw-r--r--  1 root root 1221 2010-02-20 04:30 network-interface-security.conf
-rw-r--r--  1 root root  996 2010-04-27 08:35 plymouth.conf.distrib
-rw-r--r--  1 root root  326 2010-04-27 08:35 plymouth-log.conf.distrib
-rw-r--r--  1 root root  888 2010-04-27 08:35 plymouth-splash.conf.distrib
-rw-r--r--  1 root root  731 2010-04-27 08:35 plymouth-stop.conf.distrib
-rw-r--r--  1 root root  293 2009-12-16 19:34 procps.conf
-rw-r--r--  1 root root  387 2010-04-02 00:13 rc.conf
-rw-r--r--  1 root root  822 2010-04-02 00:13 rcS.conf
-rw-r--r--  1 root root 1534 2010-05-30 22:49 rc-sysinit.conf
-rw-r--r--  1 root root  280 2010-02-24 18:26 rsyslog.conf
-rw-r--r--  1 root root  615 2010-03-08 16:11 ssh.conf
-rw-r--r--  1 root root  228 2010-04-02 00:13 tty1.conf
-rw-r--r--  1 root root  213 2010-04-02 00:13 tty2.conf.distrib
-rw-r--r--  1 root root  213 2010-04-02 00:13 tty3.conf.distrib
-rw-r--r--  1 root root  213 2010-04-02 00:13 tty4.conf.distrib
-rw-r--r--  1 root root  213 2010-04-02 00:13 tty5.conf.distrib
-rw-r--r--  1 root root  213 2010-04-02 00:13 tty6.conf.distrib
-rw-r--r--  1 root root  316 2010-04-19 09:29 udev.conf
-rw-r--r--  1 root root  769 2010-04-19 09:29 udev-finish.conf
-rw-r--r--  1 root root  356 2010-04-19 09:29 udevmonitor.conf
-rw-r--r--  1 root root  318 2010-04-19 09:29 udevtrigger.conf
-rw-r--r--  1 root root  313 2010-04-02 00:13 upstart-udev-bridge.conf

```

note that the files ending in [FONT="Fixedsys"].distrib[/FONT] have been ```
dpkg-divert --rename /path/to/file
```.

any suggestions or ideas are very welcome. i am a bit puzzled as to why i cannot seem to log into the container through the console or through ssh.

all of my container configuration is following the resources listed at the top of this post. but if there is something specifically needed, please let me know.

EDIT:
I also wanted to mention that i receive the following message on my host console when the container is started
```

init: lxc pre-start process (2) terminated with status 32

```

i've added [FONT="Fixedsys"]/path/to/container/rootfs/etc/init/lxc.conf[/FONT] from [http://github.com/phbaer/lxc-tools/blob/master/lxc-ubuntu]("http://github.com/phbaer/lxc-tools/blob/master/lxc-ubuntu") 
```

# LXC &#8211; Fix init sequence to have LXC containers boot with upstart

# description &#8220;Fix LXC container - Lucid&#8221;

start on startup

task
pre-start script
mount -t proc proc /proc
mount -t devpts devpts /dev/pts
mount -t sysfs sys /sys
mount -t tmpfs varrun /var/run
mount -t tmpfs varlock /var/lock
mkdir -p /var/run/network
touch /var/run/utmp
chmod 664 /var/run/utmp
chown root.utmp /var/run/utmp
if [ "$(find /etc/network/ -name upstart -type f)" ]; then
chmod -x /etc/network/*/upstart || true
fi
end script

script
start networking
initctl emit filesystem --no-wait
initctl emit local-filesystems --no-wait
initctl emit virtual-filesystems --no-wait
init 2
end script

```

---

### Post by .primus on 2010-06-01
as an update to this issue, if i run
```

sudo lxc-start -n somename /bin/bash

```

i end up inside my container with a root shell.

then if i start sshd, i am able to ssh to the container.

the burning question is: why does this work?

---

### Post by .primus on 2010-06-01
so it appears that
```

/etc/init/mountall.conf

```

was the culprit. once i diverted this init config and then changed the ssh.conf to start on startup, it worked like a charm!

---

### Post by dreamysab on 2010-06-15
Hi .primus and everyone,
I am a relative newbie so forgive my lack of knowledge in advance. I have used this script to generate a container:

[COLOR="DimGray"]#!/bin/bash

#
# template script for generating ubuntu/lucid container for LXC
#
# This script is based on lxc-debian (Daniel Lezcano <daniel.lezc...@free.fr>)
#

# Copyright Â© 2010 Wilhelm Meier
# Author: Wilhelm Meier <wilhelm.me...@fh-kl.de>
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2, as
# published by the Free Software Foundation.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License along
# with this program; if not, write to the Free Software Foundation, Inc.,
# 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
#

configure_ubuntu()
{
    rootfs=$1
    hostname=$2

    # disable selinux in ubuntu
    mkdir -p $rootfs/selinux
    echo 0 > $rootfs/selinux/enforce

   # configure the network using the dhcp
    cat <<EOF > $rootfs/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
EOF

    # set the hostname
    cat <<EOF > $rootfs/etc/hostname
$hostname
EOF
    # set minimal hosts
    cat <<EOF > $rootfs/etc/hosts
127.0.0.1 localhost $hostname
EOF

    # provide the lxc service 
    cat <<EOF > $rootfs/etc/init/lxc.conf
# fake some events needed for correct startup other services

description     "Container Upstart"

start on startup

script
        rm -rf /var/run/*.pid
        rm -rf /var/run/network/*
        /sbin/initctl emit stopped JOB=udevtrigger --no-wait
        /sbin/initctl emit started JOB=udev --no-wait
end script
EOF

    cat <<EOF > $rootfs/lib/init/fstab
# /lib/init/fstab: lxc system fstab
none            /spu                      spufs           gid=spu,optional      0 0
none            /tmp                      none            defaults              0 0
#none            /var/run                  tmpfs           mode=0755,nosuid,showthrough      0 0
none            /var/lock                 tmpfs           nodev,noexec,nosuid,showthrough   0 0
none            /lib/init/rw              tmpfs           mode=0755,nosuid,optional         0 0
EOF

    # reconfigure some services
    if [ -z "$LANG" ]; then
        chroot $rootfs locale-gen en_US.UTF-8
        chroot $rootfs update-locale LANG=en_US.UTF-8
    else
        chroot $rootfs locale-gen $LANG
        chroot $rootfs update-locale LANG=$LANG
    fi

    # remove pointless services in a container
    chroot $rootfs /usr/sbin/update-rc.d -f ondemand remove

    chroot $rootfs /bin/bash -c 'cd /etc/init; for f in $(ls u*.conf); do mv $f $f.orig; done'
    chroot $rootfs /bin/bash -c 'cd /etc/init; for f in $(ls tty[2-9].conf); do mv $f $f.orig; done'
    chroot $rootfs /bin/bash -c 'cd /etc/init; for f in $(ls plymouth*.conf); do mv $f $f.orig; done'
    chroot $rootfs /bin/bash -c 'cd /etc/init; for f in $(ls hwclock*.conf); do mv $f $f.orig; done'
    chroot $rootfs /bin/bash -c 'cd /etc/init; for f in $(ls module*.conf); do mv $f $f.orig; done'

    echo "Please change root-password !"
    echo "root:root" | chroot $rootfs chpasswd    

    return 0
}

download_ubuntu()
{
    
packages=dialog,apt,apt-utils,resolvconf,iproute,inetutils-ping,vim,dhcp3-client,ssh,lsb-release

    cache=$1
    arch=$2

    # check the mini ubuntu was not already downloaded
    mkdir -p "$cache/partial-$arch"
    if [ $? -ne 0 ]; then
        echo "Failed to create '$cache/partial-$arch' directory"
        return 1
    fi

    # download a mini ubuntu into a cache
    echo "Downloading ubuntu minimal ..."
    debootstrap --verbose --variant=minbase --components=main,universe 
--arch=$arch --include=$packages lucid $cache/partial-$arch
    if [ $? -ne 0 ]; then
        echo "Failed to download the rootfs, aborting."
        return 1
    fi

    mv "$1/partial-$arch" "$1/rootfs-$arch"
    echo "Download complete."

    return 0
}

copy_ubuntu()
{
    cache=$1
    arch=$2
    rootfs=$3

    # make a local copy of the miniubuntu
    echo -n "Copying rootfs to $rootfs ..."
    cp -a $cache/rootfs-$arch $rootfs || return 1
    return 0
}

install_ubuntu()
{
    cache="/var/cache/lxc/ubuntu"
    rootfs=$1
    mkdir -p /var/lock/subsys/
    (
        flock -n -x 200
        if [ $? -ne 0 ]; then
            echo "Cache repository is busy."
            return 1
        fi

        arch=$(arch)
        if [ "$arch" == "x86_64" ]; then
            arch=amd64
        fi

        if [ "$arch" == "i686" ]; then
            arch=i386
        fi

        echo "Checking cache download in $cache/rootfs-$arch ... "
        if [ ! -e "$cache/rootfs-$arch" ]; then
            download_ubuntu $cache $arch
            if [ $? -ne 0 ]; then
                echo "Failed to download 'ubuntu base'"
                return 1
            fi
        fi

        echo "Copy $cache/rootfs-$arch to $rootfs ... "
        copy_ubuntu $cache $arch $rootfs
        if [ $? -ne 0 ]; then
            echo "Failed to copy rootfs"
            return 1
        fi

        return 0

        ) 200>/var/lock/subsys/lxc

    return $?
}

copy_configuration()
{
    path=$1
    rootfs=$2
    name=$3

    cat <<EOF >> $path/config
lxc.utsname = $name

lxc.tty = 4
lxc.pts = 1024
lxc.rootfs = $rootfs
lxc.mount  = $path/fstab

lxc.console = /dev/console

lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 4:0 rwm
lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm
EOF

    cat <<EOF > $path/fstab
proc            $rootfs/proc         proc    nodev,noexec,nosuid 0 0
devpts          $rootfs/dev/pts      devpts defaults 0 0
sysfs           $rootfs/sys          sysfs defaults  0 0
EOF

    if [ $? -ne 0 ]; then
        echo "Failed to add configuration"
        return 1
    fi

    return 0
}

clean()
{
    cache="/var/cache/lxc/ubuntu"

    if [ ! -e $cache ]; then
        exit 0
    fi

    # lock, so we won't purge while someone is creating a repository
    (
        flock -n -x 200 
        if [ $? != 0 ]; then
            echo "Cache repository is busy."
            exit 1
        fi

        echo -n "Purging the download cache..."
        rm --preserve-root --one-file-system -rf $cache && echo "Done." || exit 
1
        exit 0

    ) 200>/var/lock/subsys/lxc
}

usage()
{
    cat <<EOF
$1 -h|--help -p|--path=<path> --clean
EOF
    return 0
}

options=$(getopt -o hp:n:c -l help,path:,name:,clean -- "$@")
if [ $? -ne 0 ]; then
        usage $(basename $0)
        exit 1
fi
eval set -- "$options"

while true
do
    case "$1" in
        -h|--help)      usage $0 && exit 0;;
        -p|--path)      path=$2; shift 2;;
        -n|--name)      name=$2; shift 2;;
        -c|--clean)     clean=$2; shift 2;;
        --)             shift 1; break ;;
        *)              break ;;
    esac
done

if [ ! -z "$clean" -a -z "$path" ]; then
    clean || exit 1
    exit 0
fi

type debootstrap
if [ $? -ne 0 ]; then
    echo "'debootstrap' command is missing"
    exit 1
fi

if [ -z "$path" ]; then
    echo "'path' parameter is required"
    exit 1
fi

if [ "$(id -u)" != "0" ]; then
    echo "This script should be run as 'root'"
    exit 1
fi 

rootfs=$path/rootfs

install_ubuntu $rootfs
if [ $? -ne 0 ]; then
    echo "failed to install ubuntu"
    exit 1
fi

configure_ubuntu $rootfs $name
if [ $? -ne 0 ]; then
    echo "failed to configure ubuntu for a container"
    exit 1
fi

copy_configuration $path $rootfs $name
if [ $? -ne 0 ]; then
    echo "failed write configuration file"
    exit 1
fi

if [ ! -z $clean ]; then
    clean || exit 1
    exit 0
fi[/COLOR]

[COLOR="Sienna"]Source: [http://www.mail-archive.com/lxc-devel@lists.sourceforge.net/msg00273.html](http://www.mail-archive.com/lxc-devel@lists.sourceforge.net/msg00273.html)[/COLOR]

What I have done so far:
put the above script in /usr/local/bin/lxc-ubuntu
mkdir -p /var/lib/lxc/lx1
lxc-ubuntu -p /var/lib/lxc/lx1

Code:
[COLOR="DimGray"]debootstrap is /usr/sbin/debootstrap
Checking cache download in /var/cache/lxc/ubuntu/rootfs-amd64 ...
Copy /var/cache/lxc/ubuntu/rootfs-amd64 to /var/lib/lxc/lx1/rootfs ...
Copying rootfs to /var/lib/lxc/lx1/rootfs ...Generating locales...
  en_AU.UTF-8... done
Generation complete.
 Removing any system startup links for /etc/init.d/ondemand ...
   /etc/rc2.d/S99ondemand
   /etc/rc3.d/S99ondemand
   /etc/rc4.d/S99ondemand
   /etc/rc5.d/S99ondemand
Please change root-password ![/COLOR]


This downloads a rootfs-amd64 into /var/cache/lxc/ubuntu/ and generates a rootfs, config and fstab located in /var/lib/lxc/lx1
(I changed my own locales in the script)

Noteworthy I think is that making a directory gives the container it's own directory in /cgroups on the host when I "execute" a process in the container.

/var/lib/lxc/lx1/config looks like this:
[COLOR="DimGray"]lxc.utsname =
lxc.tty = 4
lxc.pts = 1024
lxc.rootfs = /var/lib/lxc/lx1/rootfs
lxc.mount  = /var/lib/lxc/lx1/fstab
lxc.console = /dev/console
lxc.cgroup.devices.deny = a
# /dev/null and zero
lxc.cgroup.devices.allow = c 1:3 rwm
lxc.cgroup.devices.allow = c 1:5 rwm
# consoles
lxc.cgroup.devices.allow = c 5:1 rwm
lxc.cgroup.devices.allow = c 5:0 rwm
lxc.cgroup.devices.allow = c 4:0 rwm
lxc.cgroup.devices.allow = c 4:1 rwm
# /dev/{,u}random
lxc.cgroup.devices.allow = c 1:9 rwm
lxc.cgroup.devices.allow = c 1:8 rwm
lxc.cgroup.devices.allow = c 136:* rwm
lxc.cgroup.devices.allow = c 5:2 rwm
# rtc
lxc.cgroup.devices.allow = c 254:0 rwm[/COLOR]

/var/lib/lxc/lx1/fstab looks like this:
[COLOR="DimGray"]proc            /var/lib/lxc/lx1/rootfs/proc         proc    nodev,noexec,nosuid 0 0
devpts          /var/lib/lxc/lx1/rootfs/dev/pts      devpts defaults 0 0
sysfs           /var/lib/lxc/lx1/rootfs/sys          sysfs defaults  0 0[/COLOR]

I have tried a few different configurations of the config with various errors when I attempt to get the container started.

This is where I am at:

I have chrooted into the rootfs and chaged the sources.list (grabbed from the host) installed aptitude, vim-nox and a few others.

[COLOR="DimGray"]root@host:~# lxc-start -n lx1
lxc-start: unknow key lxc.console
lxc-start: failed to process 'lxc.console'
lxc-start: failed to read configuration file[/COLOR]

If I edit the config to provide networking I get this:
[COLOR="DimGray"]root@host:~# lxc-start -n lx1
lxc-start: network is not created for 'lxc.network.ipv4' = '192.168.XXX.XXX/24' option
lxc-start: failed to process 'lxc.network.ipv4'
lxc-start: failed to read configuration file
[/COLOR]
In any event I can't get up and running so ...

My questions:
1. How do I add the diversion of mountall that you mention above?
2. How do I get ssh to start on startup?
4. Since I am working with a headless server what can I do to login to the container as root from a local machine. I know how to add users with adduser but the root user is already added here.
5. Anything I need to do to my configuration or gaps in my understanding here.

This is contents of /etc/init in the rootfs that the script generates:

[COLOR="DimGray"]console-setup.conf       
hwclock-save.conf.orig       
mountall-reboot.conf  
networking.conf                  
plymouth-splash.conf.orig  
rc-sysinit.conf 
tty1.conf
tty2.conf.orig
tty3.conf.orig
tty4.conf.orig
tty5.conf.orig   
tty6.conf.orig
udev-finish.conf.orig
control-alt-delete.conf  
lxc.conf                     
mountall-shell.conf   
network-interface.conf           
plymouth-stop.conf.orig    
rsyslog.conf     
udevmonitor.conf.orig
dmesg.conf               
module-init-tools.conf.orig  
mounted-dev.conf      
network-interface-security.conf  
procps.conf                
ssh.conf          
udevtrigger.conf.orig
hostname.conf            
mountall.conf                
mounted-tmp.conf      
plymouth.conf.orig               
rc.conf 
upstart-udev-bridge.conf.orig
hwclock.conf.orig        
mountall-net.conf            
mounted-varrun.conf   
plymouth-log.conf.orig           
rcS.conf                     
udev.conf.orig[/COLOR]

Thanks in advance.

---

