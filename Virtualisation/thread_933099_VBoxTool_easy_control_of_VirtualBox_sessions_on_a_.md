---
title: "VBoxTool: easy control of VirtualBox sessions on a headless server"
date: 2008-09-29
forum: Virtualisation
---

### Post by markba on 2008-09-29
I would like to present my latest Open Source project: VBoxTool

It provides easy control of virtual machines of VirtualBox on a Linux headless server, published as free and open source software.

Currently VirtualBox lacks a decent management environment for controlling virtual sessions on a headless server environment. VBoxTool mimics partly Virtual Machine Manager  which controls sessions for other virtualization solutions like Qemu, KVM, etc. Unfortunately, VirtualBox is not in the list of supported engines (nor will be in the near future). 

**Features**

Heart of the framework is a script which can do several actions (start, save, backup, etc.) on all registered VirtualBox sessions in batch mode. It is a wrapper around VBoxManage (the commandline interface of VirtualBox), so execution is also by command line. 

[LIST]
[*]**Show info of all registered sessions**. Name, status (running, saved, etc.) and other info like the configured VRDP port are shown with the command 'vbox show'. When a session is running, also CPU load and memory usage are shown. As an alternative, 'vbox showrun' shows info only of running sessions.

[*]**Mass operation: save, start, stop**. Save all running sessions with one command: 'vbox save'. Start all saved sessions with 'vbox start'. Stop all running sessions with 'vbox stop'.

[*]**Mass backup**. Backup all sessions using rsync with one command: 'vbox backup'. When a session is running, it is saved and restarted after the backup. The next level of backup, could mean that online backup (thus without bringing the session offline) is possible*.

[*]**Batch start**. Controlled start of several sessions, defined in a configuration file, /etc/vboxtool/machines.conf. Only sessions named in that file will be started by 'vboxtool autostart'.

[*]**Mass configuration of VRDP port and port forwarding**. Configure VRDP port and port forwarding for all sessions, all at once in one command: 'vboxtool autostart'. Configuration takes place in /etc/vboxtool/machines.conf. When using port forwarding, there's no need for host interfacing anymore (in Linux, a tedious, complex task).

[*]**Autostart at host boot**. When the host boots, all sessions registered in /etc/vboxtool/machines.conf will be started in the background, issuing a 'vboxtool autostart' command under the named vbox_user in /etc/vboxtool/vboxtool.conf. 

[*]**Autosave at host halt**. When the host has a controlled down, i.e. halted, all running sessions are automatically saved.

[*]***System monitoring**. Monitor server status, session cpu load and memory in a graphical image. This will be done by developing and implementing a Munin plugin. Munin  is a system monitoring  platform with a plugin structure.

[*]***Webserver**. Next to develop is a webserver which points to the automation script. With this you can activate all functions from the script, all by a web page, so without requiring shell access.
[/LIST]
* Not (yet) implemented.
** Partly implemented.

**Command: vbox autostart**

Through autostart, sessions can be started in a controlled way: only the sessions in the configuration file will be started. As a bonus, the VRDP port and portforwarding pairs (also configurable) can be set at startup time. Option autostart depends on a configuration file, /etc/vbox/machines.conf. Each line in this file is a separate machine. 

Structure of each line: <session-name>,<vrdp-port>,<hostport-guestport>|<...>. 

The given VRDP port is set statically to the session, prior to starting; state is discarded when session is in savestate. You can issue as many portwarding pairs as you like.

Example for /etc/vbox/machines.conf:
```
Ubuntu Desktop,3391,2022-22
Ubuntu JeOS,3392,2022-22|80-80
```

**Resources**
[LIST]
[*][_VBoxTool website_]("http://vboxtool.sourceforge.net/")
[*][_Sourceforge project_]("http://sourceforge.net/projects/vboxtool")
[*][_Download_]("http://sourceforge.net/project/showfiles.php?group_id=239993")
[/LIST]

I'm looking forward for any feedback from anyone who thinks this software is usefull.

---

### Post by itxaka on 2008-09-29
looks awesome!

Will try it to see how it works :)

---

### Post by markba on 2008-10-02
For those who are interested: **version 0.2 of VBoxTool is released**.

Changes:
- configurable port forwarding: no host interfacing needed!
- comment out lines in /etc/vbox/machines.conf with '#'

