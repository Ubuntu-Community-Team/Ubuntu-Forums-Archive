---
title: "How to identify if my ubuntu has virtual server into it"
date: 2022-10-09
forum: Virtualisation
---

### Post by cifuentesatilio on 2022-10-09
Hello community,

Beforehand thank you for your answers.

Context:
Some months ago the company fired the person in charge of IT and good/sadly I am support them while they hired a new one, into the "transition" that the company requested to him was that he needed to left the credentials and the information of where are the servers installed, until here all good but this person just messed up with all and left mixed and "wrong" information and just extended many things to not provide the correct information so, right now we can't we into some servers because he didn't left some credentials and some locations of the servers or how he "start again" those servers when he got errors (and he got a lot); you can think you have an issue and a bad transition, and yes but right now we want to solves, so all the blames we will accepted.

----

With this context I am very worried because we can't identify some servers, I can't get where the server is (host) because we have the IP but when we looked for them there are not into the servers farm, so we expect that these servers are virtualized or in some cases dockerized (this is the least) and my question is how can I identify or find this servers into ubuntu?

I was looking for docker but when I executed "docker info" I didn't get any container upload and I don't know how to look for virtual servers into ubuntu.

Please let me know if you need more information.

Thank you,

---

### Post by MAFoElffen on 2022-10-09
If it is Ubuntu and has VM's running, most likely it is running KVM/QEMU.

To check if KVM is installed
```

systemctl status libvirtd

```
Press <Q> to exit If it is...

If so, then to list running VM's
```

virsh list

```
To list all VM's, even if unloaded
```

virsh list -all

```
To find the IP address for that Server, to ssh into it, then get the name from that list of that running VM, example Server_Fred
```

virsh domifaddr Server_Fred

```

---

### Post by The Cog on 2022-10-09
Those virsh and systemctl commands above need running with sudo.
Also, if either docker or podman are installed then you probably have containers installed.
podman is pretty-much command compatible with docker, written by Red Hat.
```
sudo docker images
sudo podman images
```
Podman can run images without root, so if that's installed you may have to try **podman images** for each each user on the system to find them.

Remember that if you have an IP address and it's on the local network then the command **ip neighbor** will give the MAC address, which may help figure out which physical machine the IP address it is on.

---

### Post by TheFu on 2022-10-09
'virsh' doesn't need sudo, unless it is setup wrong.  

Group membership in the libvirt or libvirtd (depends on the OS release) is all that is needed for any userid to manage VMs that use virsh or virt-manager or any libvirt control tool.

Besides VMs and Docker, there are lxc containers.  To see those, assuming an lxd install:
```
$ lxc list --all
```

There are other hypervisors. Each will have their own control interface.  I'd search the installed packages on each host for some commonly used terms to get a clue quickly.
```
$ dpkg -l "*virtual*"
$ dpkg -l "*qemu*"
$ snap list --all 
```
LXD is only shipped as a snap package.
If qemu/KVM are installed, you have a family of possible controllers for the hypervisor.

Whenever firing an admin, all the relevant information needs to already be known and cataloged.  Best not to provide advanced information either.  When I worked as an admin, I had paper "run books" which documented key changes to each system.  I also had a CMDB - for each system. That would clearly have hardware, software, and if it was a virtual machine.  Top organizations do this, but a 1-man shop who actually is a profession should too.  

Planning and documentation should be sufficient so that if 1 person is killed in a bus accident today, the business isn't screwed.  Additionally, all passwords need to be securely stored and available to key management.  I have a "work" keePassXC DB and refresh that monthly with the VP of Operations/CIO who just keeps the file and knows how to unlock it, but never has.  There are hundreds of credentials in that DB - including license keys, contacts, warranty information, company credit card contacts and credentials.  Basically, anything that I won't place into the run-book.  My peers do the same for system/deployment logins.  We don't share personal logins.   Systems don't usually have a root account, so those credentials aren't shared. We use sudo and by policy, nobody abuses it to become root. This way, all commands are logged using normal sudo command logging.  Each system has a primary admin, so we don't step on each other's toes.

The CMDB can be a formal tool, if the company likes "cheese".  I just dump 'lshw' and 'inxi -Fxx' output into files that are included in the nightly backup for each system. Other system data is captured in the backups too, mainly to make solving other issues easier.  For example, a machine readable dump of all partition tables for all storage happens.  Should any storage fail, we have the exact specifications for the replacement storage and can layout the partitions EXACTLY using that saved information in 1 sgdisk command.  Very convenient and prevents mistakes.

---

