---
title: "Precise beta won't install"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jerrylamos on 2012-03-08
Booted CD Daily Live updated as of today on Acer Aspire 1 netbook which has another partition running Precise Unity-3D just fine.

The "install icon" on the desktop is not there.

Selecting "Install" from the launcher flickers a few times and then nothing.  Tried rebooting.  no help.  Did a zsync.  No help.  Booted live and did sudo apt-get update, sudo apt-get dist-upgrade.  No help.

ubuntu-bug ubiquity says: 
"this is not an official package.  Please remove third party package"

I'm logged in and running CD live now.  Works O.K.

Is there a cli for starting install?

BTW, Beta installed and running fine (for a Beta) on two of my other test pc's.  Some oddities nothing serious.

Anything to try?  I can't enter a launchpad bug since ubuntu-bug won't work either.

Thanks for ideas,

Jerry

---

### Post by philinux on 2012-03-08
> **jerrylamos said:**
> 
Is there a cli for starting install?


Jerry

Try ubiquity from cli.

Not sure if it needs sudo, I guess not but I cant remember.

---

### Post by jerrylamos on 2012-03-08
> **philinux said:**
> Try ubiquity from cli.

Not sure if it needs sudo, I guess not but I cant remember.

Thanks, results as follows:

ubuntu@ubuntu:~$ sudo ubiquity
Inhibit all polling failed: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

Any ideas?  Any way to do a launchpad bug that would be helpful?

Thanks.

Jerry

---

### Post by jerrylamos on 2012-03-09
zsync every day and try again:

no install icon on desktop

install from launcher flickers a while.  A launch icon appears briefly seems to be "gksudo".

install from cli fails as above posts:

> ubuntu@ubuntu:~$ sudo ubiquity
Inhibit all polling failed: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

Same thing either "ubiquity" or "sudo ubiquity" or "gksudo ubiquity"

Have been booting .iso from USB port.  Copied today's zsync updated file to hard drive, booted the .iso, same result.

?  Any ideas anyone?

Jerry

---

### Post by jerrylamos on 2012-03-09
Startup disk creator with today's zsync of precise Beta onto a USB pen drive.

