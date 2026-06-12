---
title: "Owner of Vbox Shared Folder"
date: 2013-02-23
forum: Virtualisation
---

### Post by yahyaerturan on 2013-02-23
First I am quite new to Ubuntu and trying to commit myself to it as a PHP developer. Well, I am running on a guest Xubuntu 12.10 system based on Windows7 host.

I shared my web_projects folder and managed to access it by adding my ubuntu user to vboxsf group under /media folder. I symlink a folder inside web_projects as virtual host but it simply says access denied because owner of shared folder is root. What I need to do is changing default owner of vbox shared folder so I can reach them through apache.

I made some digging[1] that ends up with:

    yahya@ubuntu:~$ sudo mount -t sf_web_projects -o uid=1000,gid=1000 share /home/yahya/mirror
    mount: unknown filesystem type 'sf_web_projects'

[http://askubuntu.com/questions/30396/error-mounting-virtualbox-shared-folders-in-an-ubuntu-guest](http://askubuntu.com/questions/30396/error-mounting-virtualbox-shared-folders-in-an-ubuntu-guest)

---

### Post by lmarmisa on 2013-02-24
I recommend this procedure:

1) Be sure that GuestAdditions are installed in VM.

2) Define a shared folder on the VB menu. For example, I have defined the folder "d:\share" with the name "share". Important: do not tick the Auto-Mount option!!!.

3) Create the mount point in VM:

```

sudo mkdir /media/share

```4) Edit file /etc/rc.local

```

gksudo gedit /etc/rc.local

```and add the command mount:

```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR=Blue]mount.vboxsf -w -o uid=1000,gid=1000 share /media/share[/COLOR]

exit 0

```Save and exit.

Finally reboot the VM and check if the shared folder is automounted properly.

You can define symlinks typing commands similar to this:

```

ln -s /media/share share

```Best regards,

Luis

---