### Post by MAFoElffen on 2022-10-09
> **MAFoElffen said:**
> [COLOR=#ff0000]If it is Ubuntu[/COLOR] and has VM's running...
Note the first four words...
```

mafoelffen@Mikes-ThinkPad-T520:~$ systemctl status libvirtd
&#9679; libvirtd.service - Virtualization daemon
     Loaded: loaded (/lib/systemd/system/libvirtd.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2022-10-09 08:42:35 PDT; 14min ago
TriggeredBy: &#9679; libvirtd-ro.socket
             &#9679; libvirtd.socket
             &#9679; libvirtd-admin.socket
       Docs: man:libvirtd(8)
             https://libvirt.org
   Main PID: 1119 (libvirtd)
      Tasks: 32 (limit: 32768)
     Memory: 25.2M
        CPU: 24.288s
     CGroup: /system.slice/libvirtd.service
             &#9500;&#9472;1119 /usr/sbin/libvirtd
              &#9500;&#9472;1346 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/Isolated_Net_192.conf  --leasefile-ro --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
              &#9500;&#9472;1347 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/Isolated_Net_192.conf  --leasefile-ro --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
              &#9500;&#9472;1388 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/NAT_Network_172.conf --leasefile-ro  --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
              &#9500;&#9472;1389 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/NAT_Network_172.conf --leasefile-ro  --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
              &#9500;&#9472;1430 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro  --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
              &#9500;&#9472;1431 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro  --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
              &#9500;&#9472;1469 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/Routed_Net_172.conf --leasefile-ro  --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
              &#9492;&#9472;1470 /usr/sbin/dnsmasq  --conf-file=/var/lib/libvirt/dnsmasq/Routed_Net_172.conf --leasefile-ro  --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper

Oct 09 08:44:51 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPREQUEST(virbr0) 192.168.122.186 52:54:00:92:d4:7b
Oct 09 08:44:51 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPACK(virbr0) 192.168.122.186 52:54:00:92:d4:7b Michaels-iMac
Oct 09 08:48:31 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPREQUEST(virbr0) 192.168.122.180 52:54:00:86:5a:38
Oct 09 08:48:31 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPACK(virbr0) 192.168.122.180 52:54:00:86:5a:38
Oct 09 08:49:35 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPDISCOVER(virbr0) 52:54:00:27:4d:dd
Oct 09 08:49:35 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPOFFER(virbr0) 192.168.122.131 52:54:00:27:4d:dd
Oct 09 08:49:35 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPDISCOVER(virbr0) 52:54:00:27:4d:dd
Oct 09 08:49:35 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPOFFER(virbr0) 192.168.122.131 52:54:00:27:4d:dd
Oct 09 08:49:35 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPREQUEST(virbr0) 192.168.122.131 52:54:00:27:4d:dd
Oct 09 08:49:35 Mikes-ThinkPad-T520 dnsmasq-dhcp[1430]: DHCPACK(virbr0) 192.168.122.131 52:54:00:27:4d:dd darkstar

```
```

mafoelffen@Mikes-ThinkPad-T520:~$ virsh list
 Id   Name               State
----------------------------------
 1    macOS-Simple-KVM   running
 2    android-x86-9.0    running
 3    fedora             running
 4    slackware15        running

mafoelffen@Mikes-ThinkPad-T520:~$ virsh list --all
 Id   Name                          State
----------------------------------------------
 1    macOS-Simple-KVM              running
 2    android-x86-9.0               running
 3    fedora                        running
 4    slackware15                   running
 -    debian11                      shut off
 -    ubuntu-2004-aarch64           shut off
 -    ubuntu-2004-aarch64-Desktop   shut off
 -    ubuntu-aarch64-template       shut off
 -    ubuntu18.04-aarch64           shut off
 -    ubuntu20.04                   shut off
 -    ubuntu20.04-10                shut off
 -    ubuntu20.04-11                shut off
 -    ubuntu20.04-2                 shut off
 -    ubuntu20.04-2-desktop         shut off
 -    ubuntu20.04-3                 shut off
 -    ubuntu20.04-4                 shut off
 -    ubuntu20.04-5                 shut off
 -    ubuntu20.04-6                 shut off
 -    ubuntu20.04-7                 shut off
 -    ubuntu20.04-8                 shut off
 -    ubuntu20.04-9                 shut off
 -    ubuntu20.04-ZFS               shut off
 -    ubuntu20.04-ZFS-02            shut off
 -    ubuntu20.04-ZFS-tester        shut off
 -    ubuntu22.04                   shut off
 -    Ubuntu22.04Daily              shut off
 -    ubuntu4.10                    shut off
 -    ubuntu5.04                    shut off
 -    ubuntu_server_18.04           shut off
 -    vm1                           shut off
 -    win11                         shut off
 -    windows10                     shut off
 -    windows11-Unsupported         shut off

mafoelffen@Mikes-ThinkPad-T520:~$ virsh net-list
 Name               State    Autostart   Persistent
-----------------------------------------------------
 default            active   yes         yes
 Isolated_Net_192   active   yes         yes
 NAT_Network_172    active   yes         yes
 Routed_Net_172     active   yes         yes

mafoelffen@Mikes-ThinkPad-T520:~$ virsh net-dhcp-leases default
 Expiry Time           MAC address         Protocol   IP address           Hostname            Client ID or DUID
---------------------------------------------------------------------------------------------------------------------------------------------------------
 2022-10-09 09:49:35   52:54:00:27:4d:dd   ipv4       192.168.122.131/24   darkstar            01:52:54:00:27:4d:dd
 2022-10-09 09:18:26   52:54:00:2d:ab:5b   ipv4       192.168.122.196/24   u-server-raid5-01   ff:56:50:4d:98:00:02:00:00:ab:11:d0:dc:38:e6:2a:5c:82:6d
 2022-10-09 09:48:31   52:54:00:86:5a:38   ipv4       192.168.122.180/24   -                   01:52:54:00:86:5a:38
 2022-10-09 09:44:51   52:54:00:92:d4:7b   ipv4       192.168.122.186/24   Michaels-iMac       01:52:54:00:92:d4:7b
 2022-10-09 09:39:44   52:54:00:a2:d2:98   ipv4       192.168.122.253/24   ubuntuarm01         ff:56:50:4d:98:00:02:00:00:ab:11:cc:5e:ae:1f:25:0c:a5:62

```
You do not need to use 'sudo' if just checking status of a daemon... And if Ubuntu, then you do not need 'sudo' to use 'virsh' commands, if the user is a member of groups libvirt and kvm. With other Distros, you do need to use sudo....

***
Agreed with 'TheFu'. On my Last Sys Admin job, I had to write Job Books for every server. How to do things, maintenance, inventory, config's of what was on/in each machine (software and accesory), whether on metal or VM. Schedules of jobs. Current Storage reports. Scripts for those jobs... All aspects of my job. ETC. All current passwords in a report, and were kept locked physically in their safe, with one copy of the backups, job books, the disaster recovery manual, router and wireless AP config's, Bootable usb keys for each physical server. A copy of all those were also kept at a secure location offsite.

Documentation is everything. Physical security of computers, access keys, manuals, etc. is paramount.

I was the only IT person. If I died or was or somehow not physically available, business had to go on. I made sure that everything was secure, and prepared for a disaster. Me not being available was a factor, in a disaster. 

When I left that position, one of the things I had to do, was to make sure someone there could read the job books and do what was there to get into everything and do what was in all those books and manuals.

---

### Post by cifuentesatilio on 2022-10-09
Hello everyone,

Thank you for your guide, I have been searching in the servers and unfortunately I hadn't found anything yet.

In all the cases when I ran systemctl status libvirtd the result was "Unit libvirtd.service could not be found.", also th virsh or virt-what instruction said the same as not be installed.

with lxc list also didn't found or show anything in the results.

with dpkg -l "*virtual*" almost all the cases shows the follow information:

[FONT=Helvetica]Desired=Unknown/Install/Remove/Purge/Hold[/FONT]
[FONT=Helvetica]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT]
[FONT=Helvetica]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/FONT]
[FONT=Helvetica]||/ Name                       Version      Architecture Description[/FONT]
[FONT=Helvetica]+++-==========================-============-============-=================================[/FONT]
[FONT=Helvetica]un  lxc-docker-virtual-package <none>       <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtualbox-guest-dkms      <none>       <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtualbox-guest-modules   <none>       <none>       (no description available)[/FONT]

