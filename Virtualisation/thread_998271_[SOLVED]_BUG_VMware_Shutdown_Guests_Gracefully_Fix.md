---
title: "[SOLVED] BUG VMware Shutdown Guests Gracefully Fixed"
date: 2008-11-30
forum: Virtualisation
---

### Post by MrFSL on 2008-11-30
**[SIZE="4"]VMware Server:** Version 2.0.0 Build 122956[/SIZE]
**[SIZE="4"]Ubuntu Server:** 8.04 (Hardy)[/SIZE]

**[SIZE="4"]ISSUE:**[/SIZE]
After editing Virtual Machines Startup / Shutdown Settings, Ubuntu Guests do startup but do not shutdown gracefully.

**[SIZE="4"]FIX:**[/SIZE]
1) You must install VMware Tools on the Guest. 


2) According to the VMware Server documentation and help file the following script is executed during our graceful poweroff
```
/etc/vmware-tools/poweroff-vm-default
```


If we look at the contents we see that this file is not enough to power off our virtual:
> echo `date` ": Executing '$0'"

scriptsdir="`dirname $0`/scripts/`basename $0`.d"
if [ -d "$scriptsdir" ]; then
    for scriptfile in "$scriptsdir"/*; do
	[ -x "$scriptfile" ] && "$scriptfile" poweroff-vm
    done
fi


In fact if the folder */etc/vmwre-tools/scripts/poweroff-vm-default.d* does not exist then nothing is really executed at all. We need to create this folder and put a shutdown script inside it.

```
# Create the directories
sudo mkdir /etc/vmware-tools/scripts
sudo mkdir /etc/vmware-tools/scripts/poweroff-vm-default.d

# Create the script
sudo su
echo "halt" > /etc/vmware-tools/scripts/poweroff-vm-default.d/halt.sh
chmod 550 /etc/vmware-tools/scripts/poweroff-vm-default.d/halt.sh
```


3) You have to make sure that root has an "Administrator" role under permissions in the web interface.

This is the real bug. During initial setup of the server I was asked what user I wanted as the Administrator. Since I use sudo (Ubuntu default) my root user has no password. Therefore I set my user as the Administrator. This is fine but **you have to add root to the permissions with its own administrator role. **

_This is why:_
When the host OS is shutting down and *"/etc/init.d/vmware stop"* is called it uses ***"vmware-vimsh"*** to automate shutdown. 
Specifically:
```
# In my case $authdPort = 902
vmware-vimsh" -r -n -e '"hostsvc/connect localhost '$authdPort'; hostsvc/login; 'hostsvc/autostartmanager/autostop'"'
```

This is executed as root, and if root does not have an administrative role in vmware it errors out with: 
> Failed to login: vim.fault.NoPermission


4) Once all the above is done we can execute from the host OS:
```
sudo /etc/init.d/vmware stop
sudo /etc/init.d/vmware start
```

Then from the Guest OS we can check that our script was executed using:
```
tail /var/log/vmware-tools-guestd
```


A bug report has already been filed by myself with VMware. Hopefully this helps some of you.


MrFSL

---

### Post by orever on 2009-06-17
Thanks for this post, it really helped me.  However, the scripting you mention is redundant, as the poweroff script is run before the system is sent a shutdown message.  Once the shutdown message is sent, the system will shut down normally as if you had pressed the power button on a real server.

The real key is giving 'root' Administrative access inside of the VMware console.  Once you do that, you don't need any scripting and the system will shutdown correctly.

---

