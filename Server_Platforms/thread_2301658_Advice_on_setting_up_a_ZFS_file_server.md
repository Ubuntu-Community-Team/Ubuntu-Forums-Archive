---
title: "Advice on setting up a ZFS file server"
date: 2015-11-04
forum: Server Platforms
---

### Post by Chris_Shelton on 2015-11-04
Hi all,

I'll first explain my situation:

I work for a small (~45 people) software development company and have been tasked with replacing our current NAS. We currently have a 1-bay 2TB QNAP device that serves primarily Windows users (+1 Mac user) via Samba. 

This works fine for us, but, we need something with more space which is RAID'd for obvious reasons. I started out by looking at other QNAP devices which could hold more disks, but they are very expensive, they use traditional RAID rather than ZFS which I want to use, and I believe I can build something better for cheaper.

So I bought all the parts: Xeon CPU, Supermicro MoBo, 32GB ECC RAM and 6 x 2TB WD Red disks etc.

I was recommended to look into NAS4Free, but I discovered that it stores user passwords in plain text - no good.
I then looked into FreeNAS, but was informed that I had to set up Windows shares and manage permissions via Windows Explorer - again, no good.

I decided to ditch the ready-built solutions and try configure my own from scratch with Ubuntu. But I'm not sure on a few things. As far as I'm aware, I will need:

Ubuntu Server LTS
Gnome (to manage via GUI)
SSH
ZFS
Samba

I want the ZFS data to be set up in RAID-Z2, which will be backed up to Azure every night so that is safe.

My main question is, what about the configuration of Ubuntu itself, how do I back that up? If my boot disk fails for some reason, I want to be able to be able to get back up and running with users and all other bits of configuration as quick as possible. Is there an equivalent of downloading a 'config file' that can be restored back to a fresh installation? What is the recommended way of doing this?

Thanks in advance for any help, Chris.

---

### Post by darkod on 2015-11-04
Is the GUI really necessary for you? You can manage all over ssh.

Do you plan to run the OS from the same disks, or separate disks for the OS and separate ZFS array for data? It's probably best the OS to be separate, which means you will need couple of small disks in software raid1 for the OS. Do you have space for them in the case? If not, there are other options too...

Backing up the ubuntu config depends mostly of what you are running. If there is only samba, you can make regular backups of the smb.conf and that should be enough (unless you have specific configuration in another file). Basically, as long as you backup the main configuration files that you will modify, it's easy to restore them. And they are the most important ones.

You can always do regular rsync of the whole root partition but note that there will be some open files in ude that will not sync 100%. However, it should still be enough for good restore.

---

### Post by Lars Noodén on 2015-11-04
There's not much on the OS side that needs backing up.  The full contents of /etc using rsync plus the output of *dpkg --get-selections* are about it.  They could even be saved on small USB sticks.  

The data in /var and /home are another matter though.

---

### Post by lukeiamyourfather on 2015-11-04
> **Chris_Shelton said:**
> I then looked into FreeNAS, but was informed that I had to set up Windows shares and manage permissions via Windows Explorer - again, no good.

That doesn't sound right. Either way Ubuntu and ZFS on Linux are a good combination. I suggest using a dedicated drive for the operating system if you haven't already planned on doing that. Like Lars said there's not much to backup except the contents of /etc unless you install other random stuff or have third party software.

---

### Post by Chris_Shelton on 2015-11-11
> **darkod said:**
> Is the GUI really necessary for you? You can manage all over ssh.

Do you plan to run the OS from the same disks, or separate disks for the OS and separate ZFS array for data? It's probably best the OS to be separate, which means you will need couple of small disks in software raid1 for the OS. Do you have space for them in the case? If not, there are other options too...

Backing up the ubuntu config depends mostly of what you are running. If there is only samba, you can make regular backups of the smb.conf and that should be enough (unless you have specific configuration in another file). Basically, as long as you backup the main configuration files that you will modify, it's easy to restore them. And they are the most important ones.

You can always do regular rsync of the whole root partition but note that there will be some open files in ude that will not sync 100%. However, it should still be enough for good restore.

Thanks for your reply.