and others gave me the result:

[FONT=Helvetica]Desired=Unknown/Install/Remove/Purge/Hold[/FONT]
[FONT=Helvetica]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT]
[FONT=Helvetica]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/FONT]
[FONT=Helvetica]||/ Name                      Version            Architecture Description[/FONT]
[FONT=Helvetica]+++-=========================-==================-============-==================================[/FONT]
[FONT=Helvetica]un  python-virtualenv         <none>             <none>       (no description available)[/FONT]
[FONT=Helvetica]ii  python3-virtualenv        20.0.17-1ubuntu0.4 all          Python virtual environment creator[/FONT]
[FONT=Helvetica]un  virtual-mysql-client      <none>             <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtual-mysql-client-core <none>             <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtual-mysql-server      <none>             <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtual-mysql-server-core <none>             <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtualbox-guest-dkms     <none>             <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtualbox-guest-modules  <none>             <none>       (no description available)[/FONT]
[FONT=Helvetica]ii  virtualenv                20.0.17-1ubuntu0.4 all          Python virtual environment creator[/FONT]

with the instruction dpkg -l "*qemu*" I didn't have results and with the instruction snap list --all I have the follow result in all the servers

[FONT=Helvetica]Name    Version        Rev    Tracking       Publisher   Notes[/FONT]
[FONT=Helvetica]core18  20220830       2560   latest/stable  canonical&#10003;  base,disabled[/FONT]
[FONT=Helvetica]core18  20220831       2566   latest/stable  canonical&#10003;  base[/FONT]
[FONT=Helvetica]core20  20220805       1611   latest/stable  canonical&#10003;  base,disabled[/FONT]
[FONT=Helvetica]core20  20220826       1623   latest/stable  canonical&#10003;  base[/FONT]
[FONT=Helvetica]lxd     4.0.9          22526  4.0/stable/&#8230;   canonical&#10003;  disabled[/FONT]
[FONT=Helvetica]lxd     4.0.9-8e2046b  22753  4.0/stable/&#8230;   canonical&#10003;  -[/FONT]
[FONT=Helvetica]snapd   2.57.1         16778  latest/stable  canonical&#10003;  snapd,disabled[/FONT]
[FONT=Helvetica]snapd   2.57.2         17029  latest/stable  canonical&#10003;  snapd[/FONT]

