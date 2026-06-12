---
title: "Backup of vmware workstation VMs"
date: 2011-03-09
forum: Virtualisation
---

### Post by garethsimpsonuk on 2011-03-09
Hi all,

I'm looking for a way to backup my Virtual Machines using Vmware Workstation. I understand that there can be problems backing up a VM while it is running but shutting it down briefly isnt a problem.

I'm hoping that this whole process can be automated / scripted.

Any ideas?

Thanks

---

### Post by aeiah on 2011-03-09
are the virtual machines just vmdk images (or whatever the extension is)? you should be able to just copy the virtual hard drives and virtual machine files. what does your vm directory look like and what's in your vmware settings directory? maybe there's something in the settings that could do with being copied.

ive only backed up/restored virtualbox and kvm virtual machines. i cant imagine vmware is much different though. have you followed any guides?

---

### Post by new_tolinux on 2011-03-09
As said, most of it is in the folder where VMWare has its disks.
Since I've changed that folder a long time ago, I don't know which one is the default folder, but that should not be to hard to find out (just look where the datastore is located, for example in the vmware webinterface).

It stores at least so much, that when I copied the whole folder to replace the machine it was running on, and just copied it back on the new machine, it ran out-of-the-box.
Although I did change the datastore-location to the place where my virtual machines were stored before starting the first one ;)

---

### Post by garethsimpsonuk on 2011-03-09
Thanks for the replies. Yes I know where the folder is and it contains the vmdks and the vmx (config files). 

My question is more how to automate this process. 

1. How to shut the VMs down using scripts
2. Take a copy of the whole vmware dir (subfolders contain VMs)
3. Dump into a separate folder which can be backed up using our offsite backup solution (crashplan)

Oh and this is vmware workstation so it has a gtk GUI not a web interface. 

Any help is appreciated

---

### Post by new_tolinux on 2011-03-09
1. No idea (at least not yet, if I have a little more spare time I will look in it tonight)
2. should not be that hard, something like "cp -R /path/to/vmware/ /path/to/backup/"
3. should be solved with 2.

---

### Post by garethsimpsonuk on 2011-03-10
bump

---

### Post by new_tolinux on 2011-03-10
> **garethsimpsonuk said:**
> bump
[http://www.vmware.com/support/ws5/doc/ws_learning_cli_vmrun.html](http://www.vmware.com/support/ws5/doc/ws_learning_cli_vmrun.html)

---

### Post by garethsimpsonuk on 2011-03-10
Thanks for the link. I'm working on shutting down safely and starting VMs from the cli and it seems to be working.

In the manual is says to add the "soft" option to safely shutdown the guest. I have done this but the VM seems to shut down very quickly and I'm not convinced that it is shutting down safely (especially as I haven't specified a un and pw).

So the question is, where in Ubuntu will it tell me if the last shutdown was a soft shutdown or a power out?

Thanks

---

### Post by bodhi.zazen on 2011-03-10
*Thread moved to **Virtualization**.*

---

### Post by new_tolinux on 2011-03-10
> **garethsimpsonuk said:**
> So the question is, where in Ubuntu will it tell me if the last shutdown was a soft shutdown or a power out?
Probably in the logfiles.....

But I'm everything but a VMware expert, I have it up and running here, and I know enough to have it working my way, but that's more or less where it ends.

---

### Post by garethsimpsonuk on 2011-03-10
ok thanks new_tolinux

Does anyone else know of a way to check that the system was shut down safely?

---

### Post by bodhi.zazen on 2011-03-10
> **garethsimpsonuk said:**
> ok thanks new_tolinux

Does anyone else know of a way to check that the system was shut down safely?

Unless VMWare gives you some indication, only way would be to boot it.

If there are problems it will try to fix them.

---

### Post by new_tolinux on 2011-03-10
> **garethsimpsonuk said:**
> ok thanks new_tolinux

Does anyone else know of a way to check that the system was shut down safely?
I know one way for some server-OS-es...
Since shutting down gives a signal like the power-off button is pushed, some Windows-Server-OS-es ask you for a shutdown-reason the next time an administrator is logging in.

---

### Post by garethsimpsonuk on 2011-03-10
So you're saying that I should just hope that any errors caused will be fixed? Thanks but I think I prefer to not cause errors in the first place!

It's not the only way the event is logged in syslog or somewhere I just haven't figured out a way to interpret it yet.

Thanks

---

### Post by garethsimpsonuk on 2011-03-10
@new_tolinux yes that was going to be my next option. Any windows os displays a message if shutdown incorrectly asking if you wish to start in safe mode so I might try that.

Seems to be a long winded solution though! Oh well, adapt and overcome

---

### Post by new_tolinux on 2011-03-10
> **garethsimpsonuk said:**
> So you're saying that I should just hope that any errors caused will be fixed? Thanks but I think I prefer to not cause errors in the first place!
No, that's not what I'm saying.
Windows server needs a reason why it is/was shut down. That reason isn't supplied when you turn off the machine by pushing the on/off-button shortly, although the system does shut down properly.
Only when it's not shut down properly, it asks about safe mode (etc).

