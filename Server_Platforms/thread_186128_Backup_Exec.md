---
title: "Backup Exec"
date: 2006-06-01
forum: Server Platforms
---

### Post by brubach on 2006-06-01
ubuntu v5.10

am curious if anyone has been able to install and use symantec's backup exec remote agent (RALUS)  

I need to backup files on a SAMBA server

I can't get it to  install

---

### Post by johnc4510 on 2006-06-01
Their web page does not show that it is compatible with Ubuntu, and it also didn't list Debian. Note, I only skimmed the first page.

---

### Post by moopere on 2006-06-02
[QUOTE=brubach]ubuntu v5.10

am curious if anyone has been able to install and use symantec's backup exec remote agent (RALUS)  

I need to backup files on a SAMBA server

I can't get it to  install[/QUOTE]


I've got a breezy server here using BE10 so it can work.  Its not supported by veritas on debian/ubuntu but you will get it working without too much trouble.

I don't have my notes in front of me, but did leave detailed instructions on the veritas support forums - look for posts with debian in the subject.

Cheers,
Craig

---

### Post by linuxone on 2006-06-05
Hi,

[QUOTE=brubach]am curious if anyone has been able to install and use symantec's backup exec remote agent (RALUS)[/QUOTE]

this depends on the BackupExec version. Yesterday I tested the Linux agent from BackupExec 9.0, but this fails and does not run. Agent install only mentions kernel releases 2.0, 2.2 and 2.4 but not 2.6. Of course I don't downgrade the kernel to test only this simple agent. 

> I need to backup files on a SAMBA server

for files stored into a Samba share you certainly don't need any backup agent. Linux already contains all you need for backup ....

For example you can create a compressed tar archive and copy this to a Windows machine so it also can be included into your BackupExec job. Sample:

--- do_backup.sh --------------------
[color=green]#!/bin/sh

## store the backup into your samba share
cd /usr/local/samba/backup

## also include /etc to backup your system config!
## **exclude file** does contain the backup dir!
/bin/tar czf linuxsamba.tgz /usr/local/samba /etc \ 
       -X /usr/local/samba/backup/exclude[/color]
-------------------------------------

Now you'd copy this archive to a Windows machine. You can do this from linux using smbmount (ie. add these commands to the backup script) or by a DOS batch file via Windows Task from your target Windows machine. Then add the copied linux archive to your backup job.

Add the shell script to crontab (use: "sudo crontab -e") to run it automaticly each night, see "man crontab":

[color=green]0 1 * * * /path/to/do_backup.sh[/color]

Thomas

---

### Post by moopere on 2006-06-11
Hmm, my memory of having left detailed instructions appears to be a little off.  Heres the post I was thinking of

