---
title: "Start Virtualbox VM automatically"
date: 2015-06-21
forum: Virtualisation
---

### Post by ktz84 on 2015-06-21
Hi,

I'm going away for 8 days and need to ensure that if my computer reboots that Virtualbox restarts one of my VMs as it runs my OwnCloud server. The host is Ubuntu 15.04 and I need it start a vm running Ubuntu Server 14.04.

My initial thought was to use automatic login and then set the screen to lock automatically. As one of my startup applications I have my VM supposedly start at log in however that never starts. I got the command from right clicking on the VM on virtualbox and doing send to desktop then copying the start command into the command line in startup applications. The command looks like this:

```
/usr/lib/virtualbox/VirtualBox --comment "Ubuntu Server 14.04" --startvm "9a2cf95e-0380-4283-a9b6-242xxxxxx"
```

If I run this code in a terminal it runs the VM so there isn't an issue with the command itself.

Also the screen lock doesn't work probably because it's now outdated. The command for it is:

```
gnome-screensaver-command -l
```

All that happens when the computer starts is the computer logs in and throws up a dialog box asking for the password to unlock the login keyring. I can open applications such as chrome and run them and use the computer mostly for anything that doesn't require a password.

So all in all not at all a successful attempt.

Am I even going about this the right way and if so how do I resolve my existing issues and if I'm not then what is the best way to approach this.

---

### Post by ktz84 on 2015-06-21
Ok just noticed a problem. Lurking the background I never noticed but the VM did try to run however it couldn't as it was throwing this message:

```
Kernel driver not installed (rc=-1908)
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]


as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.
```

I do have dkms installed and I do not get this message if I try to run the vm from the command line using the command in startup applications or normally through the Virtualbox GUI so no idea why it is whining when it runs from the startup applications.

Edit:

Just noticed the bit about permissions. I wonder is it because the keyring isn't unlocked therefore it can't run. How do I go about getting rid of that without setting no password for my username which I'm not willing to do?

---

### Post by TheFu on 2015-06-21
Look at **VboxManage**.
You need a headless startup - probably easiest to add it to /etc/rc.local - be certain to change the userid with su before running it.  Also, if your HOME is encrypted, I don't think this will work.

In short - you cannot run GUI applications at boot, only at login.
Think of your system as a true server and run services/daemons the "server way" - without a GUI.

