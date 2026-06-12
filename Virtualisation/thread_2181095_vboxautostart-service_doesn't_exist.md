---
title: "vboxautostart-service doesn't exist"
date: 2013-10-16
forum: Virtualisation
---

### Post by marno11 on 2013-10-16
Hi All,

I was hoping to get my VirtualBox virtual machines to auto start when the host boots. but "service vboxautostart-service restart" doesn't work. I was wondering if anyone has come across this before or has an idea how to fix it.

I have followed all the steps which have been commonly posted in a few places, which in summary are:

> 
Edit the file /etc/default/virtualbox to include the following two lines:

VBOXAUTOSTART_DB=/etc/vbox
VBOXAUTOSTART_CONFIG=/etc/vbox/autostart.cfg

Create /etc/vbox/autostart.cfg file and add:

# Default policy is to deny starting a VM, the other option is "allow".
default_policy = deny
# Create an entry for each user allowed to run autostart
marno11 = {
allow = true
}

Set permissions on directory to the vboxuser group and make sure users can write to the directory as well as sticky bit.

# chgrp vboxusers /etc/vbox
# chmod 1775 /etc/vbox

Add the user to the vboxusers group.

# usermod -a -G vboxusers marno11

Set the path to the autostart database directory with

$ VBoxManage setproperty autostartdbpath /etc/vbox

choose the VM’s to start.

$ VBoxManage modifyvm Test_VM --autostart-enabled on

This created a file /etc/vbox/marno11.start

Now restart the vboxautostart-service to read in the changes.
# service vboxautostart-service restart

That last bit didn't work:
```

$ Service vboxautostart-service restart
vboxautostart-service: unrecognized service
```

I guess becasue vboxautostart-service doesn't exist
```

ls /etc/init.d/v*
/etc/init.d/virtualbox
```

-----------------------------------

Just a copy of the files incase people are interested:

File: /etc/default/virtualbox 
```

# Defaults for virtualbox initscript
# sourced by /etc/init.d/virtualbox
# installed at /etc/default/virtualbox by the maintainer scripts

#
# This is a POSIX shell fragment
#

# Set this to 1 if you would like the virtualbox modules to be loaded by
# the init script.
LOAD_VBOXDRV_MODULE=1

# SHUTDOWN_USERS="foo bar"
#   check for running VMs of user 'foo' and user 'bar'
#   'all' checks for all active users
# SHUTDOWN=poweroff
# SHUTDOWN=acpibutton
# SHUTDOWN=savestate
#   select one of these shutdown methods for running VMs
#   acpibutton and savestate causes the init script to wait
#   30 seconds for the VMs to shutdown
SHUTDOWN_USERS="all"
SHUTDOWN=acpibutton

# The autostart service is activated by setting two variables. The first one
# is VBOXAUTOSTART_DB which contains an absolute path to the autostart
# database directory. The second variable is VBOXAUTOSTART_CONFIG which
# points the service to the autostart configuration file which is used
# during boot to determine whether to allow individual users to start a VM
# automatically and configure startup delays.

VBOXAUTOSTART_DB=/etc/vbox
VBOXAUTOSTART_CONFIG=/etc/vbox/autostart.cfg
```

Having the virtual machines shut down just before the host shuts down works well

File: /etc/vbox/autostart.cfg                          
```

# Default policy is to deny starting a VM, the other option is "allow".
default_policy = deny

# marno11 is allowed to start virtual machines
marno11 = {
    allow = true
}
```

File: /etc/vbox/marno11.start                          
```

1
```

```

$ virtualbox --help
Oracle VM VirtualBox Manager 4.2.10_Ubuntu
```

---

