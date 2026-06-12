---
title: "Cloning old server to a new server with virtualization"
date: 2019-01-10
forum: Virtualisation
---

### Post by ODBWilson on 2019-01-10
Hi all,

I am new to virtualization and would like to know more on virtualization.
I have two old Linux servers (Master and Slave server) on Fedora Core 4 running for more than ten years.  Two servers run with Linux HA for web server, ftp server and a customized JAVA app.  A MySQL dual master replication server is installed as well.  There are no more spare hardware for the old serer in the market.  I have no choice to upgrade to the new server.

Now I wanna clone the old FC4 master and slave servers to two new servers on Ubuntu 18.04 with virtualization setup. Can virtualization on the new servers do that? What is the best way to do the clone, and how?  It is because two old servers are LIVE.  And we can't stop them.  

Thanks,
Wilson

---

### Post by TheFu on 2019-01-11
You must stop them.

But you can test a migration using virtualization, just don't do it on the same subnet.

Running a really old, unsupported, Linux install, on most networks is dangerous. There are many, many, remote exploits out there. If these 2 systems run on an air-gapped network, then I wouldn't worry, provided there are very strict controls for all new software introduced to that network.

I wouldn't try to move from Fedora to Ubuntu 18.04 without very good reason.  IMHO, 18.04 networking isn't ready for production use in non-trivial setups.  Stick with 16.04 - it has support until 2021 or why not go with CentOS?  CentOS will feel more like what you have, though there are huge changes in all that time.

Regardless, you will need to bring down the cluster, for a minute or so. This assumes you get everything else moved over, which might not be possible with Java.

If you intend to keep FC4 systems (cough, bad idea usually), you could take a system backup and restore that into a VM.  The networking and heartbeat will work a little differently. You'll want to manually setup any bridges needed on the VM hosts.  I'm assuming you want 2 VM hosts to retain some redundancy.  I'd suggest you begin with a simple VM and run that for a few weeks at least before attempting any cluster stuff.  

With KVM, there are some interesting back-end storage options which can aid with redundancy.

---

### Post by ODBWilson on 2019-01-11
Thanks for your reply.  I will use Centos7 as the server for virtualization.  I have to stick to FC4 as there is nearly impossible to upgrade the PHP 5.04 codes to PHP5.6/PHP7.0.  It is on the private network, so security is not an issue.

Can you recommend a tool to backup the old server to a VM? Actually I can stop the slave server to backup first.  And then turn it back on for operation and stop master server for the backup.  But I am not sure everything will do as before.

Another option is that I can install FC4 from scratch as a VM host on the new server and then install each services one by one: Web, MySQL, FTP, and JAVA app (I have an installation disk for that).  Of course, I need to transfer PHP codes, DB, and contents from the old server manually. And then test for a while and setup the Linux HA and Dual MySQL Replication later.  

To me, it seems that reinstallation of FC4 on a vm host is a better option.
Which approach do you recommend?

---

### Post by TheFu on 2019-01-11
This is an opportunity to validate your backup/restore procedures.  Ignore that any VM is involved.  That shouldn't matter, assuming you have the VM networking setup correctly.

Any backup/restore tool will work. Pick your poison. I do daily, automatic, versioned, backups for all my systems. I treat VMs and physical machines the same, so it doesn't matter.  The physical host doesn't backup the VM storage, that would be wasteful.  
I thought for years thta using VM tools for backup would be the best solution. Eventually, we ran out of backup window periods and couldn't keep doing that.  Switched to treating them like physical VMs and backup times dropped from 45-90 minutes per VM to 1-4 minutes per VM.  The backup tools are smarter than the hypervisor backup tools, by far.

---

### Post by ODBWilson on 2019-01-12
You meant I can simply backup the old slave FC4 server with Clonezilla, and restore to a VM host on KVM?
And do the same for the master server.  If I setup the networking stuffs correctly, it will work like a charm as before.
Correct me if I am wrong.  Much appreciated.

---

