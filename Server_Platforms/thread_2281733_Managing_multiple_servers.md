---
title: "Managing multiple servers"
date: 2015-06-09
forum: Server Platforms
---

### Post by alfirdaous on 2015-06-09
Hello everybody,

Is there anyway that I can manage multiple servers on the same time, i.e: typing a command like:

```

apt-get update

```

type it one and it will be done on my 3 servers using Ubuntu.

Thanks in advance

---

### Post by Lars Noodén on 2015-06-09
If you use Konsole or some other fancier terminal you can send the commands to multiple tabs at the same time.  

Otherwise, as you start to scale up there would be Ansible or Puppet.

---

### Post by nerdtron on 2015-06-09
If you only have 3 servers then you can try to install terminator on your machine.

```
 sudo apt-get install terminator 
```

Now that terminator is installed, open it and open all your server, either 1 tab each or split the terminal screen (feature of terminator). Then you can broadcast command to all open terminal sessions on that window, (another feature of terminator)

---

### Post by alfirdaous on 2015-06-09
I think that opening the 3 servers on tabs, if one of them disconnected, it will still work or not?

---

### Post by nerdtron on 2015-06-09
Terminator is will not know if an ssh session is disconnected or not. If you choose broadcast to all (or to a group), then anything you type on one terminal will also be sent on all other terminals sessions. Whether it's the correct server or not, it your call.

---

### Post by alfirdaous on 2015-06-09
well, this is what I got:

```

# terminator

** (terminator:16522): WARNING **: Command line `dbus-launch --autolaunch=7705b2b191ded915585b7fc100000004 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
You need to run terminator in an X environment. Make sure $DISPLAY is properly set

```

---

### Post by TheFu on 2015-06-09
ClusterSSH (cssh) is how I started doing this. It opens an xterm on a set of remote systems and will type on all of them as you type inside a little box. Having 20 xterms up can be confusing.  Just sayin'.

Then I moved to a little script that ssh'ed into each machine and ran commands. This is what every lazy admin from 1985 - 2010 did. I still have the script and use it sometimes when I want the real output from the commands put into a central log file.

Then I moved to ansible that basically ssh's into each machine and runs commands, but also includes many, many, many other built in capabilities. You can use ansible to just run remote commands, but that isn't where the real power lies.
```
# Run a single command on selected remote hosts ("powered" is a list of systems in the ansible "hosts" file)
ansible -i ./hosts -a "cat /var/run/reboot-required" powered
```
You can have Ansible run multiple jobs concurrently on different systems.  If you want to see the power of Ansible: 
   [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)

DevOps is the term you want to google.  Ansible is the tool I chose after trying about 5 others.  Puppet, Chef, CFengine, Rexify, SaltStack, ... I don't know where you are in the world, but THIS Friday, there is free all-day Chef training at the SouthEast Linux Fest in Charlotte, NC.  There is also an UbuCon on Friday - so I'm torn on which to attend.

If you have more than 3 systems, it is time to look into having a local apt-cache - just to get the packages from the internet once.

---

### Post by alfirdaous on 2015-06-09
Thanks [**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685"), I am having just 3 servers, and begining to manage 3 of them

---

### Post by Lars Noodén on 2015-06-09
Terminator and Konsole only run in a graphical environment, usually on you desktop.  

If you are not using any graphics then you can manage a small number of connections in tmux by splitting panes *ctrl-b "*, starting an SSH session in each pane.  You can switch between the panes with *ctrl-b &#8593;* or *ctrl-b &#8595;*  Then synchronize the panes *ctrl-b :setw-synchronize-panes on*.

---

### Post by TheFu on 2015-06-09
> **alfirdaous said:**
> Thanks [**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685"), I am having just 3 servers, and begining to manage 3 of them

Just so there isn't any confusion. Ansible is easiest to use when ssh-keys have been pushed from the controller to the clients (i.e. servers).  I use my normal "desktop" as the ansible controller, but it could be any Linux machine on the network that has ssh keys on all the remote systems to be managed.

There is a 20 min Getting Started Ansible video at the ansible website. Don't worry - you don't have to learn much at all just to run update && dist-upgrade on all the systems every week. Actually, I think I posted that recipe on the forums last week. You will need to learn a minimal amount of YML (trivial file format) and you will need to create a file often named "hosts" which groups your servers so that you can do things on all of them together. Formally, this is call the "inventory." There are plenty of Ansible-for-beginners blog-articles.  Almost NONE will be about running weekly patches, so they get into the weeks quickly.  I think most people just set an environment variable or put a setting into the ~/.ansible.cfg for their inventory file and forget about it.

Just a quick example "hosts":
```
[algo]
ubudesk
zcs43 
redmine
zcs43
qbe

[romulus]
romulus

[owncloud]
owncloud


