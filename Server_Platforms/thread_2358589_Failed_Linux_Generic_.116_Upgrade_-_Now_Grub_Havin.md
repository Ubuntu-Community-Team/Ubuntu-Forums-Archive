---
title: "Failed Linux Generic .116 Upgrade - Now Grub Having Issues - Stuck"
date: 2017-04-12
forum: Server Platforms
---

### Post by w-kym-wittal on 2017-04-12
I am running Ubuntu 14.04 LTS, 64 bit server.  I recently attempted to upgrade the Linux code to the .116 release, but it errored due to low disk space.  To fix the low disk space I deleted (placed into Trash) the .110 files and the .112 files.  When I reboot, I get the Grub, but when I try to launch into the .110 files or the .112 files, nothing (since I moved them of course) (.116 does not work due to the errors).

I have older .108 stored as well, but they hang for some reason and even older files do not seem to get very far.

I think the solution is as simple as finding the deleted files in Trash and moving them back.  I am having a terrible time doing that (cannot find the deleted files in Trash - can see Trash, but nothing there).  I also tried to recover the files from a recent backup, but no luck getting the backup to be recognized.  I also tried to just copy new versions of the .112 files into the directory, but was overwhelmed by all of the choices/versions, etc.

I would like some help as to how to find and move the deleted files with the terminal (or gui if possible) or how to get the backup to be recognized (from Ubuntu desktop, not server) or how to download new files or how to reload the server system WITHOUT loosing and settings, etc.

Thank you very much, frustrated.

---

### Post by mörgæs on 2017-04-13
Hi, welcome to the fora.

When one wants to get rid of old kernels the preferred command is **sudo apt autoremove**. Not that it solves your immediate problem but for the future.

---

### Post by howefield on 2017-04-13
> **w-kym-wittal said:**
> would like some help as to how to find and move the deleted files with the terminal (or gui if possible) or how to get the backup to be recognized (from Ubuntu desktop, not server) or how to download new files or how to reload the server system WITHOUT loosing and settings, etc.

I don't believe a server installation has a "trash" so rm'ing a file means it is really gone and fairly difficult, if not impossible to retrieve. 

The thread may be better off in the "*Server Platforms*" forum, if you want it moving let me know or use the report button.

---

### Post by w-kym-wittal on 2017-04-14
Yes, please, move to the 'Server Platforms' forum.  Thanks for the replies/comments.

---

### Post by howefield on 2017-04-15
Moved to the "*Server Platforms*" forum as requested and free "*bump*".

---

### Post by darkod on 2017-04-15
The solution is not to look for files to copy/move, but instead to install them properly. Because there is more to installing kernel files than just copying them.

And for future reference, ALWAYS check free space first before updating your server, especially if you are not doing regular housekeeping of the disk space. Because once you get into low free space problem, it's not very easy to get out. Usually apt-get autoremove will not work either.

And when you delete kernel files in an emergency, you never delete the file you are currentl running (did you check which kernel was loaded before deleting?), and you never delete recent ones, just older ones. And you never reboot before emoving or repairing the last kernel that failed to be installed when you ran out of space.

Anyway, lets see what you have now and how we can help...

1. How are you booting the machine now? Can you boot into recovery mode or it is completely unbootable?
2. If it's completely unbootable, do you have the ubuntu desktop live cd so you can use it to boot into live mode and work from there?

---

### Post by w-kym-wittal on 2017-04-16
Thanks for the feedback.  Clearly I have more to learn.

I can boot the machine and get into GRUB.  It lists multiple kernels (.116, .112, .110, .108 and then a couple of older ones).  I can boot in recovery mode on any of them.  Booting into any of the kernels either states files not found (for the kernels I deleted) or does not boot properly for .116 (because it did not install properly).  The .108 kernel I have never touched, yet it will not boot into that.

I can also load a desktop version (14.04) and work with it.

Also, I tried Boot Recovery Disk, but it fails since it cannot find the .112 kernel to 'erase' and start over.

Thanks for any assistance/advice you can provide.

---

### Post by darkod on 2017-04-17
If you can load the recovery mode of any kernel, this should be easy to fix. In the recovery menu select "drop to root shell". That will load a shell where you will be working as root, that means you don't need to use sudo in front of commands.

After the shell loads, first you need to do is remount the root partition for writing because the shell loads it read only. After that try fixing any missing packages/dependencies:
```
mount -o remount,rw /
apt-get update
apt-get install -f
```

If that finishes correctly, what you can do is autoremove all unnecessary packages which will free some space and then reboot:
```
apt-get autoremove
reboot
```

