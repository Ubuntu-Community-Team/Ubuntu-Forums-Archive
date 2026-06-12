---
title: "Can't seem to use VMBuilder on Ubuntu Server?"
date: 2015-01-09
forum: Server Platforms
---

### Post by josh111 on 2015-01-09
Hi! I seem to have run into a problem with VMBuilder on Ubuntu Server in that it won't let me get past the ```
vmbuilder kvm ubuntu
``` command to actually use the virtual machine. The process stalls at ```
 : Calling hook: bootstrap
``` and never goes any farther.  I am quite new to Ubuntu server but I am catching on pretty quickly. I was wondering what I was doing wrong or is there something I can do to fix this issue.  Any help will be greatly appreciated! Thanks a bunch in advance!

---

### Post by nerdtron on 2015-01-10
HHmmm running a KVM server?
I haven't used kvm builder so no idea on that one. But I manage Ubuntu VM Server using the Vitrual Machine Manager from my ubuntu desktop.

It's basically like virtual box GUI, although it's on my desktop. And the VMs are running on the server.
[http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/](http://www.howtogeek.com/117635/how-to-install-kvm-and-create-virtual-machines-on-ubuntu/)

---

### Post by MAFoElffen on 2015-01-10
```

mafoelffen@snoopy:~$ apt-cache policy python-vm-builder
python-vm-builder:
  Installed: 0.12.4+bzr489-0ubuntu2
  Candidate: 0.12.4+bzr489-0ubuntu2
  Version table:
 *** 0.12.4+bzr489-0ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```\ So I use it... but not how you are trying to use it. This is how I understand it.

I use pyhton-vm-builder. There is also ubuntu-vm-builder... They are both scripts that automate / simplify building libvert guests. The scripts help fill in the needed options to fill in the blanks needed to create the guest.

```

mafoelffen@snoopy:~$ vmbuilder kvm ubuntu --help
2015-01-09 21:24:24,863 INFO    : logging to file: /tmp/tmps7k5Xj
Usage: vmbuilder hypervisor distro [options]

