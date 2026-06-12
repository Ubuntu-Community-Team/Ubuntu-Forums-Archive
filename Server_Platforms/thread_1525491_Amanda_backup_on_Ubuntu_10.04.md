---
title: "Amanda backup on Ubuntu 10.04"
date: 2010-07-06
forum: Server Platforms
---

### Post by troberts007 on 2010-07-06
Has anyone installed Amanda backup software on Ubuntu 10.04? Any links to how to's or instructions would be greatly appreciated.

---

### Post by stlsaint on 2010-07-07
see [here.]("http://wiki.zmanda.com/index.php/FAQ")

---

### Post by MakOwner on 2010-10-05
> **stlsaint said:**
> see [here.]("http://wiki.zmanda.com/index.php/FAQ")

Which is really neat and all but almost everything documented out there says "walk through the configuration and figure out what your distro did that is different from default".

Apparently Ubuntu veers a bit from the path of a default installation for the software.  I just wonder if anyone has any idea why?  

- Standards are a wonderful thing -- everyone has their own.  ](*,)

---

### Post by posterlion on 2010-12-27
It is a pretty easy thing to do, once you've suffered for about a month trying.  :)

But I'll get you started if you want to try it.

1) decide which server you want to use.  I'd use a new server strickly for amanda.  If you can't spare a server, then I'd look into vmware or xen and get virtualized first.  Life is so much easier after that. but anyway . . . you've selected your server so next step.

2) login to your server and:

sudo aptitude install xinetd

after xinetd is installed do

sudo aptitude install amanda-server

you will be asked to configure postfix.  The easy thing is to select "local only" and accept any defaults after that.

then

sudo aptitude install amanda-client

You are done with the install, now it's time to configure the server.  Amanda should install with the user backup and group backup.  Let's check it.

3) Check your groups

michael0@am26:~$ groups backup
backup : backup disk tape

4) set the password for user backup

michael0@am26:~$ sudo passwd backup
[sudo] password for michael0:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
michael0@am26:~$

5) Now comes the fun part, you will need to fix three bugs (at least I call them bugs).  If you have any fantasy of being a linux administrator you need get comfortable working as root.

Become root:

sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
su -
Password:
root#

Bug #1: amanda forgets to copy the template.d directory to /var/lib/amanda from /usr/share/doc/amanda-common/examples.  We'll do that now.

root@am26:~# cd /usr/share/doc/amanda-common/examples
root@am26:/usr/share/doc/amanda-common/examples#cp -r template.d /var/lib/amanda
root@am26:

Bugs #2 and #3:

You are preparing to run the amserverconfig script, however, there are some errors in two of the script constants.  We'll fix them now.

root@am26#cd /usr/lib/amanda/perl/Amanda
root@am26:/usr/lib/amanda/perl/Amanda#cp Paths.pm Paths.pm.orig

The above copy command backed up the original Paths.pm file.  Now you need to do:

nano Paths.pm

Near the bottom of this file you need to locate two variables
$amdatadir and $localstatedir

Modify them so that they look like the following:

$amdatadir = "/var/lib/amanda";
$localstatedir = "/var";

Save the file and you are ready to run amserverconfig.

6) Run amserverconfig:

Change to user backup

root@am26:/usr/lib/amanda/perl/Amanda# su - backup
$

Now you run amserverconfig. This examples sets up vtapes.  If you are not using vtapes, you'll need to modify this accordingly.  Also, keep in mind that this example uses the amanda defaults and you may need to change them later.  But you won't know what your real values should be until you've done some research.  To run amserverconfig simply type this:\\

$amserverconfig DailySet1 --template harddisk

You will see amanda output what it is doing and if all comletes well the final line will say
DONE.

Don't get carried away after you see DONE, because you are not done.  You will still need to install amanda-client on the client(s) you want backed up and believe me, you'll have a lot of tweaking to do on your server as well.  ENJOY. 

Here are a few links to check out:

[http://blog.learnadmin.com/2010/07/install-and-configure-amanda-backup.html](http://blog.learnadmin.com/2010/07/install-and-configure-amanda-backup.html)
[http://wiki.zmanda.com/man/amserverconfig.8.html](http://wiki.zmanda.com/man/amserverconfig.8.html)
[http://ubuntuforums.org/showthread.php?p=2470030](http://ubuntuforums.org/showthread.php?p=2470030)

---

### Post by becky585 on 2011-06-13
Firstly sorry for commenting on an old thread but I just followed this and it was perfect except one thing was missing.

Before step 6 you need to ungzip all the .gz files in /var/lib/amanda/template.d or when running the amserverconfig you will get[FONT=monospace]:[/FONT]ERROR: copy dumptypes failed: No such file or directoryTherefore, you need to do the following:

cd /var/lib/amanda/template.d

gunzip advanced.conf.gz
gunzip advanced.conf.in.gz
gunzip dumptypes.gz
gunzip tapetypes.gz

Then you can type dir to check that you have ungziped them all, if you have move on to step 6.

Hope this helps others :)
& thanks @posterlion for a great tutorial

---

### Post by TedLeRoy on 2012-03-25
Thanks for the post posterlion and becky585! :KS

[edit]Removed link to a bug fix that was covered by posterlion

---

