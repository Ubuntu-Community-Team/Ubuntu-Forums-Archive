---
title: "How to re-install Windows?"
date: 2015-04-20
forum: Windows
---

### Post by kat5 on 2015-04-20
I will admit it, I feel old. My daughter convinced me to try Ubuntu... I don't like it. I want to switch my laptop back to running Windows 7, I understand Windows and I'm just not up to learning a whole different OS. My daughter has gone out of town for the next several months and I can't get her to help me switch my system back. I have my Windows 7 install disk, but I can't seem to get my system to switch back. Could someone please tell me how I can switch back to the OS that I understand? I have a Lenovo Thinkpad that was running windows 7. When I put the disk in it gives me the option to boot from the CD and then it starts loading the Windows info...  It gets to the section where it asks where I want to install Windows, and I have two disk partition options. (Disk 0 Partition 1, 458.0 GB total size, 0.0 MB free space, System), and (Disk 0 Partition 2, 7.7 GB, 0.0 MB total size, 0.0 MB free space, Logical). Down at the bottom of the install screen it says that Windows can not be installed to Disk 0 Partition 1. I can't seem to get past this point, could someone please help me to reformat or reinstal Windows 7 on my laptop? Thanks much,

(A very frustrated) Kat

---

### Post by yancek on 2015-04-20
You should have a Repair option on the windows installation media when you boot it.  Take a look at the link below which gives an explanation and has some images indicating what you should see.  You probably need to overwrite the code in the master boot record which is explained at this link.  You indicate you see a message that windows cannot be installed to this partition.  Is there any explanation as to why.  Seems pretty unusual that you can't even begin the installation but I've never installed windows 7 so I don't know what to expect.  

Since you are trying to install windows you might be better off at a windows forum or at the support.microsoft.com site since they should have more knowledge of their operating system.  The second link is to a windows forum but I have no idea if that will work.

[http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on](http://askubuntu.com/questions/133533/how-to-remove-ubuntu-and-put-windows-back-on)

[http://www.sevenforums.com/installation-setup/203961-how-do-i-uninstall-linux-install-windows-7-a.html](http://www.sevenforums.com/installation-setup/203961-how-do-i-uninstall-linux-install-windows-7-a.html)

---

### Post by kat5 on 2015-04-20
Thank you yancek. I decided to try this forum first just in case my hard drive needed to be reformatted, I don't know how to reformat using ubuntu so figured I would try here. Then try Microsoft if all else failed.

---

### Post by westie457 on 2015-04-20
When running the Windows DVD do you get a screen that looks like this?

---

### Post by kat5 on 2015-04-20
Yes, exactly like that but with only two partitions as listed. The area that gives the reformat option is grayed out though, so it won't let me re format.

---

### Post by yancek on 2015-04-20
Are you using this computer now with Ubuntu to post?  Or do you have another computer to use.  If you have an Ubuntu Live CD or any Linux Live CD, you could boot it and use GParted to format your partition(s) as ntfs for windows.  Usually, you would be better off using windows to format a windows filesystem.

When you boot your windows installation media, do you see the Repair your Computer option shown in the image at the askubuntu link I posted?  If you select that option and enter the commands indicated, it should put windows code in the master boot record.  That might be the problem as windows sees unknown boot code and...?  I've seen countless posts with similar problems when people try to install windows with a drive having Linux boot code.  Hard to believe something that simple could be the problem but it's simple enough to try.

---

### Post by kat5 on 2015-04-20
[FONT=Verdana]No, I'm using a shared Windows PC to post here. I don't have an ubuntu Disk at all. Truthfully, I'm not even sure how my daughter installed it. Yes, I see the Repair your Computer option. I have been trying to follow the instructions in one of your links, but it seems to stall out on the command prompt Clean All. It just sits there when I get to that stage and doesn't seem to be doing anything.[/FONT]

---

### Post by oldfred on 2015-04-20
Moved to Windows sub-forum. Which is more for dual booting issues.

Linux uses ext4 format & swap and that seems to be the two partitions you have.
But Windows cannot correctly see the Linux partitions.
Windows wants a blank drive or a NTFS formated primary partition with the boot flag. It will install in one partition, but normally creates a small 100MB boot and the main NTFS partition, if drive is blank.

So you need to erase drive with Windows, not sure if you can force it to just reformat entire drive, or use third party tools. 
With Linux we would suggest using gparted which can be a separate liveCD or is on the Ubuntu install disk.

Windows forums may have the details to reformat or suggest third party partition tools.
       [http://www.eightforums.com/](http://www.eightforums.com/)
[http://www.sevenforums.com/](http://www.sevenforums.com/)
Install Windows 7
[http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html](http://www.sevenforums.com/tutorials/52291-partition-hard-drive-windows-7-install.html)

Others have suggested these:

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by kat5 on 2015-04-20
Sadly I don't understand most of what you said. I don't know anything about Linux and don't have the Ubuntu install disk. Thank you for all of the links and help though. I will keep trying or I will just have to wait for my daughter to be available to help me out. I'd really rather not wait that long to be able to use my laptop, but if that's what it takes, that's what it takes.

---

### Post by westie457 on 2015-04-21
> **kat5 said:**
> Yes, exactly like that but with only two partitions as listed. The area that gives the reformat option is grayed out though, so it won't let me re format.
Select a partition and click on Delete. Do this for all partitions listed.
When there is no partitions listed click on the 'Next' button. The Windows installer should then inform you that 2 partitions will be created and formatted as NTFS. Click yes (or agree/continue).
Windows installation should then proceed.

In the future if you decide to come back to Ubuntu ask your daughter to set up a dual-boot system for you or ask on these forums for guidance.
We will try to keep advice as simple as possible.

---

### Post by yancek on 2015-04-21
If you don't have the Ubuntu installation disk, you can download GParted which is a partition manager to accomplish what you want.  I'm not clear as to whether you can still boot into Ubuntu on your laptop.  In any case if you can boot it or boot the other computer you are using and go to the link below.  Scroll down the page until you see this:

 Download gparted-live-0.22.0-1-i586.iso

Click on it and you should get a new window with several options.  Click on Save.  If you are using Ubuntu, you can open a terminal and type brasero and it should open.  Or click on the Dash icon, the circular Ubuntu logo in the extreme upper left of the Desktop.  You should then see the brasero icon, click it and the software probram will open and you should see an option to "burn image", click on it and then navigate to the /home/user/Downloads directory and select the gparted iso file you downloaded and burn it to a CD.

If you get that done, leave the CD in the drive and reboot the computer and watch the bottom of the screen immediately after booting for a message saying to hit ?? key to enter setup.  ?? will be replaced by F2, F10 or some other key.  Once you get into the BIOS, look for a boot option and change the boot priority to have the CD drive boot first and boot GParted.  The link below is a tutorial explaining how to do this.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

If you don't understand the above, wait for your daughter or someone else familiar with the process.

---

