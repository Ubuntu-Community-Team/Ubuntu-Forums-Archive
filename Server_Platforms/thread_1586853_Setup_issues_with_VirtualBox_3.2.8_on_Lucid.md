---
title: "Setup issues with VirtualBox 3.2.8 on Lucid"
date: 2010-10-02
forum: Server Platforms
---

### Post by Jonners59 on 2010-10-02
I am trying to set up Vista on my Lucid within VirtualBox so I can run 3CX IP PBX.

I have installed the virtualBox and set up a virtual space called "Vista", but when I start it (Power on) I get an error message - Please see screenshot enclosed.

If I run the command  [HTML]'/etc/init.d/vboxdrv setup'[/HTML] as instructed in terminal I get.

[HTML]root@server:/home/server# /etc/init.d/vboxdrv setup
WARNING: All config files need .conf: /etc/modprobe.d/dahdi, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/dahdi.blacklist, it will be ignored in a future release.
 * Stopping VirtualBox kernel module                                             *  done.
 * Recompiling VirtualBox kernel module                                         
 * Look at /var/log/vbox-install.log to find out what went wrong
root@server:/home/server# 
[/HTML]

And yes, I have installed DKMS from Synaptic package manager....

Log states:
[HTML]Attempting to install using DKMS
  removing old DKMS module vboxdrv version  3.2.8

------------------------------
Deleting module version: 3.2.8
completely from the DKMS tree.
------------------------------
Done.

Creating symlink /var/lib/dkms/vboxdrv/3.2.8/source ->
                 /usr/src/vboxdrv-3.2.8

DKMS: add Completed.

Error! Your kernel headers for kernel 2.6.32-25-generic-pae cannot be found at
/lib/modules/2.6.32-25-generic-pae/build or /lib/modules/2.6.32-25-generic-pae/source.
You can use the --kernelsourcedir option to tell DKMS where it's located, or you could install the linux-headers-2.6.32-25-generic-pae package.
Failed to install using DKMS, attempting to install without
Makefile:159: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.[/HTML]

My account name is server
and my kernel is stored at....
linux image: /boot/vmlinuz-2.6.32-25-generic-pae

ANy help please....?

---

### Post by Groodles on 2010-10-02
You need to install the "linux-headers" package for your kernel.