[http://forums.veritas.com/discussions/thread.jspa?messageID=4415848&#4415848]("http://forums.veritas.com/discussions/thread.jspa?messageID=4415848&#4415848")

(I'm at the very bottom under the handle 'moo moo')

I must have made some hand written notes (instead of posting) - bah!  I will find them here someplace and post them both here and at veritas so Debian/Ubuntu ppl have a chance of getting it working.

The steps are quite easy, though not at all intuitive.  Hopefully the link above will give a pointer to the files required, you then 'alien' them, install each with dpkg -i.

Fiddle with /etc/VRTSralus/ralus.cfg if you need to, then plonk VRTSralus.init into /etc/init.d/ making sure its executable.

You can use "/etc/init.d/VRTSralus.init start" to try the thing out without rebooting.

Good luck, it -does- work and work really well.  I'll be back in a few days with some sort of howto when I can find my notes.

Cheers,
Craig

---

### Post by cltrenholm on 2006-11-15
I have followed the steps you have higlighted here and those contained in the posting on the Veritas sight as well as ensuring that root was part of the beoper group. However, when issuing _/etc/init.d/VRTSralus.init start_ the agent still fails to start. It does not throw an error or give any indication as to why.

Does this sound familiar or does anyone have an idea as to what I may be doing wrong?

---

### Post by dbdavidson on 2008-03-24
This is how I did it.

My Network:
Media Server: Backup Exec 10d  (Rev. 5629) on Windows Server 2003
Client Server: Ubuntu Server 7.10

I write this so that others may benefit from a very frustrating week in my life.  I’ve been out of the Linux game for a while but at a friend’s suggestion I chose Ubuntu for a new Linux development server.  As I discovered there was one downside to this choice -- no official Backup Exec support.

A little background for those catching up...  There is available a Remote Agent for Linux and Unix Servers (RALUS) but Ubuntu is not supported since it is a Debian-based platform.  The software is available in RPM-form only and makes Redhat-like assumptions about your system.  I found a few resources on the web to help me out and I will cite them when possible.  Thanks to all the other contributors in the Linux community.

I was still committed to Ubuntu so the struggle began…

One could convert the RPMs using Alien but I went with the other approach:

root:~# apt-get install rpm

There, now we’re RPMish.

You’ll also need this library for the eventual 'beremote' binary.  Trust me.  (Thank you to [http://www.digitalsanctum.com/2007/01/28/libstdc-libc62-2so3-on-ubuntu/](http://www.digitalsanctum.com/2007/01/28/libstdc-libc62-2so3-on-ubuntu/) and my friend Aaron who found it.):

root:~# apt-get install libstdc++2.10-glibc2.2

Okay, now we’re ready for the fun stuff.  Go here:

[http://seer.entsupport.symantec.com/docs/279329.htm](http://seer.entsupport.symantec.com/docs/279329.htm)

Download Q180968.BE.RALUS.10.1.5629.3.ESD.tar (I did this on my local machine and FTP’d it over to the server.)  This was the newest version that I could find online.  (Does anyone else find Symantec’s website frustratingly complex?)  You may also find it on your media server in C:\Program Files\[VERITAS or Symantec]\Backup Exec\NT\Agents\RALUS depending on your version.  My version had two tar files with README files inside telling me the tar files were empty.)

I created '/tmp/beremote' and:

root:/tmp/beremote# tar -xvf Q180968.BE.RALUS.10.1.5629.3.ESD.tar

If we 'cd' into linux we see a promising 'installralus' executable.  Not quite yet…

If you run that the install will immediately fail because you do not have root privileges.  (Try it yourself if you must.)  “But I AM root," you say.  Indeed, but not in the Redhat way the install script is expecting.  We can "fix" that:

root:/tmp/beremote/linux# nano ralus/scripts/install/CPI40.pm

[Yes I use Nano.  Mock me if you must.]

We need to comment out lines 1839 to 1841:

   }
  }
#        if ($id ne "uid=0(root)") {
#                _die("$COMM{PROG} must be run by a user with root ID", 10, 1179$
#        }
        _comm_process_args(@_);
                        

Save the file.  But don’t ./installralus just yet.  If you do it will fail again because of dependencies.  The needed items are there but not in RPMland.  So we’re going to force the RPM installation without a dependency check then run the install script for the configuration:

root:/tmp/beremote/linux/pkgs/linux# rpm -i --force -v --nodeps pkgs/linux/VRTSvxmsa-4.2.1-211.i386.rpm 
root:/tmp/beremote/linux/pkgs/linux# rpm -i --force -v --nodeps pkgs/linux/VRTSralus-10.00.5629-0.i386.rpm

Okay, now you can:

root:/tmp/beremote/linux# ./installralus

Answer the questions as appropriate using the help at the Symantec website above and in the BE Administrator’s Guide.

Once completed you should be good to go:

root:~# /opt/VRTSralus/bin/VRTSralus.init start

You should see:

Starting Symantec Backup Exec Remote Agent ......
Starting Symantec Backup Exec Remote Agent:                              [  OK  ]

Confirm with:

root:~# ps –ef | grep beremote

If life is good you should see:

[stuff] /opt/VRTSralus/bin/beremote

On your media server you should see your Ubuntu server under 'Remote Selections > Unix Agents'.

In order to browse the server you will need to right-click the server and change the 'Connect As…' options by adding your root user and password.  That should be it.

Wait, do you get an error?  Perhaps like this:

"An error was encountered while attempting to browse the content of \\[server].  The function is not implemented."

Next question, do you have a valid license for RALUS?  As it turns out I didn’t .  Go to 'Help > About Symantec Backup Exec for Windows Servers > License Information'.

I had “Backup Exec 8.x and 9.x Agent for Unix” but that is not sufficient for the 10d (10.1).  The correct license will cost you around $350.

Not in the mood to spend money?  That’s okay.  You can use the legacy agent.

Go here:  [http://gentoo-wiki.com/HOWTO_Legacy_Veritas_Backup_Exec_Remote_Agent_for_Linux_and_Unix](http://gentoo-wiki.com/HOWTO_Legacy_Veritas_Backup_Exec_Remote_Agent_for_Linux_and_Unix)

That works too.  It doesn’t have the options that the new agent does and it is SLOW in comparison but it is free and free is good.

I hope I didn't miss anything.  If you have any difficulties I'm happy to try and help.

Good luck!

---

### Post by moffa on 2008-03-27
When trying to run ```
/bin/rpm -i --force -v --nodeps pkgs/linux/VRTSvxmsa-4.2.1-211.i386.rpm
```
I get bash: /bin/rpm: No such file or directory

I tried ```
 rpm -i --force -v --nodeps pkgs/linux/VRTSvxmsa-4.2.1-211.i386.rpm 
```

but I get error: can't create transaction lock on /var/lib/rpm/__db.000

I fixed it by creating a directory /var/lib/rpm

I also had to edit the file to find /bin/rpm in /usr/bin/rpm

---

### Post by dbdavidson on 2008-03-27
On the first count that's my fault.  I forgot I had created a symbolic link from /bin to /usr/bin where Debian keeps it.  I'll fix the doc above.

On the second count, are you root?

---

### Post by gothaggis on 2008-03-27
I'm a bit of a noob, so pardon.  When I try to run ./installralus, i get

Exec: 1: ./perl/bin/perl: not found

What do I need to change?

---

### Post by dbdavidson on 2008-03-27
Looks like you need Perl:

root:# apt-get install perl

should do the trick.

---

### Post by gothaggis on 2008-03-27
yeah, I have perl installed :(

---

### Post by dbdavidson on 2008-03-27
Unfortunately, the machine on which I had this deployed died and I don't have Ubuntu availabe to snoop around until the new server arrives.

If Perl is indeed installed then the script isn't finding it.  Examine where the script is looking and either add a soft link or modify the script.

I didn't have this problem.  Sorry I can't be more help.

---

### Post by moffa on 2008-03-27
> **gothaggis said:**
> I'm a bit of a noob, so pardon.  When I try to run ./installralus, i get

Exec: 1: ./perl/bin/perl: not found

What do I need to change?

I don't think you extracted the tar fully.  In the linux path, there should be a perl folder as well.  Is it there?  In the perl folder there should be bin and lib directories.

---

### Post by gothaggis on 2008-03-27
yep, the perl folder is there.  so the script should be running that version of perl, and not the version that was already installed on my machine? i will mess with the installralus file to try and change the path

---

### Post by loryguru on 2008-03-31
gothaggis: 
for me, changing the path to the perl binary I had in my machine in the installralus script resolved the issue.

In particular I changed the PDIR variable as follows:
PDIR=/usr

So the installation ended successfully.
But I can't run the agent with
/opt/VRTSralus/bin/VRTSralus.init start

I obtain FAILED in the start sequence.

I checked the beremote.service.log in /var/VRTSralus
and I found a message stating:
/opt/VRTSralus/bin/beremote: No such file or directory

Obviously I made a check and the beremote file exists and has executable bit set.

My system is an Ubuntu Server Dapper AMD64, maybe the beremote binary is not runnable under AMD64 platform?

Thanks for any help.
Best Regards
Lorenzo *the guru*

---

### Post by gothaggis on 2008-04-18
maybe - I too am running AMD64 bit.  A previous sys admin had it working on one of our servers, but no idea how he got it working (also amd64)

---

### Post by gothaggis on 2008-04-21
finally got it to install and now i am running into the same problem - it fails when trying to start it, and the log says this:

/opt/VRTSralus/bin/VRTSralus.init: 98: /opt/VRTSralus/bin/beremote: not found


beremote does exist and is set to executable - even trying to run beremote from the directory it is in results in a 'no such file or directory' message

this is on ubuntu gutsy - amd64

---

### Post by gothaggis on 2008-04-22
update:  yep looks like I just needed the 64bit version of RALUS which I found in the....RALUS64 directory lol.  This solved all of my problems (I did have to edit the installralus script to point to the correct version of perl)  thanks to everyone for the help.

---

### Post by WayneIT on 2008-06-30
While trying to follow the outlined procedure in Hardy 8.04, I hit a speedbump:

```

apt-get install libstdc++2.10-glibc2.2
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libstdc++2.10-glibc2.2

```

Being a Linux novice, the solution wasn't apparent. After some experimentation, I figured out what to do.

Download the required package from [http://packages.debian.org/etch/i386/libstdc++2.10-glibc2.2/download](http://packages.debian.org/etch/i386/libstdc++2.10-glibc2.2/download)

and install it via:

```
dpkg -i libstdc++2.10-glibc2.2.deb
```

Then the rest of the installation should proceed as planned, and the daemon will start when you're done.

Hope that helps any other noobs out there.

---

### Post by tabascoterrier on 2008-07-01
It took me a little while to get this working, even though the forums have been a big help.  So I thought I'd post my install instructions to a) help others and b) save me from loosing them.

This is for the Backup Exec 11d agent on Gutsy:

Prerequisites:
Backup Exec server will do a reverse lookup on the connecting IP - Linux server needs a PTR record.

tcp/10000 must be free on the Linux box (clashes with webadmin)

Agent talks to Backup Exec server on tcp/6101

Backup Exec needs a Ralus license.

---

create a beoper group and make root a member
# groupadd beoper
# adduser root beoper

copy VRTSralus.tar.gz and VRTSvxmsa.tar.gz from /ralusCD/pkgs/Linux to a scratch directory
# cp /ralusCD/pkgs/linux/* ~/ralus/

untar VRTSralus and VRTSvxmsarpms, convert to deb and install
# tar -zxvf *.gz
# alien -d *.rpm
# dpkg --install *.deb

install the (old) c++ library needed by ralus
# apt-get install libstdc++5
	
Add Backup Exec server to /etc/VRTSralus/ralus.cfg
Software\Symantec\Backup Exec For Windows\Backup Exec\Engine\Agents\Agent Directory List 1=backupserver.domain.com

Copy /opt/VRTSralus/bin/VRTSralus.init to /etc/init.d/
# cp /opt/VRTSralus/bin/VRTSralus.init /etc/init.d/

Symlink to /etc/rc.X
# update-rc.d VRTSralus.init defaults

Start daemon
# /etc/init.d/VRTSralus.init start

If service fails to start, check /var/VRTSralus/beremote.service.log

Create new backup job in BE console, Linux agent should have registered under 'Favourite resources'.  
If so, select the new server and provide root credentials when prompted.


To run in debug mode, first stop the daemon (if running)
# /etc/init.d/VRTSralus.init stop

And start with console logging enabled
# /opt/VRTSralus/bin/beremote --log-console

---

### Post by RoboJ1M on 2008-07-02
HA! I just spent the last two days writing the exact same guide!! :P

Here's mine:

```
How to install RALUS 11d on Ubuntu Server 8.04 (Hardy)

1) Install libstdc++2.10-glibc2.2
wget [http://ftp.kfki.hu/linux/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb](http://ftp.kfki.hu/linux/ubuntu/pool/universe/g/gcc-2.95/libstdc++2.10-glibc2.2_2.95.4-24_i386.deb)
sudo dpkg –i libstdc++2.10-glibc2.2_2.95.4-24_i386.deb

2) Install libstdc++5
sudo apt-get install libstdc++5

3) Install RALUS
mount /dev/cdrom
tar -xzvf /cdrom/pkgs/Linux/VRTSralus.tar.gz
tar -xzvf /cdrom/pkgs/Linux/VRTSvxmsa.tar.gz
sudo apt-get install alien
sudo alien --scripts VRTSralus-11.00.7170-0.i386.rpm
sudo alien --scripts VRTSvxmsa-4.4-021.i686.rpm
sudo dpkg -i vrtsralus_11.00.7170-1_i386.deb
sudo dpkg -i vrtsvxmsa_4.4-22_i386.deb

4) Configure Linux group
sudo addgroup beoper
sudo adduser <username> beoper

5) Configure RALUS
sudo nano /etc/VRTSralus/ralus.cfg 

And add a line like this for each Backup Exec server that will back up the Linux machine. 
So, assuming your Backup Exec server has an IP of 10.0.0.11 the line would be:

Software\VERITAS\Backup Exec\Engine\Agents\Agent Directory List A=<10.0.0.11>

6) Test RALUS
sudo /opt/VRTSralus/bin/VRTSralus.init start
sudo /opt/VRTSralus/bin/VRTSralus.init stop

6) Add startup script for RALUS
sudo touch /etc/init.d/ralus
sudo chmod +x /etc/init.d/ralus
sudo update-rc.d /etc/init.d/ralus
sudo nano /etc/init.d/ralus

Add the follwing to the file:

#! /bin/sh

/opt/VRTSralus/bin/VRTSralus.init $1

7) Test boot script
sudo reboot
login
ps aux | grep beremote
```
***NB***

You won't be able to even *see* your server in Backup Exec until you buy a RALUD 11d license.
According to the man I spoke to at Symantec, I can get a 60 day trial license by downloading the backupExec 11d trial and extracting it from there.
He didn't say how and we're just installing it on a test machine at the moment.

...

Does anybody know how to actually *restore* your server if it goes bang? Do you have to install a blank OS and RALUS and then do a restore? Or is there some sort of rescue boot CD you use?

J1M.

---

### Post by tabascoterrier on 2008-07-02
Ah well, two guides are better than none ;)

> 
Does anybody know how to actually *restore* your server if it goes bang? Do you have to install a blank OS and RALUS and then do a restore? Or is there some sort of rescue boot CD you use?


The route I'm taking is an O/S install, add the RALUS agent and do a flat restore...  Fine in theory, although I'll wait till the testing finishes before I claim victory.

For a bare metal restore, [Mondo Rescue]("http://www.mondorescue.org/") looks promising.

---

### Post by RoboJ1M on 2008-07-02
The Symantec guy told us about how BE 12 has some sort of rescue boot disk.

Not that we're forking out for that.

J1M.

---

### Post by RoboJ1M on 2008-07-02
[ftp://ftp.mondorescue.org/ubuntu/8.04/mondorescue.sources.list](ftp://ftp.mondorescue.org/ubuntu/8.04/mondorescue.sources.list)

sweet.

---

### Post by tabascoterrier on 2008-07-02
> **tabascoterrier said:**
> Fine in theory, although I'll wait till the testing finishes before I claim victory.

Hmm, my full restore experiences have been rather negative.

Booting into single user mode, and kicking off a restore from the Backup Exec console works fine until it hits /lib - the job fails with an 'Access denied' on ld-2.6.1.so, and I'm left with a very knackered Ubuntu box which won't boot.

I guess I'll be using Backup Exec for data only, and Mondo / periodic disk images for 'system state'.

---

### Post by RoboJ1M on 2008-07-02
OK, I tried adding our local admin account 'administrator' to beoper and using that instead of root.

We're getting can't connect/can't authenticate/server not running/incorrect version error message. (Why can't they ever tell you which one it is??)

How do you authenticate as root when you don't know that password for root?

```
sudo su
passwd
```

will that do it?

We're using a demo of BE 12d with RALUS 11d, I've read that they are backwards compatible.

There is know way at the moment to test it on our real BE 11d withough buying the license... :'(

J1M.

---

### Post by RoboJ1M on 2008-07-02
Ignore me, I just put the right IP in my firewall settings.
Test backup is running now.

---

### Post by tabascoterrier on 2008-07-02
> **RoboJ1M said:**
> We're getting can't connect/can't authenticate/server not running/incorrect version error message. (Why can't they ever tell you which one it is??)

I've not tried using a non-root user - but you're spot on, 
```
sudo passwd
``` will change your root password and allow you to use that.

Might be worth ensuring that your user is a member of the beoper group too.

Stopping the daemon, and running /var/opt/VRTSralus/bin/beremote --log-console might give you some insight (unless of course that's where you're getting your error from already!)

Failing that, it could well be the version mismatch :(

I'm told by our helpdesk guys that version 12 agents work on 11d servers, but they don't think it works the other way round.

If you have your original 11d install media, I think you can install that keyless as a 60 day trial.

---

### Post by RoboJ1M on 2008-07-02
> **tabascoterrier said:**
> Hmm, my full restore experiences have been rather negative.

Booting into single user mode, and kicking off a restore from the Backup Exec console works fine until it hits /lib - the job fails with an 'Access denied' on ld-2.6.1.so, and I'm left with a very knackered Ubuntu box which won't boot.

I guess I'll be using Backup Exec for data only, and Mondo / periodic disk images for 'system state'.

You should try posting on the Symantec forums. The Symantec staff are very helpful, even to us lowly Ubuntu Server users.

J1M.

---

### Post by RoboJ1M on 2008-07-03
Hi,

OK it's working now. The test backup server had two IP addresses and I only added rules for one to the firewall between them (so it was 'Can't connect' from that stupid catch all error)

RALUS 11d does work with 12, there was no problems.
Adding our "administrative" (in the Ubuntu sense) account "administrator" to beoper allowed us to back up with that account, no need to use root.

Now we just have to wait for a license for the real backup server (which runs 11d) :(

J1M.

---

### Post by nagios on 2008-07-18
This article was insanely helpful in allowing me to install BE 11d via RPM on an AMD64 Ubuntu 8.04 server. A couple of symlinks here and couple of changes to the script there and it's almost like the installer was designed for Debian. Many, MANY thanks to all who posted.

---