Try booting into the latest kernel in normal mode (not recovery) and see if it loads.

---

### Post by w-kym-wittal on 2017-04-17
I ran the first suite of code and it appears to have failed (the final  line is error code (1)).  It seems to be having trouble  finding/downloading kernel .112 and configuring kernel .116 (from what I  can tell as the messages are scrolling past).

I tried rebooting, went back to GRUB, tried booting .112 normally and received the following:

Loading Linux 3.13.0-112-generic
error: file '/vmlinux-3.13.0.112-generic' not found
Loading initial ramdisk ...

Then it hangs.

Any thoughts?

---

### Post by darkod on 2017-04-18
You are still running 3.13?

Try this:
1. Boot into recovery mode again.
2. Do the read-write remount command.
3. Try installing newer LTS stack (kernel) with:
```
apt-get install --install-recommends linux-generic-lts-xenial
```

That will try to install the xenial kernel enabled for 14.04. Let us know how it went...

---

### Post by w-kym-wittal on 2017-04-18
I ran the LTS stack process and it errored out:

E: Sub process /usr/bin/dpkg returned error code (1)

I tried rebooting, same result, back to GRUB.

I tried the LTS stack process again, see attached (poor) screenshot - [ATTACH=CONFIG]274628[/ATTACH]  (Sorry, cannot seem to get photo right side up).

I typed y, the following is the result:[ATTACH=CONFIG]274629[/ATTACH]

Any of this useful?  Thanks again for your patience.

---

### Post by darkod on 2017-04-18
Ok, some more info needed obviously... Can you please post the output of:
```
df -h
dpkg --list | grep linux-image | grep generic
ls -lh /boot/
uname -r
```

If you can use ssh remote session (not sure it works in recovery mode) then you can easily copy paste the commands output inside CODE tags.

Failing that, you can also try to finish necessary dependencies and to finish configuring all pending packages (the last screen is complaining the configure of one kernel was not completed):
```
apt-get install -f
dpkg --configure -a
```

Note that these two commands will not do much good if you have the root or /boot full (no free space).

PS. One of the screens also says you have linux-generic-lts-xenial already installed so I wonder why upgrading 3.13.0-116 is an issue because with xenial kernel you should be on something like 4.4.0-xx now.

---

### Post by w-kym-wittal on 2017-04-19
I went the easiest way (for me) and ran the code requested and took photos.  Results below:df -h
[ATTACH=CONFIG]274651[/ATTACH]
dpkg --list | grep linux-image | grep generic
[ATTACH=CONFIG]274654[/ATTACH][ATTACH=CONFIG]274655[/ATTACH]  
(see next post for remaining screen shots of this command)
ls -lh /boot/
[ATTACH=CONFIG]274652[/ATTACH]
uname -r
[ATTACH=CONFIG]274653[/ATTACH]

I have not gone any further with the second suite of code.  I will wait until you have reviewed this to attempt the package configuration process.  Thanks.

---

### Post by w-kym-wittal on 2017-04-19
Remaining screenshots:

dpkg --list | grep linux-image | grep generic[ATTACH=CONFIG]274656[/ATTACH][ATTACH=CONFIG]274657[/ATTACH]  (one more coming)

---

### Post by deadflowr on 2017-04-19
You can run a reinstall to pull in the proper files for any of the missing kernel images,
try
```
apt-get install --reinstall linux-image-3.13.0-112-generic
```
that should add those missing /boot files.
once you do that, you can then purge the same package with
```
apt-get purge linux-image-3.13.0-112-generic
```
if that works, run the same again changing the version.
And then rinse and repeat until all are fixed and purged.
Then you should be able to fix the -116 version.

---

### Post by w-kym-wittal on 2017-04-19
Unable to send last photo at this time (I do not have enough permissions/beans to add 1 more photo).

---

### Post by darkod on 2017-04-19
Since it reports 4.4.0-72 in there I wonder why would it need 3.13.0-116 at all. The latest kernel and default boot option should be 4.4.0-72. Is it?

You can try what deadflowr suggests, you can also try running update-grub to see if it recreates new .conf file in case there are issues with the current one. I never had to run update-grub from recovery mode but I hope it will work.

You can also try reinstalling grub but it seems to be loading fine up until the grub boot menu because you can use it...

PS. I just re-read your first post, and since you removed files from /boot manually you should definitely try update-grub command. It should detect only 4.4.0-72 and leave only that one in the grub menu. As for all the other kernels that you say won't work, that is normal since there are no files for any kernel except 4.4.0-72 in /boot.

