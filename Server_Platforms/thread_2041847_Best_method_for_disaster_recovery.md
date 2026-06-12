---
title: "Best method for disaster recovery"
date: 2012-08-13
forum: Server Platforms
---

### Post by GabrielSyme on 2012-08-13
I've currently been running our small business on an Ubuntu PDC I set up following an excellent tutorial from quite a while ago. It's run great, but just a week ago, my server's hardware gave out. Fortunately the drives were fine, and I was able to swap them into another machine without much fuss and get back up and running. Now, I want to upgrade my server to a Zentyal installation, and I realize I don't have a good backup system in place to recover from a similar catastrophe where the actual harddrives are fried. 

What's the best way to backup and recover from a complete server melt-down? I want to be able to recover the entire system to completely new hardware should the need arise. I do backups of all our files, but right now, if something dies, I will have to rebuild the server from scratch. I want to be able to restore everything (LDAP, databases, configurations, ect.) to a new machine as if nothing happened. What's the most common way to do this on an Ubuntu server?

---

### Post by koenn on 2012-08-13
> **GabrielSyme said:**
> 
What's the best way to backup and recover from a complete server melt-down? I want to be able to recover the entire system to completely new hardware should the need arise. 

There's no such thing as a "best method". But you do need a plan.

If you're expecting to recover on new hardware, you have to anticipate doing an OS install from scratch. You're plan should thus include answers to questions such as
  - how quickly can you get that hardware
  - do you still have the install CD. Can you find it in an emergency
  - do you install with all the installer defaults or do you customize ? Do you remember all settings, all answers to the installer's questions ? Can you automate this ? 

Next, do you know know the names off all the packages uou need to install to reproduce that server ? All the custom config to make them do what you need ? all the tweaks and workarounds to get them to work right ? 

Also, do you know how to install them and configure them in such a manner that they can use restored data rather than start blank ?

And can you restore the data ? How old will the be compared to the data on the fried server ? Is that a problem . 


All of these can be solved ; the answers however depend greatly on your specific environment, so there are no recipes for this. You think about it, make choices, come up with solutions, and start preparing for them ; that's you're recovery plan. 

Of course "completely fried server" is only one failure mode. "Drunk sysadmin wipes disk" is another one. "server doesn't reboot after upgrade" or "database disappears during apllication upgrade" are also interesting. You'll need a solution for those as well, if your  "fried server" plan doesn't have adequate solutions for this sort of issues. 
EG : a common "failed server recovery plan" in a virtualized environment is : put back a copy of the virtual machine. Question : are you going to revert an entire server, including all data, to yesterday's state to fix a broken database or something of that nature ?

---

### Post by koenn on 2012-08-13
Here are some techniques you might want to use. 
They're no substitute for a disaster recovery plan (re my previous post), but could be used to implement certain parts of it. 

[http://users.telenet.be/mydotcom/howto/linux/automatic.htm](http://users.telenet.be/mydotcom/howto/linux/automatic.htm)

---

### Post by Wim Sturkenboom on 2012-08-14
> 
What's the best way to backup and **recover from a complete server melt-down**?
A secondary server ;) Depending on acceptable loss of data, copy your backup data to the secondary system or use replication.

Also, don't forget to validate your backups (md5sum comes to mind); you would not be the first one with a perfect backup plan to find out that a backup is corrupted.

---

### Post by GabrielSyme on 2012-08-14
> **koenn said:**
> 
EG : a common "failed server recovery plan" in a virtualized environment is : put back a copy of the virtual machine. Question : are you going to revert an entire server, including all data, to yesterday's state to fix a broken database or something of that nature ?
Thanks for your response Koenn. I'm definitely thinking of a senario where I want to revert the entire server. My ideal workflow would be to revert the server to how it was a few days or a week ago, get everything running correctly, and then restore the individual data that may have been changed since that last full system backup. I have a good system in place for backing up individual files and databases, but the thought of having to set up a new server from scratch, remember all my configurations, settings, ect. and then restore the data is daunting. Would you recommend virtualization as an easy way to achieve a full system restore, taking perhaps weekly snapshots of the server which I can restore from in a catastrophe?

---

### Post by thnewguy on 2012-08-14
I agree with the first response, there isn't one best method, but there are some things to consider.

1. You could either have an image of your OS or a list of installed packages you could download in a batch.

2. Regular (and tested) backups of your data and configuration files. At least two backups should be made, one on-site for easy access and one off-site in case something happens to your physical location.