Same failures as booting the .iso file.  Added "installer_debug_log" and "bug" files to launchpad post:
[https://bugs.launchpad.net/ubuntu/+source/ldm-ubuntu-themes/+bug/950167](https://bugs.launchpad.net/ubuntu/+source/ldm-ubuntu-themes/+bug/950167)

Anything else?

Jerry

---

### Post by fantab on 2012-03-10
There seems to be some bug in daily builds which doesn't appear to effect everyone. I too had problem installing PRECISE Daily Build. I was trying to "Install Ubuntu" it did not work... then I "Try Ubuntu" and then installed from launcher and I worked for me. Or you can download the Beta 1 release and install it.

---

### Post by keithpeter on 2012-03-10
> **jerrylamos said:**
> 
ubuntu@ubuntu:~$ sudo ubiquity
Inhibit all polling failed: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success

Did an install last night from the live session desktop icon. It stopped, and using the 'details' box showed a command similar to the one you have quoted.

I just rebooted and went straight to 'install Ubuntu' skipping the live session. Went ok.

This is an old xeon quad core desktop with nvidia graphics card.

---

### Post by jerrylamos on 2012-03-10
Fired up sudo gparted and found a casper-rw on the other hard drive.  Must be the .iso is set to do "persistent".  

Formatted the casper-rw and renamed it.

Install went normally then....apparently there's no check to see if some of the files on an existing casper-rw don't match the .iso.

Jerry

---

### Post by jonnyboysmithy on 2012-03-11
Are you using a cd? maybe its damaged? or it corrupted during burning?
You could try to remake the live usb if thats what you're using.
Maybe download another copy or verify that the one you got is intact.

---

### Post by jerrylamos on 2012-03-12
> **jonnyboysmithy said:**
> Are you using a cd? maybe its damaged? or it corrupted during burning?
You could try to remake the live usb if thats what you're using.
Maybe download another copy or verify that the one you got is intact.

Johnnyboysmithy,

Thanks for your thoughts.

Problem was the .iso comes up in "persistent" mode, I didn't know that.  There was a "casper-rw" 1 GB partition on the other hard drive, which must have had some data from a previous live mode that wasn't compatible with the new .iso.

Sure looks like the .iso comes up, looks for a casper-rw, then uses data off the casper-rw without noticing it doesn't match the new .iso.

Anyway, formatted and renamed the casper-rw so the .iso wouldn't see it and then the .iso came up as intended.

Typing this from the new install running fine except for usual known Beta launcchpad bugs.

Do note the .iso live CD was running fine live except for install.

Precise is supposed to be a really long term LTS and it is shaping up to be just that, stable.  

I'll have to look around for some new stuff for bugs.  Until precise +1 development ubuntu is available in a couple months?  

Jerry

---

### Post by tlcstat on 2012-03-18
Greetings,
Can't get zsync to update iso. 

Results.
tlcstat@tlcstat-ubuntu:~$ sudo zsync [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso.zsync)
[sudo] password for tlcstat: 
#################### 100.0% 56.2 kBps DONE 

reading seed file precise-desktop-i386.iso: ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** **************************Read precise-desktop-i386.iso. Target 53.3% complete. *********
downloading from [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:)
##########---------- 53.3% 1.3 kBps aborted 8 ETA 

failed to retrieve from precise-desktop-i386.iso
Aborting, download available in precise-desktop-i386.iso.part
verifying download...tlcstat@tlcstat-ubuntu:~$ 

Any suggestions?

---

### Post by Gregory Lee on 2012-03-18
> **tlcstat said:**
> Any suggestions?
Don't use zsync.

---

### Post by tlcstat on 2012-03-18
Greetings,

Original by Gregory Lee
> Don't use zsync. 

Thanks!
I tried your suggestion and it works.

tlcstat

---

### Post by cariboo on 2012-03-18
I've had a problem using zsync a couple of times so far during this cycle. I don't know if it's a problem with the server, or something else. I found waiting a couple of hours usually solves the problem.

**Update:** I just used zsync to update my 64-bit iso, it restarted twice, but it did complete the update.

---

### Post by tlcstat on 2012-03-18
Greetings,
Ok, Got it working. Had to use the -i option and define my original iso. That's what I was originally doing but evidently when it started to fail and I tried different options I got off track.
tlcstat


ubuntu:~$ sudo zsync -i precise-desktop-i386.iso [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso.zsync)
#################### 100.0% 54.9 kBps DONE 

reading seed file precise-desktop-i386.iso: ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************Read precise-desktop-i386.iso. Target 53.3% complete. 
reading seed file precise-desktop-i386.iso: ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************************************************** ************Read precise-desktop-i386.iso. Target 53.3% complete. 
Read precise-desktop-i386.iso.part. Target 53.4% complete. 
downloading from [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:)
##########---------- 53.4% 2.9 kBps 
##########---------- 53.5% 6.3 kBps ETA 
##########---------- 54.1% 2.3 kBps ETA 
##########---------- 54.6% 2.0 kBps ETA 
###########--------- 55.0% 0.7 kBps ETA 
###########--------- 55.2% 1.4 kBps ETA 
###########--------- 55.3% 4.1 kBps ETA 
###########--------- 55.3% 3.0 kBps TA 
###########--------- 55.3% 4.6 kBps ETA 
###########--------- 55.3% 1.2 kBps TA 
###########--------- 55.3% 1.8 kBps TA 
###########--------- 55.3% 1.5 kBps 
###########--------- 55.3% 4.3 kBps 
###########--------- 55.3% 1.9 kBps 
###########--------- 55.3% 0.7 kBps ETA 
###########--------- 55.5% 26.7 kBps A 

downloading from [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:)
###########--------- 55.5% 4.3 kBps 
###########--------- 55.5% 4.2 kBps TA 
###########--------- 55.8% 4.3 kBps TA
+

Greetings,
Most definitely working. I use GPRS internet so I wanted to keep the download to a minimum. 
tlcstat

downloading from [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:)
###########--------- 55.5% 4.3 kBps 
###########--------- 55.5% 4.2 kBps TA 
###########--------- 55.8% 4.3 kBps TA 
###########--------- 57.4% 3.6 kBps TA 
############-------- 61.0% 4.9 kBps TA 
##############------ 72.9% 2.9 kBps TA 
##################-- 90.9% 0.6 kBps TA 
###################- 95.4% 59.8 kBps A 

downloading from [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:)
###################- 100.0% 58.5 kBps 

downloading from [http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/precise-desktop-i386.iso:)
#################### 100.0% 5.0 kBps DONE 

verifying download...checksum matches OK
used 392921088 local, fetched 342890475
tlcstat@tlcstat-ubuntu:~$

---

