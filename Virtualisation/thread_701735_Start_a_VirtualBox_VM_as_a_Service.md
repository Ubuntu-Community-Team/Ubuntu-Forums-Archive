---
title: "Start a VirtualBox VM as a Service"
date: 2008-02-19
forum: Virtualisation
---

### Post by deejross on 2008-02-19
Hello All,

I've been searching around trying to figure out how to run a VirtualBox virtual machine at boot. I found many articles on how to install and remove services. I've also found articles on running a VM from the command line, which is all well and good, but I haven't found how to run a command at boot.

A similar question was asked [here, in the forums]("http://ubuntuforums.org/showthread.php?t=601749"), but the initial question on how to start on boot was never answered. Basically, all I want to do is run this command at boot:
```
VBoxVRDP -startvm "XP"
```

The problem is that the command does not immediately drop back to the prompt, like a service/daemon does. So how does one go about something like this? Thanks in advance for your help.

Ross

---

### Post by Whiffle on 2008-02-19
I see two options here.

One, make it run at boot.  You'd have to create a startup script for it, and tell it to run on a different virtual terminal as a user (although i'm not sure how you'd get around having to log in), with its own X-server.  This would feel pretty useless to me but could be done i think.

I think more of what you're after is to have it start on login, running as your user, and available to run in seamless mode.  In which case you would add the command you posted to whatever login script your window manager uses.

For me, I added a button for that command to my menu.  I don't use widnows much, but its right there if i need it.

---

### Post by deejross on 2008-02-19
Thanks for your speedy reply.

But, I want it run as a server on a headless server. VirtualBox gives you the ability to run virtual machines on a server without an X server, and to access the VM, you would use rdesktop (via the RDP protocol). Hence the name, VBoxVRDP.

VMware Server gives you a similar option in its GUI to start the virtual machine at system boot. I'm basically looking for the same functionality in VirtualBox.

---

### Post by Whiffle on 2008-02-19
Ooh okay.  Makes more sense now.

try looking at 

/etc/init.d/skeleton

Its an init script skeleton, add your own commands and you can make your own init script.

---

### Post by deejross on 2008-02-19
I started looking at that, but wasn't clear on a couple of things. Hope you don't mind if I ask you to clear a couple things up for me :D

First, making an init.d script from /etc/init.d/skeleton, you replace the values of the variables at the top of the file with the command you want to run, and that's all you need to touch?

Second, This works for commands that block the terminal until the command completes, right?

Third, I read somewhere that adding an ampersand to the end of a command would make it run like a service, is that true? Example: "VBoxVRDP -blah &" would return control of the terminal immediately and not block it until the vm was closed.

I've never really messed with init scripts before and I haven't found a clear explanation of how to modify them to my needs, so I hope you don't mind helping me out with a couple questions.

Thanks, Ross

---

### Post by Whiffle on 2008-02-19
Well, I have yet to make an init script, but I'll try.


It does look like all you have to change is the part at the top, usually.  However, I don't think an XP vm will be willing to shutdown like a regular linux service.  You might modify the do_stop and do_start functions  to use the commands this guy did:
[http://forums.virtualbox.org/viewtopic.php?p=16401&sid=1a3489bdb67f1ad0a0366be569932be8](http://forums.virtualbox.org/viewtopic.php?p=16401&sid=1a3489bdb67f1ad0a0366be569932be8)

It does appear to work with things that steal the terminal, ie dont automatically run as daemons.  However, since it needs to be modified to make it work, it might take some fanagaling to get it working just right.

Heres a blurb on the &

> If a command is terminated by the control operator &#8216;&&#8217;, the shell executes the command asynchronously in a subshell. This is known as executing the command in the background. The shell does not wait for the command to finish, and the return status is 0 (true). When job control is not active (see Job Control), the standard input for asynchronous commands, in the absence of any explicit redirections, is redirected from /dev/null.
[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameters](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameters)


I'm actually interested in this idea too, so I'm going to try putting together an init script.  I'll let you know if anything happens, although it might be a while.

---

### Post by deejross on 2008-02-19
Glad I peaked your interests :) I will also attempt making a init script and see what I can come up with. Surely, one of us should be able to make it work.

