---
title: "LTSP kernel image permissions with Ubuntu 14.04"
date: 2014-05-05
forum: Server Platforms
---

### Post by dschuur on 2014-05-05
We've been successfully running **LTSP** with Ubuntu 12.04 for several years in our school computer lab. Recently we updated our server to **Ubuntu Server 14.04** (by performing an upgrade from the command line). After the server upgrade was complete, I removed and purged the LTSP package (ltsp-server) and reinstalled to get a "fresh" install.

I then built a new client using **ltsp-build-client** and rebooted the server. Upon booting a thin client, I got the following error:  **could not find kernel image: vmlinuz**

I tracked down what appears to be a permissions problem in **/var/lib/tftpboot/ltsp/amd64/**  The **vmlinuz-3.13.0-24-generic** file is owned by root and had file permissions set to 640. There appeared to be permission problems for System.map-3.13.0-24-generic and the pxelinux.cfg/litsp* files as well.  I used chmod to set the permissions to 644 and the thin clients were able to proceed with booting. It also seems that everytime I run ltsp-update-image I have to fix the permissions again...

Has anyone else experienced this? Any sage advice?

Also, which LDM session is recommended when using LTSP under Ubuntu 14.04? Unity sessions do not appear to be working properly in my thin clients - users can log in, but only the desktop appears with no unity side panel...

thanks,
Derek

---

### Post by dschuur on 2014-05-20
Just an update in case others want a follow-up, I have made some progress on this thread:

[COLOR=#000000]After updating to Ubuntu 14.04, LTSP thin-client users can log in but only a desktop background appears... After some exploring, I discovered that if one removes the **.dmrc** file from a user's home directory the user can log in and things work as expected :) Our users had old .dmrc files left behind which were set for a unity session. It seems that the .dmrc trumps the LDM_SESSION setting in the lts.conf file. (Note - make sure there are no settings that you need to keep before removing your .dmrc file).

Also, I am currently setting LDM_SESSION to use the "gnome-fallback" session - after fixing things as above I got unity running but it was extremely slow...

As far as the permissions problem in [/COLOR]**/var/lib/tftpboot/ltsp/amd64/**, each time I rebuild the image I need to execute the following commands to restore permissions:
cd /var/lib/tftpboot/ltsp/amd64/
chmod 644 vmlinuz-3.13.0-24-generic 
chmod 644 System.map-3.13.0-24-generic 
chmod 644 pxelinux.cfg/ltsp*

Is this a bug or is there something I am missing?

thanks,
Derek

---

### Post by dschuur on 2014-05-26
Just another quick update regarding the file permissions issue in **/var/lib/tftpboot/ltsp/amd64/** -- I tracked the issue down to a modified **umask** setting in **/etc/login.defs**. The umask settings were changed to 027 so that the default file permissions prevent users from being able to read files in other peoples home folders. Unfortunately this had the undesired side-effect that the default file permissions of the image files created by **ltsp-update-image** were no longer readable either...

The file permissions of the vmlinuz boot image file should always be world-readable regardless of any changes in login.defs, no?  It seems this problem could be averted in the future by simply adding a line to the **generate_image** function in **ltsp-update-image** script to **chmod o+r** the image file... Is this a change that might be useful to submit?

thanks,
Derek

---

### Post by Ashlyn_Gilly on 2014-06-05
Hi. I also work at a school and am trying to run LTSP with Ubuntu 14.04. I really have no idea where to start. Not many of the tutorials I have looked up online have worked for me. Would you be willing to help me get started with running an ltsp onto 14.04? Thank you.

---

### Post by dschuur on 2014-06-19
As far as I recall, the installation of LTSP under 14.04 was essentially the same as with previous versions of Ubuntu (albeit that 14.04 packages include some newer software versions).

The issue I was running into was due to a modified umask setting (and a bug has been filed documenting this issue - see: [https://bugs.launchpad.net/ltsp/+bug/1320994](https://bugs.launchpad.net/ltsp/+bug/1320994) ). Once the umask setting was returned to its default value, the installation worked fine.

---

### Post by felix10 on 2014-06-30
Hi, I haven't try 64bit.  I was able to get 32 bit up and running, but my problem was I'm not able to get thin client to log on automatically like ubuntu 10.10.  Does anyone know how to configure the thin client to logon automatically and clean up profiles when log off.  the how to on ubuntu 14.04 ltsp 32 bit I've follow was at [www.talkingtek.com](www.talkingtek.com).

---

