---
title: "Vmware workstation 8 on Ubuntu 12.04"
date: 2012-05-01
forum: Virtualisation
---

### Post by chaitanyakumar on 2012-05-01
Hi All,

I have Ubuntu desktop version 11.10. I have installed vmware-workstation 8.0.2 long time back in it. After vwmare is installed, I got a message that kernel needs to be updated. I have googled and found a solution. I dont remember those steps, but it is something like apt-get install kernel-headers, apt-get install kernel-dlevel, something like this..  2 days back, when I have tried to update my software, I got a notification that there is an update. I have updated it successfully. Now my ubuntu version is Ubuntu 12.04 LTS. From the time it is upgraded, I am not able to open vmware. When I open vmware, it gives me a message, "Before you can run vmware, several modules must be compiled and loaded into running kernel". I get a prompt to install or cancel. If I click install, it says stopping vmware services, and after few mins, it says unable to start services. I have googled the same message but no use. For each and every command(like sudo apt-get install linux-headers etc..) it says it is upto date. Please suggest me what to do now.

Thanks,
Chaitanya.

---

### Post by Jelly Doughnut on 2012-05-02
This is a known issue.  VMware 8.0.2 is not compatible with the 3.2.x kernel in 12.04LTS.  To get it to work, you will have to patch some of the VMware components.

Follow the directions in the third message (the message from mfelker) at the link below.  First you need to completely uninstall VMware Workstation 8.0.2.  Then reinstall it and before you run it the first time, patch it.  This procedure fixes the issues for me.

[http://communities.vmware.com/message/2034437](http://communities.vmware.com/message/2034437)

---

### Post by chaitanyakumar on 2012-05-04
Hi [Jelly Doughnut,]("http://ubuntuforums.org/member.php?u=1629184")

First of all thank you very much for replying.. I am very sorry to say that I am unsuccessful in using the patch. I have checked the third reply. I have downloaded the tar.gz file, extracted to my desktop. we have .sh script and .patch file in it. I have run .sh script. It gave me a message that this script works only for vmware workstation 8.0.2 and vmware player 4.0.2. While installing, I saw the setup installing vmware player 2 version. Is this the problem and bcoz of this script is not working? Please let me know what needs to be done. I am using vmware 8.0.2 version only. As I was using the same version from more than a month, I am sure about it. Please help....

---

### Post by SlugSlug on 2012-05-04
fix here 

[http://ubuntuforums.org/showthread.php?t=1954164](http://ubuntuforums.org/showthread.php?t=1954164)



[http://weltall.heliohost.org/wordpre...l-3-2-and-3-3/]("http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/")

---

### Post by chaitanyakumar on 2012-05-04
No luck slugslug,

I have gone through both the links. I have already seen [http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/](http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/) link. I was telling about the same one in my previous post. I downloaded the patch, but while installing, it says, Sorry, this script is only for VMware workstation 8.0.2 or vmware player 4.0.2. Exiting. Please find the same in my attachment. This is what I have mentioned in my previous post... Please do the needful. 

Thanks,
Chaitanya.

---

### Post by SlugSlug on 2012-05-04
whats output of 

vmware-installer -l

---

### Post by chaitanyakumar on 2012-05-05
Hi 

Output is: vmware-workstation   8.0.2.591240. Please find the same in the screenshot.

---

### Post by chaitanyakumar on 2012-05-06
Thank you very much guys,

Now my problem is resolved.

I did it manually following the below process:


Find the source code
On my system it is at /usr/lib/vmware/modules/source

Untar source modules
tar xvf vmnet.tar
This creates a subfolder containing the source files (in this case, vmnet-only).

Apply the patch
Assuming the patch file is ~/Downloads/vmware3.2.0.patch
patch -p1 < ~/Downloads/vmware3.2.0.patch

Re-Tar the source folder
tar cvf vmnet.tar vmnet-only/

Rerun the module compilation process and hope the patches fix the problem.

Thanks to all,
Chaitanya.

---

### Post by schuettr on 2012-06-24
Had same problem with Ubuntu 12.04 and workstation 8.04. This fixed it up. Thanks for the info

---

### Post by BrianMCollins on 2012-07-03
> **chaitanyakumar said:**
> Thank you very much guys,

Now my problem is resolved.

I did it manually following the below process:


Find the source code
On my system it is at /usr/lib/vmware/modules/source

Untar source modules
tar xvf vmnet.tar
This creates a subfolder containing the source files (in this case, vmnet-only).

Apply the patch
Assuming the patch file is ~/Downloads/vmware3.2.0.patch
patch -p1 < ~/Downloads/vmware3.2.0.patch

Re-Tar the source folder
tar cvf vmnet.tar vmnet-only/

Rerun the module compilation process and hope the patches fix the problem.

Thanks to all,
Chaitanya.

Happy, happy, happy - thanks so muc, worked like a charm!

---

### Post by vab3 on 2012-07-27
This worked for me upgrading to vmware 8.04 on Ubuntu 12.04. 

After applying the patch, you can type:

sudo vmware-modconfig --console --install-all

at the command line to complete the upgrade process.

---

### Post by jjapol on 2012-08-20
This was also a successful fix for me.
Ubuntu 12.04 with Vmware Workstation 8.0.4.7xxxxx
Note I did NOT have to uninstall VmWS prior or after patching.
Thanks all for posting!
jjapol

---

### Post by yuwang on 2012-09-22
> **chaitanyakumar said:**
> Thank you very much guys,

Now my problem is resolved.

I did it manually following the below process:


Find the source code
On my system it is at /usr/lib/vmware/modules/source

Untar source modules
tar xvf vmnet.tar
This creates a subfolder containing the source files (in this case, vmnet-only).

Apply the patch
Assuming the patch file is ~/Downloads/vmware3.2.0.patch
patch -p1 < ~/Downloads/vmware3.2.0.patch

Re-Tar the source folder
tar cvf vmnet.tar vmnet-only/

Rerun the module compilation process and hope the patches fix the problem.

Thanks to all,
Chaitanya.


Thanks! you saved my day!

---