Ross

---

### Post by deejross on 2008-02-19
Well, I got mine working, but I don't know how "clean" it is or what problems it may have. All I know is that it boots the VM when I say "start" and shuts the VM down when I say "stop". Feel free to correct anything, as this is my first init script and I have no idea what I'm doing :)

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          VirtualBox - XP-Radio
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: Handles the XP-Radio virtual machine
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO

# Author: Ross Peoples <ubuntu.ross.peoples@gmail.com>

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin

#
# CHANGE THESE AS NEEDED
#
# Name given to the virtual machine
VM_NAME="XP-Radio"

# Name of this file, excluding /etc/init.d/
THIS_FILE=vbox-xp-radio

# Username to run as
RUNAS_USERNAME=ross

#
# END CHANGE THESE AS NEEDED
#

DESC="VirtualBox - ${VM_NAME}"
DAEMON=/usr/bin/VBoxVRDP
DAEMON_ARGS="-startvm \"${VM_NAME}\""
PIDFILE=/var/run/$THIS_FILE.pid
SCRIPTNAME=/etc/init.d/$THIS_FILE

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$THIS_FILE ] && . /etc/default/$THIS_FILE

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	#start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
		#|| return 1
	#start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
		#$DAEMON_ARGS \
		#|| return 2
	# Add code here, if necessary, that waits for the process to be ready
	# to handle requests from services started subsequently which depend
	# on this one.  As a last resort, sleep for some time.

	su $RUNAS_USERNAME -c "VBoxManage startvm ${VM_NAME} -type vrdp"	
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $THIS_FILE
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.

	su $RUNAS_USERNAME -c "VBoxManage controlvm ${VM_NAME} acpipowerbutton && sleep 10"

	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	#
	# If the daemon can reload its configuration without
	# restarting (for example, when it is sent a SIGHUP),
	# then implement that here.
	#
	# start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	echo "Reload not supported"
	return 0
}

case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$THIS_FILE"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$THIS_FILE"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop}" >&2
	exit 3
	;;
esac

:

```

---

### Post by LpBv on 2008-06-09
Hi,

Thanks for that scripts, that's what's I were looking for monthes ... 
Do you know if I can modify it to use it with vmware-server ?

Regards,

LpBv

Edit : How can I add it to /etc/init.d/ script in hardy ? Thanks

---

### Post by brendankidwell on 2008-10-30
Here is my attempt at making an init.d script for a VirtualBox system. Mine suspends-to-disk during shutdown instead of acpishutdown, and more importantly, properly reports error codes (success; service is already in that mode; start/stop operation failed). Please modify it for yourself to suit your needs.

I think you should also create "/etc/default/virtualbox" correctly according to the instructions found in "/etc/init.d/vboxdrv"; specify what users' vms to look for when shutting down vboxdrv, and what type of shutdown should be performed on the VM. I don't know if this is completely necessary, but I'm just covering my bases in case vboxdrv gets the shutdown command before my own init.d script.

**IMPORTANT!** Fill in all the values marked with "!!" according to your local configuration.

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          virtualbox-!!SHORTNAME
# Required-Start:    $local_fs $remote_fs vboxdrv vboxnet
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: !!LONGNAME virtual machine
# Description:       !!LONGNAME virtual machine hosted by VirtualBox
### END INIT INFO
 
# Author: Brendan Kidwell <brendan@glump.net>
#
# Based on /etc/init.d/skeleton from Ubuntu 8.04.
 
# Do NOT "set -e"
 
# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="!!LONGNAME virtual machine"
NAME=virtualbox-!!SHORTNAME
SCRIPTNAME=/etc/init.d/$NAME
 
MANAGE_CMD=VBoxManage
VM_OWNER=!!USERNAME
VM_NAME="!!LONGNAME" #This has to be the name exactly as it appears in your VirtualBox GUI control panel.
 
# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME
 
# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS
 
# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions
 
#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
 
	sudo -u $VM_OWNER $MANAGE_CMD showvminfo "$VM_NAME"|grep "^State:\s*running" >/dev/null && {
	    echo "$VM_NAME" is already running.
	    return 1
	}
 
	sudo -u $VM_OWNER $MANAGE_CMD startvm "$VM_NAME" -type vrdp >/dev/null || {
	    echo Failed to start "$VM_NAME".
	    return 2
	}
 
	echo "$VM_NAME" started or resumed.
	return 0
}
 
#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
 
	sudo -u $VM_OWNER $MANAGE_CMD showvminfo "$VM_NAME"|grep "^State:\s*running" >/dev/null || {
	    echo "$VM_NAME" is already stopped.
	    return 1
	}
 
	sudo -u $VM_OWNER $MANAGE_CMD controlvm "$VM_NAME" savestate || {
	    echo Failed to stop "$VM_NAME".
	    return 2
	}
 
	echo "$VM_NAME" suspended.
	return 0
}
 
#
# Display "State" field from showinfo action
#
do_status()
{
	sudo -u $VM_OWNER $MANAGE_CMD showvminfo "$VM_NAME"|grep "^State:\s*.*$"
}
 
case "$1" in
  start)
	[ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  status)
	do_status
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|status}" >&2
	exit 3
	;;
esac
 
:
```