```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by Jonners59 on 2010-10-03
Many thanks, fixed that problem after a re-boot.

Still under the same, I hope you can help - same subject as heading so I will continue.

Now this is working, I have tried to load my 64-bit Vista CD, but it will NOT install.  I get messages that it can't find boot and that the "VT-x/AMD-V are not enabled.  I am currently using this 64-bit Vista OS on the machine without any issues whilst I transition to Ubuntu as prime OS.  It is an AMD-64bit CPU, so what am I doing wrong?

I have enabled this in Settings - System - Acceleration

---

### Post by Jonners59 on 2010-10-05
Any help, PLEASE - ANYONE>

---

### Post by CharlesA on 2010-10-05
Did you select Windows Vista 64-bit as the OS type?

Also are you running 32-bit or 64-bit Lucid?

---

### Post by Jonners59 on 2010-10-05
> > **CharlesA said:**
> Did you select Windows Vista 64-bit as the OS type?

Also are you running 32-bit or 64-bit Lucid?

I selected 64-bit. The second question is more interesting.  Neither of my 64-bit machines were able to install the 64-bit 10.4...  Is this the problem and how do I navigate around it?

---

### Post by CharlesA on 2010-10-05
> **Jonners59 said:**
> I selected 64-bit. The second question is more interesting.  Neither of my 64-bit machines were able to install the 64-bit 10.4...  Is this the problem and how do I navigate around it?

Really? Did they give you errors when you tried to install?

How did you try to install?

---

### Post by arrrghhh on 2010-10-05
I think if your host OS is 32-bit, the guest has to be 32-bit...

Perhaps with VT-x/AMD-V tech (the chip technology that aides in virtualization) you can do it... But I'm not positive.

Did you try enabling either of those, assuming your proc supports it?

---

### Post by CharlesA on 2010-10-05
> **arrrghhh said:**
> I think if your host OS is 32-bit, the guest has to be 32-bit...

Perhaps with Intel-V or AMD-whatever they call it tech (the chip technology that aides in virtualization) you can do it... But I'm not positive.

You can run a 64-bit guest on a 32-bit host if you have VT-x or AMD-V enabled (aka have a CPU supporting [hardware virtualization]("http://en.wikipedia.org/wiki/Intel_VT-x"))

---

### Post by Jonners59 on 2010-10-07
> **CharlesA said:**
> Really? Did they give you errors when you tried to install?

How did you try to install?
I shall step back...  I do not believe it is the 64-bit version(s) of 10.4 OS.  Certainly whenever I select the 64-bot aps, they will not install, I always have to use the 32-bit.  When I try to install them it says not the correct op system.  I then try the 32-bit and the ap loads without any probs

I'm not techie, as you have probably guessed, rather a dabbler...  Is there something I have done wrong or is this just an IT oddity...  Is there a report I can run to confirm 'stuff'?  And how does this affect what I am trying to do?????

---

### Post by CharlesA on 2010-10-07
It sounds like you installed the 32-bit version.

Try running **uname -a** and see if it says x86_64 or just x86.

x86=32-bit
x86_64=64-bit

---

### Post by Jonners59 on 2010-10-08
> **CharlesA said:**
> It sounds like you installed the 32-bit version.

Try running **uname -a** and see if it says x86_64 or just x86.

x86=32-bit
x86_64=64-bit


Oh, hell...  It is:
Linux server 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux

What can I do without a complete rebuild!!!!!

Would the easiest thing for me to do be to delete the virtual partition and create a new one at 32-bit, then buy and install a 32-bit Vista or Windows7???

My ONLY reason to do this is to install 3CX (IP PBX) as I can't get any decent ones on Ubuntu - yes, there is Asterex, but can't get it to go and is far to complex.  I have 3CX up and running, if I can install in the VM all I have to do is then use the back up file - job done and my main PC/Server is running on Ubuntu not Vista!

PS added screenshot of VirtualBox partition description

---

### Post by CharlesA on 2010-10-08
If you don't want to do a complete rebuild, just install a 32-bit version of Windows.

Personally if I had to pick between 7 and Vista, I'd pick 7, since it's newer and I haven't run into any problems running it in a VM.

Also: i686 is also 32-bit, but you figured that out already. :P

---

### Post by Jonners59 on 2010-10-08
> **CharlesA said:**
> If you don't want to do a complete rebuild, just install a 32-bit version of Windows.

Personally if I had to pick between 7 and Vista, I'd pick 7, since it's newer and I haven't run into any problems running it in a VM.

Also: i686 is also 32-bit, but you figured that out already. :P
Thanks Charles...

What do you think went wrong with my install?  It's done the same on both my 64-bit machines.

PS:  I assume I delete the partition I created and build another at 32-bit instead?

---

### Post by CharlesA on 2010-10-08
> **Jonners59 said:**
> Thanks Charles...

What do you think went wrong with my install?  It's done the same on both my 64-bit machines.

PS:  I assume I delete the partition I created and build another at 32-bit instead?

The only thing I can think of is that you installed from a 32-bit livecd, instead of a 64-bit livecd. By default, you are directed to a download of the 32-bit version of Ubuntu from ubuntu.com.

You can select 64-bit from there, or just go to: [http://releases.ubuntu.com](http://releases.ubuntu.com) to find it there.

Note: If your machine didn't have Hardware virtualization enabled, it would not list 64-bit in VirtualBox.

What you could do before you completely switch installs to a 32-bit version of Windows is to recreate the virtual machine. You don't need to delete the virtual hard drive, but just delete the VM and recreate it.

---

### Post by Jonners59 on 2010-10-17
> **CharlesA said:**
> The only thing I can think of is that you installed from a 32-bit livecd, instead of a 64-bit livecd. By default, you are directed to a download of the 32-bit version of Ubuntu from ubuntu.com.

You can select 64-bit from there, or just go to: [http://releases.ubuntu.com](http://releases.ubuntu.com) to find it there.

Note: If your machine didn't have Hardware virtualization enabled, it would not list 64-bit in VirtualBox.

What you could do before you completely switch installs to a 32-bit version of Windows is to recreate the virtual machine. You don't need to delete the virtual hard drive, but just delete the VM and recreate it.
Charles
I have now installed Windows 7 in the virtual partition.  I have also installed the ap (3CX) within the virtual machine, but need to be able to get to the other partitions in the main machine, so that I can back up and in this case access the config-backup to set up the application 3CX and use the wav files...  How do I do this?  There seems to be nothing available to take me outside the virtual partition.

Also no other machines appear in the network....

---

### Post by Jonners59 on 2010-11-03
Any help anyone, please????

---

### Post by CharlesA on 2010-11-03
Didn't see that. O_o

Make sure you are using bridged networking on the guest. It should be able to see the host's network.

---

### Post by Jonners59 on 2010-11-03
> **CharlesA said:**
> 
Make sure you are using bridged networking on the guest. It should be able to see the host's network.
Yup, I have that set up....  I am wondering.

The PC does not see the rest of the network, nor can the others see it.  The Share function states it is missing packages.  I have a thread out on this already, but no solutions.  COULD this be the cause????

Also, what of the strange behaviour of the application.  I know you may not know much about the app, but it should work as normal within the virtual machine, surely.  So where are these wav files and why is it not able to send e Mails....  Could it be linked to the above???????

---

### Post by CharlesA on 2010-11-03
Is it even getting an ip address?

```
ifconfig eth0
```

It's probably linked to it not being able to see the network.

---

### Post by Jonners59 on 2010-11-03
Yes, it is...  And it can see the internet.

---

### Post by CharlesA on 2010-11-03
Hrm.

Are you able to ping the other machines by hostname or ip address?

---

### Post by Jonners59 on 2010-11-05
> **CharlesA said:**
> Hrm.

Are you able to ping the other machines by hostname or ip address?

Yes, in both directions.

The Virtual machine can not see any of the drivers (they are not in the usual places in Windows) that reside on the Server.  It can not see the host machine in Network places either.

The host machine can not see any other machine on the network and is not findable.

But all can PING all by IP Address

---

### Post by CharlesA on 2010-11-05
My bet is that it's a name resolution problem.

Do you have a DNS server somewhere?

---

### Post by Jonners59 on 2010-11-05
Only on the Broadband router, facing the public DNS.  See below

**DHCP Server Configuration** Enabled 
**DNS Server IP Address** Force DNS manual setting
Primary IP Address   4.2.2.2
Secondary IP Address  208.67.220.220

We use a fixed IP address assigned to the MAC address

---

### Post by CharlesA on 2010-11-05
Hrm. Try adding the ip address and hostname to the hosts file and see if that gets it to see that machine.

---

### Post by Jonners59 on 2010-11-05
> **CharlesA said:**
> Hrm. Try adding the ip address and hostname to the hosts file and see if that gets it to see that machine.

Sorry can you show me, please.

The PC I am on is called BaroniPC and its IP address is 192.168.1.62

The "Server" PC is called Server and its IP address is 192.168.1.50

WHere and how do I do what you suggest

---

### Post by CharlesA on 2010-11-05
If it's a Linux box, hosts would be here: /etc/hosts

If it's a windows box, hosts would be here: c:\windows\system32\drivers\etc\hosts

---

### Post by Jonners59 on 2010-11-22
Hi CharlesA
Sorry, dissappeared off the radar.  Had to rebuild everything again!!!!!  Grrrr.
 
Still can't see the partitions on the host machine, but also noted that the VirtualBox, does not start the virtual machine automatically should a reboot occure.  This could be a great pain for me as the app is our telephone system and so if Ubuntu decides to do a restart or if we have a power outage (although very rare, we had a 1 minute outage last week) then we loose the phones in the house, until manual intervention.  If we are away on hols for a couple of weeks this could be disasterous.
 
Is there a way round this?

---

### Post by Jonners59 on 2010-11-25
Any help please????

---

### Post by CharlesA on 2010-11-25
> **Jonners59 said:**
> Hi CharlesA
Sorry, dissappeared off the radar.  Had to rebuild everything again!!!!!  Grrrr.
 
Still can't see the partitions on the host machine, but also noted that the VirtualBox, does not start the virtual machine automatically should a reboot occure.  This could be a great pain for me as the app is our telephone system and so if Ubuntu decides to do a restart or if we have a power outage (although very rare, we had a 1 minute outage last week) then we loose the phones in the house, until manual intervention.  If we are away on hols for a couple of weeks this could be disasterous.
 
Is there a way round this?

I use two scripts to stop/start any running virtual machines should I need to reboot the host.

Here's the stop script:

```
#!/bin/bash