this is very very annoying because I really don't know where to look at.

---

Also with your comment 'TheFu' and 'MAFoElffen' I am 100% agree with both of you, the thing is this person (fired one) didn't has any documentation and right know we are looking in any document and server to find where is the applications and how he "has" until today configured, we have been working with some apps with critical operation to move to another servers but in this moment we started found issues almost every week with one virtual server and we have not found it to today.

As I said he left the credentials but in his "instructions" wasn't any location of the servers, so the only way to test were is every server has been turning off see what services are affected and document but we can't do that in the following weekends.

Thanks for your help.

---

### Post by TheFu on 2022-10-10
That provides some good information.  What I'd do is start building a CMDB for each system to get the count and size of each physical computer.

I'd run 'inxi -Fxx' on each box that I know and save the output into text files for each as a place to start.
```
mkdir ~/CMDB
inxi -Fxx > ~/CMDB/${hostname}.inxi
```

If the systems don't have virsh or qemu anything, then they don't have any QEMU/KVM-based hypervisor on them. Period.
If they have lxd, like your example shows, I'd run 'lxc list' to get a list of the Linux Containers.  There may be zero or there may be 100.
```
mkdir ~/CMDB
lxc list  > ~/CMDB/${hostname}.lxc-list
```

Another way to gather facts about systems is to use ansible's "fact gathering".  If you have more than 5 machines, it would be worth learning ansible.  But doing that is beyond what we'd do in these forums.  I think the output is in json, so it is easy to grep specific information from.

Companies want to sell you ansible, but you don't need/want any of the commercial stuff.  The normal CLI stuff, F/LOSS, does everything, and the gathering of system facts is freakishly impressive. Hundreds to thousands of things about each system are included.  Plus, ansible is an easy way to run the same command on 1, 5, 200, 2000 systems.  I'd planned to show the ansible command to gather facts, but sometime in the last few weeks, my ansible workstation appears to have gotten a new version of ansible which changed the interface enough that it isn't able to do the connections to the other systems here.  I've been using v2.9.x and somehow, it is running v3.8.10 which is a huge change.  I knew the API was changing and I've been avoiding those changes ... but it appears not well enough.  The good news is they document the changes, deprecation  methods for each release. [https://docs.ansible.com/ansible/latest/porting_guides/porting_guide_3.html](https://docs.ansible.com/ansible/latest/porting_guides/porting_guide_3.html) is an example.  Because ansible is only installed on 1 workstation for simple setups like mine, I don't need to setup anything beside ssh on all the other systems to use ansible.

Just thought of another hypervisor we haven't checked for - virtualbox.  
```
dpkg -l "*vbox*"
```
I really hope no server admin would use that, but noob admins might. It is worth a check.