The GUI is necessary really, not particularly for me as I am okay with doing things on the CL, however, the new NAS is going to be managed by placement students who get changed every year and their knowledge of Linux can't be relied upon. Unless it is advised not to have one?

I'm not really sure about what to do with the OS really, I need some advice. Unfortunately I don't have any more SATA ports which would make that a bit tricky. All 6 slots are taken up by disks for ZFS which means I currently have Ubuntu installed on a 16GB USB stick. I don't mind having to reinstall Ubuntu fresh in case of a failure, but I wanted a quick-ish way to restore things like users/permissions/shares etc. Is there any way to keep a backup of the OS, or keep the important config files inside the ZFS pool somehow? As that would automatically get backed up nightly.

The main things I will be editing are: users(+paswords), groups, permissions, samba shares, ZFS user quotas.
Would these all be covered in /etc?

> **lukeiamyourfather said:**
> That doesn't sound right. Either way Ubuntu and ZFS on Linux are a good combination. I suggest using a dedicated drive for the operating system if you haven't already planned on doing that. Like Lars said there's not much to backup except the contents of /etc unless you install other random stuff or have third party software.

Thanks for your reply.

I do believe that is correct, I have had numerous people on the forums tell me so. 

I don't have any spare SATA ports to run a separate disk for the OS, currently just on a 16GB USB stick. Would it be okay to keep using the USB stick and make regular copies /etc? There won't be any other third part software bits etc.

> **Lars Noodén said:**
> There's not much on the OS side that needs backing up.  The full contents of /etc using rsync plus the output of *dpkg --get-selections* are about it.  They could even be saved on small USB sticks.  

The data in /var and /home are another matter though.

Thanks, this seems to be the most recommended way of doing it. Is there anyway to actually store the copy of /etc in the pool? Then that would be automatically backed up offsite overnight.

---

### Post by darkod on 2015-11-11
Hmmm, /etc on the pool... Not sure, I have never tried it. Haven't played too much with ZFS in ubuntu, only quick tests.

The problem in my opinion is that ZFS depends on the package you will install in ubuntu, so I am not sure if it "starts" the pools before "booting the OS". If for example you put /etc as mdadm array, I know that can work. But on zfs pool, you have to test...

First of all, the specific mount points (partitions,arrays) are usually done right from the start, in the installer. The installer can create mdadm but it can't create zfs. So how would you tell it that /etc is on a pool.

You could install without separate /etc and then "move it", but not sure if that's preferred...

Doing rsync of most important parts sounds like the best option... Leave /etc in the main /.

Ubuntu should run fine from usb stick, the only issue is that usb sticks are not designed for too many read/writes. On the other hand, ubuntu system files should not be too read/write intensive, and all data will be on the disks. But depending on the stick it might die sooner rather than later. One possible option would be using CF cards, which are little better equipped for OS to be running on them. But if using standard CF-to-SATA adapter you still need where to plug it into a sata port. Maybe a PCIE SATA controller to add at leats 2 sata ports? In such case you could use 2 CF cards plugged into those new 2 sata ports, and have mdadm raid1 for the OS. Just one suggestion...

If you buy SATA controller and you have physical space for HDDs (but no sata ports), you can use standard HDDs instead of any CF cards... Depending what works best for you... With no HDD space you can only do USB stick or CF card...

---

### Post by Lars Noodén on 2015-11-11
> **Chris_Shelton said:**
> Is there anyway to actually store the copy of /etc in the pool? Then that would be automatically backed up offsite overnight.

Setting up ZFS again would need some of the stuff you would be saving from /etc/  You could do a backup to ZFS in addition to a local backup, but before you could use it for a restore you would have to install a machine and get ZFS up and running again, or else travel to your other ZFS machine and make a new stick from that.  If you have /etc/ plus dpkg output on the stick you can keep that locally for backup and use the ZFS part for a backup of your backup. 

