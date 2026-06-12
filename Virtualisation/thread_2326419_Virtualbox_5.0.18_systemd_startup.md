---
title: "Virtualbox 5.0.18 systemd startup"
date: 2016-05-31
forum: Virtualisation
---

### Post by JayWeb on 2016-05-31
Hi,

I have setup a headless virtualbox on ubuntu server 16.04 and everything is working fine except I am unable to get it to automatically start on boot using systemd.

The service file looks like this (/lib/systemd/system/vbox.service):
```

[Unit]
Description=VBox Virtual Machine Service


[Service]
Type=simple
User=administrator
ExecStart=/usr/bin/VBoxHeadless --startvm "Windows2012"
ExecStop=/usr/bin/VBoxManage controlvm "Windows2012" poweroff


[Install]
WantedBy=multi-user.target

```

When I run **systemctl status vbox.service** command after boot I get the following:
```

vbox.service - VBox Virtual Machine Service
   Loaded: loaded (/lib/systemd/system/vbox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Tue 2016-05-31 23:22:41 BST; 2min 54s ago
  Process: 1000 ExecStop=/usr/bin/VBoxManage controlvm Windows2012 poweroff (code=exited, status=1/FAILURE)
  Process: 961 ExecStart=/usr/bin/VBoxHeadless --startvm Windows2012 (code=exited, status=1/FAILURE)
 Main PID: 961 (code=exited, status=1/FAILURE)


May 31 23:22:41 server VBoxHeadless[961]:          You will not be able to start VMs until this problem is fixed.
May 31 23:22:41 server systemd[1]: vbox.service: Main process exited, code=exited, status=1/FAILURE
May 31 23:22:41 server VBoxManage[1000]: WARNING: The character device /dev/vboxdrv does not exist.
May 31 23:22:41 server VBoxManage[1000]:          Please install the virtualbox-dkms package and the appropriate
May 31 23:22:41 server VBoxManage[1000]:          headers, most likely linux-headers-generic.
May 31 23:22:41 server VBoxManage[1000]:          You will not be able to start VMs until this problem is fixed.
May 31 23:22:41 server VBoxManage[1000]: VBoxManage: error: Machine 'Windows2012' is not currently running
May 31 23:22:41 server systemd[1]: vbox.service: Control process exited, code=exited status=1
May 31 23:22:41 server systemd[1]: vbox.service: Unit entered failed state.
May 31 23:22:41 server systemd[1]: vbox.service: Failed with result 'exit-code'.

```

If I run the command **sudo systemctl start vbox** it starts up no problem and the status is fine.
```
administrator@server:~$ systemctl status vbox.service
&#9679; vbox.service - VBox Virtual Machine Service
   Loaded: loaded (/lib/systemd/system/vbox.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2016-05-31 23:17:52 BST; 31s ago
 Main PID: 4489 (VBoxHeadless)
   CGroup: /system.slice/vbox.service
           &#9500;&#9472;4489 /usr/lib/virtualbox/VBoxHeadless --startvm Windows2012
           &#9500;&#9472;4500 /usr/lib/virtualbox/VBoxXPCOMIPCD
           &#9492;&#9472;4505 /usr/lib/virtualbox/VBoxSVC --auto-shutdown


May 31 23:17:52 server systemd[1]: Started VBox Virtual Machine Service.
May 31 23:17:53 server VBoxHeadless[4489]: 31/05/2016 23:17:53 Listening for VNC connections on TCP port 3390
May 31 23:17:53 server VBoxHeadless[4489]: 31/05/2016 23:17:53 Listening for VNC connections on TCP6 port 5900

```

I have tried to install virtualbox-dkms and linux-headers-generic, but they are already installed. I assume the problem is something to do with **WARNING: The character device /dev/vboxdrv does not exist **but I am not sure how to fix it, since it works fine when I run it manually.

I am quite new to linux, so I might be missing something very obvious.. Can someone tell me how I should proceed to try and fix this?

Thanks

---

### Post by MAFoElffen on 2016-06-01
Iknow our wiki page says service files go into directory /lib/systemd/system/ ... But, what is the usual convention "explained" 
- - custom service files should be placed in /etc/systemd/system/- the path for package-installed service files is /usr/lib/systemd/system/
- the path for system service files is /lib/systemd/system/

So by that convention, tht custom service file should be located in /etc/systemd/system/