BTW, you probably don't want to share all that CMDB information. Some sensitive stuff will be included which shouldn't be shared.

If no containers are running/installed, well, that's sorta good and bad.  It means that you haven't found all the physical system and/or the prior guy wasn't following best practices in isolating different core services from each other using VMs or containers.  lxd/lxc containers are just 1 method.  Docker, and 20 other container managers are possible. I don't use docker and have avoided after attending some classes which showed some of the warts, but the format it uses and the methods used by it are standards for most other containers ... but not lxd.  I use lxd, though it is far from perfect, it is closer to normal virtual machines than any other linux containers, so the migration from full virtual machines to containers going through lxd is relatively painless.  My main reservation with lxd is the snap packaging of the tool, not with the containers. They are light and fast like every other Linux container. Sigh.  If only the management tool wasn't locked inside snap packaging, I'd be much happier.

BTW, my CMDB scripts are run just prior to daily backups on each system. I need to capture a list of VMs and containers, it seems.

It would be helpful to know how many systems are involved.  The way we ask for information for 3 systems is different than the way we'd ask for information from 20 or 50 systems.

---

### Post by MAFoElffen on 2022-10-10
@TheFu - Re-look at his output. I know it's not in code tags, so you might have missed it...

In his output for 'dkg -l "*virtual" has:
```

[FONT=Helvetica]Desired=Unknown/Install/Remove/Purge/Hold[/FONT]
[FONT=Helvetica]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/FONT]
[FONT=Helvetica]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/FONT]
[FONT=Helvetica]||/ Name                       Version      Architecture Description[/FONT]
[FONT=Helvetica]+++-==========================-============-============-=================================[/FONT]
[COLOR=#008000][FONT=Helvetica]un  lxc-docker-virtual-package <none>       <none>       (no description available)[/FONT][/COLOR]
[COLOR=#ff0000][FONT=Helvetica]un  virtualbox-guest-dkms      <none>       <none>       (no description available)[/FONT]
[FONT=Helvetica]un  virtualbox-guest-modules   <none>       <none>       (no description available)[/FONT][/COLOR]

```
A clean Ubuntu Server with KVM/QEMU installed has this for the same (mine):
```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/tri>
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                Version      Architecture Description
+++-===================-============-============-===========>
un  cli-virtual-machine <none>       <none>       (no descrip>
~

```

So even though LXD comes on all Ubuntu servers, look at the green line where he had additional installed... So I would have him do this command, which would show all running LXD containers:
```

$ sudo lxc list -c ns,user.comment:comment

```
Which for no running would just have this output
```

+------+-------+---------+
| NAME | STATE | COMMENT |
+------+-------+---------+

```
But if they "are" running any containers, it would list additional lines for those...

Next, in all his output, he has the red highlighted lines, which are only present if they installed "VirtualBox"... But since the output is also with the Green hightlighted LXD/Docker line, they might be running "Docker Machine with VirtualBox"... so using the VirtualBox CLI:
```

vboxmanage list vms
vboxmanage list runningvms

```
Would show registered VM's from both Vagrant and Docker Machine with VirtualBox... and any running VirtualBox VM's

Just saying... I think he "is" on the right track so far.

---

### Post by TheFu on 2022-10-10
The virtualbox guest stuff seems to be lists on all Ubuntu. I don't think the client stuff is installed on the host system, but I haven't used vbox in about a decade and never on a Linux host.  I do recall that there are 
vboxmanage and VboxManage - binaries based on if the F/LOSS version is used or the one directly from Oracle with commercial aspects included.  Has that changed?

I'd hate to miss something because of a case sensitive search.  Basically, since 2010, I've been using KVM/qemu for a number of reasons after looking at nearly every other option and deciding they weren't as good for our needs or those of our clients.

---

### Post by MAFoElffen on 2022-10-11
You are right... Ubuntu repo's don't use the Oracle version of the CLI, is rather "VBoxManage" as the executable.

I got curious and spun up a 22.04 server and installed Docker, VirtualBox, and docker-machine... To see exactly what it installs and how to ID it... It has different output on "dpkg -l | grep 'virtual' " than the OP. None of the output had the VBox Client packages installed.

ID is
```

docker --version
VBoxManage --version
docker-machine --version

```
then with output from any of those digging deeper on each
```

sudo docker ps -a
sudo docker container ls -a
VBoxManage list vms
VBoxManage list runningvms
docker-machine ls

```

---

### Post by MAFoElffen on 2022-10-12
I have been thinking about this. We are guessing "what may be there" because we do not have enough information and we cannot see what is there.

