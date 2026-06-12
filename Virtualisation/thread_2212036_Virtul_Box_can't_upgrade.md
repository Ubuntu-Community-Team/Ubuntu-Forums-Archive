---
title: "Virtul Box can't upgrade"
date: 2014-03-19
forum: Virtualisation
---

### Post by bojo on 2014-03-19
Hi All,

I have Ubuntu desktop **12.04** (fully updated) with virtual box **4.2.14**. I also have a VM - Ubuntu **12.04 server** - fully updated. The VM is configured as a bridged network interface and has some servers - Apache, SSH, Squid etc. 

The issue - if I upgrade to any 4.2 version of VirtualBox - the machine starts behaving almost as a NAT (_I can not access the servers from another machine on the LAN but I can access them from the host_).

Each time before trying to upgrade VirtualBox - I make a backup with clonezilla. So when I see that things go wrong - I revert with clonezilla and everything is fine again. However - I still can not upgrade to anything newer.

Today I had a different test - I export the VM to .OVA file as a backup. If I am to import this backup in VirtualBox as is - it works fine (again - no change to the virtualbox 4.2.14). However - if during the import I am to "re initialize" the network interface so I can have a new MAC address - the VM can not obtain an IP - the network interfaces can not be configured (needless to say - it is a bad state).

Guys - if you have seen something like this or have any idea how I can go around it - please help.
Ahead of time - for me this is a production machine - used heavily on daily bases so my tests would be limited and likely over the weekend. Never the less - I do appreciate help.

I haven't yet tried upgrade to virtual box 4.3

Thank you,

BB

---

### Post by ian-weisser on 2014-03-21
```
$ rmadison -u ubuntu virtualbox
 virtualbox | 4.1.12-dfsg-2ubuntu0.5 | precise-updates/universe  | source, amd64, i386
 virtualbox | 4.2.16-dfsg-3          | saucy/multiverse          | source, amd64, i386
 virtualbox | 4.3.6-dfsg-2           | trusty/multiverse         | source, amd64, i386
```

The VB servers I have run have not had the problem you describe.
Since you're using 4.2.14 on 12.04, you're not using VB from the Ubuntu Repositories. The support this forum can provide to unsupported software is limited...
You should probably ask in the VB forums, too.

---

### Post by bojo on 2014-03-29
Thank you, this is a good advice. Yes - I have used the virtualbox repository. I will check with them. Just FYI - in case somebody else stumbles on this. 4.2.14 works well on 12.04. However - any update / upgrade was not successful. I just tried upgrade to 4.3.10. The VMs behave well "except"!!! if I am trying to access the servers - port 80 for example - it will never load. Odly enough - if I am to scan the ports - they appear open but connection never happens. I went all the way to completely removing virtualbox (including configuration files) installing again, importing VM from archive and even installing new freenas in order to access some server. Every time the behavior is the same - if I access the servers in the VM from the host (or another VM) - everything is OK - if I am to access the servers from a different real machine on the network (using android tablet for testing) it just does not work. Revert back to the image using clonezilla restores the functionality. 

Again - appreciate the advice...

---

### Post by bojo on 2014-05-04
So... I wanted to give you a feedback. No - it is not resolved yet but still - it would be good to share the result.