Say this file (mod'ed frpm your's) is located there with a file name vbox.service:
```

# vbox.service
[Unit]
Description=VBox Headless Virtual Machine Service
## Optional, but note this:
# Requires=systemd-modules-load.service
# After=systemd-modules-load.service



[Service]
## This was the original setting, which only worked for the OP on CLI:
#Type=simple
## The following chaange let it start at boot:
Type=idle
 User=administrator
Group=vboxusers
ExecStart=/usr/bin/VBoxHeadless --startvm "Windows2012"
## next could also be turned off as savestate
ExecStop=/usr/bin/VBoxManage controlvm "Windows2012" poweroff


[Install]
WantedBy=multi-user.target

```
Where is the config file for the VM Windows2012? And is the user a member of the Linux Group vboxusers?

Lastly-- I saw you manually start it as a SystemV service. Before now, if you tried to start it as a service at boot time, you had to add it to the bootup lineup with the rc utils. Now is also true in Systemd. So... 

Did you enable it? Similar to this:
```

sudo systemctl enable vm_name.service

```

---

### Post by JayWeb on 2016-06-02
Thanks for the reply [COLOR=#000000]MAFoElffen.

**vbox.service file**
I used your sample of the vbox.service and moved the file from [/COLOR][COLOR=#000000]/lib/systemd/system/vbox.service to[/COLOR][COLOR=#000000] /etc/systemd/system/[/COLOR][COLOR=#000000]vbox.service

[/COLOR][COLOR=#000000]**Where is the config file for the VM Windows2012?**
The structure is currently like this:
/home/administrator/Windows2012.vdi
[/COLOR][COLOR=#000000]/home/administrator/VirtualBox VMs/Windows2012/Windows2012.vbox[/COLOR][COLOR=#000000]

[B]Is the user a member of the Linux Group vboxusers?
[/B][/COLOR]```
administrator@server:~$ getent group vboxusers
vboxusers:x:118:administrator
```
**sudo systemctl enable vm_name.service**
Yes, I had previously done this, although to make sure I disabled it and enabled it again. It said the symlink was created successfully.


I restarted Ubuntu after these changes, but I still get the same error.
```
administrator@server:~$ systemctl status vbox.service
â vbox.service - VBox Headless Virtual Machine Service
   Loaded: loaded (/etc/systemd/system/vbox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2016-06-02 22:30:25 BST; 21min ago
  Process: 999 ExecStop=/usr/bin/VBoxManage controlvm Windows2012 poweroff (code=exited, status=1/FAILURE)
  Process: 947 ExecStart=/usr/bin/VBoxHeadless --startvm Windows2012 (code=exited, status=1/FAILURE)
 Main PID: 947 (code=exited, status=1/FAILURE)


Jun 02 22:30:24 server VBoxHeadless[947]:          You will not be able to start VMs until this problem is fixed.
Jun 02 22:30:24 server systemd[1]: vbox.service: Main process exited, code=exited, status=1/FAILURE
Jun 02 22:30:24 server VBoxManage[999]: WARNING: The character device /dev/vboxdrv does not exist.
Jun 02 22:30:24 server VBoxManage[999]:          Please install the virtualbox-dkms package and the appropriate
Jun 02 22:30:24 server VBoxManage[999]:          headers, most likely linux-headers-generic.
Jun 02 22:30:24 server VBoxManage[999]:          You will not be able to start VMs until this problem is fixed.
Jun 02 22:30:25 server VBoxManage[999]: VBoxManage: error: Machine 'Windows2012' is not currently running
Jun 02 22:30:25 server systemd[1]: vbox.service: Control process exited, code=exited status=1
Jun 02 22:30:25 server systemd[1]: vbox.service: Unit entered failed state.
Jun 02 22:30:25 server systemd[1]: vbox.service: Failed with result 'exit-code'.

```

---

### Post by MAFoElffen on 2016-06-03
You know that my commands where genralized right?
```

sudo systemctl vbox.service enable

```
So let's say you did that, still got those errors ... and if you ssh in while it is running, add that users credentials and do it manually
```

sudo systemctl vbox.service start
sudo systemctl vbox.service status

```
What does it do?

---

### Post by JayWeb on 2016-06-03
If I do that it works.

```

â vbox.service - VBox Headless Virtual Machine Service
   Loaded: loaded (/etc/systemd/system/vbox.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2016-06-03 20:38:17 BST; 8s ago
 Main PID: 1637 (VBoxHeadless)
    Tasks: 35
   Memory: 43.3M
      CPU: 5.809s
   CGroup: /system.slice/vbox.service
           ââ1637 /usr/lib/virtualbox/VBoxHeadless --startvm Windows2012
           ââ1648 /usr/lib/virtualbox/VBoxXPCOMIPCD
           ââ1653 /usr/lib/virtualbox/VBoxSVC --auto-shutdown


Jun 03 20:38:17 server systemd[1]: Started VBox Headless Virtual Machine Service.
Jun 03 20:38:18 server VBoxHeadless[1637]: 03/06/2016 20:38:18 Listening for VNC connections on TCP port 3390
Jun 03 20:38:18 server VBoxHeadless[1637]: 03/06/2016 20:38:18 Listening for VNC connections on TCP6 port 5900

```

But when I reboot, it doesn't.
```
 
â vbox.service - VBox Headless Virtual Machine Service
   Loaded: loaded (/etc/systemd/system/vbox.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2016-06-03 20:40:54 BST; 18s ago
  Process: 998 ExecStop=/usr/bin/VBoxManage controlvm Windows2012 poweroff (code=exited, status=1/FAILURE)
  Process: 938 ExecStart=/usr/bin/VBoxHeadless --startvm Windows2012 (code=exited, status=1/FAILURE)
 Main PID: 938 (code=exited, status=1/FAILURE)


Jun 03 20:40:53 server VBoxHeadless[938]:          You will not be able to start VMs until this problem is fixed.
Jun 03 20:40:53 server systemd[1]: vbox.service: Main process exited, code=exited, status=1/FAILURE
Jun 03 20:40:53 server VBoxManage[998]: WARNING: The character device /dev/vboxdrv does not exist.
Jun 03 20:40:53 server VBoxManage[998]:          Please install the virtualbox-dkms package and the appropriate
Jun 03 20:40:53 server VBoxManage[998]:          headers, most likely linux-headers-generic.
Jun 03 20:40:53 server VBoxManage[998]:          You will not be able to start VMs until this problem is fixed.
Jun 03 20:40:54 server VBoxManage[998]: VBoxManage: error: Machine 'Windows2012' is not currently running
Jun 03 20:40:54 server systemd[1]: vbox.service: Control process exited, code=exited status=1
Jun 03 20:40:54 server systemd[1]: vbox.service: Unit entered failed state.
Jun 03 20:40:54 server systemd[1]: vbox.service: Failed with result 'exit-code'.

```

---

### Post by JayWeb on 2016-06-03
I just had a look at dmesg and found the following (marked in red):

```

[   33.199319] capability: warning: `VBoxHeadless' uses 32-bit capabilities (legacy support in use)
[COLOR=#ff0000][   34.849423] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel[/COLOR]
[   34.855100] vboxdrv: Found 6 processor cores
[   34.873741] vboxdrv: TSC mode is Invariant, tentative frequency 3515524573 Hz
[   34.873744] vboxdrv: Successfully loaded version 5.0.18_Ubuntu (interface 0x00240000)
[   34.879721] VBoxNetFlt: Successfully started.
[   34.888920] VBoxNetAdp: Successfully started.
[   34.894876] VBoxPciLinuxInit
[COLOR=#ff0000][   34.897609] vboxpci: IOMMU not found (not registered)[/COLOR]

```

I am not sure what they mean but thought they could be something important?

---

### Post by MAFoElffen on 2016-06-04
Previous post (???) If it starts from the commandline with those  commands then it's successfully using the service file, as if it would on startup. That does not make sense. The startup message showed it was located in the correct didrectory for a custom service file, so I assume it is startign after the system services (custom's are started later in the process). The only way to really confirm that would be to either look at a bootlog jpg (are you familiar with bootlog?) or to go through the syslog to verify that...

And your next post- The first error, I am not worried about at the moment. I get a tainting error with proprietary NVidia modules, so am used to ignoring tainting messages. Just to be sure, I'll check my logs tomorrow and search for that one.

Now the second message does have my interest. You have virtualization turn on in the BIOS correct? Could you confirm that please?

---

### Post by JayWeb on 2016-06-04
I got it working!

I changed Type to idle instead of simple in vbox.service and it works!

Thanks for all your help with this.

---

### Post by MAFoElffen on 2016-06-04
Great! Updated the service file in post #2 to reflect what worked for you (so that it might help others seeing that later).

---

