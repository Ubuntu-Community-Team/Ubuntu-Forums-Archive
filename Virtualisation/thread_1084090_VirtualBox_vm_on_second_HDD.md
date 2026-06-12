---
title: "VirtualBox vm on second HDD?"
date: 2009-03-01
forum: Virtualisation
---

### Post by dunski on 2009-03-01
ok my level of experience is pretty low in Linux so probably best to assume I know nothing! 

The background is I've installed VirtualBox and the reason is that I temporarily need to run WinXP. I don't want to dual boot and looking at the Wine db there are issues when running the software I need to use. It's a legacy program I need to export some files and data from, once I have retrieved the files I can ditch WinXP again and go back to having a spare drive. (This process will take many hours so I can't ask someone who has a WinXP machine to do it for me)

I've got x64 Ubuntu Intrepid installed on a primary HDD and have two other internal drives. One for shared data and an empty drive which is currently formatted FAT32. 

I've installed VirtualBox (and added root and my main user to the group) and would like to set up a virtual machine on my empty drive (formatting to whatever is required). I've read that using the same disk for two OS's can slow things down, plus the primary drive is only 20gb so just want to keep it as clean as possible.

My problem is that I can't see a way of doing this. When you work through the set up new vm The only drive I can see is my primary and neither of the two other drives. In a very long winded way, what I'm asking is; Am I missing something blatantly obvious? and Is this a hand slapping on forehead moment where I've just been thick?! I've logged in as root and that has the same problem (I thought it might be my hdd permissions were not set up correctly). I just can't seem to find the two drives in VirtualBox new vm setup. (they appear in places ok)

The only workaround I can think of is if it were possible to set up the vm on the primary then move it somehow to the empty drive?

I've read through what seems to be an epic number of fora and help guides but haven't found anything which seems relevant. Help at this point would be very gratefully received!

cheers, 
dunski

---

### Post by bodhi.zazen on 2009-03-01
I assume the drive you are wanting to use is otherwise blank.

So, format it to ext3. Then mount it at say /media/vbox

```
sudo mkdir /media/vbox

sudo mount /dev/sdxy /media/vbox

sudo chown user.user /media/vobx
```

Now start virtualbox and make a new hard drive for windows, save it in /media/vbox.

You will need to change "user" to your log in name and "/dev/sdxy" to the correct hard drive / partition.

If you want to add the mount at boot, you will need to edit fstab :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by dunski on 2009-03-03
thanks for the quick reply on that one!

Fortunately I've found a larger hdd which I've now used for my primary drive. So I've just finished the Ubuntu reinstall and will keep it simple by having the VirtualBox and XP vm on the primary. I think for the purposes I need it for speed won't be an issue, I'll just set up an automated file conversion and it can chug away for as long as it takes.

thanks again,

---

### Post by Dedoimedo on 2009-03-04
Hello,

Placing the virtual machines on other drives is as simple as browsing through the file explorer to the desired destination.

Maybe this will interest you:
[http://www.dedoimedo.com/computers/virtualization-tips.html](http://www.dedoimedo.com/computers/virtualization-tips.html)

Dedoimedo

---

