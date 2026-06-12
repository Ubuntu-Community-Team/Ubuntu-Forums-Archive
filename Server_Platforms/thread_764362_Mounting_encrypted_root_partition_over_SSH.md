---
title: "Mounting encrypted root partition over SSH"
date: 2008-04-23
forum: Server Platforms
---

### Post by synapseattack on 2008-04-23
Hi All,

I installed Ubuntu 7.10 Server on a Dell Poweredge 1850 using the Guided Partitioning installed with encryption through LVM/LUKS.

I am trying to mount the root partition remotely using SSH following the instructions I found at [Debian-Administration.org post 579]("http://www.debian-administration.org/articles/579") and also the comment titled "[WORKING] Ubuntu 7.10 AMD64" (NOTE: Changes to the script found in the comment are a must cause of errors in the posting, my updated script is below). 

```
#!/bin/bash

# We add dropbear to the initrd&nbs p;to be able do mount crypto partit ions from remote


PREREQ=""
prereqs()
{
     echo "$PREREQ"
}

case $1 in
prereqs)
     prereqs
     exit 0
     ;;
esac

# Begin real processing below this line

# load the prepared functions of de bians initramfs enviroment
source /usr/share/initramfs-tools/hook-functions


# build the directorys
DIRS='/usr/bin/ /usr/sbin/ /proc/ /root/ /var / /var/run/ /var/run/'

for now in $DIRS ; do
    if  [ ! -e  ${DESTDIR}$now ] 
    then
       mkdir -p ${DESTDIR}$now
    fi
done

# copy the main ssh-daemen including libarys
copy_exec /usr/sbin/dropbear /usr/sbin/
copy_exec /usr/bin/passwd /usr/bin/
copy_exec /bin/login /bin/
copy_exec /usr/bin/killall /usr/bin/
copy_exec /sbin/route /sbin/
copy_exec /usr/bin/awk /usr/bin/


# some libarys not autoincludet by  copy_exec
copy_exec /lib/libnss_compat.so.2 /lib/
copy_exec /usr/lib/libz.so.1 /usr/lib/
copy_exec /etc/ld.so.cache /etc/
copy_exec /lib/libutil.so.1 /lib/


# we copy config and key files
cp -pr /etc/dropbear ${DESTDIR}/etc/
cp -pr /etc/passwd ${DESTDIR}/etc/
cp -pr /etc/shadow ${DESTDIR}/etc/
cp -pr /etc/group ${DESTDIR}/etc/
cp -pr /root/.ssh ${DESTDIR}/root/
cp -pr /etc/nsswitch.conf  ${DESTDIR}/etc/
cp -pr /etc/localtime  ${DESTDIR}/etc/

# we don't have bash in our initrd
# also we only add the root account
cat  /etc/passwd | grep root | sed s/\\/bash/\\/sh/  > ${DESTDIR}/etc/passwd
cat  /etc/shadow | grep root | sed s/\\/bash/\\/sh/  > ${DESTDIR}/etc/shadow
cat  /etc/group | grep root | sed s/\\/bash/\\/sh/  > ${DESTDIR}/etc/group


# the blocker script to request inp ut action befor running cryptroot
# this let us run cryptroot on local terminal or inside ssh
# dirty but effektive
cat >${DESTDIR}/scripts/local-top/cryptroot_block << 'EOF'
#!/bin/sh
PREREQ="network_ssh"
prereqs()
{
     echo "$PREREQ"
}

case $1 in
prereqs)
     prereqs
     exit 0
     ;;
esac

# Begin real processing below this line

echo Type "ok" and press enter to put in passphrase:

INPUT='wait'

while  [ $INPUT != 'ok' ]   ; do
 read INPUT
done

EOF
chmod 700 ${DESTDIR}/scripts/local-top/cryptroot_block


cat >${DESTDIR}/scripts/local-top/network_ssh << 'EOF'
#!/bin/sh

# we start the network and ssh-server


PREREQ=""
prereqs()
{
     echo "$PREREQ"
}

case $1 in
prereqs)
     prereqs
     exit 0
     ;;
esac

# Begin real processing below this  line


# build up helpful enviroment
 [ -d /dev ] || mkdir -m 0755 /dev
 [ -d /root ] || mkdir --mode=0700 /root
 [ -d /sys ] || mkdir /sys
 [ -d /proc ] || mkdir /proc
 [ -d /tmp ] || mkdir /tmp
mkdir -p /var/lock
mount -t sysfs -o nodev,noexec,nosuid none /sys
mount -t proc -o nodev,noexec,nosuid none /proc

mkdir /dev/pts
mount -t devpts -o gid=5,mode=620 /dev/pts /dev/pts

# the Network setup edit ipaddres and gateway to your needs
ifconfig eth0 172.16.0.10 netmask 255.255.255.0
/sbin/route add default gw 172.16.0.1
# If you like to use dhcp make sure you include dhclient or pump  in
# /etc/initramfs-tools/hooks/dropbear via
#     copy_exec /sbin/dhclient

# for debugging ssh-server you may  run it in forgound
#      /usr/sbin/dropbear -E -F
# for more debugging you may run it with strace
# therefore you have to include strace and nc at top of
# /etc/initramfs-tools/hooks/dropbear via
#     copy_exec /usr/bin/strace
#     copy_exec /usr/bin/nc
# then start nc on another host and run
#     /usr/sbin/dropbear -E -F   2>&1 | /bin/nc -vv <ip of other host> <nc port of o ther host>
#     e.g.:
#     /usr/sbin/dropbear -E -F   2>&1 | /bin/nc -vv 192.168.1.2 8888
/usr/sbin/dropbear  -b /etc/dropbear/banner
EOF
chmod 700 ${DESTDIR}/scripts/local-top/network_ssh


cat >${DESTDIR}/etc/dropbear/banner << 'EOF'

     To unlock root-partition run
        unlock


EOF


# script to unlock luks via ssh
# dirty but effektive
cat >${DESTDIR}/usr/bin/unlock << 'EOF'
#!/bin/sh

/bin/sh /scripts/local-top/cryptroot && mv /scripts/local-top/cryptroot /root && kill `ps | grep cryptroot_block|grep -v grep |/usr/bin/awk '{ print $1 }'`

EOF
chmod 700 ${DESTDIR}/usr/bin/unlock

# make shure we exit dropbear at&nb sp;the end of the startup process
cat >${DESTDIR}/scripts/local-bottom/rm_dropbear << 'EOF'
#!/bin/sh
PREREQ=""
prereqs()
{
     echo ""
}

case $1 in
prereqs)
     prereqs
     exit 0
     ;;
esac

# Begin real processing below this  line
# we kill dropbear ssh-server

/usr/bin/killall dropbear

EOF
chmod 700 ${DESTDIR}/scripts/local-bottom/rm_dropbear
```

With this I am getting the following errors:
> mount: Mounting none on /sys failed: Device or resource busy
mount: Mounting none on /proc failed: Device or resource busy
SIOCSIFADDR: No such device
SIOCSIFNETMASK: No such device
SIOCSADDRT: No such process
Type ok and press enter to put in passphrase: 

I can not ping the static IP I set in the dropbear or SSH to it. I'm guessing that SIOCSIFADDR is the network device and because it is not seen I am not able to set the IP.

Any help at all would be awesome. Thanks in advance!

~SA

---