About the GUI, the *easy* way is to avoid it altogether on the server.  Here are a few of the advantages I see.  Common tasks done with the shell can be scripted and the scripts launched with a word or even a clickable icon.  It's easier to type up a guide that way without needing screen shots.  And it's far easier over the phone to talk someone through a task with the shell than with the GUI, "no not that click on the other thing which is colored __ and looks like a __ and might be visible near ___"    It allows you to work remotely with ease if something comes up, saving you a trip in.  And lastly you can mentor someone over the phone by both logging in and calling up a shared [screen](http://manpages.ubuntu.com/manpages/trusty/en/man1/screen.1.html) or [tmux](http://manpages.ubuntu.com/manpages/trusty/en/man1/tmux.1.html) session and looking over their shoulder as they work.

About the only down side to the shell is that Microsoft has spent millions over years disparaging the shell because they had nothing as powerful.  So many people have heard that they should be afraid of the shell or that it is hard.  They still don't have anything as powerful and flexible but have now added a weaker imitation.  So bash/ksh/zsh is like 'powershell(r) on steroids'

There are some other things you could do with restricted shells and allowing only certain scripts, too.

---

### Post by Chris_Shelton on 2015-11-11
> **darkod said:**
> Hmmm, /etc on the pool... Not sure, I have never tried it. Haven't played too much with ZFS in ubuntu, only quick tests.

The problem in my opinion is that ZFS depends on the package you will install in ubuntu, so I am not sure if it "starts" the pools before "booting the OS". If for example you put /etc as mdadm array, I know that can work. But on zfs pool, you have to test...

First of all, the specific mount points (partitions,arrays) are usually done right from the start, in the installer. The installer can create mdadm but it can't create zfs. So how would you tell it that /etc is on a pool.

You could install without separate /etc and then "move it", but not sure if that's preferred...

Doing rsync of most important parts sounds like the best option... Leave /etc in the main /.

Ubuntu should run fine from usb stick, the only issue is that usb sticks are not designed for too many read/writes. On the other hand, ubuntu system files should not be too read/write intensive, and all data will be on the disks. But depending on the stick it might die sooner rather than later. One possible option would be using CF cards, which are little better equipped for OS to be running on them. But if using standard CF-to-SATA adapter you still need where to plug it into a sata port. Maybe a PCIE SATA controller to add at leats 2 sata ports? In such case you could use 2 CF cards plugged into those new 2 sata ports, and have mdadm raid1 for the OS. Just one suggestion...

If you buy SATA controller and you have physical space for HDDs (but no sata ports), you can use standard HDDs instead of any CF cards... Depending what works best for you... With no HDD space you can only do USB stick or CF card...

When I said to keep the config files inside the pool, I meant keep a copy of /etc in the pool so that gets backed up. The system would still boot as normal from main/ but the copied version would be stored on the pool. Best thing seems to be just take a copy of /etc using rsync and store it offsite along with the backup of the ZFS data. How would I go about getting the /etc restored back to a new installation of Ubuntu if it decided to fail? Would there be much messing about to get the system up and running again, with ZFS? I will reconsider the installation onto a USB stick, if there is a budget for it, I will get a PCIE SATA controller so I can install onto a proper HDD.

> **Lars Noodén said:**
> Setting up ZFS again would need some of the stuff you would be saving from /etc/  You could do a backup to ZFS in addition to a local backup, but before you could use it for a restore you would have to install a machine and get ZFS up and running again, or else travel to your other ZFS machine and make a new stick from that.  If you have /etc/ plus dpkg output on the stick you can keep that locally for backup and use the ZFS part for a backup of your backup. 

About the GUI, the *easy* way is to avoid it altogether on the server.  Here are a few of the advantages I see.  Common tasks done with the shell can be scripted and the scripts launched with a word or even a clickable icon.  It's easier to type up a guide that way without needing screen shots.  And it's far easier over the phone to talk someone through a task with the shell than with the GUI, "no not that click on the other thing which is colored __ and looks like a __ and might be visible near ___"    It allows you to work remotely with ease if something comes up, saving you a trip in.  And lastly you can mentor someone over the phone by both logging in and calling up a shared [screen]("http://manpages.ubuntu.com/manpages/trusty/en/man1/screen.1.html") or [tmux]("http://manpages.ubuntu.com/manpages/trusty/en/man1/tmux.1.html") session and looking over their shoulder as they work.

About the only down side to the shell is that Microsoft has spent millions over years disparaging the shell because they had nothing as powerful.  So many people have heard that they should be afraid of the shell or that it is hard.  They still don't have anything as powerful and flexible but have now added a weaker imitation.  So bash/ksh/zsh is like 'powershell(r) on steroids'

There are some other things you could do with restricted shells and allowing only certain scripts, too.


What exactly would ZFS need from /etc to be running as normal? If I start with a fresh installation of Ubuntu, get a copy of /etc from my offsite backup restore it, then install ZFS, do I just need to import the pool to get it working again? You make good points with regards to the GUI, I will take it to my line manager along with your recommendations, thanks.

---

### Post by darkod on 2015-11-11
For getting the system up and running again, and in the most efficient manner, I would go step by step... (and I can't answer all of your questions, I don't know)

1. The zfs pools. Easy enough. For the zfs pools you only need to import them, once you have the ubuntu OS and zfs package installed again. I have even done a test between ubuntu with zfs and FreeNAS, importing a pool created by the "other" system. It worked, in both directions. So importing the pools should not be an issue. Permissions should remain intact after pool import too (maybe someone with more zfs experience can comment on this?). That is an important point, not needing to do the shared files/folders permissions again. Depending on your structure and complexity, redoing permissions might take ages. But I'm pretty sure an imported pool retains them.

2. Samba. Unless I'm very wrong, for samba shares all you need is the /etc/samba/smb.conf copy. If you include that in your rsync backups, after you reinstall ubuntu and samba, simply overwrite the default smb.conf with your backup, restart samba, and you should have your shares.

3. Users and passwords. According to your post, you plan to keep local users/passwords? That might be complex to recover. Is a more centralized user management possible? Like AD or LDAP? In such case the users are not on your ubuntu server so no need to worry about restoring them. On the other hand, if you plan to use local users, the list of users and groups are in /etc/passwd and /etc/group. Restoring this files from backup should give you the same lists you had, but I'm not sure if it can work like that. Don't forget, users are important for system security so simple overwrite of /etc/passwd might not be enough. Also, I have actually never investigated where does ubuntu store the passwords. If you can restore that file with the passwords and the /etc/passwd and it works, perfect. Someone else can comment on this? There are probably loads of google hits too if you do a search on this subject.

I see the above as most important for a recovery of the machine. The default system files you don't need to worry about since you will be reinstalling and all of them will get installed. You only restore from backup (overwrite) the most essentials that you need. If I missed something, comment...

---

### Post by Lars Noodén on 2015-11-11
> **darkod said:**
> if you plan to use local users, the list of users and groups are in /etc/passwd and /etc/group. Restoring this files from backup should give you the same lists you had, but I'm not sure if it can work like that. Don't forget, users are important for system security so simple overwrite of /etc/passwd might not be enough. Also, I have actually never investigated where does ubuntu store the passwords. If you can restore that file with the passwords and the /etc/passwd and it works, perfect.

Ubuntu has the users and groups in four files, for passwords and such:

/etc/group
/etc/gshadow
/etc/passwd
/etc/shadow

and these two additional files are needed:

/etc/subgid
/etc/subuid

---

### Post by mastablasta on 2015-11-11
regarding GUI - you can use a browser GUI such as Ajenti, Zentyal (Ubuntu), ClearOS, Nethserver (CentOS).. you then administer the server via browser. and this is probably the comments from FreeNAS refered to. to use a browser. and since in windows default is IE... if you must have a GUI it is better to have a browser based one.

regarding OS on USB. i had mine die in abotu 6 months or so. the second one looks like will outlast it. you could use a USB hard disk maybe? Swapiness should be reduced if the whole OS is on USB
ZFS is a file system. Linux has similar one called BTRFS. but ZFS on linux should also be OK, though it is more developed for BSD as i understand.

---

### Post by lukeiamyourfather on 2015-11-11
> **Chris_Shelton said:**
> I do believe that is correct, I have had numerous people on the forums tell me so.

Try it for yourself. It takes 15 minutes to setup. From everything you've described it sounds like FreeNAS is exactly what you're looking for.

---