But thinking of it, that won't be much help either, since you're probably always too late to see the question which let you boot in safe mode, and will always see the question why the system was shut down and you also need to login for that.

All toghether, I guess that there is no "nice" way to see what happened.

---

### Post by garethsimpsonuk on 2011-03-10
That quote was directed at bodhi.zazen not you.

The question waits for like 30 seconds which is plenty of time. If not, it will be in the log viewer (which I know how to read in Windows!).

The nice way is to check the log files, it's just that no-one who knows how has posted yet!

---

### Post by bodhi.zazen on 2011-03-10
> **garethsimpsonuk said:**
> @new_tolinux yes that was going to be my next option. Any windows os displays a message if shutdown incorrectly asking if you wish to start in safe mode so I might try that.

Seems to be a long winded solution though! Oh well, adapt and overcome

Some errors will be logged, some will not, such is the nature of any OS. On top of all that, you are adding a layer of complexity by running virtualization.

If VMWare Workstation does not give you this information you are unlikely to find anything on the host Logs, although you can look at the VMWare logs if you wish. I am not familiar enough with VMWare workstation to know where to look.

You can try to mount the VMWare disk, which is a whole separate can of worms, and you should understand that if there are errors mounting the disk can introduce more problems.

At the end of the day, errors are rare, Linux dies a good job at fixing them, but if there is a problem you will need post error messages. Of course, there can be all kinds of problems with virtual machines (again another layer of complexity). Virtual machines can have a multitude of problems, everything from a problem host side to a problem with the virtualization technology to a problem guest side.

One solution is to work off of a base OS or snapshot.

At the end of the day, this is why we have backups.

---

### Post by garethsimpsonuk on 2011-03-10
> Some errors will be logged, some will not, such is the nature of any OS. On top of all that, you are adding a layer of complexity by running virtualization.

Well a hard shutdown is logged in Windows and Linux whether the OS is virtualised or not.
> 
If VMWare Workstation does not give you this information you are unlikely to find anything on the host Logs, although you can look at the VMWare logs if you wish. I am not familiar enough with VMWare workstation to know where to look.

It wont be in the host logs, it will be in the guest logs.

> You can try to mount the VMWare disk, which is a whole separate can of worms, and you should understand that if there are errors mounting the disk can introduce more problems.

I can't see how mounting a VMDK is going to help.

> At the end of the day, errors are rare, Linux dies a good job at fixing them, but if there is a problem you will need post error messages. Of course, there can be all kinds of problems with virtual machines (again another layer of complexity). Virtual machines can have a multitude of problems, everything from a problem host side to a problem with the virtualization technology to a problem guest side.

Errors wont be rare when your cutting the power nightly to 4 VMs. I prefer to do the process properly using ACPI. 

Yes there can be problems anywhere and everywhere lol, thanks.

> One solution is to work off of a base OS or snapshot.

Sure

> At the end of the day, this is why we have backups.

Yes this is what I am trying to achieve. Thanks for your time.

Does anyone know how to find out if Ubuntu was shutdown gracefully?

---

### Post by bodhi.zazen on 2011-03-10
> **new_tolinux said:**
> Only when it's not shut down properly, it asks about safe mode (etc).

So ...

You boot Windows, it identifies errors, and offers to fix them.

Same behavior with Linux, only the behavior is a bit different and, in my opinion, Linux in general does a better job at identifying and fixing errors. Most such errors are on the hard drive and have to do with time stamps and if changes to the journal were written to the disk. Most of the time they are trivial to fix with either OS, occasionally there is data loss.

Occasionally there are catastrophic problems with the disk and in that event you will need to know how to fix them, if possible.

Occasionally with virtual machines there is some kind of corruption to the configuration files or virtual disk.

---

### Post by garethsimpsonuk on 2011-03-10
I don't think you're grasping the point here. Booting windows is simply a test to see if the OS was shutdown via soft off.

I know data loss is rare but I prefer the preventative approach rather than the reactive approach.

Thanks for your help and time but if you could leave this thread open for someone who might have the answer to my question that would be great. Thanks

---

### Post by wormyblackburny on 2011-03-10
You are making this way too difficult. Don't shut them down, just suspend them. That will ensure no new data is being written during the copy of the files to back them up. Heck, it probably doesn't even matter if you move it WHILE it is running. That is the beauty of V-motion. It is designed to allow moving a running machine to a different server if it needs additional processor space. Take my setup for instance. If im running RHEL VM in windows, when I close VMware it suspends the machine. When I boot to Ubuntu and fire it up it gives a warning asking was the image moved and I just say yes and bam, its back up. The only time you would have to worry about seeing that error is if you were doing a restore anyway, so it is a moot point. I love VMware and V-sphere, their product is incredible if you can afford it. VMware workstation can also pull an image from a running machine on the network and create a virtual machine copy of it too.....

---

### Post by wormyblackburny on 2011-03-10
So I guess the actual answer to writing a script would be here:

**EDIT** [http://www.vmware.com/support/ws5/doc/ws_learning_cli_vmrun.html](http://www.vmware.com/support/ws5/doc/ws_learning_cli_vmrun.html) 
is for workstation, the one below is for Server edition..

[http://www.cyberciti.biz/tips/vmware-cmd-utility-examples.html](http://www.cyberciti.biz/tips/vmware-cmd-utility-examples.html)

Script will:
1) run command to suspend
2) scp folder to backup server
3) resume machine (start it)

even better, you could use the output of vmware-cmd -l to automatically list all the servers and load each one into a $tring then run the commands to suspend the machine, copy it, and restart it then grab the next valus from the output and rinse and repeat....

---

### Post by bodhi.zazen on 2011-03-10
I grasp what you are asking, but this kind of thing is not logged in Linux, or at least it does not work the way you envision.

During the boot process fsck will check the journal on your file system and every 30 boots (default) check the disk for errors.

Even if there were such a file, how do your propose to check it ? Your only option to check for such a log would be to either boot Ubuntu and review the logs or mount the Ubuntu partition from a live CD and check the logs.

Now since you are talking about mounting a VMware image, that is one step more complicated. Directly mounting the image on the host is possible, but I would not advise that as you would be mounting the image without checking the file system.

You could boot your VMware image with any live iso and search the logs. They are in /var/log you can try looking at /var/log/message for kernel messages or /var/log/dmesg but I do not think you will find anything.

I think part of the problem is that this is not Windows and you really do not understand how Linux works.

If you wish, read up on fsck and how the journal works on ext3 or ext4

Here are some references to get you started:

[http://lwn.net/Articles/322823/](http://lwn.net/Articles/322823/)

[http://www.articlealley.com/article_1624468_11.html](http://www.articlealley.com/article_1624468_11.html)

Take note with that second one, the solution is to upgrade to a newer kernel, and so the information in many of these articles is sometimes kernel related and outdated, but I think you need to understand the ext3 or ext4 journal (and various opting if you want to change them).

Note: many of these articles refer to patches, and patches from 2009 for example have already been applied.

Also note: Some of the information is "logged" in proc, which is a virtual file system, part of the kernel.

/proc/sys/vm/dirty_*

This information is not stored on the hard drive or in system logs.

Also note that "severe data loss" typically refers to any data that was in use at the time of the power failure , specifically data that has not yet been written to the hard drive. You can tune the way this works as well if you wish.

I also suggest you make a test machine, be bad to it, power is down, and boot it so you can watch (and learn) the linux behavior.

---

### Post by garethsimpsonuk on 2011-03-11
> You are making this way too difficult. Don't shut them down, just suspend them.

Shutting down is preferable because you can't move a suspended machine. It would have to be booted up and then shutdown before it could be moved to a different CPU architecture for example.

> Script will:
1) run command to suspend
2) scp folder to backup server
3) resume machine (start it)

Yes that is what I need however I need to shutdown the machine rather than suspend. It's all working but I just need to confirm the machines are being shutdown gracefully.

> even better, you could use the output of vmware-cmd -l to automatically list all the servers and load each one into a $tring then run the commands to suspend the machine, copy it, and restart it then grab the next valus from the output and rinse and repeat....

Sounds very cool but beyond my scripting skills! We don't have that many machines anyway and the finer grained control on the machines is useful (we will be backing up at different intervals).

> I grasp what you are asking, but this kind of thing is not logged in Linux, or at least it does not work the way you envision.

During the boot process fsck will check the journal on your file system and every 30 boots (default) check the disk for errors.

Even if there were such a file, how do your propose to check it ? Your only option to check for such a log would be to either boot Ubuntu and review the logs or mount the Ubuntu partition from a live CD and check the logs.

The entry is stored in syslog like I said. You just need to search for it. This forum post explains how: [http://ubuntuforums.org/showthread.php?p=7063300]("http://ubuntuforums.org/showthread.php?p=7063300")

> Now since you are talking about mounting a VMware image, that is one step more complicated. Directly mounting the image on the host is possible, but I would not advise that as you would be mounting the image without checking the file system.

You could boot your VMware image with any live iso and search the logs. They are in /var/log you can try looking at /var/log/message for kernel messages or /var/log/dmesg but I do not think you will find anything.

Why would you need to do this? Personally I just booted the VM and checked syslog!

> I think part of the problem is that this is not Windows and you really do not understand how Linux works.

No I think the problem is that you are giving out incorrect information. As shown above it is entirely possible to check how the system was last shutdown. Now that you know, I hope that you will give out the correct answer if asked this again in future.

I will mark this thread as complete now. For anyone else in a similar situation, I can confirm that the following command results in a safe shutdown for me:

> vmrun -T ws  stop "/home/gareth/vmware/NagiosWeb/NagiosWeb.vmx" soft

Thanks to all that posted

---

### Post by wormyblackburny on 2011-03-11
"Shutting down is preferable because you can't move a suspended machine.  It would have to be booted up and then shutdown before it could be moved  to a different CPU architecture for example."

You didn't say you were moving them, you are simply backing them up. I stand by just suspending, copying the file, then starting them up again if that is the case. Either way, whatever works best for you... :)

---

### Post by garethsimpsonuk on 2011-03-12
Well considering this is backup, being able to move to another machine is a key feature imo.

Thanks

---