For port forwarding, here some background-info why this is usefull: [http://vboxtool.sourceforge.net/portforwarding.html](http://vboxtool.sourceforge.net/portforwarding.html)

Website: [http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/)
Download: [http://sourceforge.net/project/showfiles.php?group_id=239993](http://sourceforge.net/project/showfiles.php?group_id=239993)
Sourceforge: [http://sourceforge.net/projects/vboxtool](http://sourceforge.net/projects/vboxtool)

---

### Post by markba on 2008-10-16
**For those who are interested: version 0.3 of VBoxTool is released. **

**Changes:**

- Autostart at host boot, autosave at host halt
- Compatibility break with 0.2: renamed main script 'vbox' to 'vboxtool', moved config folder from '/etc/vbox' to '/etc/vboxtool'

**Benefits of autostart at boot, autosave at halt:**

> - **Servers become self proficient**. A server, hosting VirtualBox and running sessions in a production environment, can be rebooted without knowing all the intricate details of bringing down the individual sessions. Even when an unexpected down happened e.g. by a power surge, sessions come up when the machine is booted, even when it is done by unqualified personnel: pushing a power button is not that complicated I presume.
- **Save time to access sessions on a desktop machine**. When a session is automatically opened in the background at boot, it can be easily accessed by rdesktop or similar rdp-viewer, without any delay because the session is already up-and-running, waiting for anyone to access it.
- **Be sure sessions are always saved at halt**. When sessions are running, be it headless or with GUI, be it on a server or a desktop, it is sure all sessions will be saved when the machine is downed. Normally, sessions become in 'aborted' state when nothing is done as the machine is going down. Bringing sessions automatically into savestate saves time when these sessions are started again after the next boot because the sessions don't have to boot, but also prevents data loss.
[http://vboxtool.sourceforge.net/autostart-at-boot-and-autosave-at-halt.html](http://vboxtool.sourceforge.net/autostart-at-boot-and-autosave-at-halt.html)

Website: [http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/)
Download: [http://sourceforge.net/project/showfiles.php?group_id=239993](http://sourceforge.net/project/showfiles.php?group_id=239993)
Sourceforge: [http://sourceforge.net/projects/vboxtool](http://sourceforge.net/projects/vboxtool)

---

### Post by ronaldrand on 2009-03-10
Hello Markba,

Currently I am liking vboxtool. The only problem is, when I hibernate my computer and come back, my WindowsXP VirtualBox is in an aborted state. Any workarounds? Does vboxtool do anything when you hibernate?

---

### Post by ronaldrand on 2009-03-11
Well, I managed to get vboxtool to save state before hibernation. Here's what I did. It's probably an ugly hack but I'm a noob:

In /usr/lib/pm-utils/sleep.d/000WindowsXP put:

> #!/bin/sh
# Save state of WindowsXP while hibernating and resume afterward.
# Note: Put your username after the sudo -u because this script runs as root and vboxtool can't find the VBox as root.

case "$1" in
        hibernate)
                sudo -u ron vboxtool save
                wait
                ;;
        thaw)
                sudo -u ron /home/ron/StartWindowsXP.sh
                ;;
        *)
                ;;
esacThe thaw is not working properly. I still don't know why. Perhaps if I figure it out I'll be back to update this.

My StartWindowsXP.sh looks like this:

> #!/bin/sh
/usr/local/bin/vboxtool autostart
echo "Sleeping for 30 seconds..."
sleep 10
rdesktop -z -P -K -u ron -n user localhost:3389
VBoxManage controlvm "WindowsXP" setvideomodehint 1280 750 32
exit $?It runs fine from an Application Launcher.

---

### Post by markba on 2009-07-04
For those who might interest in this: I released version 0.4 of VBoxTool as of today.

Major points : it's working with VBox > 2.2 and under Jaunty.

Website: [http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/)
Download: [http://sourceforge.net/project/showfiles.php?group_id=239993](http://sourceforge.net/project/showfiles.php?group_id=239993)
Sourceforge: [http://sourceforge.net/projects/vboxtool](http://sourceforge.net/projects/vboxtool)

A complete oversight of changes:
[http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/tags/release-0.4/changelog.txt?view=markup](http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/tags/release-0.4/changelog.txt?view=markup)

* Major bug fixes

o Auto start en stop stopped working in Ubuntu Jaunty (bug 2789649)
o VBoxTool is working again with VirtualBox >= 2.2 (bug 2775886)
o Command 'vboxtool stop' stops sessions (by poweroff). (bug 2317852)

* Enhancements

o Configurable backup folder (feature request 2213713)
o Added logging (feature request 2275101).
o Added option 'vboxtool showconfig' (feature request 2275280)
o Sessions are paused in stead of saved prior to backup (feature request 2805829).

* Minor bug fixes & enhancements

o Extracting of default folders is working again; due to changed CLI-output from VBoxManage (bug 2815159)
o Output of vboxtool does now contain 'backup' (feature request 2813155)
o Modifying vboxtoolinit to work with OpenSolaris/Solaris (bug 2527710).
o Backup destination path is shown in logfile (feature request 2806034)
o Added a generic -nologo for VBoxManage command (feature request 2393874).
o Expanded readme.txt, added configuration details (feature request 2275085).
o When issuing vboxtoolinit, it produced an error. (bug 2317839).
o Documented backup option in help (feature request 2216423).
o Pause state was not detected. (bug 2318332).
o Modified output of 'show' and 'showrun' command for consistency and easy text manipulation
o Code refactoring, changed all variable name: consistent separator '_'

---

### Post by digision on 2010-10-05
Hello markba,

I'am using Ubuntu 10.04 as host and VirtualBox 3.2.8.
The problem is vboxtool doesn't work at host startup.

Is there any new vboxtool version that work under ubuntu 10.04 and VirtualBox 3.2.8.

Thanks.

---

### Post by SuperCurro on 2010-11-23
Hi

I've the same problem, ti doesnt start at startup in ubuntu 10.04 LT. Any solution?

---

### Post by markba on 2012-04-09
I've adapted the vboxtool script for correct use with 3.x. There's no new version yet (that would be 0.5), but you can download it directly from the svn-repo:
[http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/script/vboxtool?revision=72&view=markup](http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/script/vboxtool?revision=72&view=markup)

See the changelog for the changes:
[http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/changelog.txt?view=markup](http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/changelog.txt?view=markup)

---

### Post by markba on 2012-04-30
After a log period, i've made an update to the project and brought it to version 0.5. Now the script is compatible with VBox 4.x (downwards to 3.x) and works also for OSE-version.
[http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/)

A complete revisionlog:
>   - This version will break compatability of 2.x versions, i.e. these are not supported anymore
    but they may still work
  - Extended compatability:
    - compatible with version 4.x while providing backwards compatability with 3.x
    - compatible with ose version (3.x/4.x) while providing backwards compatability with non-ose
  - Option syntax single dash is deprecated in VBox 3.1.x. These should be replaced by a double 
    dash. (bug 2908385)
  - Backup repaired. In 3.x, de extraction for the main vdi-file is changed, grep for "Primary 
    master" is changed into "(UUID:". Also added log-messages and made copying of snapshots 
    conditional. (bug 2954442 & 2903768; note that this bug in not entirely solved, because 
    handling multiple vdi's is not yet supported).
  - Extraction of PID for status purposes is made more specific. This is done by using UUID for
    identification and an extra grep on "[v]irtualbox". This solves the problem that there are
    multiple PID's returned (thus resulting in an error); this is the case when the name of a 
    session is a substring of another session and also when the name of the session is, by
    coincidence the same as another daemon (say: oracle for the vbox-session and for the 
    database server). (bug 2961192 & 2836110)
  - When there is no VRDP-port defined in machines.conf, do not apply this (bug 2893328)
  - Repair double dash option syntax in $vbox_command modifyvm $uuid -vrdpport
  - Removing the requirement of having a trailing comma in machines.conf (bug 2952485)
  - When a vm is not or registered invalid in machines.conf, show and log a warning; this will
    facilitate debugging
  - Dynamic setting of the vbox starttype: either 'vrdp' or 'headless'. On version 4.x only the 
    option 'headless' exist, both in ose or non-ose. But in version 3.x, option 'vrdp' is 
    available, but *only* in the non-ose variant; the ose version only has 'headless'. Using
    'headless' on a non-ose version essentially disables vrdp functionallity so it is not safe
    to use headless on the only option. The strategy is to find out if a vrdp option is available,
    otherwise use headless. This strategy means compatability between 3.x and 4.x to both versions
    ose and non-ose.
    - bug 3151695
    - feature request 2854538
    - patch 2948748
  - Do not use VRDP because it is deprecated, use VRDE. To provide backwards compatability with 3.x,
    the correct syntax is determined dynamically (bug 3518250)
  - Do not set VRDP-ports when VRDP is disabled. This is the case when using 3.x/ose or 4.x without 
    an extension pack. It is not only useless but also risky because the setting seems to work but 
    the VRDP-port is not stored, so everytime the session starts, the current state is discarded as 
    the first step of (trying to) set to VRDP-port. Discarding state multiple times can lead to 
    data loss of session corruption (bug 3518251)

In the meantime, the total download count has reached over 20.000 (since end of 2008 ), so I guess the script is usefull for many people.

---