(For more info, see my additional comments on [VirtalBox as a Service in Linux]("http://www.glump.net/dokuwiki/howto/virtualbox_as_a_service").)

I hope this helps some people.

---

### Post by Noccy on 2009-01-30
Any workarounds to use this with the VirtualBox OSE? Still have a few pages that need hosting under ISS running in a VirtualBox vm. Would be lovely to be able to set this up :)

Best regards,
Chris

---

### Post by SeijiSensei on 2009-07-20
Anyone still looking for a solution to running VirtualBox VMs at boot should take a gander at [**vboxtool**](http://vboxtool.sourceforge.net/).  It's a script to manage VMs from the command prompt.  I'm just trying it out now.

---

### Post by turexy on 2009-07-31
Hi,

I wrote a very simple loop which takes data to process from different file. Let say that we are hosting two VMs one is named Gary.w2k3 and the second Simon.Debian.

1. create a folder /etc/virtualbox and cd to it
# mkdir /etc/virtualbox 
# cd /etc/virtualbox

2. create a file named vm.list and edit it so it contains VM names in one column, save the file. eg:
# nano vm.list

Gary.w2k3
Simon.Debian



3. create a file named autostart.vm and copy/paste code below:

```
#!/bin/bash


for VPS in `cat /etc/virtualbox/vm.list`; do

        VBoxHeadless -startvm "$VPS" &
        sleep 40

done

exit 0
```

4. save the file and give it execute attribute 
# chmod +x autostart.vm

5. edit /etc/rc.local and put this "/etc/virtualbox/autostart.vps" just above "exit 0" and save the file.

sleep 40 is a time interval in seconds between loops to let each system fully boot before starting next one. You can change it to whatever you like.

It works for me, I hope it will work for you guys.

---

### Post by markba on 2009-08-17
> **turexy said:**
> Hi,

I wrote a very simple loop which takes data to process from different file. ......

Starting a session should work fine, but there are two problems with this solution:

1. Sessions are always started as root, so the sessions themselves should be present under de root home dir (i.e. /root). Normally, it is not needed nor recommended to work (create, start, etc) under root. Ypu can run commands on different user context by using the 'su' command in /etc/rc/local.

2. The solution does not take care of shutting down sessions (preferably: saving) on halt. When they are not saved on system halt, they become an 'aborted' state with possible data loss.

For these two problem, vboxtool, of which I'm the author, takes care. It does actually do the same as the published script on the post above, but a lot more:

> VBoxTool currently consist only of a set of scripts. With this scripts, virtual 
machines of VirtualBox in a Linux headless server can be controlled. Start, stop, 
save, backup and show status of sessions in batch mode from the command line.


Here an excerpt of the installation en configuration manual:
[http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/readme.txt?revision=49](http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/readme.txt?revision=49)


```
INSTALLATION

Note. Precede commands with 'sudo' when not operated as root.

* Place the main script script/vboxtool in /usr/local/bin

* Make vboxtool executable: 
    chmod +x /usr/local/bin/vboxtool

* Place the init script script/vboxtoolinit in /etc/init.d

* Make vboxtoolinit executable: 
    chmod +x /etc/init.d/vboxtoolinit
  
* Activate the init script vboxtoolinit:
    update-rc.d vboxtoolinit defaults 99 10
  
* Create a folder /etc/vboxtool. In here, two config files have to be created, see
  configuration section below, type 'vboxtool help' for more instructions.
  
Note. To remove vboxtoolinit from autostart: update-rc.d -f vboxtoolinit remove

CONFIGURATION

Note. Configuration from vboxtool does *not* taking place on *running* sessions, 
so save or stop all sessions before issueing the autostart command.

* Create /etc/vboxtool/machines.conf:
    <session name>,<VRDP-port>

   The VRDP-port enables RDP-clients like rdesktop to connect. It may be left blank.

* Create /etc/vboxtool/vboxtool.conf:
    vbox_user='<user name>'

* Issue the following command:
    vboxtool autostart

  VBoxTool will configure sessions (VRDP-port). By now, session(s) should be up and 
  running and configured.

* Check if sessions or running, with the assumed vrdp-port:
    vboxtool show 

  Show only the running sessions:
    vboxtool showrun

* Check if sessions configured in /etc/vboxtool/machines.conf are be automatically 
  started at reboot. Reboot your system, check with: vboxtool showrun

```

For more info, see [http://vboxtool.sourceforge.net/](http://vboxtool.sourceforge.net/) or ask me.

---

### Post by Jordanwb on 2009-09-20
I am interested in starting a vm at start up. I used brendankidwell's init script, but I don't know how to make it start up at boot. Which /etc/rc#.d folder to I link it to?

---

### Post by RomanIvanov on 2009-12-21
use original/owner/main page of the script [http://www.glump.net/dokuwiki/howto/virtualbox_as_a_service](http://www.glump.net/dokuwiki/howto/virtualbox_as_a_service)

it was fixed for start up launch.

---

### Post by RomanIvanov on 2009-12-28
To whom It may concern:

I used Debian5 as guest host, and needed to run it as service. markba's skript works fine for SUN Virtual Box, but have a problem for Virtual Box OSE.

```
sudo update-rc.d virtualbox-testserver defaults 21
```

to start "**--type headless**":

```
sudo -H -u $VM_OWNER $MANAGE_CMD startvm "$VM_NAME" --type headless
```

---

### Post by diskmaster23 on 2010-01-24
I tried to use VBoxtool, but I keep running into problems. I am using Xubuntu 9.04.

Is anyone else having trouble using vboxtool with using vboxtool in 9.04?

The problems I keep running into are that the vboxtool doesn't start and stop, and it doesn't respond to commands once autostart command is used.

---

### Post by nexes128 on 2010-08-05
Use an & at the end of the command it will fork it into the backgroud(keep in mind you'll have to shutdown the vm from within the vm or kill the pid to stop it)

```
VBoxVRDP -startvm "XP"&
```

---

### Post by kostiskag on 2011-09-16
Hi [brendankidwell]("http://ubuntuforums.org/member.php?u=694562")!!! I followed your guide
i must say that you made to me clear a lot stuff like services and stuff i also saw articles about runlevels at debian ubuntu wich made me understand better what you were saying in the guide but the last command where you say
sudo update-rc.d virtualbox-!!SHORTNAME defaultsdidnt work for me because of priority issues virtualbox starts in priority somwere 24 so when you do this without priority makes your image init faster than the virtualbox itself wich will fail. so i used something like:
sudo update-rc.d virtualbox-!!SHORTNAME defaults 70

now virtualbox starts first and your VM next

---