3. Documentation. Lots of it. You should have a list of any changes you've made to a default server install (in detail).

4. Consider having a spare server around that you could immediately get up and running if the first one fails. Or consider running two servers, the main one and a second one which has the exact same data and packages.

5. Whatever methods you put in place, test them. Some weekend pretend your main server is dead, completely dead, and see how long it takes you to get another machine up and running doing all the things the first one did. This will be a good learning experience as it will show the good and weak points in your recovery plan.

Hope that helps.

---

### Post by koenn on 2012-08-14
> **GabrielSyme said:**
> Would you recommend virtualization as an easy way to achieve a full system restore, taking perhaps weekly snapshots of the server which I can restore from in a catastrophe?

No, 
like I said, DRP is not about recipes and 1-size-fits-all solutions. 

In your case : you have, presumably, 1 small business server. Say you virtualize it, and work out a decent way to make 'system' backups of it. 
Next, your hardware gives up. You still can't recover : you need to get a new server, reinstall whatever hypervisor you were using, possibly reconfigure that to your custom needs, and redeploy the virtual machine. You still gonna need a plan for all that, now. 
This problem is possibly easier than recovery of an SBS that does anything and everything, but it's still a problem.

reality check: After a disaster, you probably want to be up and running in 1-2 days. Do you know how you're going to be able to buy a suitable server, and have it delivered to your place, in less than 2 days ? 
Wim Sturkenboom's suggestion that you need a 2nd server is not such a bad idea.

Virtualization is great for recovery plans if you already running multiple hypervisors, preferably more than strictly necessary so one can fail and all your guests can run on the remaining hosts,  and if you can easily move virtual machines from one host to another.
But that's not your case here, I think. unless you think it's worth the money.


In your case I'd probably go with
- good documentation : what is this server running, why is the configuration the way it is
- scripts to (semi)-automatically recreate the system from scratch
- backups of config files, to copy into a newly installed server (as plan B) and for reference if you need to do things by hand 
- your data/database backups

it helps if you already start planning for this while you're installing the system, e.g. take note of where (other than in /etc) you've tweaked the config so this can be included in a file backup (if you're not simple backing up the entire tree) 


You can also go with disk images for this, but I don't trust them. You're going to have to be sure that your new hardware is identical to the failed server, or run the risk that the system you've imaged doesn't run correctly, or only with lots of ad hoc tweaking, on the new hardware. That's fine if you have all the time in the world and enjoy the tweaking, but, imo, too big a risk if you have a recovery goal of, say, 1 business day max. 


I've heard people suggest to simply backup all files (i.e. the entire system), and do recovery on a new system by chrooting the old files. Sounds like something that might work, but it would require testing,  you'll need to practice it, and you'll still want a step-by-step procedure at hand if you have to do it in a crisis. 
(this is something that always should be part of a DRP)
And personally, I'd still  like a plan B with that, too.


In all of the above scenarios, obviously you still need regular backups of data, especially databases, too. I'd never rely on an image or a file copy of an open database for, say, recovery of a database to a consistent state.

---

### Post by LHammonds on 2012-08-17
As mentioned, there are many different ways to go about it.

I personally prefer to run the OS in a virtual environment.  A backup of the virtual files or entire partitions will work identically on any other server that supports the base virtual system.

I use VMware's ESXi server on IBM BladeCenter but if it goes belly up, I can have ESXi installed on a Dell PowerEdge server and be up-and-running very quickly with the same image...no OS concerns about the underlying hardware.  The BladeCenter can be an 8-CPU server with fiber-channel to a RAID-10 SAS array and the Dell can be a PERC-6i RAID-5 SCSI system but it won't matter one bit to the virtual Ubuntu server since it only interfaces with the VMware virtual hardware.

But that is something to consider BEFORE getting hardware.  Since you already have a bare-metal install, that doesn't help you much but it might help someone looking to do the same thing later.

LHammonds

---

### Post by LHammonds on 2012-08-17
One thing you could do is a backup and then restore in a virtual on your desktop.  If you are running Windows, install VirtualBox and setup a virtual machine and see if you can get the backup to restore and run in your VM.  If you can, you will be able to try out whatever upgrade you have in mind for you real server to get an idea of how it will or will not work and maybe even come up with some fairly solid upgrade docs/procedures for the real server upgrade.

LHammonds (sorry about not editing my last post, my phone hates edits)

---

