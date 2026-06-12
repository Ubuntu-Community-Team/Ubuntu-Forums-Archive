---
title: "Boot failure after running update-initramfs"
date: 2011-02-15
forum: Server Platforms
---

### Post by PapaNerd on 2011-02-15
Here is an interesting problem.  Two systems, both running 10.04.2 LTS, fail to boot (hang in the "ubuntu" screen) after an update via apt-get.  

The following files worked fine:
initrd.img-2.6.32-21-generic
initrd.img-2.6.32-26-generic
initrd.img-2.6.32-27-generic

However, after manually running "update-initramfs -u", the initrd.img file size goes from 8.3MB to 14.1MB.  Restoring the system requires booting from a CD, mounting the hard disk file system, and copying back in the old version of initrd.img, but it would be really nice to be able to update these systems.

Both systems are running encrypted file systems, one with one encrypted partition and the other with two encryptped partitions, which were installed by geneally following the out-of-date documentation on the [https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid](https://help.ubuntu.com/community/EncryptedFilesystemOnIntrepid) page, plus working around these missing files in the sample /etc/initramfs-tools/scripts/local-top/cryptoroot script:
/etc/console-setup/boottime.kmap.gz
/sbin/usplash
/sbin/cryptsetup
/bin/chvt

That script now looks like this:```
PREREQ="udev"

prereqs()
{
	echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
	prereqs
	exit 0
	;;
esac

if [ -f /etc/console-setup/boottime.kmap.gz ]
  then /bin/loadkeys -q /etc/console-setup/boottime.kmap.gz
  fi
modprobe -qb dm_crypt
modprobe -qb sha256_generic

# The following command will ensure that the kernel is aware of
# the partition before we attempt to open it with cryptsetup.
if [ -x /sbin/udevadm ]
  then
    /sbin/udevadm settle
    sleep 5
  fi

if [ -x /bin/chvt ]
  then
    if grep -q splash /proc/cmdline
      then
	/bin/chvt 1
	sleep 2
      fi
  fi

/sbin/cryptsetup luksOpen /dev/sdb1 cryptodisk
sleep 2

if [ -x /sbin/usplash ]
  then
    if grep -q splash /proc/cmdline
      then
	/sbin/usplash -c
	sleep 2
      fi
  fi

# ----- end of file ----- #
```

Is something in the setup for the encrypted file systems causing initrd.img to be re-built improperly?

---

