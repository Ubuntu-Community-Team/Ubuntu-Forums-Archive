---
title: "switching from SME server to ubuntu"
date: 2007-11-02
forum: Server Platforms
---

### Post by cyclefiend2000 on 2007-11-02
Currently, we are using SME Server Version 6.01-01 as our file server OS where I work. I work for a small company, and this OS has worked well for us. However, it is time to upgrade our server OS. 

The server was setup and maintained by former employee. While there are some nice features to this software, there are some pretty big drawbacks as well. The two biggest drawbacks as I see it are 1) there is no good way to upgrade the OS other than wiping the harddrive and installing the latest version (unless this has changed in the newer versions) and 2) the software requires the harddrive be unpartitioned. Because of this when you do an upgrade you are wiping out all the documents. To me it makes more sense to have the documents on the own partition(s) so if you need to wipe the OS, the documents are untouched. 

I have been using kubuntu at home and I really like the OS, and the ease of installation and most other tasks. 

I am considering using ubuntu at work as our new server OS. I have a few questions first though. 

1) With SME you are able to perform some administration tasks via a web interface. Is there a possibility of installing something similar on ubuntu?

2) Right now we have a back-up server that rsync's with the main server regularly. If the main server goes down, we can replace it with the backup and be back up and running in a short amount of time with little or no data loss. How easy/hard would it be to do this with ubuntu?

Those are the only questions I can think of at the moment. Any input or ideas are welcome! Thanks! 

--Bradley

---

### Post by tkharris on 2007-11-02
What you're going to need is Samba or NFS ( If there are windows computers you're going to need Samba ).  There is a web application that does Samba configuration called SWAT.  I've personally never used it, but it's the only one I've heard of to date.

You'll be able to set up cronjobs to run rsync fairly easily.

I would recommend using Debian for this task over Ubuntu.  Although Ubuntu makes a decent and easy to install/maintain/use Linux desktop I still see Debian as a far better choice for servers ( Not starting a flame war, expressing an opinion ).

---

### Post by dantrevino on 2007-11-02
There are tons of gui tools for samba.  Some work better than others and all are in various states of development.  Not all are available in the ubuntu repos either.

