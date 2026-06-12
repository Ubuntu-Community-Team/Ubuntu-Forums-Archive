---
title: "There was an error creating the child process for this terminal"
date: 2009-05-10
forum: System76 Support
---

### Post by eaone on 2009-05-10
I just upgraded to Jaunty 9.04 and everything seems fine except the monitor.  My eyes were hurt and I thought it might have something to do with the refresh rate or the nvidia driver.  So I downgraded the driver from the recommended version (which I forgot the number) to the one before.  Many problems arrived after I restart the machine.  The main problem I run into is that I cannot start a Terminal.  I got an error "There was an error creating the child process for this terminal".  Here is the error mesg I found in .xsession-errors.  Looks like I am having some permission problems.  I tried couple suggestions I found online but they are not helping.  Any help will be greatly appreciated!

Edith

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: shm.c: shm_open() failed: Permission denied
GNOME_KEYRING_SOCKET=/tmp/keyring-kYJlat/socket
SSH_AUTH_SOCK=/tmp/keyring-kYJlat/socket.ssh

(gnome-settings-daemon:6234): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:6234): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/edith/.config/metacity/sessions/10754eed4d4c7cc3b6124194111862427900000060340022.ms: Failed to open file '/home/edith/.config/metacity/sessions/10754eed4d4c7cc3b6124194111862427900000060340022.ms': No such file or directory
E: shm.c: shm_open() failed: Permission denied
E: shm.c: shm_open() failed: Permission denied
E: shm.c: shm_open() failed: Permission denied
Failure: Module initalization failed
Initializing trackerd...
Tracker-Message: Checking XDG_DATA_HOME is writable and exists
Tracker-Message:   XDG_DATA_HOME is '(null)'
Tracker-Message:   XDG_DATA_HOME set to '/home/edith/.local/share'
Tracker-Message:   Path is OK
Tracker-Message: Setting IO priority
Tracker-Message: Setting up monitor for changes to config file:'/home/edith/.config/tracker/tracker.cfg'
Tracker-Message: Loading defaults into GKeyFile...
Tracker-Message: Legacy config option 'IndexEvolutionEmails' found
Tracker-Message:   This option has been replaced by 'DisabledModules'
Tracker-Message:   Option 'DisabledModules' removed 'evolution'
Tracker-Message: Legacy config option 'IndexThunderbirdEmails' found
Tracker-Message:   This option is no longer supported and has no effect
Tracker-Message: Legacy config option 'SkipMountPoints' found
Tracker-Message:   Option 'IndexMountedDirectories' set to true
Tracker-Message: Setting up stopword list for language code:'en'
** (nm-applet:6275): DEBUG: applet_common_device_state_changed
** (nm-applet:6275): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:6275): DEBUG: foo_client_state_changed_cb
** (gnome-panel:6259): DEBUG: Adding applet 0.
** (gnome-panel:6259): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:6259): DEBUG: Adding applet 1.
** (gnome-panel:6259): DEBUG: Adding applet 2.
** (gnome-panel:6259): DEBUG: Adding applet 3.
** (gnome-panel:6259): DEBUG: Adding applet 4.
** (gnome-panel:6259): DEBUG: Adding applet 5.
** (gnome-panel:6259): DEBUG: Adding applet 6.
** (gnome-panel:6259): DEBUG: Adding applet 7.
** (gnome-panel:6259): DEBUG: Adding applet 8.
** (gnome-panel:6259): DEBUG: Adding applet 9.
** (gnome-panel:6259): DEBUG: Adding applet 10.
** (gnome-panel:6259): DEBUG: Adding applet 11.
Tracker-Message: Setting up stemmer for language code:'en'
Tracker-Message: Checking directory exists:'/home/edith/.local/share/tracker/data'
** (gnome-panel:6259): DEBUG: Adding applet 12.
Tracker-Message: Checking directory exists:'/home/edith/.cache/tracker'
Tracker-Message: Registering DBus service...
  Name:'org.freedesktop.Tracker'
Starting log:
  File:'/home/edith/.local/share/tracker/trackerd.log'
** (gnome-panel:6259): DEBUG: Adding applet 13.
** (gnome-panel:6259): DEBUG: Adding applet 14.

(gnome-panel:6259): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:6259): DEBUG: Adding applet 15.

** (nautilus:6260): WARNING **: Unable to add monitor: Not supported
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
evolution-alarm-notify-Message: Setting timeout for 58848 1242000000 1241941152
evolution-alarm-notify-Message:  Sun May 10 17:00:00 2009

evolution-alarm-notify-Message:  Sun May 10 00:39:12 2009

** (update-notifier:6290): DEBUG: /usr/lib/update-notifier/apt-check returned 1 (security: 0)
** (update-notifier:6290): DEBUG: crashreport_check

Window manager warning: Invalid WM_TRANSIENT_FOR window 0x3a00003 specified for 0x3a0002d ().
```

---

### Post by eaone on 2009-05-10
after doing more research, I fixed the problem with a suggestion from this post
[https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927)

>     1. The order in /etc/rcS.d is messed up (this bug). Fix:
        a. $ ls /etc/rcS.d | grep mountdevsubfs.sh
            Note the number next to the "S" in the returned filename (e.g. the 05 in S05mountdevsubfs.sh).
        b. $ sudo mv /etc/rcS.d/S_mountdevsubfs.sh /etc/rcS.d/S11mountdevsubfs.sh
            where _ is the number in the old filename.


I have also tried the suggestion of adding a line in /etc/fstab to mount /dev/pts.  But it did not work for me.  Now that my terminal is working , I tried mount|grep /dev/pts  and there is nothing to grep.  I suspect my problem had nothing to do with mounting devpts.

---

### Post by rbfthomas on 2009-05-12
If you don't mind my asking, how did you get to command line without opening terminal?

---

### Post by thomasaaron on 2009-05-13
Ctrl-Alt-F1 through Ctrl-Alt-F6 will open terminals. Ctrl-Alt-F7 will bring you back to your Desktop.

Due to an nVidia bug, some nVidia machines will not do this.

---

### Post by susenj on 2009-05-24
Thanks eaone!
i tried the first fix but found that the number after 'S' is 11 itself.
So i was worried but when i did the second fix 
that is 
{
1. The order in /etc/rcS.d is messed up (this bug). Fix:
        a. $ ls /etc/rcS.d | grep mountdevsubfs.sh
            Note the number next to the "S" in the returned filename (e.g. the 05 in S05mountdevsubfs.sh).
        b. $ sudo mv /etc/rcS.d/S_mountdevsubfs.sh /etc/rcS.d/S11mountdevsubfs.sh
            where _ is the number in the old filename.
    2. Or, you modified /etc/init.d/mountdevsubfs.sh (maybe to get VirtualBox to work; that workaround is no longer needed) and dpkg refuses to update it ([bug 360160]("https://bugs.launchpad.net/bugs/360160")). Fix:
        $ sudo cp /etc/init.d/mountdevsubfs.sh.dpkg-dist /etc/init.d/mountdevsubfs.sh
If you do one of these fixes, reboot afterwards.
}

and rebooted...hollaa..
terminal is okay.!
Thanks again!:p:p:-({|=


> **eaone said:**
> after doing more research, I fixed the problem with a suggestion from this post
[https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927](https://bugs.launchpad.net/ubuntu/+source/insserv/+bug/321927)



I have also tried the suggestion of adding a line in /etc/fstab to mount /dev/pts.  But it did not work for me.  Now that my terminal is working , I tried mount|grep /dev/pts  and there is nothing to grep.  I suspect my problem had nothing to do with mounting devpts.

---

