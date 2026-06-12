---
title: "automating backups from windows to ubuntu server"
date: 2009-02-23
forum: Server Platforms
---

### Post by dajasc on 2009-02-23
I'm looking for the easiest way to automate backups from a windows machine (actually several windows machines) to a server running Ubuntu.

I am definitely not an advanced user at all so don't be afraid to state (what you think is) the obvious.

Here is my situation.  The Ubuntu (8.04 LTS) machine is web facing and on a different subnet from the Windows LAN.  They are connected through a router/firewall.  The firewall will not allow any connections that are initiated from the Ubuntu machine to the windows LAN.  However all of the windows machines can connect to the Ubuntu machine to get web pages, ftp, ssh access, etc. 

So can I do something to have periodic automated backups from the windows machines onto the Ubuntu one given that the connection must be initiated from the windows side?  

I suspect I might get "use rsync" as an answer.  I guess that's fine if that's the consensus but the configuration of that on windows looks absolutely horrible to me.  If that is the best way I'll give it a shot.  My first stupid question would be the windows machines then are the rsync "server" correct?  If yes does an rsync client need to run on the Ubuntu machine or not?

If it matters, the windows machines are all running XP pro. 

Thanks in advance for the help.

---

### Post by HermanAB on 2009-02-23
Rsync is your friend...

The Linux machine will be the server.  The best way to run rsync is over SSH, so Linux will need the ssh-server package.  Windows will need Cygwin with rsync client.

Another way is to use a FTP script as described here:
[http://aeronetworks.ca/windows-backup.html](http://aeronetworks.ca/windows-backup.html)
in which case you need the vsftp package on Linux.

Cheers,

Herman

---

### Post by dajasc on 2009-02-23
That's what I was afraid of... configuring rsync in windows.

Oh well, better get to it.

---

### Post by mhelmer on 2009-02-23
The question i have is what exactly are you trying to backup up?

If its files, or anything on a hard drive for that matter i would configure SAMBA on your Ubuntu server. The host(s) that need to be backed up can mount a share, or a hard drive on the Ubuntu server that is the destination for the backup. Then through a windows batch script you can use the "xcopy" command to copy anything from the local (windows) machine to the Samba share (Ubuntu server). 

Then schedule a task through the Windows machine and the backup is automated.

I hope this helps, this solution works great for what i back up (at home and work).

---

### Post by dajasc on 2009-02-23
Yes, it's just a bunch of documents that need to be backed up - presentations, spreadsheets, that sort of stuff.

My only problem with that is that I can't get the share from the Ubuntu server to show up on any of the windows machine unless I change settings on the firewall.  At least I think the firewall is the problem.  If I plug a windows machine into the same subnet as the Ubuntu server it can see the share no problem.  Ideas?

---

### Post by mhelmer on 2009-02-23
You'll need to setup a wins server and local master to communicate across the subnets.

Here is a link that should resolve the issue.

[http://brneurosci.org/linuxsetup38.html](http://brneurosci.org/linuxsetup38.html)

---

### Post by dajasc on 2009-02-24
Ok, I have rsync server running on the Ubuntu machine.  I have Deltacopy (an rsync implementation for windows) on the windows machine.  I can get DeltaCopy client to find the virtual directory I have set up.  When I have it run a backup it never actually does anything.  When I run manually it just says executing forever.

On syslog (on Ubuntu machine) I can see when I request the virtual directory list.  It never attempts to log on to actually make the transfer.  Ideas?

---

### Post by dajasc on 2009-02-24
Ok I switched off connect with SSH.  Now it works.  What do I need to do to connect through SSH?  Or maybe the better question, is there any point since this is over a LAN?

---

### Post by HermanAB on 2009-02-25
If it is on a LAN, then you don't need to run it through SSH, but all you would do is use the rsync -e ssh kinda thing.

Note that if you use Samba or NFS (Much easier than Samba) and you have the remote directory mounted, then you don't need the rsync server.  You can then simply use rsync as a 'better copy command' and the network file system will take care of the transport.

Cheers,

Herman

---

### Post by dajasc on 2009-02-25
I'm not sure I understood that last bit.  You mean mount the windows directories that I want to backup on the Ubuntu machine?

If I'm understanding that correctly the firewall is refusing to allow that sort of behavior but it is working fine at the moment using the rsync server on Ubuntu machine and DeltaCopy on the Windows machines.  At least it is so far, I've only run some tests, not the actual stuff that needs to be backed up.

---

### Post by koenn on 2009-02-25
> **mhelmer said:**
> You'll need to setup a wins server and local master to communicate across the subnets.

Here is a link that should resolve the issue.

[http://brneurosci.org/linuxsetup38.html](http://brneurosci.org/linuxsetup38.html)
technicalyy, you only need a router to communicate across subnets. You can have DNS for name resolution. WINS is only required for some specific features such as populating and browsing the 'Network Neighborhood' on windows machines, (or it used to be required in NT4, not sure about more recent Windows)

---

### Post by koenn on 2009-02-25
> **dajasc said:**
> Ok, I have rsync server running on the Ubuntu machine.  I have Deltacopy (an rsync implementation for windows) on the windows machine.  I can get DeltaCopy client to find the virtual directory I have set up.  When I have it run a backup it never actually does anything.  When I run manually it just says executing forever.

On syslog (on Ubuntu machine) I can see when I request the virtual directory list.  It never attempts to log on to actually make the transfer.  Ideas?
If I remember correctly, the default config for rsync in daemon mode is to create read-only modules. You have to set them writable in rsync conf. Also, check the file system permissions.



I see what you're trying to do, and I agree with others that an rsync/deltacopy combination, or simply copying to a samba share, would be the first things to try. But I don't quite understand the concept of what you're doing.

You have a server connected to the internet. It's on a different subnet and apparently you use it as a DMZ. You don't allow traffic from the server/the DMZ into the (secured) LAN. Makes perfect sense so far, it's a classic DMZ arrangement. 

But then you are willing to copy data from the LAN to the server in DMZ. Does that make sense ? you have a DMZ / firewall setup to protect your LAN hosts (including, presumably, the data on them), but your backup solution puts copies of data outside the firewall ...

---

### Post by dajasc on 2009-02-25
Yes I understand the confusion regarding the security issues.  I am willing to put SOME of the data from the LAN side onto the server.  Specifically a subset of it that people would like to access from outside and that isn't all that sensitive anyway.  Actually at this point I believe I have it all working with rsync.

Still I'm going to try and set up access to that data via ftp with TLS to secure it to the extent possible. That isn't going so well since the proftp package that is the current one for Ubuntu (1.3.1) turns out to have a broken implementation of TLS.  So I either need a different ftp server or I have to hope that the developers package up the newest version for Ubuntu.  I did check on proftp's site, there is a version with a fix for the TLS problem that is stable.

---

### Post by pdtpatrick on 2009-02-25
or you can use Unison.

---

### Post by dajasc on 2009-02-27
Well that's interesting I'd never heard of Unison.  I may give that a try as well.

---