[powered]
hadar 
romulus 
vpn
spammer 
c720
xen41 
zcs43
lubuntu ansible_connection=local
rordesk 
rorlap
istar

```

All my systems are snowflakes.  If you were running 100 DB servers, you could use 
```
[dbs]
db[00-99]
```
Or 
```
[dbs]
172.29.1.[100-199]
```
[http://docs.ansible.com/intro_inventory.html](http://docs.ansible.com/intro_inventory.html) explains more options.

Ansible isn't perfect. But out of all the choices, it is by far the easiest to start and I haven't come across anything it didn't do that was needed. Out of the box, ansible is slower than the others, but there is much to be said for using existing ssh-based connections. Until I have 100+ systems to manage, don't think I'll switch from ssh connections - then there are other methods that ansible supports.  

Anyway - enjoy. Controlling all your systems from 1 command is empowering - almost god-like.

---

### Post by nerdtron on 2015-06-09
> **alfirdaous said:**
> well, this is what I got:

```

# terminator

** (terminator:16522): WARNING **: Command line `dbus-launch --autolaunch=7705b2b191ded915585b7fc100000004 --binary-syntax --close-stderr' exited with non-zero exit status 1: Autolaunch error: X11 initialization failed.\n
/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
You need to run terminator in an X environment. Make sure $DISPLAY is properly set

```

You should use terminator on your Ubuntu Desktop computer not on your server.

---

### Post by LHammonds on 2015-06-09
> **alfirdaous said:**
> Is there anyway that I can manage multiple servers on the same time, i.e: typing a command like:

```

apt-get update

```

type it one and it will be done on my 3 servers using Ubuntu.

I use crontab.  Not issue commands to be sent to others but to script and automate what needs to be done on all of my servers.

I write scripts to do data backups, partition backups, copying backup files to remote locations, synchronizing time to a central server, starting and logging apt-get upgrades, etc.

I then schedule them in crontab to run at various times.  I usually never have to login/touch my server's consoles.  If I do, I try to figure out how to script it and automate it if necessary or at least put it in a menu that I can pull up and execute on demand (or any of my server admins that might not be familiar with the system...e.g. restart services, reboot or shutdown)

Check my sig for links to my forum with examples of such scripts.

LHammonds

---

### Post by alfirdaous on 2015-06-10
I think I could use some bash scripts, if anybody can help with that

---

### Post by nerdtron on 2015-06-10
scripting? we can have a whole book for that. This one is easy to read: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)
What command would you like the script to do and what commands are going to put in it?

---

### Post by alfirdaous on 2015-06-11
I wrote this script, but I think is not running, I put it on the /etc/cron.daily/ directory:

```

#!/bin/sh
apt-get update && apt-get -y upgrade

```

Permissions are:
```

# ls -l /etc/cron.daily/backup_update 
-rwxr-xr-x 1 root root 47 Feb  6  2014 /etc/cron.daily/backup_update

```

---

### Post by TheFu on 2015-06-11
That script will work fine in an interactive root shell, but cron doesn't provide much, if any, environment. Which is why using the full path to all programs called is a best practice.

Plus, IMHO, I think automatic updates like that are a bad, bad, bad, bad, bad, idea. Things sometimes break and with THAT script, you don't have any way to determine why.

However, there is already a way to allow daily, automatic, patching, if you choose that. There's some script somewhere that can be enabled.  I don't use it, won't use it ever, having been burned too many times myself and being forced to dig a system out after the fact.  For the last decade, I've been running a script weekly to patch systems. The output from that script is logged - stdout AND stderr.  That why when something bad happens, and it will, there is hope to find the root cause.  Most of the time, it is just 1 program that fails, but once in a while, installing a new kernel will fail and make the system non-bootable.

But you can do as you like. Find the existing toggle to enable, automatic, daily, updates. I think it is somewhere in /etc/  Don't forget these do NOT reboot a system if that is needed. So this definitely isn't auto-pilot.

---

### Post by LHammonds on 2015-06-11
You definitely need to read some Bash scripting books for the basics.

You can find examples of my scripts on my forum (in my sig).  I do have a script for apt updates that just apply security updates and logs the results since I do not have the time to baby all the servers I run (wish I did).   I don't have my servers set to auto-reboot so that allows me to review the update logs before issuing a reboot.  As TheFu mentioned, I also have been left with an unbootable system (in the 10.04 days) and had to use rescue discs to fix boot process.  I usually reboot non-critical servers 1st just to test the water and save the most critical for last as an additional safety measure.

Here is a [direct link]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=210#p395") to my update script but please know it was built with my system in mind along with "standard" variables being pulled in from another file to make it all work but you'd need to find that info further up in the article.  I have every step documented but realize it is difficult to just put blinders on and read just a single section in the article.

LHammonds

---

### Post by alfirdaous on 2015-06-12
Thanks everybody for your usual support, appreciate it

---