[http://www.samba.org/samba/GUI/](http://www.samba.org/samba/GUI/)

Ubuntu is plenty suitable as a file server.  In my experience, the only thing I wish for is a usable OpenVZ.

If you'll have KDE desktops in your office, Knetwork includes a samba configuration tool (listed on the page above).  I've never used it, so cant speak to its usability, but its something to look for.

Its sounds like you're not in a critical situation, so I suggest you download the ubuntu server CD and kick the tires.  Keep in mind that Long Term Support (LTS) will be available with 8.04.

dan

---

### Post by cyclefiend2000 on 2007-11-02
thanks for the link. 

i looked at gosa ([https://oss.gonicus.de/](https://oss.gonicus.de/)). it looks like it pretty much does all the same stuff the web frontend we have now does. 

have you ever used it? or something similar?

which version of ubuntu would you recommend for a file server?

we are not in a critical situation right now. the biggest issue is that one particular web page that we use fairly often will not work correctly. [http://www.ngs.noaa.gov/OPUS/](http://www.ngs.noaa.gov/OPUS/)

when we try to upload a file we get this error message...
> The connection was reset
The connection to the server was reset while the page was loading.

we have tried it in IE and firefox. i talked to our old network admin. he said he thought it was because we had an old version of squid. we talked to him about coming in and upgrading all our stuff, but he was wanting to charge a small fortune to do it. 

so i have been researching setting the thing up myself since.

edit: i use kubuntu at home. we are pretty much locked into using windows at work because of the cad software we use. there is nothing i have found comparable in linux.

---

### Post by koenn on 2007-11-02
> **cyclefiend2000 said:**
> 
2) Right now we have a back-up server that rsync's with the main server regularly. If the main server goes down, we can replace it with the backup and be back up and running in a short amount of time with little or no data loss. How easy/hard would it be to do this with ubuntu?
This one should be easy. you can rsync between the two servers.
Once, just to see if it would work, I rsync'ed a complete server (i.e. everything under /, excluding /proc and /tmp) to a 2nd machine, rebooted it, and found it  identical to the original server. 
I did that in VMWare so the "hardware" was identical. If you don't have 2 identical machines, you'd have to work out a way to avoid that hardware specific software (modules, ....) and settings are copied over, but other than that, it's a no-brainer. 
The only thing you can't copy with rsync is stuf outside the filesystem (boot records; swap partition) - you'd need to set that up first (or use dd to clone a disk)

---

### Post by koenn on 2007-11-02
> **cyclefiend2000 said:**
>  2) the software requires the harddrive be unpartitioned. Because of this when you do an upgrade you are wiping out all the documents. To me it makes more sense to have the documents on the own partition(s) so if you need to wipe the OS, the documents are untouched. 
That's weird. You mean you can't have  additional disks / partitions and mount those to /srv or /home or /var or wherever you want to keep your data ?

---

### Post by Wharf Rat on 2007-11-02
> **dantrevino said:**
> ...
Its sounds like you're not in a critical situation, so I suggest you download the ubuntu server CD and kick the tires.  Keep in mind that Long Term Support (LTS) will be available with 8.04.

dan
Personally, I did just that and I have am about as unimpressed with the server as I am impressed with the desktop.  

So far,  I can share SAMBA folders on my home net with no security (Ubuntu clients).  Or, have NO access for my Ubuntu clients.  XP --- out of the question.


So far I have  used Xubuntu and Ubuntu Gnome for interfaces  -- as well as CLI.

---

### Post by cyclefiend2000 on 2007-11-04
> **koenn said:**
> That's weird. You mean you can't have  additional disks / partitions and mount those to /srv or /home or /var or wherever you want to keep your data ?

maybe i am misreading the information, but that is what i think it is saying....

[http://wiki.contribs.org/SME_Server:Documentation:FAQ](http://wiki.contribs.org/SME_Server:Documentation:FAQ)
> Hard Drives, RAID's, USB Hard Drives

    * How should I setup my hard-drives? 

We never recommend anything other than a single disk install or multiple disks of the same type. Anything else and you are following an unrecommended setup and you will need to navigate for yourself. Repeat, we never recommend anything other than a single disk install or multiple disks of the same type. If you're thinking of doing anything else (setup your own partitions), read this section again.

[http://wiki.contribs.org/AddExtraHardDisk#2_Partition](http://wiki.contribs.org/AddExtraHardDisk#2_Partition)
> 
Alternative 1: Use /home to mount the new disk

On standard Linux machines, the /home directory contains the user's directories and is therefore a popular place to mount a bigger disk.

However, on a SME server this is not a good idea:

SME stores all its configuration files in /home/e-smith/db.
If for whatever reason your disk doesn't mount, the configuration files will no longer be accessible, causing all kinds of nasty problems.

Mounting your second disk to /home or even /home/e-smith/files effectively means that your first disk will no longer be used to store user files.
In some cases that might be a good idea, but in most cases you are just wasting the remaining space of your first disk.

Alternative 2: A much better approach is to leave the second disk mounted at /mnt/newdisk and to create symlinks (symbolic links) for specific ibays or user folders.


actually, i just reread the second quoted section. i think i can add partitions. however, the installation documents discourage it. stupid if you ask me. would be much easier to upgrade the OS if they would more easily allow partitions for the documents. 

if i decide to stick with sme, i am definitely going to setup ibay partitions this time.

---

### Post by NTBlade on 2007-11-05
Hi,

It's very easy to upgrade SME

As far as Iknow, an SME Server upgrade has NEVER wiped out your existing documents.
Threre is also good reason to mount extra storage in ibays.

You really gotta go and read the manual, wiki and ask in the contribs forums.  You'll get all the help and answers you need.

NTB

---