'lxc-docker-virtual-package' is not an Ubuntu Repo package...

Inventory your servers by running the [UbuntuForums 'system-info']("https://github.com/UbuntuForums/system-info") script on each by running:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && chmod +x system-info && ./system-info

```
When it asks to upload to a pastebin, choose yes by typing the <Y><Enter> keys and write down the URLs to post here in a post...

In that report are sections for the repo's they are using and what manually installed packages are installed through APT, Snap and Flatpak. That will provide us the information to see what is installed on your server(s) in the way of a virtual host. That will guide us all in helping you find your VM Server(s).

---

### Post by MAFoElffen on 2022-10-14
What makes me curious is the presence of python 'virtulenv' packages installed on most of his servers.... virtualenv script opens/creates chroot environments.

If using those python virtualenv scripts, if there is an open chroot, then 
```

echo $VIRTUAL_ENV

```
...would show the Path to the active chroot.

If no chroot active, then that variable will not be populated.

---

### Post by TheFu on 2022-10-14
Does virtenv == chroot?  It doesn't in ruby or perl.  virtualenv doesn't require root, so it isn't using any chroot.

It just means that environment variables are set to put the requested python binaries and libraries before the system ones.   Sorta like changing the LD_LIBRARY_PATH order to pick up a specific shared library first.

> Virtualenv is a tool to create isolated Python environments quite like chroot jail on Unix systems. In a chroot, programs cannot access anything outside of chroot but in virtualenv as the name implies, it creates isolated environments only with respect to libraries, but the programs can still access the files and folders normally.
Reads to me to be similar to what ruby (rvm) and perl (perlbrew) tools accomplish.  They just manipulate environment variables. Nothing more.

---

### Post by MAFoElffen on 2022-10-15
Oh Okay... I see that now. 

I created a script to check if a system is a virtual host and list any guests of over a dozen different host services and also can ID if it is running in a virtualized environment as a guest and ID what virtual host system that is running in...

I know. I have too much time on my hands and I am going a bit stir crazy...
```

#!/bin/bash

## MAFoElffen, <mafoelffen@ubuntu.com>, 2022.10.12
## Find Virtual Hosts and it's Guest VMs
#

#################
### FUNCTIONS ###
#################

function CheckKVM() {
IsLibVirt=$(systemctl status libvirtd | grep 'Loaded: ' | awk '{print $2}')
if [ "$IsLibVirt" == "loaded" ]
then
    echo -e "The 'libirtd' daemon is loaded. Suspected using KVM/QEMU."
    
    # Test for KVM
    VirshVersion=$(virsh --version 2> /dev/null )
    KvmVersion=$(kvm --version 2> /dev/null )
    if [ !z $VirshVersion ]
    then
        echo -e "Virsh version: $VirshVersion" 
    fi
    if [ !z $KvmVersion ]
    then
        echo -e "KVM version: $KvmVersion" 
    fi
else
    echo -e "'libvirtd' daemon is not loaded."
fi
}

function CheckChroot() {
    PidList=$(sudo ls /proc/[1-9][0-9][0-9][0-9] | grep '/proc/' | sed 's/://g' | sed 's/\/proc\///g' )
    
    for Pid in "${PidList[@]}"
    do
        ChRootTest=$(sudo -la /proc/$Pid/root | grep '/proc/' | awk '{print $11}' )
        if [ "ChRootTest" != "/" ]
        then
            echo "PID: $Pid is a chroot"
        fi
    done
}

function CheckFromSnap() {
    SnapList=$(sudo snap list | grep -e 'lxd\|docker' | awk '{print $1}' )
    if [ !z $SnapList ]
    then
       for Snap in "${SnapList[@]}"
       do
           if [ "$Snap" == "docker" ]
           then
               DockerVersion=(docker --version 2> /dev/null )
               echo "Docker Version: $DockerVersion"
               # Docker List
               sudo docker ps -a
               sudo docker container ls -a
               DmVersion=$(docker-machine --version)
               if [ !z $DmVersion ]
               then
                   echo "Docker-Machine Version: $DmVersion"
                   docker-machine ls
               fi
           elif [ "$Snap" == "lxd" ]
           then
               LxdVersion=$(lxd --version 2> /dev/null )
               echo "LXD Version: $LxdVersion"
               lxc list -c ns,user.comment:comment
           fi
       done 
    fi
}

