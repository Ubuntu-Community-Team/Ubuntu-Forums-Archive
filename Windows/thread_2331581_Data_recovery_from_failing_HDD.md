---
title: "Data recovery from failing HDD"
date: 2016-07-23
forum: Windows
---

### Post by murna on 2016-07-23
[SIZE=2][FONT=arial]Greetings,  I am using a 4 year old asus notebook with preinstalled win 7 home premium x64. Since a recent windows update I was unable to boot to win (I know those are ubuntu forums and I will get to that in a second). I am seriously considering buying a new SSD since this one is probably already failing and even if its not is just a matter of time because as I said I have had the notebook for about 4 years now. So the priority for me now is to somehow get my files out of this one and then do a clean install of win7. 

A friend recommended bootable ubuntu via USB to acces my data and copy them to a external drive. He also told me to run these two commands in the terminal: 

**df -h** and **lsblk **(here is a pic from the results [http://i.imgur.com/tkBtyHC.jpg](http://i.imgur.com/tkBtyHC.jpg)) 

I should note that my friend also advised me to use a software called partition wizzard to look how the partitions looked like at the moment so I tried that aswell. When I booted it from the USB it looked like this [http://imgur.com/yElDTXy](http://imgur.com/yElDTXy). There is a option panel on the left with a option to ,,explore,, a partition so I did that and found out that all my files were in the 149 GB OS partition which represents the /dev/sda2 partition in the first pic from ubuntu terminal.

So I went back and booted into ubuntu to copy the files from the OS partition into my external drive but I was not able to acces the OS partition. It gave me this error message [http://i.imgur.com/QGq26sX.jpg](http://i.imgur.com/QGq26sX.jpg). When I tried to google the error message I found a possible solution to that particular problem which was to paste this into the terminal: **sudo ntfsfix /dev/sda2** (can this be reverted?)

So I did that, heres the pic [http://i.imgur.com/S4ZpSgm.jpg](http://i.imgur.com/S4ZpSgm.jpg). The thing is that when I went back to check if I could finally acces the OS partition, now it wasnt there anymore, here is a pic again [http://i.imgur.com/YyGM65n.jpg](http://i.imgur.com/YyGM65n.jpg).

I wanted to check in the partition wizzard if perhaps something changed there aswell and it did [http://i.imgur.com/PWNWtcZ.jpg](http://i.imgur.com/PWNWtcZ.jpg). The OS partition is now renamed to NTFS but I dont see my files there anymore as you can see on the picture [http://i.imgur.com/uX9JYA8.jpg](http://i.imgur.com/uX9JYA8.jpg). I dont know what to think of it since it still says theres 149 GB of files there.

I am new to ubuntu and generaly not that tech savy so I thought I would ask you guys before I do any more harm since really dont know what to do anymore.[/FONT][/SIZE]

---

### Post by oldfred on 2016-07-23
Moved to Windows sub-form since really Windows issues.

I do not know Windows recovery well.

But one of your screen shots shows NTFS partition 100% full. Windows NTFS need 30% free to work well, and at 10% free you have little room to run defrag and it then can take forever. At 100% you may have lost data, and left system partially updated, or broken.

Did you backup the sda5 data partition? I would do that first.

Many that use Windows as well as Ubuntu suggest that Windows tools work best, only a few are free. You can use Linux tools and in many cases will work.
But if Windows operating system is corrupted, then you may not be able to recover a working system.

It may still be a good idea to back up system. But better to have backed up before issues. A reason to backup now, might be if attempted repairs make it worse, you have a way to restore to where you are now and can try difference repair choices.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

       
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

In Linux two recovery tools are testdisk and part of testdisk photorec.
Test disk can restore partitions, but has a deeper search to look for files. If file structure ok, it fiinds full file names.
And photorec is just a file scan tool. It scans drive for anything that looks like a file. It will recover deleted files, but not full filename, just extension.
       
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
      [/URL]
 [URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step
[/URL]
 [http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) 

      
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 
    [URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"]
[/URL] 

    [URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by murna on 2016-07-23
> **oldfred said:**
> Moved to Windows sub-form since really Windows issues. I do not know Windows recovery well.

I am not realy doing anything in windows currently since I cant even boot into windows, thats why I am booting to ubuntu and majority of questions I had where dealing with ubuntu.

> **oldfred said:**
> But one of your screen shots shows NTFS partition 100% full. Windows NTFS need 30% free to work well, and at 10% free you have little room to run defrag and it then can take forever. At 100% you may have lost data, and left system partially updated, or broken.

Well all of my files and folders are on the NTFS partition and I cant acces it from anywhere so there is no way for me atm to make room or move files etc..

> **oldfred said:**
> Did you backup the sda5 data partition? I would do that first.

There doesnt seems to be anything on that partition, only empty folders

> **oldfred said:**
> Many that use Windows as well as Ubuntu suggest that Windows tools work best, only a few are free. You can use Linux tools and in many cases will work.
But if Windows operating system is corrupted, then you may not be able to recover a working system.
I am not trying to repair, my goal is to recover my files and data and then do a clean reinstall

> **oldfred said:**
> It may still be a good idea to back up system. But better to have backed up before issues. A reason to backup now, might be if attempted repairs make it worse, you have a way to restore to where you are now and can try difference repair choices.

As I said before that is what Iam trying to do, back up my files and do a clean reinstall on a new SSD, but iam currently unabble to backup my files since I cannot acces the partition where they are stored which is the OS(NTSF)/sda2 partition

---

### Post by oldfred on 2016-07-23
When NTFS is hibernated or corrupted the Linux NTFS driver will not mount it to prevent further corruption that chkdsk then might not be able to fix.
But you may be able to force mount in read only (ro) mode to copy data.

       

 But better to run chkdsk from a Windows repair CD first, only use this if you have to copy data.

 sudo mount -o ro /dev/sda2 /mnt 
(/mnt is an existing default mount point, but you have to drill down from computer, / (root), /mnt to find if it mounted.

sudo mkdir /media/windows
sudo mount ntfs-3g -o force,rw /dev/<device-name> /media/windows 
Or
sudo mount ntfs-3g -o force,rw /dev/sda2 /media/windows 
(this is using a mount you created and then is in the /media folder, it may then show in Naulitus as well).

---

### Post by murna on 2016-07-23
I am going to reply a bit later today since I want to dig through the links you have posted first.

---

### Post by murna on 2016-07-24
[SIZE=2]Ok so I tried to make an image of the drive with ddrescue. It took almost 8 hours but I have the image now [http://i.imgur.com/j81U8Fg.jpg](http://i.imgur.com/j81U8Fg.jpg). 

I then followed this guide [https://www.technibble.com/guide-using-ddrescue-recover-data/](https://www.technibble.com/guide-using-ddrescue-recover-data/), you can skip under point 3a where it says ,,Working with image files containing multiple partitions,,. 

I followed the steps there, gotten the offset as they said and then tried this mount command **[COLOR=#222222]sudo mount -t ntfs-3g -o force,ro,offset=23071910400 recovery.img /mountpoint [/COLOR]** after that I got this error message [COLOR=#222222][FONT=Verdana][http://i.imgur.com/pUuv8yP.jpg](http://i.imgur.com/pUuv8yP.jpg). And now I am stuck again.[/FONT][/COLOR][/SIZE]

---

### Post by oldfred on 2016-07-24
Never tried to mount an image. Not sure if the NTFS driver supports that directly.
But it looks like the hibernation is still the issue.

Some more info, as you have backup you could try the remove hiberfile option?
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by murna on 2016-07-24
I have actually disabled hibernation on my notebook about a year ago since it was eating up alot of disk space or something like that so I was leaving it either on most of the time or shutting it off occasionally but it never went into hibernate since then.

---

### Post by oldfred on 2016-07-24
fast start up in Windows 8 or later is hibernation.

But then errors may be just because NTFS is corrupted. And back to running chkdsk from Windows.
Some third party Windows repair tools will run chkdsk, but better to have a Windows repair flash drive.

---

### Post by murna on 2016-07-24
Well I was using win 7 so I dont know about that and yes, Ive run chkdsk couple of times almost a week ago (I am dealing with this issue for about 2 weeks now) but it didnt do anything. Here are couple of pics:

[http://imgur.com/xPGcPDT](http://imgur.com/xPGcPDT)
[http://imgur.com/XkAcKpA](http://imgur.com/XkAcKpA)
[http://imgur.com/PJ6Kxe5](http://imgur.com/PJ6Kxe5)

---

### Post by oldfred on 2016-07-24
Was not the original issue that you were at 100%, so even chkdsk does not have room to do anything.

You either need to delete some data, not sure how, if you cannot get to partition.
Or see if any of the third party Windows partitions tools will let you expand it, so you have some working room.

---

### Post by murna on 2016-07-25
What I realy want to know is why the partition with my files suddenly disappeared after I typed sudo ntfsfix /dev/sda2 in the terminal. I submitted the question on askubuntu aswell and thanks to the pictures it is pretty well demonstrated there what I mean by that. [http://askubuntu.com/questions/802122/can-sudo-ntfsfix-dev-sda2-be-somehow-reverted](http://askubuntu.com/questions/802122/can-sudo-ntfsfix-dev-sda2-be-somehow-reverted)

---

### Post by oldfred on 2016-07-25
The Linux NTFS driver will not mount (not see) NTFS partitions that need chkdsk.
The ntfsfix adds the chkdsk flag so that next time you boot Windows it will run chkdsk. Linux tools cannot do chkdsk.
And you have to have space in NTFS partition for chkdsk to run.

---

### Post by murna on 2016-07-25
oh I see, now I atleast know what was going on

---

