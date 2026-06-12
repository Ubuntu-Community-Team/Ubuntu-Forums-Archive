---
title: "Backing up a remote webserver"
date: 2008-11-30
forum: Server Platforms
---

### Post by Rizla on 2008-11-30
Hey Guys,

I have a VPS server that I manage myself and its been working great for the past 8 months that i've had it up.  I was reading a post about new vulerabilities in the kernel and wanted to update my system.  The problem is that I havent made any backups yet (i know.. piss poor admin..).  Before I upgrade I want to make sure that all my vital conf files are backed up in case something goes wrong i can rebuild.

Question is.. How do i go about backup up my system to my local machine?  My server is sitting on a server in some random data center.

I have currently have apache, mysql, php, postfix, dns, and ftp running on the server.

WHats the best way to back everything up?  Also, as a follow up.  I'd like to clone my setup remotely in case somethign fubar's i have a 1:1 image of it that i can restore.  Any ideas?

Thanks

---

### Post by m_l17 on 2008-11-30
List of backup solutions:

[http://www.debianhelp.co.uk/backup.htm]("http://www.debianhelp.co.uk/backup.htm")

I like rsnapshot: 

[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

How to:

[http://www.rsnapshot.org/howto/](http://www.rsnapshot.org/howto/)

[http://www.debianhelp.co.uk/rsnapshot.htm]("http://www.debianhelp.co.uk/rsnapshot.htm")

rsnapshot and ssh:

[http://troy.jdmz.net/rsnapshot/]("http://troy.jdmz.net/rsnapshot/")

---

### Post by Rizla on 2008-11-30
> **m_l17 said:**
> List of backup solutions:

[http://www.debianhelp.co.uk/backup.htm]("http://www.debianhelp.co.uk/backup.htm")

I like rsnapshot: 

[http://www.rsnapshot.org/]("http://www.rsnapshot.org/")

How to:

[http://www.rsnapshot.org/howto/](http://www.rsnapshot.org/howto/)

[http://www.debianhelp.co.uk/rsnapshot.htm]("http://www.debianhelp.co.uk/rsnapshot.htm")

rsnapshot ans ssh:

[http://troy.jdmz.net/rsnapshot/]("http://troy.jdmz.net/rsnapshot/")

Thanks man, i'll get them a shot later today.

---

### Post by tubezninja on 2008-11-30
Before you go updating your kernel, check with your VPS provider.  While companies like Linode and Slicehost offer ubuntu, they are NOT using the standard kernels that come with each release.  Instead, they use a custom-compiled kernel that is fine-tuned for Xen or whatever VM package they're using.

The best thing to do is ask them if they use their own kernels (or, if you've given a choice of kernel when you set up your VPS, then it's pretty much guaranteed it's custom).  If so, check with them as to what their latest version is.  If yours is out of date, sending in a support ticket asking to be upgraded should ensure that you get the needed patches with minimal risk to the stability of your VPS.

---

### Post by jamesrfla on 2008-11-30
What about using Ubuntu to back up both Ubuntu and Windows computers? Also can I chose what to back up?

---

### Post by mitchroberts on 2008-11-30
Here are some free linux backup apps on this page

[http://www.foogazi.com/2008/02/25/free-linux-backup-solutions/](http://www.foogazi.com/2008/02/25/free-linux-backup-solutions/)

---

### Post by hictio on 2008-12-01
> **jamesrfla said:**
> What about using Ubuntu to back up both Ubuntu and Windows computers? Also can I chose what to back up?

Take a look at this project [BackupPC](http://backuppc.sourceforge.net/), and a page with tips and steps for the setup: [BackupPC Setup Manual](http://taksuyama.com/?page_id=5)

---

### Post by Rizla on 2008-12-01
> **scaredpoet said:**
> Before you go updating your kernel, check with your VPS provider.  While companies like Linode and Slicehost offer ubuntu, they are NOT using the standard kernels that come with each release.  Instead, they use a custom-compiled kernel that is fine-tuned for Xen or whatever VM package they're using.

The best thing to do is ask them if they use their own kernels (or, if you've given a choice of kernel when you set up your VPS, then it's pretty much guaranteed it's custom).  If so, check with them as to what their latest version is.  If yours is out of date, sending in a support ticket asking to be upgraded should ensure that you get the needed patches with minimal risk to the stability of your VPS.

Thanks for that heads up.  I opened up a support ticket to my VPS provider (VPSlink, cheap and great thus far) and they told me that i shouldnt update the kernel because they do use a custom kernel for XEN.

glad i posted this question for that nugget alone.  They said if I upgraded the kernel i would have fubar'd it.

---