### Post by newbie-user on 2013-10-16
Here's the contents of vboxautostart-service:
```
#!/bin/sh
#
# VirtualBox autostart service init script.
#
# Copyright (C) 2012 Oracle Corporation
#
# This file is part of VirtualBox Open Source Edition (OSE), as
# available from http://www.virtualbox.org. This file is free software;
# you can redistribute it and/or modify it under the terms of the GNU
# General Public License (GPL) as published by the Free Software
# Foundation, in version 2 as it comes in the "COPYING" file of the
# VirtualBox OSE distribution. VirtualBox OSE is distributed in the
# hope that it will be useful, but WITHOUT ANY WARRANTY of any kind.
#

# chkconfig: 35 35 65
# description: VirtualBox autostart service
#
### BEGIN INIT INFO
# Provides:       vboxautostart-service
# Required-Start: vboxdrv
# Required-Stop:  vboxdrv
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Description:    VirtualBox autostart service
### END INIT INFO

PATH=$PATH:/bin:/sbin:/usr/sbin
DEBIAN=yes
NOLSB=

[ -f /lib/lsb/init-functions ] || NOLSB=yes
[ -f /etc/vbox/vbox.cfg ] && . /etc/vbox/vbox.cfg

if [ -n "$INSTALL_DIR" ]; then
    binary="$INSTALL_DIR/VBoxAutostart"
else
    binary="/usr/lib/virtualbox/VBoxAutostart"
fi

# silently exit if the package was uninstalled but not purged,
# applies to Debian packages only
[ -z "$DEBIAN" -o -x $binary ] || exit 0

[ -r /etc/default/virtualbox ] && . /etc/default/virtualbox

system=unknown
if [ -f /etc/redhat-release ]; then
    system=redhat
elif [ -f /etc/SuSE-release ]; then
    system=suse
elif [ -f /etc/debian_version ]; then
    system=debian
elif [ -f /etc/gentoo-release ]; then
    system=gentoo
elif [ -f /etc/arch-release ]; then
     system=arch
elif [ -f /etc/slackware-version ]; then
    system=slackware
elif [ -f /etc/lfs-release ]; then
    system=lfs
else
    system=other
fi

if [ -z "$NOLSB" ]; then
    . /lib/lsb/init-functions
    fail_msg() {
        echo ""
        log_failure_msg "$1"
    }
    succ_msg() {
        log_success_msg " done."
    }
    begin_msg() {
        log_daemon_msg "$@"
    }
fi

if [ "$system" = "redhat" ]; then
    . /etc/init.d/functions
    if [ -n "$NOLSB" ]; then
        start_daemon() {
            usr="$1"
            shift
            daemon --user $usr $@
        }
        fail_msg() {
            echo_failure
            echo
        }
        succ_msg() {
            echo_success
            echo
        }
        begin_msg() {
            echo -n "$1"
        }
    fi
fi

if [ "$system" = "suse" ]; then
    . /etc/rc.status
    start_daemon() {
        usr="$1"
        shift
        su - $usr -c "$*"
    }
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            rc_failed 1
            rc_status -v
        }
        succ_msg() {
            rc_reset
            rc_status -v
        }
        begin_msg() {
            echo -n "$1"
        }
    fi
fi

if [ "$system" = "debian" ]; then
    start_daemon() {
        usr="$1"
        shift
        bin="$1"
        shift
        start-stop-daemon --background --chuid $usr --start --exec $bin -- $@
    }
    killproc() {
        start-stop-daemon --stop --exec $@
    }
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            echo " ...fail!"
        }
        succ_msg() {
            echo " ...done."
        }
        begin_msg() {
            echo -n "$1"
       }
    fi
fi

if [ "$system" = "gentoo" ]; then
    if [ -f /sbin/functions.sh ]; then
        . /sbin/functions.sh
    elif [ -f /etc/init.d/functions.sh ]; then
        . /etc/init.d/functions.sh
    fi
    start_daemon() {
        usr="$1"
        shift
        bin="$1"
        shift
        start-stop-daemon --background --chuid $usr --start --exec $bin -- $@
    }
    killproc() {
        start-stop-daemon --stop --exec $@
    }
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            echo " ...fail!"
        }
        succ_msg() {
            echo " ...done."
        }
        begin_msg() {
            echo -n "$1"
        }
        if [ "`which $0`" = "/sbin/rc" ]; then
            shift
        fi
    fi
fi

if [ "$system" = "arch" ]; then
    USECOLOR=yes
    . /etc/rc.d/functions
    start_daemon() {
        usr="$1"
        shift
        su - $usr -c "$*"
        test $? -eq 0 && add_daemon rc.`basename $2`
    }
    killproc() {
        killall $@
        rm_daemon `basename $@`
    }
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            stat_fail
        }
        succ_msg() {
            stat_done
        }
        begin_msg() {
            stat_busy "$1"
        }
    fi
fi

if [ "$system" = "slackware" ]; then
    killproc() {
        killall $1
        rm -f $PIDFILE
    }
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            echo " ...fail!"
        }
        succ_msg() {
            echo " ...done."
        }
        begin_msg() {
            echo -n "$1"
        }
    fi
    start_daemon() {
        usr="$1"
        shift
        su - $usr -c "$*"
    }
fi

if [ "$system" = "lfs" ]; then
    . /etc/rc.d/init.d/functions
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            echo_failure
        }
        succ_msg() {
            echo_ok
        }
        begin_msg() {
            echo $1
        }
    fi
    start_daemon() {
        usr="$1"
        shift
        su - $usr -c "$*"
    }
    status() {
        statusproc $1
    }
fi

if [ "$system" = "other" ]; then
    if [ -n "$NOLSB" ]; then
        fail_msg() {
            echo " ...fail!"
        }
        succ_msg() {
            echo " ...done."
        }
        begin_msg() {
            echo -n "$1"
        }
    fi
fi

vboxdrvrunning() {
    lsmod | grep -q "vboxdrv[^_-]"
}

start() {
    [ -z "$VBOXAUTOSTART_DB" ] && exit 0
    [ -z "$VBOXAUTOSTART_CONFIG" ] && exit 0
    begin_msg "Starting VirtualBox VMs configured for autostart";
    vboxdrvrunning || {
        fail_msg "VirtualBox kernel module not loaded!"
        exit 0
    }
    PARAMS="--background --start --config $VBOXAUTOSTART_CONFIG"

    # prevent inheriting this setting to VBoxSVC
    unset VBOX_RELEASE_LOG_DEST

    for user in `ls $VBOXAUTOSTART_DB/*.start`
    do
        start_daemon `basename $user | sed -ne "s/\(.*\).start/\1/p"` $binary $PARAMS > /dev/null 2>&1
    done

    return $RETVAL
}

stop() {
    [ -z "$VBOXAUTOSTART_DB" ] && exit 0
    [ -z "$VBOXAUTOSTART_CONFIG" ] && exit 0

    exit 0

    #begin_msg "Stopping VirtualBox VMs configured for autostop";
    #vboxdrvrunning || {
    #    fail_msg "VirtualBox kernel module not loaded!"
    #    exit 0
    #}
    #PARAMS="--stop"
    #[ -n "$VBOXAUTOSTART_CONFIG" ] && PARAMS="$PARAMS -c $VBOXAUTOSTART_CONFIG"

    # prevent inheriting this setting to VBoxSVC
    #unset VBOX_RELEASE_LOG_DEST

    #for user in `ls $VBOXAUTOSTART_DB/*.stop`
    #do
    #    start_daemon `basename $user | sed -ne "s/\(.*\).stop/\1/p"` $binary $PARAMS > /dev/null 2>&1
    #done

    #return $RETVAL
}

case "$1" in
start)
    start
    ;;
stop)
    stop
    ;;
*)
    echo "Usage: $0 {start|stop}"
    exit 1
esac

exit $RETVAL

```

---

### Post by marno11 on 2013-10-19
Thanks  				 				 					 						 	[**[COLOR=#000000]newbie-user[/COLOR]**]("http://ubuntuforums.org/member.php?u=464569"),

After messing around for a while trying to work out why vboxautostart-service wasn't there in the first place, and seaching about for general information on vboxautostart-service - I couldn't find anything. :(

What do you think I would be doing wrong?

Do you install from what is in Ubuntu repo or add the oracle maintained repository and install as suggested here:
[https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)


Unlike the various guides the script you provided does not support being restarted (only stoped and started), idk if this is a problem.

Also I have been having a bit of a problem getting the scrip to run on startup, I have added it to /etc/init.d/ and used "update-rc.d vboxautostart-service defaults" from here I am able to manually start and stop, but it doesn't start on boot. Are there some logs I can look at which may show if it has failed for some reason. Or did I not set it up correctly?

---

### Post by newbie-user on 2013-10-23
Sorry for the delay. I didn't catch your primary question the first time around, that you want the vms to autostart after boot. Here's another script:
```

#!/bin/bash
#
#This init script autostarts necessary vms at boot 
#and saves running vms on shutdown

# Sed explanation: sed -e 's/^.//' -e 's/.$//'
#   1.  -e means to allow multiple arguments in a single sed command
#   2.  's/^.//' means to substitute (s) / at the beginning of the line (^), any character (.) / [substitute with nothing] /
#   3.  's/.$//' means to substitute (s) / any character (.), at the end of the line / [substitute with nothing] /

VBOXUSER=vbox
RUNNINGVMS=$(sudo -H -u $VBOXUSER vboxmanage list runningvms | cut -d " " -f1 | sed -e 's/^.//' -e 's/.$//')
STOPPEDVMS=$(sudo -H -u $VBOXUSER vboxmanage list vms | cut -d " " -f1 | sed -e 's/^.//' -e 's/.$//')

case "$1" in
  start)
        for i in $STOPPEDVMS
                do
                        echo "Starting" $i "VM"
                        sudo -H -u $VBOXUSER vboxmanage startvm $i --type headless
                        sleep 5
                done
    ;;
  stop)
        for i in $RUNNINGVMS
                do
                        echo "Saving state of" $i "VM"
                        sudo -H -u  $VBOXUSER vboxmanage controlvm $i savestate
                done
    ;;
  *)
    echo "Usage: /etc/init.d/startvm {start|stop}"
    exit 1
    ;;
esac

exit 0

```
This one autostarts and autostops the vms. You will also have to tell it when to run during boot and shutdown:
```

 update-rc.d [name of the script] defaults 99 01

```

---