1. remove virtual box
[http://askubuntu.com/questions/190004/how-to-uninstall-virtualbox-in-12-04](http://askubuntu.com/questions/190004/how-to-uninstall-virtualbox-in-12-04)
```
sudo apt-get purge virtualbox-\*
```
2. Disabled oracle's repository
3. Upgraded the OS to 14.04
All went well but there was one "fail" when the OS is starting - I was unable to verify "exactly" what was failing. I believe it was something about "green" and "processor"
4. Installed virtualbox from the ubuntu repository 4.3.10
5. Open the VMs
The result is the same as before

At this point my conclusion is that the issue is on the host itself.
I had to revert back to 12.04. Clonezilla did not do well when restoring the partitition.
this worked
[http://opensource-sidh.blogspot.ca/2011/06/recover-grub-live-ubuntu-cd-pendrive.html](http://opensource-sidh.blogspot.ca/2011/06/recover-grub-live-ubuntu-cd-pendrive.html)

And a new bump - when logging in my home - the OS would freeze to the point of hard reboot. 

Had to restore the complete disk (more than 1h) and then restore the home with the backup tool Déjà Dup Backup Tool

Also I did open a corresponding post on the virtualbox forums
[https://forums.virtualbox.org/viewtopic.php?f=7&t=60952](https://forums.virtualbox.org/viewtopic.php?f=7&t=60952)
And the guys there couldn't help me.

As for my machine - I am going to install from scratch in the future (this is the plan). The experience however was not good.

Good luck if you stumble on a situation like this...

---

### Post by bojo on 2014-05-25
Guys,

I am **stuck** completely with this one. So anything you can point to would help. So - this behavior persisted even with a completely fresh install of 14.04. Brand new install of virtualbox - from the ubuntu repository - currently 4.3.10.
Again - connections work OK - if they are on the local host. 
Connections are NOT OK if they are from a physical machine (different than the local host). 
I am finding a few threads but they don't seems to lead me to anything.

This one
[https://forums.virtualbox.org/viewtopic.php?f=7&t=55010](https://forums.virtualbox.org/viewtopic.php?f=7&t=55010)
points to the same behavior somehow. If I am to connect from a remote real host to the VM (ubuntu server 12.04) telnet at port 80 I am getting "connection closed by foreign host"
This does not happen if I am on the local host itself.

I also checked these two threads
[http://ubuntuforums.org/showthread.php?t=1945029](http://ubuntuforums.org/showthread.php?t=1945029)
[https://forums.virtualbox.org/viewtopic.php?f=7&t=43090](https://forums.virtualbox.org/viewtopic.php?f=7&t=43090)

Indeed /etc/udev/rules.d/70-persistent-net.rules within the guest had 2 references - eht0 and eth1 but even when I removed and rebooted (the file was re created to include only eth0) the problem persists.

So - my current situation - if I can not fix this I can not use the server that is in vm. 
So far I have tried - upgrade to numerous versions after 4.2.14, upgrade to ubuntu 14.04, completely fresh new install of 14.04 and VB from ubuntu's repository and the behavior is sticking.

Plese help...

---

### Post by bojo on 2014-06-02
Hi All,

Posting the solution that worked for me. I changed the MTU to 1500 (originally it was "Auto"). 
[ATTACH=CONFIG]253681[/ATTACH]

The documentation points to the following.
[COLOR="#006400"]Also, setting the MTU to less than 1500 bytes on wired interfaces provided by the sky2
driver on the Marvell Yukon II EC Ultra Ethernet NIC is known to cause packet losses
under certain conditions.
[/COLOR]
I don't know what my driver is actually but decided to give it a try. The computer is DELL XPS X2 laptop.
Also - if you edit a connection - the "device MAC address" - it was set to blank. And this is strange because everything else worked just fine on the system. Without MAC address it wouldn't function would it?
Any way - I believe - one of these (or both) made my guest to function well in bridged networking configuration.
Again - I experienced this issue ever since I tried to move to the next version - after 4.2.14 and now it appears to behave well.

---

### Post by ofnuts on 2014-06-03
There is always a MAC address burned in the network adapter hardware, which is guaranteed unique (for a *hardware* address). It can be replaced by a softer address (which can unfortunately conflict with a hardware assigned address on some other machine), which is likely the purpose of that empty field.

---

### Post by bojo on 2014-06-03
Is there a way to display all MAC addresses used by the box and the VMs with command line?
If I do ifconfig - it only displays eth0, lo and wlan0 (meanwhile I have 2 VMs running one with bridged networking and one with NAT)?

---

### Post by ofnuts on 2014-06-04
The MAC addresses used by a  VirtualBox are in the ".vbox" file that defined the virtual box:
```

        <Adapter slot="0" enabled="true" MACAddress="080027B301CB" cable="true" speed="0" type="Am79C973">

```

---