function CheckVBox() {
    VBoxVersion=$(VBoxManage --version 2> /dev/null )
    VBoxListVMs=$(VBoxManage list vms 2> /dev/null )
    VBoxListRunning=$(VBoxManage list runningvms 2 > /dev/null )
    if [ !z $VBoxVersion ]
    then
        echo "VirtualBox Version: $VBoxVersion"
        echo $VBoxListVMs
        echo $VBoxListRunning
    fi
}

function CheckPodman() {
    PmVersion=$(podman version 2> /dev/null)
    if [ !z $PmVersion ]
    then 
        echo "Podmand Version: $PmVersion"
    fi
}


function CheckAcrn() {
    # acrn
    AcrnVersion=$(acrn version 2> /dev/null )
    AcrnList=$(acrn vm_list 2> /dev/null )
    if [ !z $AcrnVersion ]
    then 
        echo "Acrn Version: $AcrnVersion"
        echo $AcrnList
    fi
}

function CheckXen() {
    #xen
    if [ -f /sys/hypervisor/properties/capabilities ]
    then 
        awk '{print $0}' /sys/hypervisor/properties/capabilities
        CheckXl=$(xl info 2> /dev/null ) # newer versions of xen
        CheckXm=$(xm info 2> /dev/null ) # older versions of xen
        if [ !z $CheckXm ]
        then 
            echo "Xen Version Information: "
            echo $CheckXm
            xm list
        elif
        then
            echo "Xen Version Information: "
            echo $CheckXl
            xl list
        fi
    fi
}

function CheckVmware() {
    # Vmware Player List:
    VpVms=$(vmrun list 2> /dev/null ) # list all running virtual machines
    VpCons=$(vctl images 2> /dev/null ) #list all containers
    if [ !z $VpVms ]
    then
        echo $VpVms
    fi
    if [ !z $VpCons ]
    then
        echo $VpCons
    fi
    
    Vmw1=$(vmware -l 2> /dev/null ) #determine detailed buid number info for the lastest update applied for vmware hosts
    Vmw2=$(vmware -v 2> /dev/null ) # determine the build number of the vmware host
    if [ !z $Vmw1 ]
    then
        echo $Vmw1
    fi
    if [ !z $Vmw2 ]
    then
        echo $Vmw2
    fi

    Esxi1=$(esxupdate info 2> /dev/null ) # To view the  build numbers of RPMs and VIB of the path bundles
    Esxi2=$(esxupdate query 2> /dev/null )
    if [ !z $Esxi1 ]
    then
        echo $Esxi1
        echo $Esxi2
        vmware-checkvm -h 2> /dev/null # from vmwtool, version of vms. Checks vmware host
        vmware-toolbox-cmd -v 2> /dev/null # version of vmware toolbox
        vmwtool version 2> /dev/null
        esxcli vm process list  2> /dev/null # list all vsphere vms on this system

        ## vSphere Via PowerCLI:
        # Connect-VIServer -Server ESXHostnameOrIPAddress
        # get-view -ViewType HostSystem -Property Name, Config.Product | select Name,{$_.Config.Product.FullName},{$_.Config.Product.Build} | ft -auto
    fi

}

function CheckOpenNebula() {
  # OpenNebula
  OnInfo=$(onehost list 2> /dev/null ) # List the host information
  if [ !z $onInfo ]
  then
      echo $OnInfo
      onevm list 2> /dev/null # List running instances
  fi
}

function CheckOpenVz() { 
    # OpenVZ
    vzlist -a  2> /dev/null# List all running instances
}

function CheckVagrant() {
    # Vagrant
    VgVer=$(vagrant --version 2> /dev/null )
    if [ !z $VgVer ]
    then
        echo $VgVer
        vagrant box list
    fi
}

function CheckOpenVz() {
    #openvz
    # openvz VERSION
    prlsrvctl info 2> /dev/null
}

function CheckProMox() {
    # ProMox
    qm list 2> /dev/null
    vzlist 2> /dev/null
    pveversion -v 2> /dev/null
}


## Running inside a virtual host section...

function IdVmHost() {
    # Test running inside of something
    test1=$(systemd-detect-virt -c) # Check if running inside a container and ID
    test2=$(systemd-detect-virt -v) # Check if running inside a VM and ID
    test3=$(systemd-detect-virt -r] # Check if running inside a chroot and ID

    if [ !z $test1 ]
    then 
        echo "Host is $test1"    
    elif [ !z $test2 ]
    then
        echo "Host is $test2"
    elif [ !z $test3 ]
    then
        echo "Host is $test3"
    else
        echo "Host unknown"
    fi
}

