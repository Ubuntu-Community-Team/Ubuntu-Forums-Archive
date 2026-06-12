---
title: "Major Problem!!!"
date: 2007-01-26
forum: Ubuntu Christian Edition
---

### Post by quickuser on 2007-01-26
All of a sudden Vista is not booting up past the logo screen (with the green animated progress bar). Actually, it goes into blank screen mode after 1-2 minutes and nothing happens ever after that.

Worst yet, even the Vista Ultimate CD (which I used originally to install, twice before) is NOT loading past the same screen (logo)! it first goes through the 'loading windows files...' then boots to the logo screen and nothing happens for several minutes!

I also tried booting in safe mode, it goes through the scrolling of loading files and always gets stuck on crcdisk.sys file

Originally before all this I simply booted (not installed) from Ubuntu CD to test it out. I attempted to install and was stuck on step 5/6 where it asks for partition. I made it 40GB (120GB total drive) and nothing was happening, I successfully canceled and then all broke loose after that.

What should I do? I'm really stuck, can't boot of Vista CD nor drive. I have critical data on my hard drive.

Vista RTM Ultimate
SONY VGN-FE-770G

dxdiag info

------------------
System Information
------------------
Operating System: Windows Vista™ Ultimate (6.0, Build 6000) (6000.vista_rtm.061101-2205)
System Manufacturer: Sony Corporation
System Model: VGN-FE770G
BIOS: Phoenix NoteBIOS 4.0 Release 6.1
Processor: Intel® Core™2 CPU T5600 @ 1.83GHz (2 CPUs), ~1.8GHz
Memory: 2038MB RAM
Page File: 1181MB used, 3114MB available
Windows Dir: C:\Windows
DirectX Version: DirectX 10
DX Setup Parameters: Not found
DxDiag Version: 6.00.6000.16386 32bit Unicode

---

### Post by geek_Man on 2007-01-26
How big was your old NTFS partition (that is if you had Windows)?

---

### Post by jhaitas on 2007-01-26
sounds like a blessing to me

---

### Post by jhaitas on 2007-01-26
my recommendation... 

remove vista and never look back

---

### Post by mhancoc7 on 2007-01-26
> **jhaitas said:**
> my recommendation... 

remove vista and never look back

While I do agree, this is really not helpful to the op's situation. Let's try to help him if we can.

Jereme

---

### Post by jhaitas on 2007-01-26
what does microsoft's technical support have to say on the issue?

 or is this an "unauthorized" copy of vista

---

### Post by jhaitas on 2007-01-26
if you have critical data on your harddrive you can mount your windows partition and back-up the aforementioned critical data...

---

### Post by foob on 2007-01-26
If you tried to install after Vista was already on your machine and you used the resize tool when you tried to partition, chances are that that is where the problem is. Microsoft Windows has always done a poor job of defragmentation and cleanup and chances are something got botched during the resize or attempt to do so because your files, drivers, etcetera were scattered throughout the drive. My advice would be to start over and not use Vista period or if you insist on using both, establish your partitions from the start and with a cleaned and empty hard drive. Usually, the resize works best only if you are working with two or three different distros of Linux. Resizing with Windows and Linux together seems to cause problems as I've seen this before...in fact several times.

---

### Post by jhaitas on 2007-01-26
i agree with foob... i always had nightmares with partitions with with windows starting from 98 on to XP... you must realize ms believes they are the only game in town... as such, they do not take care to make sure their software behaves well with others... i seriously doubt that ubuntu or any linux distro would be responsible for this...

unfortunately for you - since vista has not officially been released (nevermind the fact that ms has attrocious tech support) - microsoft is not likely to be too helpful to you in your plight... this is why i now avoid microsoft software like the plague (this coming from a former ms fanboy)... the only microsoft software i run these days is the firmware on my XBOX360

---

### Post by geek_Man on 2007-01-26
And also, if what was mentioned before is the case, your critical data might be lost. Sorry.

---

### Post by jhaitas on 2007-01-26
a risk you take when using badly behaved - unsupported software

---

### Post by geek_Man on 2007-01-26
Gee, I wonder who doesn't like Microsoft? Hmmmmm...

---

### Post by jhaitas on 2007-01-26
hmmmm

---

### Post by quickuser on 2007-01-26
Please see this and help
[http://www.ubuntuforums.org/showthread.php?t=346780](http://www.ubuntuforums.org/showthread.php?t=346780)

I need to copy stuff over to my usb drive but it won't give me access

This is a laptop so I cannot use the drive elsewhere

---

### Post by Immolatus on 2007-01-26
:lolflag: 
windows......My suggestion is this. run out and buy yourself an external hdd enclosure from some chain electronics store that will support a 2.5" drive and try to mount it by usb on another machine and extract from there. then reformat that sucker but only reformat 50% ntfs and install vista first on that partition and than instal linux on the empty space when the installer gives the option. This way you can't screw up the partitioning if you use the auto function. BTW...vistas RC has been noted and documented to be very cranky with grub installed on the same drive.

good luck.

---

### Post by quickuser on 2007-01-26
I never said I was using Vista RC.  I said Vista, however its Ultimate RTM from MSDN

I restarted again in live boot mode of course and now when I go to computer I see the 104.8GB volume drive. (wasn't there before), this is the Windows partition

When I try to open it I get an error

unable to mount the selected volume
error: device /dev/sda2 is not removable
error: could not execute pmount

So I ran sudo mount /dev/sda2 /media/windows -t ntfs -r -o uid=999,gid=999,umask=444
and now I get "you do not have the permissions necessary to view the contents of 'windows'

What should I do?

---

### Post by mysticrider92 on 2007-01-26
Try "sudo nautilus /media/windows". That should open a nautilus window with root privleges so you can copy things off. Also, what are you using to rescue it? A Ubuntu live cd won't easily give you access to your drives. The Knoppix live cd is a better choice. Also, I don't know what all of those arguments in the mount command you used are, but I don't know if all of them are necessary. I usually just use mount /dev/sda2 /mnt/sda, but I have never tried it with an NTFS partition.

---

### Post by chris308 on 2007-02-13
Not sure if this is still a pending problem, but I would suggest you try a bootable CD like UBCD for windows, browse the hard drive to recover your data to a flash drive.  Once done you can reinstall Vista/XP.

I work as a network manager at a k-12 school and I do this often before reinstalling a borked system.

Hope this helps.

Chris

---

