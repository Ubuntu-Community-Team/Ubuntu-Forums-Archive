---
title: "Ubuntu-server virtual machine internet keeps dying"
date: 2013-09-26
forum: Virtualisation
---

### Post by hiig on 2013-09-26
Setup:

Windows 7 running Ubuntu-server via VMware Workstation. Ubuntu runs in terminal with byobu, and its sole purpose is to function as an internet crawler.

On occasion, I would get a message saying that the network adapter was reset. These don't have any other consequence, and I can continue using the VM normally. However, I also get another type of message:

task kworker/2:0:20 blocked for more than 120 seconds

...and then something about /proc/sys/kernel/hung_task_timeout_secs

So, why are my processes getting blocked (what the hell does that even mean?), and how do I stop this? It's a major inconvenience to have to reset my VM 3 or more times in a day, and start everything back up again.

I should also mention that the ifconfig eth0 down method does not work, once this hung message comes up. Typing that in will only hang the terminal, and nothing happens, nor can I type anything else into that terminal.

---

### Post by QIII on 2013-09-27
*Moved to **Virtualisation***

---

### Post by hiig on 2013-10-08
No one?

---

### Post by Amorphous Serendipity on 2013-10-08
Hi hiig,

The times I've seen the scenario that you describe, it  ended up being an issue with the VM properly writing itself to the disk.  This was caused by incompatibilities with VMware Tools.

Do you have VMware Tools currently installed on your VM?

If so, I would remove them, and if needed, replace them with open-vm-tools:
[https://launchpad.net/ubuntu/+source/open-vm-tools](https://launchpad.net/ubuntu/+source/open-vm-tools)

I hope this assists in resolving your issue.

---

### Post by hiig on 2013-10-09
I'm assuming after removal, I just apt-get the packages listed? Do I have to configure anything in the VMware settings? And am I supposed to use all listed packages? For instance, if I don't have a GUI, or need the debug tools, can I simply just install the dkms package and leave it at that?

---

### Post by Amorphous Serendipity on 2013-10-09
> **hiig said:**
> I'm assuming after removal, I just apt-get the packages listed? Do I have to configure anything in the VMware settings? And am I supposed to use all listed packages? For instance, if I don't have a GUI, or need the debug tools, can I simply just install the dkms package and leave it at that?

Yes the open-vm-tools should be in the repo. You shouldn't need to  change your VMware settings. As long as your pulling the packages from  the Ubuntu repo, than you should be fine, as the packages have been  tested for compatibility.

sudo apt-get install open-vm-tools
sudo apt-get install open-vm-dkms
sudo apt-get install open-vm-toolbox

I believe that should get you were you need to be.

---

### Post by hiig on 2013-10-09
The dkms package is not downloading. I'm getting 404 errors.

EDIT: Same thing for toolbox. The only one that installed successfully was tools.

---

### Post by Amorphous Serendipity on 2013-10-09
> **hiig said:**
> The dkms package is not downloading. I'm getting 404 errors.

EDIT: Same thing for toolbox. The only one that installed successfully was tools.

hiig,

Sorry for giving you incorrect information, I haven't looked at the open-vm-* packages in a long time. The dkms and toolbox packages were merged into the open-vm-tools package.

Please see the below links:
[https://launchpad.net/ubuntu/+search?text=open-vm-tools](https://launchpad.net/ubuntu/+search?text=open-vm-tools)
[https://launchpad.net/ubuntu/+search?text=open-vm-dkms](https://launchpad.net/ubuntu/+search?text=open-vm-dkms)
[https://launchpad.net/ubuntu/+search?text=open-vm-toolbox](https://launchpad.net/ubuntu/+search?text=open-vm-toolbox)

So if you installed open-vm-tools, you should have everything. Are you still receiving errors from the kernel.

---

### Post by hiig on 2013-10-09
The errors generally happen once or twice every few days, so I'll give it a week before saying anything with confidence.

However, how do I know if it is working? If I look at my processes in top, there used to be a vmware tools process. I haven't seen anything under V or O (for open vm), so I'm not sure if it did get set up.

VMware also still shows 'Install VMware Tools' under the VM menu, so again, I'm not sure if it did install, or not.

What does open-vm do, anyway? To my understanding, it's almost exactly the same thing as the normal vm-tools, but where would I go to change settings and the like?

---

### Post by Amorphous Serendipity on 2013-10-09
> **hiig said:**
> The errors generally happen once or twice every few days, so I'll give it a week before saying anything with confidence.

However, how do I know if it is working? If I look at my processes in top, there used to be a vmware tools process. I haven't seen anything under V or O (for open vm), so I'm not sure if it did get set up.

VMware also still shows 'Install VMware Tools' under the VM menu, so again, I'm not sure if it did install, or not.

What does open-vm do, anyway? To my understanding, it's almost exactly the same thing as the normal vm-tools, but where would I go to change settings and the like?

hiig,

The open-vm-tools project goal is to basically create an open source version of VMware Tools that has all of the features.

Bad news:
[LIST]
[*]Currently does not have all of the features.
[/LIST]

Good news:
[LIST]
[*]Was actually designed for compatibility with Linux.
[/LIST]

Essentially, if you have problems with VMware Tools, you use open-vm-tools instead.

Additionally:
[LIST]
[*]If you installed it from the Ubuntu repo without error, it is installed and working (the 404 errors for the two packages were because they no longer exist and were rolled into one package [all is well])
[*]VMware will still try to get you to install VMware Tools because technically they are not installed.
[*]You can find additional info about open-vm-tools here - ([http://open-vm-tools.sourceforge.net/about.php](http://open-vm-tools.sourceforge.net/about.php))
[/LIST]

On a side note, because I always seemed to run into random issues with VMware Player/Workstation like you ran into, I switched to VirtualBox a long time ago (works great with Linux, Windows, and you can even get it to run OS X if needed). If it's a server I use ESXi or Proxmox VE.

---

### Post by hiig on 2013-10-12
Alright, so far still none of these problems, but I've noticed that ever since I swapped to open-vm, every time I resume a VM from a suspended state, I can't get the internet back on it without completely restarting the VM. Before, I would do ifconfig eth0 down, and in a matter of seconds the network would automatically fix itself. Now, I can't do it, nor does it work if I do ifconfig eth0 up afterwards.

Any other ways to restart the network?

---

### Post by hiig on 2013-10-14
Alright, some time has passed, so now I can say whether or not open-vm worked...It didn't. Got the hung message again this morning.

Also, in regards to my post above, I figured out how to get the internet back after suspensions using service networking restart.

In any case, I'm still back to square one with the hung message.

---