function IdVirtHost() {
    ## This covers ID of a virtual instance running in:
    # mafoelffen@Mikes-ThinkPad-T520:~$ systemd-detect-virt --list
    # none
    # kvm
    # amazon
    # qemu
    # bochs
    # xen
    # uml
    # vmware
    # oracle
    # microsoft
    # zvm
    # parallels
    # bhyve
    # qnx
    # acrn
    # powervm
    # vm-other
    # systemd-nspawn
    # lxc-libvirt
    # lxc
    # openvz
    # docker
    # podman
    # rkt
    # wsl
    # proot
    # pouch
    # container-other
    ##
    VirtList=$(systemd-detect-virt --list )

    for TestInstance in "${VirtList[@]}"
    do
        test=$(systemd-detect-virt $TestInstance)
        exit_code=$?
        if [ $exit_code -eq 0 ]
        then
           echo "The hypervisor of this VM is $TestInstance"
        else
           # echo "Not: $TestInstance" ## DEBUG
        fi
    done
}


############
### MAIN ###
############
CheckKVM
CheckChroot
CheckFromSnap
CheckVBox
CheckPodman
CheckAcrn
CheckXen
CheckVmware
CheckOpenNebula
CheckVagrant
CheckOpenVz
CheckProMox
IdVmHost
IdVirtHost


```

---

### Post by TheFu on 2022-10-15
The proprietary virtualbox uses VboxManage.  
The F/LOSS virtualbox uses vboxmanage.
Can't assume one or the other. Have to check for both.

Containers aren't virtualization ... but most people think of them the same way.

Why assume anyone would install docker via snap?  I wouldn't. If there were a choice, I wouldn't install lxd via snap either, though that is a safe assumptions.  What happens when lxd is istalled, but not working?  I have that problem all the time.  For example:
```
$ echo $SnapList
lxd
$ lxd --version
Command 'lxd' is available in '/snap/bin/lxd'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
lxd: command not found
```
So I run 
```
$ /snap/bin/lxd --version
Sorry, home directories outside of /home are not currently supported. 
See https://forum.snapcraft.io/t/11209 for details.
```
that's what I get. That's what I get for using NFS and mounting HOMEs somewhere that makes sense.

rkt [https://rocket.readthedocs.io/en/latest/Documentation/subcommands/run/](https://rocket.readthedocs.io/en/latest/Documentation/subcommands/run/) or the 10 other semi-popular container managers? Guess you need to draw the line somewhere.  Some have to be installed from source. I'd put them in /usr/local/bin/, but some people might keep them in their $HOME/bin/ instead.

Do people use chroot very often anymore, outside Linux Containers?  I only use them as a way to fix OS issues when I have to boot from alternate media, but the normal OS boot isn't happening.

---

### Post by MAFoElffen on 2022-10-15
@TheFu

On Oracle's version versus F/LOSS'es VirtualBOX, you reminded me again.

Thank you. My new blood pressure med's have me a bit manic in the morning. I can't help it. I have to do things. You are giving "that time" some purpose. If I didn't do "something" I think it would be driving my wife crazy watching me pacing. LOL

In 22.04 Server, if you select to install Docker during the new Live install, it installs as Snap. So I took that new twist/turn. I've done Docker a lot, but before only from installed via Docker's binaries. When Canonical and Docker first made their agreements, I tested Docker... Back on Ubuntu 12.04 and 14.04. Then they came up with all their spinoff products and tools they they claim you "need".... Just about the same time when VMware came up with all their must-have toolsets for vSphere. I honestly was surprised that it was installed as a Snap now from the install media.

LXD. I've been doing LXD since lxc and when they introduced it and it waspesource something that you had to add and install to make it work. When I was testing it when it was new, I remember me thinking that it was sort of like 'systmd.nspawn', but a whole lot less work. Now it something that is just there as default, and installed as a Snap... LXD says that it can do both containers and virtual machines. I honestly have not tied to run a virtual machine with LXD from the Library...

When Linux kernel took some "turns" and systemd came to RHEL Linux and then Debian, I did a lot of playing with 'systemd.nspawn', which I saw as a virtualized environment. I wrote a lot of scripts playing with that and testing for that... Exploring what it could do. It seemed like a chroot, but more. Before that, I used to do a lot with Debian's 'debootstrap'. But the came LXC, which was a lot less work, so... LOL

My son and I get into these discussions a lot. I am a promoter for virtual hosts and virtual machines. His job is Azure "Containers": building containers, managing how they run and the scheduling of container jobs. He started out through OKD.io- RH Openshift and Kubernetes.

This script was a first draft. I can add to it now... LOL

---

