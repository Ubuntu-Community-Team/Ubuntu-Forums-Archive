---
title: "Using Vboxtool to autostart a virtual machine does not auto start"
date: 2012-10-07
forum: Server Platforms
---

### Post by runegang on 2012-10-07
Hi. I have been trying to autostart a virtual machine upon boot using vboxtool ([http://vboxtool.sourceforge.net](http://vboxtool.sourceforge.net)). I have followed the instructions provided and the vm runs if i execute "vboxtool autostart". It does also save the machine state when I power off the host machine. 

My problem is that it is not starting the virtual machine upon boot.

I am running a headless ubuntu server installation, 12.04, 32bit. 

I have tried searching for a solution for a while now and also tried to execute the command with /etc/rc.local with no success. Are there anyone who can help me?

Thank you very much.
Best regards
Rune

---

### Post by CharlesA on 2012-10-07
Check when the script is set to run on boot. I had to change the bootscript I use to run last, so vboxdrv was loaded.

---

### Post by runegang on 2012-10-07
I have been trying to investigate it further, but I understand that I do not know the linux system well enough to find out when it is executed. If I placed the command in rc.local, should it not be run somewhere in the end of the boot process?

I see that it is trying to execute a su command, could it be that it has something to do with permission? I have made it runable. Maybe the user needs to be logged in first? How could this be avoided or solved the easiest way if this is the case? 


If I am completely wrong, please correct me. I am asking so that I can learn some more :-)



The script placed in init.d folder is

```
#!/bin/bash
#
#  vboxtoolinit: Frontend for vboxtool for auto start sessions when booting and save 
#                sessions when host is stopped
#
#  This is a wrapper for vboxtool. It is to be placed in /etc/init.d to provide auto
#  start at boot time and stop when the host is halted. Because it's a wrapper, the 
#  original functions of vboxtool can be executed as usual, without cd'ing to 
#  /etc/init.d.
#
#  Usage: Should be placed in /etc/init.d
#
#  Copyright (C) 2008 Mark Baaijens <mark.baaijens@gmail.com>
#
#  This file is part of VBoxTool.
#
#  VBoxTool is free software: you can redistribute it and/or modify
#  it under the terms of the GNU General Public License as published by
#  the Free Software Foundation, either version 3 of the License, or
#  (at your option) any later version.
#
#  VBoxTool is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program.  If not, see <http://www.gnu.org/licenses/>.
#

### BEGIN INIT INFO
# Provides:          vboxtool
# Required-Start:    $syslog $local_fs
# Required-Stop:     $syslog $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Description:       Controls VirtualBox sessions
### END INIT INFO

# Command mapping between vboxtoolinit and vbox. Because the init-system requires specific 
# commands like 'start' and 'stop' and we don't want to execute these commands literally, 
# vboxtoolinit maps these to the desired command in vboxtool.

start()
{
  # 'vboxtoolinit start' maps to 'vboxtool autostart'; when the host boots, all sessions in 
  # the config file /etc/vboxtool/machines.conf are started
  nohup $su_command "vboxtool autostart" > /dev/null
}

stop()
{
  # 'vboxtoolinit stop' maps to 'vboxtool save'; when the host halts, all running sessions 
  # are saved, instead of stopped.
  nohup $su_command "vboxtool save" > /dev/null
}

restart()
{
  stop
  start
}

# Some constants
config_file='/etc/vboxtool/vboxtool.conf'

# Retrieve settings from config file, just by executing the config file.
# Config file $config_file should look like this:
# vbox_user='<user name>'
if [ -f $config_file ]
then
  . $config_file
else
  echo "Error: $config_file does not exist. Exiting."
  exit 1
fi

if [ ! -n "$vbox_user" ]
then
  echo "Error: vbox_user not defined in $config_file. Exiting."
  exit 1  
fi

# Implementation of user control, execute several commands as another (predefined) user, 
# thus freeing the main script vboxtool from any user related issues.
su_command="su - $vbox_user -c"

#
# Check for a commandline option
#
case "$1" in
start)
  start
  ;;
stop)
  stop
  ;;
restart)
  restart
  ;;  
*)
  ;;  
esac

exit 0

```

---

### Post by markba on 2012-10-25
Here is the installation manual: [http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/readme.txt?view=markup](http://vboxtool.svn.sourceforge.net/viewvc/vboxtool/trunk/readme.txt?view=markup)

Basically:
> 
* Place the main script script/vboxtool in /usr/local/bin
* Make vboxtool executable: chmod +x /usr/local/bin/vboxtool
* _Place the init script script/vboxtoolinit in /etc/init.d_
* _Make vboxtoolinit executable: chmod +x /etc/init.d/vboxtoolinit_
* _Activate the init script vboxtoolinit: update-rc.d vboxtoolinit defaults 99 10_
* Create a folder /etc/vboxtool. In here, two config files have to be created, see configuration section below, type 'vboxtool help' for more instructions.


For your startup-problem, you should specifically look at the underlined lines. You should NOT use /etc/rc.local: it might work, but vboxtool is designed to work with the init-system.

P.S.
I'm the creator of vboxtool.

---

### Post by runegang on 2012-10-27
Thank you very much for your reply. 

I have tried to follow the instructions from the manual but with no results. I tried once more now. 

Anyway, I am going to try again with a clean install soon when I get a new and more powerful computer.

I will report back here then. 


And once again, thank you.

---

### Post by runegang on 2012-11-04
I have now got some new hardware and a fresh install of Ubuntu Server. Now the system boots fine and the virtual machine is also booting just fine. I do not understand why it did not work on the old hardware, and I am not sure if I have the time to investigate it any further. 

Anyhow. Thank you so much for replying to my questions and your assistance.

I would also thank you, markba, for creating such a nice tool. Keep up the good work ;-)


Best regards
Rune

---

