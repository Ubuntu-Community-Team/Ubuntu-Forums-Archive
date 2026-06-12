---
title: "Problem with Virtualbox and Genymotion after updating my Ubuntu last night."
date: 2018-03-05
forum: Virtualisation
---

### Post by CCgirl6690 on 2018-03-05
Hello. 
im on ubuntu 14.04 and installed the updates last night and slept. now when i start  Genymotion i get the error that virtualbox is not installed. I used to get this error before but i always solved it with ..
```
sudo /etc/init.d/vboxdrv setup
```
But this time things go different when i do that and i get the error...
```
vboxdrv.sh: failed: modprobe vboxdrv failed. Please use 'dmesg' to find out why
```
. i did search on google. i found 2 posts last one is this one... [https://ubuntuforums.org/showthread.php?t=2350741](https://ubuntuforums.org/showthread.php?t=2350741).  But its closed and i cant reply to the thread. i have yet to try the suggestion it has in the post. Im afraid i lose my VM's if i do that?
Can someone please help me? I really need to fix this. My life depends on it. Thank you so much everyone for reading.
------EDIT :  i was able to temporary fix the issue by choosing  "advanced options for ubuntu in boot menu upon laptop reboot and choosing one version older.. this one " Ubuntu, with linux 4.4.0-112-generic "     The latest was 116 after i updated..   But on 116 i wont be able to run Virtual box anymore. im not very tech savey. thank you so much

---

### Post by cruzer001 on 2018-03-05
If it were me, I would upgrade to vBox 5.2, but my life wouldn't depend on it since I have backup.

---

### Post by CCgirl6690 on 2018-03-06
Thanks for the reply but i can't update it. it gives error in software center.. also how can i make backups?
Thanx.
Btw its sad to see this forum is dead. i remember back in years here was full of activity, but now after 24 hours. only 1 person came here. it's like dying in a dark valley yelling for help and only a wolf passing by.

---

### Post by wildmanne39 on 2018-03-06
Hello CCgirl6690,
>  now after 24 hours. only 1 person came here. it's like dying in a dark valley yelling for help and only a wolf passing by. 
Actually 8 people have looked at this thread including myself, the view count is broken so you can not go by what it shows.

Glad you are here and I hope your issue gets resolved!

---

### Post by kerry_s on 2018-03-06
it's most likely that not many people are left on 14.04, they've moved on to more updated versions.
i'm old i'm not going to remember that far back to be able to help.

i use gnome boxes for vm now a days, it's a much simpler system.

---

### Post by CCgirl6690 on 2018-03-06
Thanks Kerry,  i would want to update to a newer ubuntu but im afraid i lose my files and VM's and otherthings. it's too risky for me

---

### Post by monkeybrain20122 on 2018-03-06
You can make a snapshot of the VM (Machine > Clone: the sheep icon) and save it somewhere, then go ahead to update your OS (I advise against 'upgrade', backup your stuffs and do a clean install is a lot faster and safer) Afterwards install VBox and just restore your backup snapshot. I have done it many times.

---

### Post by kerry_s on 2018-03-06
if it's important always backup, have a copy somewhere else.
i use a simple sdcard for backup. i have a couple of them. i keep 1 just sitting in my laptop sd slot for quick saves.

---

### Post by wildmanne39 on 2018-03-06
This kernel has a bug that caused your issue here is a possible solution.

[https://askubuntu.com/questions/1008681/virtualbox-not-starting-after-kernel-upgrade](https://askubuntu.com/questions/1008681/virtualbox-not-starting-after-kernel-upgrade)

---

### Post by CCgirl6690 on 2018-03-06
> **wildmanne39 said:**
> This kernel has a bug that caused your issue here is a possible solution.

[https://askubuntu.com/questions/1008681/virtualbox-not-starting-after-kernel-upgrade](https://askubuntu.com/questions/1008681/virtualbox-not-starting-after-kernel-upgrade)

thank you so much. it suggest i need to reinstall VB as well.  it's way to risky for me. maybe i should wait for next karnel update?

---

### Post by cruzer001 on 2018-03-06
Ok, the wolf is back :P

What are you going to do if one day nothing works?  No backup yet you say your life depends on it?  Its too risky to try to repair or upgrade? Can't risk it?  

Nothing last forever, you need backup!  

The newer kernels have been a issue lately with vBox.  An upgrade to 5.2 is the most common fix.  Waiting for magic to happen with the next kernel upgrade is not.  Sure there is a risk, there's always a risk.  Every time you update your system, you risk it all.

I recommend backing up your Home directory (thats where vBox keeps its guest folders) and also create a list of installed packages to keep there too.  That's basically what I do.  Or clone the whole install.  Lots of options there.

And then you can upgrade and not worry too much :)

---

### Post by CCgirl6690 on 2018-03-08
> **cruzer001 said:**
> Ok, the wolf is back :P

What are you going to do if one day nothing works?  No backup yet you say your life depends on it?  Its too risky to try to repair or upgrade? Can't risk it?  

Nothing last forever, you need backup!  

The newer kernels have been a issue lately with vBox.  An upgrade to 5.2 is the most common fix.  Waiting for magic to happen with the next kernel upgrade is not.  Sure there is a risk, there's always a risk.  Every time you update your system, you risk it all.

I recommend backing up your Home directory (thats where vBox keeps its guest folders) and also create a list of installed packages to keep there too.  That's basically what I do.  Or clone the whole install.  Lots of options there.

And then you can upgrade and not worry too much :)

thank you cruser. by backup do you mean i just copy the home folder to another drive?  what about setting? I have genymotion and vms  with setting, how can i back up the setting? how about hidden files? Are there any program that can back up correctly?  the only reason im not doign it is because i dont have  extra hard disk to back up my files./ thanks

---

### Post by cruzer001 on 2018-03-08
> by backup do you mean i just copy the home folder to another drive? what about setting?
Yes, that's where most (not all) of your settings are kept (including your VMs).  For a detailed answer:
[https://ubuntuforums.org/showthread.php?t=2383685&p=13734862#post13734862](https://ubuntuforums.org/showthread.php?t=2383685&p=13734862#post13734862)
> I have genymotion and vms with setting, how can i back up the setting?
Like I said, your VMs are in your home directory.  I do not know where Genymotion keeps its settings, but if installed in the VM, then your covered.
> how about hidden files? 
Their in Home.
> Are there any program that can back up correctly?
Lots to choose from.  Here's some:
[https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities](https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities)
> the only reason im not doign it is because i dont have extra hard disk to back up my files
What about using a flash (thumb) drive?  How big is your home directory?
```
du -hc ~/
```
Let get pass this before we talk again about upgrading vBox :)

---

