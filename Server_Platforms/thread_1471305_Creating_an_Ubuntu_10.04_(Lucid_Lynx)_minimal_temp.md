---
title: "Creating an Ubuntu 10.04 (Lucid Lynx) minimal template for OpenVZ"
date: 2010-05-03
forum: Server Platforms
---

### Post by narcisgarcia on 2010-05-03
This is the procedure I've followed to have an Ubuntu 10.04 (32-bits) container in a working Ubuntu 8.04 (32-bits) physical server, but I still have some problems describen at bottom.

Guides and corrections taken from [Ubuntu community help](https://help.ubuntu.com/community/OpenVZ#Create%20Template), [OpenVZ forums](http://forum.openvz.org/index.php?t=msg&goto=34305), [Shadows of epiphany weblog](http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/)

I've installed Ubuntu 10.04 (32-bits) in another computer, and then installed and used debootstrap to have a basic system in a folder:
```

cd /tmp
sudo apt-get install debootstrap
mkdir lucid-chroot
sudo debootstrap --variant=minbase lucid lucid-chroot

```

To move this new installation to the server, I've packaged it and copied the package to server's /var/tmp directory:
```

cd lucid-chroot
sudo tar czf /var/tmp/debootstrap-ubuntu-10.04_minbase.tar.gz .
cd ..

```

In the OpenVZ server (physical with Ubuntu 8.04) unpack the installation for a new container:
```

sudo mkdir -p /vz/private/777
cd /vz/private/777
sudo tar xf /var/tmp/debootstrap-ubuntu-10.04_minbase.tar.gz

```

Create a new /vz/private/777/etc/apt/sources.list file for supported and secure repositories:
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ lucid main
deb-src http://archive.ubuntu.com/ubuntu/ lucid main
#deb http://archive.ubuntu.com/ubuntu/ lucid restricted
#deb-src http://archive.ubuntu.com/ubuntu/ lucid restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main
deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates main
#deb http://archive.ubuntu.com/ubuntu/ lucid-updates restricted
#deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
#deb http://archive.ubuntu.com/ubuntu/ lucid universe
#deb-src http://archive.ubuntu.com/ubuntu/ lucid universe
#deb http://archive.ubuntu.com/ubuntu/ lucid-updates universe
#deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb http://archive.ubuntu.com/ubuntu/ lucid multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ lucid multiverse
#deb http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main
deb-src http://security.ubuntu.com/ubuntu lucid-security main
#deb http://security.ubuntu.com/ubuntu lucid-security restricted
#deb-src http://security.ubuntu.com/ubuntu lucid-security restricted
#deb http://security.ubuntu.com/ubuntu lucid-security universe
#deb-src http://security.ubuntu.com/ubuntu lucid-security universe
#deb http://security.ubuntu.com/ubuntu lucid-security multiverse
#deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

```

Save the following script as /vz/private/777/etc/init/openvz.conf
```

# OpenVZ - Fix init sequence to have OpenVZ working with upstart

description "Fix OpenVZ"

start on startup

task
pre-start script
mount -t devpts devpts /dev/pts
mount -t tmpfs varrun /var/run
mount -t tmpfs varlock /var/lock
mkdir -p /var/run/network
cat /proc/mounts > /etc/mtab
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

All files need to be owned by root:
```

sudo chown -R root:root /vz/private/777

```

Now remove a broken and unneeded scripts.
```

sudo rm /vz/private/777/etc/init/mountall-shell.conf
sudo rm -f /vz/private/777/etc/init/tty*.conf
sudo rm -f /vz/private/777/etc/init/plymouth*

```

Setting initial container configuration and template name:
```

sudo vzctl set 777 --applyconfig vps.basic --save
echo "OSTEMPLATE=ubuntu-10.04" | sudo tee -a /etc/vz/conf/777.conf >/dev/null

```

Temporary network settings (IP, DNS):
```

sudo vzctl set 777 --ipadd x.x.x.x --save
sudo vzctl set 777 --nameserver x.x.x.x --save

```

Start the container and patch some devices information, remove udev start entries, and restart container:
```

sudo vzctl start 777
sudo vzctl exec 777 "cd /dev; /sbin/MAKEDEV pty"
sudo vzctl exec 777 "cd /dev; /sbin/MAKEDEV tty"
sudo vzctl exec 777 "update-rc.d -f udev remove"
sudo vzctl stop 777
sudo vzctl start 777

```

Enter to container:
```

sudo vzctl enter 777

```

Disable physical terminals (ignore "unknown job")
```

initctl stop tty1
initctl stop tty2
initctl stop tty3
initctl stop tty4
initctl stop tty5
initctl stop tty6
rm -f /etc/event.d/tty*
rm -f /etc/init/tty*

```

Update and install some additional packages (quota is needed, vim/nano are optional).
```

apt-get install --force-yes -y gpgv
apt-get update; apt-get upgrade
apt-get install -y adduser apt-utils iproute netbase nano openssh-blacklist openssh-blacklist-extra openssh-server quota ping sudo vim dialog

```

Secure /root directory, and disable root login:
```

chmod 700 /root
usermod -p '!' root

```

Fix SSH:
```

sed -i -e 's_oom never_#oom never_g' /etc/init/ssh.conf

```

Clean cached and orphan packages
```

apt-get clean
apt-get autoremove

```

Generate a unique set of ssh (host) keys.
```

rm -f /etc/ssh/ssh_host_*
cat << EOF > /etc/rc2.d/S15ssh_gen_host_keys
#!/bin/sh
ssh-keygen -f /etc/ssh/ssh_host_rsa_key -t rsa -N ''
ssh-keygen -f /etc/ssh/ssh_host_dsa_key -t dsa -N ''
rm -f \$0
EOF

chmod a+x /etc/rc2.d/S15ssh_gen_host_keys

```

disable some unnecessary boot scripts
```

update-rc.d -f ondemand remove

```

Clear log files
```

> /etc/resolv.conf \
> /var/log/messages; > /var/log/auth.log; > /var/log/kern.log; > /var/log/bootstrap.log; \
> /var/log/dpkg.log; > /var/log/syslog; > /var/log/daemon.log; > /var/log/apt/term.log; rm -f /var/log/*.0 /var/log/*.1

```

Exit the template container:
```

exit

```

On the host, stop the template, make package and remove temporary container:
```

vzctl set 777 --ipdel all --nameserver ' ' --save
vzctl stop 777
cd /vz/private/777
sudo tar czf /vz/template/cache/ubuntu-10.04-i386-minimal.tar.gz .
sudo vzctl destroy 777

```


**Well, the problems at this point are:**
[LIST]
[*]Once used the template to create a container, responds to ping but it's not accessible with ssh (*ssh: connect to host 192.168.1.77 port 22: Connection refused*)
[*]Both the temporary template container and a container created with it, stop very slowly with "vzctl stop 777"
[*]Needed to find a substitute for "dialog" package available in the "main" repository.
[/LIST]

---

### Post by bodhi.zazen on 2010-05-04
To be honest, hard to know from what you posted. It could range from anything from a typo in your init scripts to missing ssh keys to networking.

Check the logs ( 777/var/log/init.log )

I updated my blog :

[http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/](http://blog.bodhizazen.net/linux/ubuntu-10-04-openvz-templates/)

And I made templates available for download:

[http://blog.bodhizazen.net/linux/download-ubuntu-10-04-openvz-templates/](http://blog.bodhizazen.net/linux/download-ubuntu-10-04-openvz-templates/)

I will add a link on the Ubuntu wiki page.

---