Options:
  -h, --help            show this help message and exit
  --version             Show version information

  Build options:
    --debug             Show debug information
    -v, --verbose       Show progress information
    -q, --quiet         Silent operation
    -o, --overwrite     Remove destination directory before starting build
    -c CONFIG, --config=CONFIG
                        Configuration file
    --templates=DIR     Prepend DIR to template search path.
    -d DESTDIR, --destdir=DESTDIR
                        Destination directory
    --only-chroot       Only build the chroot. Don't install it on disk images
                        or anything.
    --chroot-dir=CHROOT_DIR
                        Build the chroot in directory.
    --existing-chroot=EXISTING_CHROOT
                        Use existing chroot.
    -t DIR, --tmp=DIR   Use TMP as temporary working space for image
                        generation. Defaults to $TMPDIR if it is defined or
                        /tmp otherwise. [default: /tmp]
    --tmpfs=SIZE        Use a tmpfs as the working directory, specifying its
                        size or "-" to use tmpfs default (suid,dev,size=1G).

  Disk:
    --rootsize=SIZE     Size (in MB) of the root filesystem [default: 4096]
    --optsize=SIZE      Size (in MB) of the /opt filesystem. If not set, no
                        /opt filesystem will be added.
    --swapsize=SIZE     Size (in MB) of the swap partition [default: 1024]
    --raw=PATH          Specify a file (or block device) to use as first disk
                        image (can be specified multiple times).
    --part=PATH         Specify a partition table in PATH. Each line of
                        partfile should specify (root first):      mountpoint
                        size  one per line, separated by space, where size is
                        in megabytes. You can have up to 4 virtual disks, a
                        new disk starts on a line containing only '---'. ie:
                        root 2000      /boot 512      swap 1000      ---
                        /var 8000      /var/log 2000

  Settings for the initial user:
    --user=USER         Username of initial user [default: ubuntu]
    --name=NAME         Full name of initial user [default: Ubuntu]
    --pass=PASS         Password of initial user [default: ubuntu]
    --rootpass=ROOTPASS
                        Initial root password (WARNING: this has strong
                        security implications).
    --uid=UID           Initial UID value.
    --gid=GID           Initial GID value.
    --lock-user         Lock the initial user [default: none]

  Other options:
    --ssh-key=PATH      Add PATH to root's ~/.ssh/authorized_keys (WARNING:
                        this has strong security implications).
    --ssh-user-key=SSH_USER_KEY
                        Add PATH to the user's ~/.ssh/authorized_keys.
    --manifest=PATH     If passed, a manifest will be written to PATH

  Package options:
    --addpkg=PKG        Install PKG into the guest (can be specified multiple
                        times).
    --removepkg=PKG     Remove PKG from the guest (can be specified multiple
                        times)
    --seedfile=SEEDFILE
                        Seed the debconf database with the contents of this
                        seed file before installing packages

  Network:
    --domain=DOMAIN     Set DOMAIN as the domain name of the guest [default:
                        ferreiraent.com].

  Installation options:
    --suite=SUITE       Suite to install. Valid options: dapper gutsy hardy
                        intrepid jaunty karmic lucid maverick natty oneiric
                        precise quantal raring saucy trusty [default: lucid]
    --flavour=FLAVOUR, --kernel-flavour=FLAVOUR
                        Kernel flavour to use. Default and valid options
                        depend on architecture and suite
    --variant=VARIANT   Passed to debootstrap --variant flag; use minbase,
                        buildd, or fakechroot.
    --debootstrap-tarball=FILE
                        Passed to debootstrap --unpack-tarball flag.
    --iso=PATH          Use an iso image as the source for installation of
                        file. Full path to the iso must be provided. If
                        --mirror is also provided, it will be used in the
                        final sources.list of the vm.  This requires suite and
                        kernel parameter to match what is available on the
                        iso, obviously.
    --mirror=URL        Use Ubuntu mirror at URL instead of the default, which
                        is http://archive.ubuntu.com/ubuntu for official
                        arches and http://ports.ubuntu.com/ubuntu-ports
                        otherwise
    --proxy=URL         Use proxy at URL for cached packages
    --install-mirror=URL
                        Use Ubuntu mirror at URL for the installation only.
                        Apt's sources.list will still use default or URL set
                        by --mirror
    --security-mirror=URL
                        Use Ubuntu security mirror at URL instead of the
                        default, which is http://security.ubuntu.com/ubuntu
                        for official arches and http://ports.ubuntu.com
                        /ubuntu-ports otherwise.
    --install-security-mirror=URL
                        Use the security mirror at URL for installation only.
                        Apt's sources.list will still use default or URL set
                        by --security-mirror
    --components=COMPS  A comma seperated list of distro components to include
                        (e.g. main,universe).
    --ppa=PPA           Add ppa belonging to PPA to the vm's sources.list.
    --lang=LANG         Set the locale to LANG [default: en_US.UTF-8]
    --timezone=TZ       Set the timezone to TZ in the vm. [default: UTC]

  Post install actions:
    --copy=FILE         Read 'source dest' lines from FILE, copying source
                        files from host to dest in the guest's file system.
    --execscript=SCRIPT, --exec=SCRIPT
                        Run SCRIPT after distro installation finishes. Script
                        will be called with the guest's chroot as first
                        argument, so you can use 'chroot $1 <cmd>' to run code
                        in the virtual machine.

  General OS options:
    -a ARCH, --arch=ARCH
                        Specify the target architecture.  Valid options: amd64
                        i386 lpia (defaults to host arch)
    --hostname=HOSTNAME
                        Set NAME as the hostname of the guest. Default:
                        ubuntu. Also uses this name as the VM name.

  Scripts:
    --firstboot=PATH    Specify a script that will be copied into the guest
                        and executed the first time the machine boots.  This
                        script must not be interactive.
    --firstlogin=PATH   Specify a script that will be copied into the guest
                        and will be executed the first time the user logs in.
                        This script can be interactive.

  libvirt integration:
    --libvirt=URI       Add VM to given URI
    --bridge=BRIDGE     Set up bridged network connected to BRIDGE.
    --network=NETWORK   Set up a network connection to virtual network
                        NETWORK.

  Network:
    --ip=ADDRESS        IP address in dotted form [default: dhcp].
    --mac=MAC           MAC address of the guest [default: random].
    --mask=VALUE        IP mask in dotted form [default: based on ip setting].
                        Ignored if ip is not specified.
    --net=ADDRESS       IP net address in dotted form [default: based on ip
                        setting]. Ignored if ip is not specified.
    --bcast=VALUE       IP broadcast in dotted form [default: based on ip
                        setting]. Ignored if ip is not specified.
    --gw=ADDRESS        Gateway (router) address in dotted form [default:
                        based on ip setting (first valid address in the
                        network)]. Ignored if ip is not specified.
    --dns=ADDRESS       DNS address in dotted form [default: based on ip
                        setting (first valid address in the network)] Ignored
                        if ip is not specified.

  VM settings:
    -m MEM, --mem=MEM   Assign MEM megabytes of memory to the guest vm.
                        [default: 128]
    --cpus=CPUS         Assign NUM cpus to the guest vm. [default: 1]

```
for vmbuilder, the "options" would be filled "at" to run time externally or you need to supply the options previously... Meaning at the CLI, when you enter the command, options are not optional. You either point to a script file or you add those options to your command. (You didn't, so it failed)

For example:
```

sudo vmbuilder kvm ubuntu -d myvmguest --arch=amd64 --hostname=myvmguest --suite=trusty --libvert=qemu:///system --addpackage=openssh-server --ssh-user-key=~/.ssh/id_rsa.pub

```
What is usual is to put in in an image file, but for an example here (to type leass as an example) I instead had it create a directory. For a disk image, you have to give it the particular parmeters that define that. (sizes, type, partitions, etc.)

Of course, that is just my understanding of that... I might be be wrong. I didn't see what VMBuilder added over just using virt-install. The scripts above are easier to use than either of those..

---

