---
title: "Problem with script for Virtualbox VM start/stop"
date: 2009-06-18
forum: Virtualisation
---

### Post by latoubes on 2009-06-18
Hi guys,

This is my configuration, 
Virtualbox 2.2.4.
Host -> Ubuntu 9.04, Kernel version 2.6.28-11-generic
Guest -> Ubuntu 8.04 LTS

I made a script for start/stop the Guest when the Ubuntu Host start/stop/reboot. Based on [http://farfewertoes.com/code/vboxcontrol/](http://farfewertoes.com/code/vboxcontrol/)

This script work perfect if i executed when the Ubuntu Host was completely started but if i try to put this script in the boot process of Ubuntu, the guest does not start!. Actually the virtualbox status of the VM is aborted!!?

To put the script like a service of ubuntu i used this
```

$> update-rc.d -f vboxboot defaults 99 10

```Permission of the script
```

$> -rwxr-xr-x 1 root root 3968 2009-06-17 18:45 /etc/init.d/vboxboot

```This is the script
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          vboxboot  
# Required-Start:    $local_fs $syslog $remote_fs vboxdrv
# Required-Stop:     $local_fs $syslog $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Virtual Box Images Boot
# Description:       Script for start/stop/reload/status list of VirtualBox Images
### END INIT INFO
#
# Copyright (c) 2009 Luis Toubes . toubes@gmail.com
# Permission is hereby granted, free of charge, to any
# person obtaining a copy of this software and associated
# documentation files (the "Software"), to deal in the
# Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish,
# distribute, sublicense, and/or sell copies of the
# Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice
# shall be included in all copies or substantial portions of
# the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY
# KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE
# WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
# PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS
# OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR
# OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
# OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
# SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

# Options
# The username assigned to run the images.
VBOX_USER='sysat'
# List of Images to start/stop
VBOX_IMAGE_LIST='Lisa seymour stud'
# VirtualBox Command-Line Manager
VBOX_MANAGER='/usr/bin/VBoxManage'

#COSAS NUEVAS
export PATH="${PATH:+$PATH:}/bin:/usr/bin:/usr/sbin:/sbin"
#PATH=/usr/sbin:/usr/bin:/sbin:/bin
#FIN


# Exit if the package is not installed
[ -x "$VBOX_MANAGER" ] || exit 0

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Start Script for VirtualBox Images
do_start() {
    for d in $VBOX_IMAGE_LIST
      do        
        log_action_msg "Starting VM '$d' ..."
        # Check if the VM is already running
        sudo -H -u $VBOX_USER $VBOX_MANAGER showvminfo "$d"|grep "^State:\s*running" >/dev/null && {
            log_action_msg "Ups!, '$d' is already running ..."
            continue #Go to the next element
        }

        # Starting the VM and check if is failed
        sudo -H -u $VBOX_USER $VBOX_MANAGER startvm "$d" -type vrdp >/dev/null || {
             log_action_msg "Oh, no!!!, failed to start '$d' ..."
             continue #Go to the next element
        }
   log_action_msg "'$d' started!"
      done
      return 0
}

# Stop Script for VirtualBox Images
do_stop() {
    for d in $VBOX_IMAGE_LIST
      do
        log_action_msg "Shutting down VM '$d' ..."
        # Check if the VM is already stopped
        sudo -H -u $VBOX_USER $VBOX_MANAGER showvminfo "$d"|grep "^State:\s*running" >/dev/null || {
          log_action_msg "Ups!, '$d' is already stopped ..."
          continue
        }

        sudo -H -u $VBOX_USER $VBOX_MANAGER controlvm "$d" savestate >/dev/null || {
           log_action_msg "Oh, no!!!, failed to stop '$d' ..."
           continue
        }       
      log_action_msg "'$d' suspended!"
      done
      return 0
}

do_restart() {
   do_stop
   do_start
}

do_status() {
    for d in $VBOX_IMAGE_LIST
      do
   log_action_msg "'$d': "
        sudo -H -u $VBOX_USER $VBOX_MANAGER showvminfo "$d" | grep "^State:\s*.*$"
      done 
}

   # Daemon service
   case "$1" in
     start)
        do_start
        ;;
     stop)
        do_stop
        ;;
     restart|reload)
        do_restart
        ;;
     status)
        do_status
        ;;
     *)
         log_failure_msg "Usage: $0 {start|stop|status|restart}" >&2
         exit 3
         ;;
    esac

    exit 0

```Really don't know what i am doing wrong !!! :(

Any advice?

Many thanks!

---

### Post by Jeff Anthony on 2010-03-23
Have you tried scrapping the startup script for a System > Preferences > Startup Applications entry?

I use a similar start-up shortcut on my Win computer testing the [Ubuntoogle ]("http://ubuntoogle.info")project. Apologies for the website's 'under constructionness' but I didn't see any reason to close off registration and possible help getting it set up ;).

I'm not a command expert but I think it would be something like 
```
~/.VirtualBox/VBoxManage.exe startvm  <vmname>
```

---

