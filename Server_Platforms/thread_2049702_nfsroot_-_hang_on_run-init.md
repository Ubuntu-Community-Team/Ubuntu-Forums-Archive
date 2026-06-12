---
title: "nfsroot - hang on run-init"
date: 2012-08-29
forum: Server Platforms
---

### Post by lievendp on 2012-08-29
Good morning,

My pxe-booted, nfs-rooted precise 12.04 system will not boot. After the pxe boot and nfs mount, it runs through init (/usr/share/initramfs-tools/init script) and does not respond on:

log_begin_msg "chain real fs"
echo "rootmnt: ${rootmnt}"
echo "init: ${init}"
exec run-init ${rootmnt} ${init} "$@" ${recovery:+--startup-event=recovery} <${rootmnt}/dev/console >${rootmnt}/dev/console 2>&1
log_end_msg
panic "Could not execute run-init."

What is the result for me: I see the "chain real fs" debug msg that I put in the init script but not the "done" from the log_end_msg and thus no panic either, just endless wait. 

I can however positively confirm that the nfs root gets mounted in init because the var/log files are partly populated on the nfs mount and there are no issues mentioned there.

There is even an mtab file created:

192.168.16.10:/vm/chroot2 / nfs rw,vers=4,addr=192.168.16.10,clientaddr=192.168.16.134 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /tmp tmpfs rw 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /var/tmp tmpfs rw 0 0
rpc_pipefs /run/rpc_pipefs rpc_pipefs rw 0 0

I tried two different nfs-servers but the result is the same.

What I find strange here is that the nfs in mtab seems mounted with version 4. strange because I give v3 option in my pxelinux.cfg/default file:

DISPLAY boot.txt
DEFAULT 1
LABEL 1
kernel ubuntu/precise/amd64/vmlinuz-3.2.0-29-generic
append initrd=ubuntu/precise/amd64/initrd.img-3.2.0-29-generic root=/dev/nfs nfsroot=192.168.16.10:/vm/chroot2,v3,nolock ip=dhcp rw --
PROMPT 1
TIMEOUT 0

in /etc/fstab of the nfsroot, it does not matter if I put anything to mount the / on nfs, the result in mtab is always the same.

On the net and bug-reports for ubuntu, I found something abt nfsroots not getting moved to the real mountpoint but I could not solve my issue with those infos, most are for older versions of mountall.

the kernel I use is the standard linux-image-3.2.0-29-generic from ubuntu.

Are there some kernel configs that make nfs3 work as nfs4 or something like that which trouble this setup?

Anybody having a similar issue or setup that can help me solve this?

thanks.


small edit: I cannot find a function in the initramfs-folders or shell builtin called "run-init" which is executed by the init: "exec run-init ..."
Where can I find this? Is it something script which I can read or a binary file?

Can things work if I compile a new kernel without an initrd? (Like I do for my gentoo) I do not prefer this because it would deny me the easy apt-get kernel-image for use with this system and probably other issues if I forget things in the config.

---

### Post by lievendp on 2012-08-29
nfsmount command.
So looking at the nfsmount part of this problem, I found that the nfs mount command from initramfs is not the one from busyboxy, it is an elf executable to be found at "/usr/lib/klibc/bin/nfsmount <srvrip>:/mnt/usb/pxedev/pxedev /mnt/pxedev/ -o nolock"

this mount command actually works from my laptop xubuntu 12.04 and although the mount does not showup with "mount", it is in /proc/mounts:
...
<srvrip>:/mnt/usb/pxedev/pxedev/ /mnt/pxedev nfs rw,relatime,vers=3,rsize=524288,wsize=524288,namlen=255,hard,nolock,proto=tcp,port=65535,timeo=7,retrans=3,sec=sys,local_lock=all,addr=<srvrip> 0 0

but the nfsvers option seems to be ignored:

root@Aegir:/tmp/bin# /usr/lib/klibc/bin/nfsmount <srvrip>:/mnt/usb/pxedev/pxedev /mnt/pxedev/ -o nfsvers=4,nolock
root@Aegir:/tmp/bin# cat /proc/mounts | tail -1
<srvrip>:/mnt/usb/pxedev/pxedev/ /mnt/pxedev nfs rw,relatime,**_vers=3_**,rsize=524288,wsize=524288,namlen=255,hard,nolock,proto=tcp,port=65535,timeo=7,retrans=3,sec=sys,local_lock=all,addr=<srvrip> 0 0


Why does it ignore my version of nfs here and gets version 3?
and more interesting to me is why does it ignore my initrd parameter for version 3 and sets the version to 4 if I do nfsroot boot with pxe?? wtf?

I don't understand. :-)

---

