---
title: "How do I get unprivileged containers to start on boot?"
date: 2016-04-04
forum: Virtualisation
---

### Post by Light Speed on 2016-04-04
I am having trouble getting unprivileged containers to start on boot of the host.
From lxc-ls -f I confirmed autostart is YES and they are in the onboot group.

```
cat /etc/issue
Ubuntu 14.04.4 LTS \n \l
```

```
cat /etc/default/lxc |grep LXC_AUTO=
LXC_AUTO="true"
```

 ```
lxc-ls -f
NAME            STATE    IPV4  IPV6  AUTOSTART     
-------------------------------------------------      
ops-001-dc4     STOPPED  -     -     YES (onboot) 
``` 


```
cat .local/share/lxc/ops-001-dc4/config 
# Template used to create this container: /usr/share/lxc/templates/lxc-download
# Parameters passed to the template:
# For additional config options, please look at lxc.container.conf(5)


# Distribution configuration
lxc.include = /usr/share/lxc/config/centos.common.conf
lxc.include = /usr/share/lxc/config/centos.userns.conf
lxc.arch = x86_64


# Container specific configuration
lxc.id_map = u 0 100000 65536
lxc.id_map = g 0 100000 65536
lxc.rootfs = /home/velvet/.local/share/lxc/ops-001-dc4/rootfs
lxc.utsname = ops-001-dc4
lxc.group = onboot
lxc.start.auto = 1


# Network configuration
lxc.network.type = veth
lxc.network.flags = up
lxc.network.link = virbr0
lxc.network.hwaddr = 00:16:3e:24:21:58
lxc.network.ipv4 = 10.24.7.201/21
lxc.network.ipv4.gateway = 10.24.0.1
```


The container seems fine otherwise. Wanting to move to using unprivileged containers for security so they are not running as root ID.


Is this the correct place for assistance with an issue like this?

---

### Post by MAFoElffen on 2016-04-05
Yes. This is the correct place.

3 things... 

(1) Please revisit your first post and select Edit >  Advanced Edit > Hightlight your output > Select the "#" code tag icon to surround your posted output within code tags. This makes it easier to read, takes less space on a page... and keeps the mod's off our backs (forum policy).

(2 & 3) Please post your full /etc/default/lxc and /etc/init/lxc-instance.conf files, using code tags.

I'm heading out the door for my day, and will look at this when I get back tonight. The LXC autoboot flag, when set, looks through all container conf files and looks to see which conf's have setting set to autostart. I'm thinking since your containers are on non-provisioned, and not just in the default root location, that you need to tell LXC the path to the local user's path location, where those confs are (to find them)... but need to see those 2 files of yours to confirm what needs to be changed to add that local path.
```

# default search path to .conf files:
/var/lib/lxc/<container_name>/config

# path to your conf files:
/home/<your_user_name>/.local/share/lxc/<containername>/config


```

1 question... Usually you set a delay for when to start the next container and a start order... 
```

# Autostart
lxc.start.auto = 1      # set to true
lxc.start.delay = 5     # wait 5
lxc.start.order = 100   # order to start

```
Are you just starting a single container at boot?

EDIT-- But just thought of something. Logically, "on boot or reboot," LXC autostart starts containers as root. on "non-provisioned" you are a local *user*. Do you want to keep it started by a local user?

---

### Post by Light Speed on 2016-04-05
Thank you for taking the time!

Original post now has code wrapped :)

Here is the requested data:

/etc/default/lxc
```
# MIRROR to be used by ubuntu template at container creation:
# Leaving it undefined is fine
#MIRROR="http://archive.ubuntu.com/ubuntu"
# or 
#MIRROR="http://<host-ip-addr>:3142/archive.ubuntu.com/ubuntu"


# LXC_AUTO - whether or not to start containers symlinked under
# /etc/lxc/auto
LXC_AUTO="true"


USE_LXC_BRIDGE="false"  # overridden in lxc-net
[ -f /etc/default/lxc-net ] && . /etc/default/lxc-net


LXC_SHUTDOWN_TIMEOUT=120

```