###
### stopvm.sh
### Script to save state of VMs
### Created by CharlesA
### Tested 10/27/2010
### Updated 10/27/2010
###

USR=/usr/bin/
HOME=/home/charles/
LOGS=${HOME}logs/

echo > ${LOGS}savevm.log
if [[ -n $(${USR}VBoxManage -nologo list runningvms) ]]
then
for runningvms in $(${USR}VBoxManage -nologo list runningvms | ${USR}awk -F \" '{ print $2 }';)
do
echo Saving state of $runningvms >> ${LOGS}savevm.log && ${USR}VBoxManage -nologo controlvm $runningvms savestate >> ${LOGS}savevm.log
done
else
echo "No VMs running"
fi
# eof

```

Here's the start script:

```
#!/bin/bash

###
### startvm.sh
### Script to start saved VMs up
### Created by CharlesA
### Tested 10/27/2010
### Updated 10/27/2010
###

BIN=/bin/
USR=/usr/bin/
HOME=/home/charles/
LOGS=${HOME}logs/

for vms in $(${USR}VBoxManage -nologo list vms | ${USR}awk -F \" '{ print $2 }';)
do
if [[ -n $(${USR}VBoxManage showvminfo $vms | ${BIN}grep saved) ]]
then
${USR}VBoxHeadless -s $vms > /dev/null &
fi
done
# eof
```

One thing to note about both these scripts, you need to run them as the user that is running the virtual machines else it won't find any running. I couldn't find a way around that since that's the way that VirtualBox handles who owns a VM.

I have the startvm.sh script set in a crontab like so:

```
# Start Saved VMs after reboot
@reboot ~/scripts/startvm.sh > /dev/null 2>&1

```

If you have a chance of losing power, it would probably be a good idea to get a UPS if you don't already have one.

---

### Post by Jonners59 on 2010-11-25
Charles
many thanks....  I have never created scripts before.  How do I install these.  Are they just pasted in a terminal or what?

I see your machine is called home/charles

This particular machine is called home/server

---

### Post by CharlesA on 2010-11-25
Open something like gedit and paste them in there, then save them as a file and mark them as executible.

Change yer home directory in HOME=/home/charles to whatever yer home directory is.

If you don't want a log, remove the LOG variable.

---

### Post by Jonners59 on 2010-11-26
Cheers
Done all this....  I saved them as startvm and stopvm and put them in my /home/server/  folder  Then ran the cmd lines in terminal

# Start Saved VMs after reboot
@reboot ~/scripts/startvm.sh > /dev/null 2>&1

Is this correct?

---

### Post by CharlesA on 2010-11-26
You'd have to add those to crontab like so:

```
crontab -e
```

Add it under the text. You need to path to where you placed the script, so if it's in /home/server, it would look like this:

```
@reboot ~/startvm.sh > /dev/null 2>&1
```

---

### Post by Jonners59 on 2010-11-26
Ooohh  hope this works...  was thrown by the terminal!

---

### Post by CharlesA on 2010-11-26
If you run into any problems, let me know. Since my VM host has no GUI, I had to alias halt and reboot to run the script before issuing sudo reboot/sudo halt.

---

### Post by Jonners59 on 2010-11-27
Charles
No, did not work.  Also still can not see the partitions on the 2nd Hard drive.  I have just these two problems with the vm.  The second would not be such a headache if it was not for one of my other threads, the inability to create a network, where every machine on it can see these partitions because then I could use the LAN.

I am so frustrated.  Nothing is simple.

---

### Post by CharlesA on 2010-11-27
What exactly are you trying to do?

---

### Post by Jonners59 on 2010-11-27
> **CharlesA said:**
> What exactly are you trying to do?

I am assuming Charles, you want to know the whole sad story, so:

We (the family and my one man business) have 5 PCs and Laptops, plus one PC we call a server where we store all our documents, pictures, videos, etc.  Plus one laptop in Italy (my wife is Italian so we spend much time there).

All the PCs and Laptops run Ubuntu 10.4 or 10.10 except one PC, my wife's which currently (because she will not let me touch it) runs Windows XP Pro and the Laptop in Italy that runs XP Home, but will change as soon as I can get everything else sorted.

I would like all machines to see each other and share files, etc, just because it makes life easier and is a nice to have.

I want all to see and have full access to the PC called server and for it to see all of them, so we can store and share from the server.

The server has 3 x hard drives:
1 x hard drive is for the OS
1 x hard drive is partitioned in to 7, 1 for each use I.e. shared, mine, my wife's, the kids, my wife's teaching, the business, etc.....
1 x hard drive in 2 partitions.  A small one for saving configs and the majority for backup of the 2nd hard drive (the documents, etc.

The server has the virtualbox to run Windows 7 which in turn runs our telephone system, 3CX - ONLY.  I need the vm to see the small partition on the 3rd hard drive so it can save a config file/backup and another partition on the 2nd hard drive to save voice mails.

I would also like to use the server as a media centre, so we can start to store and share films, Tv, etc.  We have just bought a new Tv that has LAN access for media viewing (it can't even see the server at present).

Then I would also like to set up a VPN, so when we are in Italy I can gain access to everything or if I am working from a clients offices using my laptop, plus to extend the telephone system.  I had this in Windows but it's all stopped since Ubuntu.

Lastly I want to have a backup and increase security from external sources, just in case.

Where have I got to:
Most machines have Ubuntu on them, and operate on their own OK, and the VM is working as is the phone system...  Some machines seems to be able to share info, but not all and certainly not the most imporatnt, the server.  We have no Media centre, no VPN, no backup and the VM for the phone system will not reboot if the server has to do a restart. So not very far!:(:(

---

### Post by CharlesA on 2010-11-27
> **Jonners59 said:**
> The server has 3 x hard drives:
1 x hard drive is for the OS
1 x hard drive is partitioned in to 7, 1 for each use I.e. shared, mine, my wife's, the kids, my wife's teaching, the business, etc.....
1 x hard drive in 2 partitions.  A small one for saving configs and the majority for backup of the 2nd hard drive (the documents, etc.

That's a hell of a setup. The way I did mine was to have 1 huge drive partitioned as one chunk and create separate folders for each user. I'm using Samba at the moment, but I have the file permissions locked down so that only they have full access to their files.

That would probably be the easiest way to do it unless you need to have a separate partition for each user.

> The server has the virtualbox to run Windows 7 which in turn runs our telephone system, 3CX - ONLY.  I need the vm to see the small partition on the 3rd hard drive so it can save a config file/backup and another partition on the 2nd hard drive to save voice mails.

I know you can mount a "raw" physical drive in VirtualBox, but it takes a bit of work. [This]("http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/") should get you started. :)

> I would also like to use the server as a media centre, so we can start to store and share films, Tv, etc.  We have just bought a new Tv that has LAN access for media viewing (it can't even see the server at present).

That's what mine is being used for as well. I had to run a local DNS server to get the machines to see each other. I am using [DNSMasq]("https://help.ubuntu.com/community/Dnsmasq") for my local DNS server, since I have a small network and running BIND would be overkill.

> Then I would also like to set up a VPN, so when we are in Italy I can gain access to everything or if I am working from a clients offices using my laptop, plus to extend the telephone system.  I had this in Windows but it's all stopped since Ubuntu.

I'm not quite sure how you can do it, since the way I connect to my home machines while away is to use SSH Tunnels/SFTP, and not a true VPN.

> Lastly I want to have a backup and increase security from external sources, just in case.

I have a script that runs every morning at 2am to backup my server to external media. It uses rsync to do the backups. Works like a charm for me.

You might take a look at [RLB (rsync local backup)]("http://silverwav.wordpress.com/2010/01/15/rsync-local-backup/") that [SilverWave]("http://ubuntuforums.org/member.php?u=210358") developed, it's quite nice. :)

> Where have I got to:
Most machines have Ubuntu on them, and operate on their own OK, and the VM is working as is the phone system...  Some machines seems to be able to share info, but not all and certainly not the most imporatnt, the server.  We have no Media centre, no VPN, no backup and the VM for the phone system will not reboot if the server has to do a restart. So not very far!:(:(

Can you give me a bit more info about the way the server is set up? Does it have a GUI installed or anything?

I found a guide [here]("http://ubuntuforums.org/showthread.php?t=1078689"), for saving the state of virtual machines if you logout or reboot, but it was written for someone with a GUI.

I wrote my script because I didn't have a GUI on my machine and couldn't get that one to work for me.

But yeah, see the links throughout my reply. :)

---

### Post by Jonners59 on 2010-11-27
Thanks Charles

That's a great deal of feedback and appreciate the effort.  I have just slopped off to try and install the media centre stuff.  I was recommended minidlna, as dlna is required for the Tv.  No real instructions or install.  Just extracted a folder within which are more folders and files, but that's it, so stuck!  So just about to give up for the day!

I'll take a slow walk through all this over the next few days and see where I get too.

A big thank you.

---

### Post by CharlesA on 2010-11-27
The only DLNA server software I am familar with is PS3MediaServer, but I don't know if it would work with yer TV.

---

### Post by Jonners59 on 2010-12-01
> **CharlesA said:**
> That's a hell of a setup. The way I did mine was to have 1 huge drive partitioned as one chunk and create separate folders for each user. I'm using Samba at the moment, but I have the file permissions locked down so that only they have full access to their files.
 
That would probably be the easiest way to do it unless you need to have a separate partition for each user.:)
 
I would like for all to have their own partition. They are also on their own Hard Drive (750G) and the Back up is on its own (1Tb), and the OS, Windows and Ubuntu on theirs (350Gb). I can take out the HD for Backup and partitions and use in other machines and all sorts..... Suites me.
 
> **CharlesA said:**
>  
I know you can mount a "raw" physical drive in VirtualBox, but it takes a bit of work. [This]("http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/") should get you started. :)
 
I followed this link and tried it out - took the two scripts you gave me out and put them on the desktop. But it did not work. It did nothing at all. After reboot I still have to start the virtual machine (Windows 7 with my 3CX). I left a message on that Thread. See if I get a reply.
 
> **CharlesA said:**
>  
That's what mine is being used for as well. I had to run a local DNS server to get the machines to see each other. I am using [DNSMasq]("https://help.ubuntu.com/community/Dnsmasq") for my local DNS server, since I have a small network and running BIND would be overkill.:)
 
Before I tried your suggestion, I managed to get the server to appear on the Tv as "DNLA Server:root", but no files or folders. After installing the DNS all the folders appeared and we can view the pics and videos.
 
Interesting I lost all the access to the partitions via the PCs and Laptops (again) a couple of days ago after trying to install miniDNLA, sadly the DNS did not put them back for them. I get a DBus error or "Server Shares not available". I need to update my other Thread re this. Thanks for the fix though!!!
 
> **CharlesA said:**
>  
I'm not quite sure how you can do it, since the way I connect to my home machines while away is to use SSH Tunnels/SFTP, and not a true VPN.:)
 
I will work on the VPN later... More pressing stuff to get through now.
 
> **CharlesA said:**
>  
I have a script that runs every morning at 2am to backup my server to external media. It uses rsync to do the backups. Works like a charm for me.
 
You might take a look at [RLB (rsync local backup)]("http://silverwav.wordpress.com/2010/01/15/rsync-local-backup/") that [SilverWave]("http://ubuntuforums.org/member.php?u=210358") developed, it's quite nice. :)
 
Mmm. I will look at those in the repositories. In Windows there was a great little app I bought, can't quite recall the name. Partition commander or something. It created an exact image of ANY hard drive and could put it on any other or a partition, whatever was wanted. Would love an Ubuntu version! Seen nothing like it so far.
 
> **CharlesA said:**
>  
Can you give me a bit more info about the way the server is set up? Does it have a GUI installed or anything? :)
 
Not really a server, it is a PC running Ubuntu and called server (see earlier threads and replies). I use it like a server. I.e. a central repository and I run my PBX off it, and future media too, but that is it. It has an AMD 64-bit processor, 4Gb RAM, though that needs more grunt. and three hard drives see above....
 
> **CharlesA said:**
>  
I found a guide [here]("http://ubuntuforums.org/showthread.php?t=1078689"), for saving the state of virtual machines if you logout or reboot, but it was written for someone with a GUI.
 
I wrote my script because I didn't have a GUI on my machine and couldn't get that one to work for me.
 
But yeah, see the links throughout my reply. :)
 
Please see above....

---

### Post by CharlesA on 2010-12-01
> **Jonners59 said:**
> I would like for all to have their own partition. They are also on their own Hard Drive (750G) and the Back up is on its own (1Tb), and the OS, Windows and Ubuntu on theirs (350Gb). I can take out the HD for Backup and partitions and use in other machines and all sorts..... Suites me.

I see. I've heard that setting up Samba and using forceuser helps to get around the permissions problems, but I'm not quite sure how a setup like that would look like.
 
> **Jonners59 said:**
> I followed this link and tried it out - took the two scripts you gave me out and put them on the desktop. But it did not work. It did nothing at all. After reboot I still have to start the virtual machine (Windows 7 with my 3CX). I left a message on that Thread. See if I get a reply.
 
My scripts are meant to be run headless, I'll poke around and see what needs to be done to get them to work on a machine running with a GUI.

I cannot recall if you are using VirtualBox OSE (from the repos) or the version from virtualbox.org. Which one are you using?
 
> **Jonners59 said:**
> Before I tried your suggestion, I managed to get the server to appear on the Tv as "DNLA Server:root", but no files or folders. After installing the DNS all the folders appeared and we can view the pics and videos.
 
Interesting I lost all the access to the partitions via the PCs and Laptops (again) a couple of days ago after trying to install miniDNLA, sadly the DNS did not put them back for them. I get a DBus error or "Server Shares not available". I need to update my other Thread re this. Thanks for the fix though!!!

Looks like you got that working per the other [thread]("http://ubuntuforums.org/showthread.php?t=1630547").
 

> **Jonners59 said:**
> Mmm. I will look at those in the repositories. In Windows there was a great little app I bought, can't quite recall the name. Partition commander or something. It created an exact image of ANY hard drive and could put it on any other or a partition, whatever was wanted. Would love an Ubuntu version! Seen nothing like it so far.

I know there are different types of backup software in the repos, but IMO, using RLB would bet he best way to do it, as it is easy to setup and configure. 

 
> **Jonners59 said:**
> Not really a server, it is a PC running Ubuntu and called server (see earlier threads and replies). I use it like a server. I.e. a central repository and I run my PBX off it, and future media too, but that is it. It has an AMD 64-bit processor, 4Gb RAM, though that needs more grunt. and three hard drives see above....

I saw the screenshot in the OP. So it's running 10.04 Desktop, at the moment, right?

---

### Post by Jonners59 on 2010-12-01
> I see. I've heard that setting up Samba and using forceuser helps to get  around the permissions problems, but I'm not quite sure how a setup  like that would look like.
How would I set it up...?
I get error messages from the other machines such as DBus error or no Server shares.  The PC does not appear in the Windows network either.

> My scripts are meant to be run headless, I'll poke around and see what  needs to be done to get them to work on a machine running with a GUI.

I cannot recall if you are using VirtualBox OSE (from the repos) or the version from virtualbox.org. Which one are you using?

I downloaded it.  It is version 3.2.10 r66523

> I saw the screenshot in the OP. So it's running 10.04 Desktop, at the moment, right?

Yes, 10.4 LTS  lucid

---

### Post by CharlesA on 2010-12-01
It's definitely a name resolution thing, then.

Does this return anything?

```
smbtree
```

Also, I posted a quick and dirty script in the [other thread]("http://ubuntuforums.org/showthread.php?p=10187368#post10187368").

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> It's definitely a name resolution thing, then.

Does this return anything?

```
smbtree
```Also, I posted a quick and dirty script in the [other thread]("http://ubuntuforums.org/showthread.php?p=10187368#post10187368").

Cheers Charles
Yes, looked at that and I hope is now cleared.

The out put of above:
[HTML]server@server:~$ smbtree
Enter server's password: 
failed tcon_X with NT_STATUS_NO_SUCH_USER
failed tcon_X with NT_STATUS_NO_SUCH_USER
server@server:~$ [/HTML]Not good.

The partitions appear on the media directory.  I.e. /media/WinC
If I do a properties and look at permissions it states owned by root and group is plugdev

When I try and create share, it gives error message: Could not change the permissions of folder "WinC"

I am guessing that IF I could take ownership of the drive I could then make share.... AND maybe it will then work.

---

### Post by CharlesA on 2010-12-02
We can deal with the permission problem in a bit.

Did testparm return any errors?

Did you add the users with ***smbpasswd -a username*** ?

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> How do you have the drive mounted?
The drive mounts automatically.  I had a thread some time ago that gave me some settings to create the auto mount.....

[http://ubuntuforums.org/showthread.php?t=1537068](http://ubuntuforums.org/showthread.php?t=1537068)

---

### Post by CharlesA on 2010-12-02
Edited my post, It looks like everything is mounted correctly, but you'd probably have to change the owner/group of the mountpoint, unless the permissions were set to 777 (drwxrwxrwx).

Anyhow, Did you see the edit I made to my previous post?

I've written up a "short" tutorial on getting samba installed and configured if you want to try it. It can be found [here]("http://charlesa.net/tutorials/samba.php"). It's probably not the best, but it worked for me when I was testing it while writing it up.

---

### Post by Jonners59 on 2010-12-02
Charles
No I didn't

Test perm errors?  explain, please

[HTML]Did you add the users with smbpasswd -a username ?[/HTML]  No, how?

---

### Post by CharlesA on 2010-12-02
Basically, if you run testparm and it doesn't spit back any errors you are fine. If it finds an error it'll let you know.

As for adding a password, the syntax is:

```
sudo smbpasswd -a username
```

Where username is whatever username you want to assign a smb password to.

EDIT: Could you make another thread, as this one is getting a bit offtopic since it looks like you got VirtualBox running.

---

### Post by Jonners59 on 2010-12-02
> **CharlesA said:**
> Basically, if you run testparm and it doesn't spit back any errors you are fine. If it finds an error it'll let you know.

As for adding a password, the syntax is:

```
sudo smbpasswd -a username
```Where username is whatever username you want to assign a smb password to.

EDIT: Could you make another thread, as this one is getting a bit offtopic since it looks like you got VirtualBox running.

Already have one.  I got it working then (as per my reply some messages below) it all stopped when adding multi media and my Tv...

---

### Post by CharlesA on 2010-12-02
> **Jonners59 said:**
> Already have one.  I got it working then (as per my reply some messages below) it all stopped when adding multi media and my Tv...
It's hard to follow since there are a ton of different problems cropping up. :(

I think the best way to go about it is to take one problem at a time and go from there.

---

