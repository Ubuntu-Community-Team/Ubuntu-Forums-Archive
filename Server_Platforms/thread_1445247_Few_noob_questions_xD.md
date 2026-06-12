---
title: "Few noob questions xD"
date: 2010-04-02
forum: Server Platforms
---

### Post by twin-08 on 2010-04-02
Hey guys I have a home server which was running windows server 08.

I downloaded ubuntu server 10.04 which I think is great quite fast, however I have a few nooby questions to ask you.

If I install a GUI, is there anyway of removing it again with out having to format and set up again?

I have an raid card with a sata 640gb hard drive as my primary drive is IDE, I was using this as a file storage server using samba, but I don't know what path the harddrive is as I changed it in windows and forgot what it is, is there a way of finding out the path? When I was installing it it was /dev/sdb so would this be the path?.

Thanks, Twin sorry if these are long questions, however I am a noob to an linux server ;D

---

### Post by cdenley on 2010-04-02
1. Yes, you can. You can always add/remove packages as much as you wish, and all of ubuntu is just a collection of packages.

To add the default gnome packages:
```

sudo apt-get install ubuntu-desktop

```
This installs the meta-package ubuntu-desktop, which because of dependencies, will result in all packages for a default desktop configuration being installed as well.

To remove it, you can remove the meta-package, then remove all packages which were installed as a dependency for another package which has since been removed:
```

sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove

```

Or you can also go the "tasksel" route to add/remove common configurations:
```

sudo tasksel

```

2. I'm assuming this is hardware raid? A typical path for a disk would be /dev/sdb. Partitions on the disk would then be /dev/sdb1 /dev/sdb2, etc. The paths are created in order, so if you have a /dev/sdb, then you also have a /dev/sda. You can list all disks (and their partitions) with this command:
```

sudo fdisk -l

```

---

### Post by twin-08 on 2010-04-02
Great thanks. Another noob question, when I try to install webmin 1.510, I get this error.

```
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
Errors were encountered while processing:
 webmin
twin@linux-server:~$

```

The command I used to install the packages where. ```
sudo aptitude install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl
```

---

### Post by KB1JWQ on 2010-04-02
Out of curiosity, why did you go with 10.04?  It's not stable enough for production yet-- if you're storing anything you even slightly care about on it, I'd urge you to reconsider until it hits release. :-)

---

### Post by cdenley on 2010-04-02
That dependency is not in the lucid repo. That webmin package was not built for ubuntu 10.04. Compatibility is one of many problems you can run into when you stray from the ubuntu repositories.

[https://bugs.launchpad.net/ubuntu/+bug/542798](https://bugs.launchpad.net/ubuntu/+bug/542798)

---

### Post by twin-08 on 2010-04-02
I had an older version of it working on 10.04.

I went with 10.04 because I wanted to see what it is like (for the gui question)

Now I will just leave the gui, and just config samba and thats me done.

Thanks for all the help guys.

---

### Post by HermanAB on 2010-04-02
Note that you don't have to uninstall the desktop packages.  I sure would not bother.  You can start/stop X whenever you want and that is usually all that s needed.

---

### Post by twin-08 on 2010-04-02
How would I do that?

---

### Post by cdenley on 2010-04-02
> **twin-08 said:**
> How would I do that?

I think on 9.10 (and probably 10.04), you can edit /etc/init/gdm.conf to prevent GDM, your graphical login manager, from loading at boot.
```

# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

[B][COLOR="Red"]#[/COLOR]start on (filesystem
[COLOR="red"]#[/COLOR]          and started hal
[COLOR="red"]#[/COLOR]          and tty-device-added KERNEL=tty7
[COLOR="red"]#[/COLOR]          and (graphics-device-added or stopped udevtrigger))[/B]
stop on runlevel [016]

emits starting-dm

env XORGCONFIG=/etc/X11/xorg.conf

script
    [ ! -f /etc/X11/default-display-manager -o "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/sbin/gdm" ] || { stop; exit 0; }

    # Check kernel command-line for inhibitors
    for ARG in $(cat /proc/cmdline)
    do
        case "${ARG}" in
            text|-s|s|S|single)
                exit 0
                ;;
        esac
    done

    if [ -r /etc/default/locale ]; then
        . /etc/default/locale
        export LANG LANGUAGE
    elif [ -r /etc/environment ]; then
        . /etc/environment
        export LANG LANGUAGE
    fi
    export XORGCONFIG

    initctl emit starting-dm DM=gdm

    exec gdm-binary $CONFIG_FILE
end script

```
Then, if that works, when your system boots, you will get a login terminal. If you login, you get a shell. If you need a graphical desktop, start gdm with:
```

sudo service gdm start

```

---

### Post by jfmanamtr on 2010-04-02
Alternatively, you can issue "update-rc.d -f gdm remove" at the command prompt & that removes GDM from startup. When you boot the PC, you will get to a bash shell & can then start X-Windows with "startx". If you ever want to start GDM at boot, you can issue "update-rc.d -f gdm defaults" to put it back in the boot sequence.
 
~John

---

### Post by cdenley on 2010-04-02
> **jfmanamtr said:**
> Alternatively, you can issue "update-rc.d -f gdm remove" at the command prompt & that removes GDM from startup.

I don't think that will work anymore, as of 9.10. There are no links in /etc/rc*.d to /etc/init.d/gdm to remove. I think /etc/init/gdm.conf replaced them.
```

cdenley@cdenley:~$ ls -l /etc/rc*.d|grep gdm
cdenley@cdenley:~$

```

---

### Post by jfmanamtr on 2010-04-02
Oops. Your right about that. I missed the part where he said 9.10. I really gotta learn to read more carefully.
 
~John

---

### Post by twin-08 on 2010-04-02
Guys does anyone know how to get my ip not like the routers ip eg 192.xxx.xx.x 

Thanks, Twin

---

### Post by jfmanamtr on 2010-04-02
[http://whatismyip.com](http://whatismyip.com)

That should do you!

~John

---

