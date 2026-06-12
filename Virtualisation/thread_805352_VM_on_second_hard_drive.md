---
title: "VM on second hard drive?"
date: 2008-05-23
forum: Virtualisation
---

### Post by braganfamily on 2008-05-23
I have 2 hard drives in my PC.  I have Ubuntu installed on sba, sdb is partitioned as primary partition ext2.

My question is, can I use the second drive (sdb) to install a VM on?  I know how to do it on the main drive (sda), but not on the other.

I don't know how that second drive should be partitioned or anything.

My first drive is limited on space, but the second is empty.

Info would be helpful.  I tried finding this on other posts but didn't see it directly addressed anywhere.

Thanks again.

bobby

---

### Post by dcstar on 2008-05-24
> **braganfamily said:**
> I have 2 hard drives in my PC.  I have Ubuntu installed on sba, sdb is partitioned as primary partition ext2.

My question is, can I use the second drive (sdb) to install a VM on?  I know how to do it on the main drive (sda), but not on the other.

I don't know how that second drive should be partitioned or anything.

My first drive is limited on space, but the second is empty.
......

In VMWare you can have VMs anywhere, just don't use the default.

---

### Post by braganfamily on 2008-05-24
Can I point to the location for the new VM before installing, like in preferences?  I've tried it but can't seem to find my second drive (sdb).  it is mounted but can't figure out how to point to it.

Or, is this something done during the "install new machine" process?  If so, how do I point to the other drive?

Also, how does the other drive have to be partitioned and formatted?

I have set up VM's before but always on primary drive.

Thanks.

bobby

---

### Post by braganfamily on 2008-05-24
Alright, got a little further.  When I try to point to /media/disk which is the moint point for my second drive, I get this:

Falied to create a hard disk image '/media/disk/Deb Drive.vdi' (VERR_ACCESS_DENIED).

Any ideas?  Where am I going wrong?

bobby

---

### Post by fjgaude on 2008-05-24
Let's see if we can steer you in the right direction. First, you have the vmware console installed on one drive and you wish to create a vm on another drive. Right, yes!

In the console do as you would to create a new vm, click on the type of vm, windows, linux, whatever. Notice Location, notice the path and the name you are giving to the new vm. Follow the prompts to the path or drive, the folder you wish to create the new vm upon. The new folder is the name you gave to the new vm.

From there it is just like you are creating the new vm on the same drive as the console is on.

Let us know how you are doing.

---

### Post by braganfamily on 2008-05-27
It will not let me use the second drive.  It says I do not have permission.  The drive owner is shown as root when I look at the properties.

This seems to be the "root" of my problem.  pardon the pun!

---

### Post by fjgaude on 2008-05-27
You should be able, while as root, go to that drive and change its permissions to that of you, the log-in user.

You might try using the command line, as root, loaded vmware, and then from the console try to create the vm on that drive. Then if you can, the vm will be in the inventory and you should be able to access it when non-root, through the console.

---

### Post by braganfamily on 2008-05-27
ok, heres the weird thing, I cannot login as root.  If I reboot and login as user "root" then password "root" it tells me incorrect login.  I haven't changed anything for root that I know of.  I may have to reinstall, this is weird.

Any idea?

again, thanks for the help.

bobby

---

### Post by fjgaude on 2008-05-27
At a terminal can you use sudo vmware? Enter your password and then see if you can find your drive.

---

### Post by braganfamily on 2008-05-28
Says, "command not found"

Also, I have been reading on some sites that user "root" login in ubuntu has to be activated, is not available by default, is that true?

thanks.

---

### Post by braganfamily on 2008-05-28
I tried to activate user "root" login in system>admin?users and groups but when I tried to login it said "system administrator cannot login in this window."

---

### Post by braganfamily on 2008-05-28
ok.  enabled "root" login, the correct way.  Logged in successfully to "root".  places>computer> right clicked on the drive icon, chose properties>permissions but it said "permissions could not be determined".

Is there another utility to accomplish changing the owner of this drive?

bobby

---

### Post by fjgaude on 2008-05-28
Since you cannpt use "sudo" there is something wrong with your install.

The root is not normally used in Ubuntu, but sudo is. That's how you get to root through the sudo command. You don't log on as root, but as a user with a name and password. That password is used with sudo, super user do.

---

### Post by braganfamily on 2008-05-28
ok.  Did re-install.  Same problem.  Is there anything special I need to do to the second drive.  When I format it as primary partition, ext3, it has a "lost and found" folder in it with a red circle and black "x" next to it.

Is that normal?  Does it need anything done to it?

I tried it on my office PC which has totally different hardware but same problem.  I'm missing something on accessing the second drive for use with VB.  I, tried a different install CD at the office, same result.

any ideas?

---

### Post by fjgaude on 2008-05-28
Likely you may need a "header" on the file, called a DOS Label. You can do that with gparted.

---

### Post by Brian96 on 2008-05-28
I'm having a similar problem. I have my VMs stored on a partition that I share between OSes. I have been doing this since Feisty, and I can't remember a) if I've ever had this problem before and b) how I overcame it.

Basically, when I try to open the VMX on my shared partition, VMWare Server tries to run it, but crashes.

For grins, I moved the VMX to my Home folder and it ran fine, so this is definitely a permissions problem.

In "gksu nautilus" I tried to change the permissions of the partition from root to my username, but it kept changing them right back (no error message).

Oh, and Bragan, if you click on the drive icon in "Computer" in nautilus it will give you the weird "permissions unknown" message. Navigate to File System => Media and the device name and you can check permissions there. I think both of us just need to change the permissions on our drive of choice; unfortunately I'm not sure why we're having so much trouble with this.

---

### Post by braganfamily on 2008-05-29
Thanks for all the info, but I decided to save time.  I moved my hard drives around and did a reinstall.  Now I have loaded ubuntu on my large drive, VM should be fine now.  Thanks again.

bobby

---

