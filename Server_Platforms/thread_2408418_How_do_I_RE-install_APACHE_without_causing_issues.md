---
title: "How do I RE-install APACHE without causing issues?"
date: 2018-12-18
forum: Server Platforms
---

### Post by Daniel_Clarke on 2018-12-18
Hi,

I need to reinstall APACHE on our web server, what is the best way to do this without it causing to many issues. What are the major issues I will face if I do this? Currently our web server is configure like so: 16.04LTS LAMP with multiple JOOMLA sites being hosted.

why we need to do this, we upgraded PHP from 7.0 to 7.1 and during that process was advised to add a repository for APACHE, something was updated an we are now unable to use SEF URLs on any of our JOOMLA sites, we have tried to troubleshoot this but have gotten no working results so we are wondering if reinstalling APACHE and going through the configuration we originally went through when it was working to see if that resolves our issue.

Any suggestions or details that could be provided about reinstalling APACHE and the problems that might occur would be greatly appreciated so we can avoid this becoming a bigger issue.

Thanks in advance

---

### Post by TheFu on 2018-12-18
Every setup is unique.  Nobody here can have a full picture of your server(s).

So, the only possible answer is to suggest that you clone the setup into a test system/virtual machine, and run a number of reinstall tests to see what happens.

We always test any upgrades in virtual machines before touching production systems. Is it part of being a professional organization, IMHO.

---

### Post by Daniel_Clarke on 2018-12-18
> **TheFu said:**
> Every setup is unique.  Nobody here can have a full picture of your server(s).

So, the only possible answer is to suggest that you clone the setup into a test system/virtual machine, and run a number of reinstall tests to see what happens.

We always test any upgrades in virtual machines before touching production systems. Is it part of being a professional organization, IMHO.

Thanks for the response, please allow me to clear a few things up. This is our test server for our developers, we would not do this on production servers before testing, this is our only in-house Ubuntu/Linux server and we are far from experts. With that said, we did come here for help so any additional suggestions or specific details would be greatly appreciated. You mentioned you would clone the server, as I said I am far from a Linux/Ubuntu expert. How would I accomplish this? Even thouhg this is our test server we do not want to make things worse, hence why we are asking questions.

Thanks

-daniel

---

### Post by TheFu on 2018-12-18
I haven't cloned a physical server in over 15 yrs.  We've be using virtual machines since around 2005.  The physical hosts aren't anything special, so we don't even back them up.  We do backup virtual machines, religiously, however.

Google "clone ubuntu" returned plenty of guides. [https://help.ubuntu.com/community/DriveImaging](https://help.ubuntu.com/community/DriveImaging) is one.  Instead of dd, I'd use **ddrescue**. It handles failures much better but is still a byte-for-byte copy. If you want to restore to a smaller partition, use something like **fsarchiver** on each partition.  Lots of people like clonezilla, I found it too complicated.

There are lots of other threads about cloning systems in these forums. Which method works best is a judgement call.

I should mention, we don't do imaging because it requires downtime, requires way, way, too much storage and takes much to long.  We do versioned backups and would use those backups to restore rather than imaging in about 99% of the situations.  Our backups don't do anything special just because they are VMs.  Physical or VM, it doesn't matter. And we don't care which hypervisor is being used. Doesn't matter for our methods.  Over the years, we've used ESXi, ESX, Xen, KVM, Virtualbox and, long ago, VMware Workstation.  Today, we only use KVM and have about 8 yrs. All the others were inferior for our needs. A few were hostile for our needs due to licensing.

I realize you probably don't have the time/authority to move to virtualization, but it really does make things much more flexible.  Where I've worked, average server workloads were 13% before we started virtualizing.  Now they are over 80%, so the hardware is much more cost effective.

At home, I virtualize everything I can too.  My desktop is virtualized, for example. ;)

Anyways, I hope this is helpful and that you find a workable solution.

---

### Post by LHammonds on 2018-12-18
If your server utilized LVM during initial setup, fsarchiver can snapshot the partitions while the server is running and write the output to a network share or mounted USB drive.  Then spin up a virtual environment of your choice and boot up a recovery ISO and use fsarchiver to restore the partitions into the VM.  Hopefully when it boots up, it can handle the physical to virtual transition of hardware.  Then install the drivers for the virtual environment and be careful to not allow networking until you can boot it up, login and edit the network configuration to use a different IP.

I documented the steps for using fsarchiver to backup and restore but it will not match your specific scenario exactly though but should get you fairly close.

[Here is the link]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220") for when I documented it for 16.04.

LHammonds

---

### Post by Daniel_Clarke on 2018-12-19
Thank you to both of you for the answers, I will do my research and come back if I encounter issues.

Thanks

-daniel

---

### Post by Daniel_Clarke on 2018-12-19
So I have successfully cloned the server and have started troubleshooting. After the process of uninstalling I tried reinstalling APACHE2 and I have ran into the following error:

The following packages have unmet dependencies:
 apache2 : Depends: apache2-bin (=2.4.18-2ubuntu3.9) but 2.4.37-1=ubuntu16.04.1+deb.sury.org+1 is to be installed
E: Unable to correct problems, you have held broken packages.

I am not a linux user, how can I resolve this?

Thanks in advance.

---

### Post by LHammonds on 2018-12-19
Make sure your repository is updated:

```
sudo apt-get update
```

Try resolving dependencies:

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

Perform some cleanup operations:
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```

If you still get the same message, see what you actually have held back:

```
dpkg --get-selections | grep hold
```

LHammonds

---