[https://www.virtualbox.org/manual/ch08.html#vboxmanage-startvm](https://www.virtualbox.org/manual/ch08.html#vboxmanage-startvm)

---

### Post by ktz84 on 2015-06-21
Oh that looks complex. I'll see if I can find an ubuntu specific guide now that I know I'm looking a headless setup.

---

### Post by TheFu on 2015-06-21
> **ktz84 said:**
> Oh that looks complex. I'll see if I can find an ubuntu specific guide now that I know I'm looking a headless setup.

Really?  1 command is complex?
[https://www.virtualbox.org/manual/ch07.html#vboxheadless](https://www.virtualbox.org/manual/ch07.html#vboxheadless)
$ VBoxManage startvm "VM name" --type headless

So - to put something like this into rc.local .... 

```
su -l {your-user-id} -c /full/path/to/VBoxManage startvm "VM name" --type headless &

```
I didn't test it. You'll need to fill in the correct stuff.

If you want to have a clean shutdown/startup - really need to create a normal init.d/ script like the 50 other examples on your box in /etc/init.d/ show.  This stuff is only hard until you do it once. Then it is trivial.

---

### Post by ktz84 on 2015-06-21
Thanks TheFu. I think I just seen the totality of the instructions and thought yikes when it really was only part that was relevant :D Unfortunately it doesn't start.

My rc.local looks like this:

```
#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


su -l myusername -c /full/path/to/VBoxManage startvm "9a2cf95e-0380-4283-a9b6-242a17022954" --type headless &


exit 0
```

The VM is stored on "/media/myusername/VM/Virtualbox VMs" and then under appropriate folder for each VM I run. The permissions on the files in the Ubuntu Server 14.04 folder are:

for the .vdi file are: myusername:myusername
however for .vbox & .vbox-prev they are: myusername:anothergroupname

All the files have read/write permissions only on the owner so I don't think the anothergroupname above will cause any issue as there are no group permissions anyway.

---

### Post by TheFu on 2015-06-21
If you didn't correct the username, the path and use the "name" for the VM, not the UUID - it won't work.

---

### Post by ktz84 on 2015-06-21
```

```Hi I do have the correct username in rc.local. And the name is my vm name also. I tried the UUID as the startvm will work with it also in the terminal so I just tried it in case that would make a difference. It didn't. I now have vm name back in rc.local and tried again and still not working.

Once I'm logged into Unity and run a terminal I can run:

```
/usr/bin/vboxmanage startvm "Ubuntu Server 14.04"
```

and it starts my VM

I then confirmed the headless runs too by running:

 ```
/usr/bin/vboxmanage startvm "Ubuntu Server 14.04" --type headless &
```

that also runs.

Is there anything I need to do in order for it to use rc.local or is that automatic?

---

### Post by TheFu on 2015-06-21
It needs to run under your userid, with YOUR environment. Using any other userid will not work.  That is what the *su -l userid* is supposed to handle. Perhaps I didn't RTFM correctly and missed the needed option for su? Please check my work.

---

### Post by ktz84 on 2015-06-21
I renamed my VM in the end as I believed the spaces were the problem however that made no difference. In any case I was beginning to wonder if rc.local was being looked at all so I googled that and found that running:

```
systemctl status rc-local.service
```

would show whether it was running or not.

At last I got some useful information. It was running but at least I got error messages. This is the output of that:

```
Jun 21 20:08:43 giro su[1045]: + ??? root:eamonnJun 21 20:08:43 giro su[1045]: pam_unix(su:session): session opened for user eamonn by (uid=0)
Jun 21 20:08:43 giro rc.local[1044]: WARNING: The character device /dev/vboxdrv does not exist.
Jun 21 20:08:43 giro rc.local[1044]: Please install the virtualbox-dkms package and the appropriate
Jun 21 20:08:43 giro rc.local[1044]: headers, most likely linux-headers-generic.
Jun 21 20:08:43 giro rc.local[1044]: You will not be able to start VMs until this problem is fixed.
Jun 21 20:08:44 giro rc.local[1044]: VBoxManage: error: Could not find a registered machine named 'UbuntuServer14.04'
Jun 21 20:08:44 giro rc.local[1044]: VBoxManage: error: Details: code VBOX_E_OBJECT_NOT_FOUND (0x80bb0001), component VirtualBox, interface IVirtualBox, callee nsISupports
Jun 21 20:08:44 giro rc.local[1044]: VBoxManage: error: Context: "FindMachine(Bstr(pszVM).raw(), machine.asOutParam())" at line 575 of file VBoxManageMisc.cpp
Jun 21 20:08:44 giro systemd[1]: rc-local.service: main process exited, code=exited, status=1/FAILURE

```

So it thinks that virtualbox-dkms is not installed however it is and apt is saying its at the newest version. Same for linux-headers-generic. The VM runs under that name if I run in a terminal when I'm logged into Unity. So I'm stumped.

---

### Post by ktz84 on 2015-06-21
OK moved to Plan B. Teamviewer and remotely logging into the host GUI to start it through the VirtualBox Manager GUI. Would still like to resolve this however at least I have something workable.

---

### Post by ajgreeny on 2015-06-21
Just recently, at evey kernel update I get that missing vboxdrv error and have to run the ```
sudo /etc/init.d/vboxdrv setup
``` command, even though I have dkms installed on the host machine.  This has only started with the past couple of versions of VBox, so I assume it has something to do with these recent versions.

I haven't bothered to look for any solution to this as it is frankly quicker just to run the setup command as shown rather than spend time searching, but I run VBox only on a local machine, and not as a server, so it is not important to me; I'm just looking a development versions of *ubuntu OSs for the sake of interest only.

---

### Post by ktz84 on 2015-06-21
I've seen that message too and in the past I was able to run the suggested command however when I run it now I'm getting:

```
sudo: /etc/init.d/vboxdrv: command not found
```

So not sure what's going on now.

---

### Post by TheFu on 2015-06-21
>  It needs to run under your userid, with YOUR environment. Using any other userid will not work. That is what the su -l userid is supposed to handle. Perhaps I didn't RTFM correctly and missed the needed option for su? Please check my work. 
**It needs to run under your userid, with YOUR environment.**  [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)  rc.local doesn't have much environment - for vboxmanage to do what you want with the correct userid AND with the correct environment - that needs to be set BEFORE calling the program.

To see the differences in environments:

a) env > ~/normal.env
b) put env > /home/the-userid-home/rc-local.env into the /etc/rc.local file and reboot.

Compare the to files - I'd use meld for this  ---- **meld ~/normal.env ~/rc-local.env**, but diff and sdiff work too.
See all those differences?  Anything jump out at missing that would impact virtualbox?  Is HOME set?  That's a big one.

---

### Post by sergio38 on 2016-04-22
What I add in my user's crontab is the following:
```
@reboot /usr/bin/VBoxManage startvm "NameOfTheVM" --type headless &
```

---