[COLOR=#000000]/etc/init/lxc-instance.conf[/COLOR]
```
description "lxc instance"
author "Christian Kampka <chris@emerge-life.de>"


stop on stopping lxc


# wait for 120 seconds for container to shutdown before killing it
kill timeout 120


# send SIGPWR to container to trigger a shutdown (see lxc-shutdown(1))
kill signal SIGPWR




instance $NAME
usage "NAME=name of LXC instance"


pre-start script
    lxc-wait -s RUNNING -n $NAME -t 0 && { stop; exit 0; } || true
end script


script
    exec lxc-start -n $NAME
end script

```


I see that in /etc/default/lxc it is looking in /etc/lxc/auto for symlinks but I do not have an auto directory.

```
ls -al /etc/lxc
total 16
drwxr-xr-x  2 root root 4096 Mar 25 14:27 **.**
drwxr-xr-x 97 root root 4096 Apr  4 15:56 **..**
-rw-r--r--  1 root root  112 Mar 16 10:28 default.conf
-rw-r--r--  1 root root   50 Mar 25 14:27 lxc-usernet

```

---

### Post by Light Speed on 2016-04-05
Ah and yes I would like to keep these unprivileged. Does the user that created the containers need to be the user that starts them for them to retain unprivileged status?

---

### Post by MAFoElffen on 2016-04-05
Checking in... I have a few moments, but not reay top dive into it yet (not free yet)... But have time to answer your two questions.

On your post #3:
> 
I see that in /etc/default/lxc it is looking in /etc/lxc/auto for symlinks but I do not have an auto directory.

Those symlinks are not required after v14.04 LTS and newer. LXC now looks in /var/lib/lxc/<container_name>/config at the indiviudual conf files.

On your last comment in post #4:
> 
Ah and yes I would like to keep these unprivileged. 

Does the user that created the containers need to be the user that starts them for them to retain unprivileged status?

Yes. Otherwise it is then it is started by root instead of you... Will get back to this later, when I get free.

---

### Post by MAFoElffen on 2016-04-05
Off now and home.

Could you please verify that while you are logged in, that you can start the containers via:
```

sudo lxc-autostart
sudo lxc-ls --fancy

```
If that works and you see them running, then while using the rights and privileges of the user of the non-privileged containers... 

If not that person, use
```

sudo -S -u Other_User

```
to use that other users rights, privileges, and their environment settings...

then run
```

crontab -e

```
as the user, to add this line
```

@reboot lxc-autostart

```

An alternative way to do that would be to edit the .configrc file and add the command as you would if you were typing it. The draw back to that method is that you would have to enter your password to confirm that each time you logged in (for loggin credentials, then again to execute this). That is not as elegant a solution as in the previous paragraph.

To test, on a fresh start or reboot, after login, check to see if they are running...

---

### Post by Light Speed on 2016-04-12
MAFoElffen - Thanks for your response and sorry for the delay. Been busy with other tasks.

I found that when I manually run the command that just lxc-autostart does nothing. I have to declare the group and I have confirmed I am able to manually start all containers in the onboot group with this command as my user:
```
lxc-autostart -g onboot
```

I am not able to get an @reboot  entry in my user crontab to work to start containers on reboot.

The command that does work manually does not work in users crontab:
```
@reboot lxc-autostart -g onboot
```

I thought it might be a path issue so  have also tried the following variations with no success:

I have tried declaring PATH:
```

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
@reboot lxc-autostart -g onboot
```

I have tried with an absolute path to lxc-autostart:
```
@reboot /usr/bin/lxc-autostart -g onboot
```

I have tried putting the command in root's crontab directing it to be run as the user:
```
@reboot user-name-here lxc-autostart -g onboot
```

Here you can where lxc-autostart should be found and is of course when running manually:
```
which lxc-autostart
/usr/bin/lxc-autostart
```

I then tried moving the lxc-autostart command to a script and run that script from users crontab (and then tried from roots crontab). I added a line in the script to print the date and time the script was run to a file to ensure the script was getting run on reboot which it was. I am about at the point were I say screw it and forget about trying to use unprivileged containers and just do everything as root but I would rather not do that.

Is there anything that obviously stands out that I am missing?

---

### Post by teemuko-koivisto on 2016-08-19
@reboot is run when the cron.service starts up. That may be too early before your network intefaces are up or your container may depend on some other stuff that is not yet available.

A dirty workaround is to add a delay before autostart is run:

```
@reboot sleep 30 ; lxc-autostart
```

---

