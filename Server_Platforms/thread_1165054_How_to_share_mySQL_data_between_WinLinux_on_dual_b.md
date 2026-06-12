---
title: "How to share mySQL data between Win/Linux on dual boot?"
date: 2009-05-20
forum: Server Platforms
---

### Post by lucasprim on 2009-05-20
Hi there!

I`ve recently installed Ubuntu on my laptop and quickly installed Apache, PHP and mySQL. I`ve found the configuration files and it all works fine, except for mySQL but maybe that`s because I`m trying to perform some impossible operations...
I also use windows so I can use Dreamweaver/Fireworks in this same machine, and I also do some dev while on windows, and that includes modifying some database relationships and tables. When I go back to Ubuntu, I`d like to have the same database i`ve been working on windows so I tried to modify /etc/mysql/mysql.cnf to get data from /media/Dados/MYSQL (my windows data folder). But whenever I try to start the server, the process fails and the following message is displayed in the syslog:

May 20 09:01:43 lucasprim-laptop kernel: [ 3473.671831] type=1503 audit(1242820903.105:24): operation="inode_create" requested_mask="a::" denied_mask="a::" fsuid=0 name="/media/Dados/MYSQL/lucasprim-laptop.lower-test" pid=12879 profile="/usr/sbin/mysqld"
May 20 09:01:43 lucasprim-laptop kernel: [ 3473.714736] type=1503 audit(1242820903.149:25): operation="inode_permission" requested_mask="::rw" denied_mask="::rw" fsuid=112 name="/media/Dados/MYSQL/ibdata1" pid=12879 profile="/usr/sbin/mysqld"

Things i`ve tested and tried:
* /media/Dados automounts on every boot
* /media/Dados/ibdata file belongs to root (cannot chown) with -rwxrwxrwx permissions
* apparmor is already configured like this:   /media/Dados/MYSQL/ r,  /media/Dados/MYSQL/** rwk,

Thanks a lot for your help! ;)

---

### Post by koenn on 2009-05-20
looks like a (file) permission problem between the Windows and the Linux instance of mysql - but I could be way off, I'm not familiar with this sort of setup.
The Linux mysqld (actually, the account it runs under, probably 'mysql' or so)  will at least need read and write permissions to /media/Dados/MYSQ (and might have to have ownership) so you have to check that. It may proof impossible on (I presume) an NTFS volume, especially as the Linux accounts will not be know to the Windows (file)system, but it's worth a shot - you may be able to work around it with very loose security settings (everyone;write or so, use at your own risk)

The better way to do this would be to run mysql on a dedicated server, and manage it trough a remote SQL client or whatever front-end you fancy, both from Linux and from Windows.

Seeing that you're doing this on a laptop, and you can't cary a server around that easily, you may need also a remote access solution, eg vpn or ssh tunnels.

An alternative would be to run myssql in a virtual machine with network between the host and the guest OS.

---

### Post by koenn on 2009-05-20
oops, missed the part where you say > **lucasprim said:**
> 
* /media/Dados/ibdata file belongs to root (cannot chown) with -rwxrwxrwx permissions


you also mention /media/Dados/MYSQL - doesn't that contradict the /media/Dados/ibdata 

can you specify  
- what the mount point on the Linux system is exactly
- what permisions the mountpoint has
- what permissions are shown for the data under the mountpoint, i.e. what unix permissions do the directories and files that are on the Windows volume end up with when mounted

You may also have to check that your mount of the Windows filesystem occurs before the linux mysql daemon starts (it looks for db files during startup)

---

### Post by lucasprim on 2009-05-20
> **koenn said:**
> oops, missed the part where you say 

you also mention /media/Dados/MYSQL - doesn't that contradict the /media/Dados/ibdata 

can you specify  
- what the mount point on the Linux system is exactly
- what permisions the mountpoint has
- what permissions are shown for the data under the mountpoint, i.e. what unix permissions do the directories and files that are on the Windows volume end up with when mounted

You may also have to check that your mount of the Windows filesystem occurs before the linux mysql daemon starts (it looks for db files during startup)

oops, i made a mistake :P actually its /media/Dados/MYSQL/ibdata

- The mount point is located at /media/Dados
- Permissions are rwxrwxrwx trough all the path to /media/Dados/ibdata, ibdata included (but i haven't touched it, think its standard)

the mounting is automatic on boot and mysqldaemon always fails even when i try to manually start it (/etc/init.d/mysql start)...

Guess i'm gonna try that Virtual Machine option you mentioned above, and i'd like to ask a couple of questions about it:

- Should i use vmware on both os`s(win&lnx) and store the machine inside some commont point(visible to win and linux)?
- Which linux solution should I use for only running a mysqldaemon?

Thank you very much for your help! :D

---

### Post by koenn on 2009-05-20
> **lucasprim said:**
> oops, i made a mistake :P actually its /media/Dados/MYSQL/ibdata

- The mount point is located at /media/Dados
- Permissions are rwxrwxrwx trough all the path to /media/Dados/ibdata, ibdata included (but i haven't touched it, think its standard)

still messy with the paths, but I suppose ibdata is (a subdir of) the windows mysql datadir, and you seem to have rw all over the place (equivalent of everyone read,write; probably what mount defaults to when mounting a non-unix fs), so my first option doesn't seem to go anywhere

> **lucasprim said:**
> 
Guess i'm gonna try that Virtual Machine option you mentioned above, and i'd like to ask a couple of questions about it:

- Should i use vmware on both os`s(win&lnx) and store the machine inside some commont point(visible to win and linux)?
- Which linux solution should I use for only running a mysqldaemon?

The way I'd go about is, would be 
- run one OS on your laptop
- run a VM program - MS VirtualPC on Windows (if you manage to run Linux inside it), Virtualbox or whatever Ubuntu's current preferred virtualisation program is, or the classics : vmware (server, workstation, ESXi ...)

- the trick is that you let the VM NIC bridge to the physical nic of your laptop. That means the VM NIC can have an address in the same network as your laptop (but not the same address; on a network with dhcp this works automatically). The laptop and the VM will be able to communicate over the network. (I don't know what happens if the laptop NIC isn't configured, eg id it's not on any network, you could test that)

Most virtualisation programs I know of know how to do this. 

- Once you have network connectivity between the host (laptop) and the guest (VM), it doesn't really matter where you install mysql (networkwise. For performance, the host might be a better idea)

- you'd have to configure mysql to listen on the network (in my.cnf) - by default it only listens on localhost

That's it. Never done it, so you'll have to make up your mind yourself as to what OS goes where and which one will run mysql and all that. 

If you want a lean Linux with only myssql, I'd install Debian 'standard system' (or even nothing added at all), and add mysql afterwards. That'll take up 500-700 mb disk space, databases not included. 
You could do the same with Ubuntu server; don't install any 'tasks' so you have a bare system; then apt-get install mysql and whatever other software you need.

Ubuntu also has jeOS (Just Enough OS) that is designed to be a minimal OS for Virtual Appliances (virtual machines set up to run 1 specific application and nothing), so it might be too minimal and a lot harder to set up, run, manage, and troubleshoot.

---

### Post by lucasprim on 2009-05-21
Thank you very much!

I'm gonna try this solution right now and see how it works! I have an DHCP router managing my network so it shouldn't be that hard!
:D

---