---

### Post by w-kym-wittal on 2017-04-19
Latest update:
1.  Ran update-grub:  Failed with the following error message
/usr/sbin/grub-mkconfig: 250: /usr/sbin/grub-mkconfig: cannot create /boot/grub/grub.config.new: Directory nonexistent
2.  Tried re-installing .112 as per instructions, failed with error messages re: .116 (unable to configure).
3.  Tried re-installing .116, went nowhere.

Grub does NOT detect 4.4.0-72, only .116, .112, .110, .108 and 2 previous ones.

I have stopped here.  Question - do I need to purge .112 now?  If I purge .112 (and the others), what do I end up with to boot?

---

### Post by darkod on 2017-04-19
Hold on... That grub message got me thinking.

You see, you said it is much easier for you taking pictures than posting text output, but it is much harder for us reading the pictures and we can miss things easily. Like I missed that you are missing the grub folder inside /boot. You seem to have deleted lot more than just kernel files. Did you delete the whole grub folder too?

You have to reinstall grub completely, to make sure all files are here. I would purge grub and then install it, recreate standard config and update it:
```
apt-get purge grub-pc grub-common
apt-get install grub-pc (it will install all needed files)
grub-mkconfig
update-grub
grub-install /dev/sda   (not sure if your disk device is /dev/sda or which one, just replace it with the correct one in the command)
```

With any luck that will install grub again and during the install it checks and detects all kernels anyway. So you might solve your problem with this. Whether you will need to install/reinstall any kernels, I don't know at this point.

And be very, VERY careful about deleting things in the future, you can't simply delete what you choose...

---

### Post by w-kym-wittal on 2017-04-20
Initially, I am sure I only deleted files, no folders or directories.  Using other tools (ie Boot Repair Disk) may have.  The best lessons learned are from the mistakes you make yourself.

Reading your instructions, I am a bit confused/concerned regarding which disk to install GRUB on.  I have attached 1 more photo of the disk compliment.  I am sure sda is not the correct one (it is my backup drive), but unclear as to which one is - cciss!c0d0 (1st logical drive) or cciss!c0dop1 (boot partition?).  Any guidance?  Thanks again for all of your help.

[ATTACH=CONFIG]274675[/ATTACH]

---

### Post by darkod on 2017-04-20
You never install grub to partitions. Except some very specific cases, so lets say never...

It should go to the MBR of the first disk in the boot order. In your case that seems to be cciss!c0d0. When you use the name of the disk instead of any partition, it installs on the MBR automatically.

---

### Post by w-kym-wittal on 2017-04-20
Partial success - get the login screen, enter my password, then the screen goes black, then cycles back to the login screen.  Same process for the Guest account (endless loop?).

Suggestions?

---

### Post by darkod on 2017-04-20
Hmmm... that can happen if the home folder is missing... But not only in that case.

Double check /home looks normal... Many things seem to be missing from this server. :)

PS. Did you also reinstall kernels, not only reinstalling grub?

---

### Post by w-kym-wittal on 2017-04-20
Home folder looks normal (I can access the terminal and look around, lots of items there).
The machine states it is using the newer kernel (4.4.0-72).

On the web, this problem has been fixed by renaming .Xauthority and then logging in again.  Fixed because this file is re-created if not there.  I am going to try this.

---

### Post by w-kym-wittal on 2017-04-20
Update - renamed .Xauthority & .ICEauthority, no luck.  I think the permissions for both of these files is correct.

When I enter the wrong password on the login screen, it recognizes that.  Remoted in via Windows, can see the desktop, Icons and look around, so I am guessing a Unity launch issue?  Still looking at solutions on the web.

---

### Post by w-kym-wittal on 2017-04-20
Success!  The new kernel broke the NVidia drivers, installed current versions and can now access account.  Getting failed messages related to older kernels, will deal with that later.  Will leave system running, as is, for a couple of days before rebooting (hopefully no issues then).

Any suggestions for clean up or things I should to make system more stable?

Thank you everyone who has helped, I _NEVER_ would have solved this by myself!

---

### Post by darkod on 2017-04-21
If the new kernel is working (after reinstalling nvidia drivers) I would say there is no need to install older kernels.

To try and clean up things you can use autoremove to remove all unnecessary packages automatically, and also try the install -f in case it still has broken dependencies. I will use sudo this time assuming you are logged into the normal mode, not as root:
```
sudo apt-get autoremove
sudo apt-get install -f
```

If autoremove complains on broken dependencies, try the install -f first then again autoremove.

---

