---
title: "Libvirt KVM migration to VMware"
date: 2021-12-16
forum: Virtualisation
---

### Post by hysteriia95 on 2021-12-16
Good afternoon.
PREMISE: Near to 0 confidence with Linux/command line.

I need someone who can explain me how to migrate vm from libvirt kvm to vmware.
In the hypervisor there is even windows machine, i have migrated them with vmware converter, but i dont know from where i have to start with the linux's.

This system is truly fascinating, but it takes time to master it!  :(  :popcorn:

---

### Post by TheFu on 2021-12-16
I've gone the other way; VMware ESX ---> KVM/libvirt.  What I did was to make a normal system backup, then setup a similar VM in virt-manager and restore the backup using a Live-Boot environment.  This worked for about 15 VMs.

Only gotchas are hardware related.  Ensure any specialized drivers are removed BEFORE the backup. Any guest additions were purged first too, since KVM doesn't have any guest additions.  

Network device names are likely to change. Correct those settings (which are different based on the exact version of Ubuntu involved).
Partition UUIDs change. Be ready to fix the /etc/fstab for new UUIDs, if you use those.  I tend to use LABEL or LVM /dev/{vgname}/{lvname} devices in my fstabs.
If there is RAID, that should be addressed outside the VM. Let the host handle it.

BTW, VMware makes 6 versions of hypervisors, so saying "vmware" is vague. Be specific.

As someone who doesn't have much Linux knowledge, things that are trivial will be very difficult.  The fstab is a trivial config file, but history shows that people new to Unix just don't understand it and are easily confused due to lack of knowledge and not understanding how to read the manpage for that file, which explains exactly what each field is and needs.

If I were trying to talk a typical MS-Windows person through this task, I'd tell them to 
[LIST=1]
[*]backup anything you cannot lose. Include a list of installed packages in the backups. Be certain to get everything spelled out here: 
[LIST]
[*]A Simple Script: [Https://ubuntuforums.org/showthread.php?t=2436006](Https://ubuntuforums.org/showthread.php?t=2436006) has more discussion.
[/LIST]
[*]Perform a fresh install under the new hypervisor.
[*]Restore the settings, then the data, then use that list of manually installed programs and install those. Don't point-n-click. That's the hard way.
[LIST]
[*]Restoring backups: [Https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](Https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
[/LIST]
[/LIST]
Those 2 links spell out what to backup, where it is (mostly) and the order of restore.  Because we don't backup the entire OS, a fresh install onto new hardware or into a new VM is the first step. That makes the restore process crazy-flexible that people using other backup methods lose.

---

### Post by hysteriia95 on 2022-01-20
Hello....
At the end i enter on the linux hypervisor with Winscp from a windows machine.
Enter in /mnt/storage, download the .img and then converted those machine with Starwind Converter.
Here we are, new environment with low-cost effort.

Thank you anyway.

---

### Post by MAFoElffen on 2022-01-21
??? What the heck?

I am a Beta tester for VMware for vSphere,. That was a personal invite from them. I have been an SME for over a decade with VM Host experience with many VM Hosts, for many companies... Sorry that I don't understand why you are here. You don't seem to relate with people very well, do you? An observation on how you shot down someone who honestly answered with good intent, on trying to help you, and the tone of your answer. Just an observation.

I ask myself: Why bother? You seem to have "all your answers" already. What could I hope to help you with? What brings you here? What answers are you really searching for? What can we help you with that you will feel actually helps you? I actually am a bit hesitant in sharing how much I really know with people, so I don't come across 'wrong' to them... I seem to be confused by your answer. (Maybe the wording of?)

As TheFu had politely said, your first post did not get into much details in what you want help in converting... You say you have some (not any detail on those) VM guest as KVM, that you want to convert to VMware Guests... (you also left out for which of the many VMware products will be your target...) How much experience, to what level of skills do you have on each? So that in not knowing, someone does not offend you by going into too much fine details...

Next, is this for "you" or commercially as helping you with your job? That question tells allot in how complex those existing VM's may be... or if just creating a new VM might be easier, in what VMware thinks is what it should be for it, from using an existing disk image of a certain OS version...

Just a Note: Be polite please. Beware of possibly coming across as talking down to people. You never know (online) who that person is and what their life experience has been. Asking for help is one thing, though some here get (Or have been) paid professionally for "their" recommendations, which they volunteer freely here. There is a lot of experience "here" in this community. Talking blinding down to someone, without knowing who they really are, might be viewed as overtly offensive. I am one of those people who try to relate with new users through Infrastructure Architects, at their level of skills and experience. I am here to help people, who want and need help. My intent is purely just that. To help people.

Want to start that over?

---

