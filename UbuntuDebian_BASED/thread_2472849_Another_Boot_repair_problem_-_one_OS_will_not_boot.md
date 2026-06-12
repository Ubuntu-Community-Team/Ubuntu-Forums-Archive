---
title: "Another Boot repair problem - one OS will not boot"
date: 2022-03-14
forum: Ubuntu/Debian BASED
---

### Post by miodrag1963 on 2022-03-14
First time using Linux, I don't even understand the answer which resolved the "Boot repair problems" topic from 2020. 

I bought a new SDD, created 6 partitions to try 6 OS's. Windowsfx is on my only primary partition, others are logical. It went fine, a nice, centered boot menu was working well. Soon I learned that Linux means Googling 'How to fix this-and-that'. After a week my Windowsfx was gradually filling all the free disk space, until there was no a single free byte left. This one I could not Google, so I formatted that partition with Gparted, to reinstall the OS. I thought that the option to make a boot flag was meant for what I did - I also created a new 600 MiB partition just for GRUB, to save it from future formats etc. 

Reinstalled Windowsfx, pointing to this new partition for boot, but then the boot menu was gone, only grub rescue prompt appeared. So I used Boot Repair and Grub Customizer. I think that first I used Boot Repair with advanced option to point to this 600 MiB partition. Boot many was back, but it was simple and it would not boot into Windowsfx. Windowsfx screen appears asking for the password and the Windowsfx password worked, only to bring an Elementary log in screen. I used Grub Customizer, to edit some menu lines from sdc3 to sdc1 - nothing, I used it again to delete all Windowsfx and Elementary menu options, hoping that Boot Repair will do the trick. I used recommended option, but it did not help - boot menu remained the same. Menu option to boot into Windowsfx still boots into Elementary, after the Windowsfx  password.

I would appreciate any idea on how to fix this.

Regards,
Miodrag

---

### Post by QIII on 2022-03-14
>  Soon I learned that Linux means Googling 'How to fix this-and-that'. 

Not really.  You may have found that WindowFx has required some research.  But Windows has done that to you at a low level over a long period of time, so you have the human tendency to believe that you didn't have to learn much.

WindowsFx is not representative of all of Linux, not is it representative of Ubuntu, on which it is based.  WindowsFx is an attempt to make Linux look and act like Windows, which means that it is a kludge.

[https://www.youtube.com/watch?v=18cW_yHo3PY&ab_channel=MrDesbocatti](https://www.youtube.com/watch?v=18cW_yHo3PY&ab_channel=MrDesbocatti)

---

### Post by QIII on 2022-03-14
Moved to*** Ubuntu/Debian BASED***.

---

### Post by miodrag1963 on 2022-03-14
That is true, I invested more in Windows. Still, this is my third serious attempt to try Linux over the last 15 years. So far every attempt failed. Imagine a new PC user being offered to try both Windows and Linux. Or imagine using two types of a TV remote controls, on one you just click a button, on the other you have to type "sudo volume up". These two concept cannot even be compared, they are different worlds. I like the idea behind Linux, that is why I keep coming back. But my impression is that Linux is (or was) extremely user-unfriendly and those who spent years using it just cannot see that most of what they learned over the years could be avoided by a more decent concept. Linux reminds me on Unix I had at my work 25 years ago. It seemed like an impressive peace of software, but we always had to call the specialist to tune it. Maybe things have changed, that is why I tried Windowsfx, Elementary and Zorin so far and I yet have to try Ubuntu, Debian and Mint on my other three partitions. Fixing the first three did not leave me any time to look at the other three.

---

### Post by oldfred on 2022-03-14
Please post the link to the Boot-Repair Summary Report as it suggests if you want help.
I do not download unknown .zip files even if they say they are Boot-Repair. That is not normal Boot-Repair.

I have the opposite with Windows.

I used to be a power user of Windows 3.1 thru XP. Converted to Ubuntu and yes it took some work.
But now the one Windows 10 system requires me to do a lot of Googling to try to find an answer.
The most frustrating thing with Windows help is that the menus end up different as versions seem to vary even if all Windows 10. And if I manage to drill down deep enough, I swear it is the old XP screen I knew years ago.

Running a command in Linux works across most gui and versions. Try that with Windows.

---

### Post by QIII on 2022-03-15
> **miodrag1963 said:**
> ...on the other you have to type "sudo volume up" ...

Why would you have to do that?  Pretty much anything you want to do can be done in a desktop environment's graphical tools, which is how one operates Windows.  However, the graphical environments are not the same and expecting them to be is a mistake.

oldfred alluded to something that I will amplify:  Because of the freedom allowed to developers in the world of Linux, there are boxes full of desktop environments, window managers and the like.  Nobody can be expert in all of them.  So in the Linux community help is usually given in the context of terminal commands because those are common across the board (with a scattered few minor differences in dialect).  *That* is why the instructions you find on the web are given in terminal commands.  Things don't *have* to be done that way.  If you learn your DE, WM, GUI, what have you, you can generally do things that way.  But it won't be identical to Windows.

The command line is about power married to finesse, not mindless ease.  "This is the weapon of a Jedi Knight. Not as clumsy or as random as a blaster, but an elegant weapon for a more civilized age."  Windows, by the way, has cmd, which Windows Jedi use.

Linux reminds you of Unix?  It ought to!  I, for one, am glad it reminds me of Unix -- which I was using *45 years ago*, long before I ran into that silly new Windows thing that was useless as anything more than a toy for people who could not use real computers.

---

### Post by miodrag1963 on 2022-03-15
Nice to hear you two having such a nice experience with Linux. On a rare occasions when meeting some Linux users here, I had the impression that they were confident and comfortable  with their choice. Even a shade of some underground-resistance dedication. I know about GUI, would be helpless without it. But I remember that after using GUI to fetch applications, and something did not work well, I discovered that the best way to get software is the hard way, since the GUI way may cause some problems. Then using some ppa thing as recommended all over the Web, only to learn that it does not work properly and the updated info was to use the orthodox way, since that ppa was abandoned, etc. And I learned all that only too late. I would depend heavily on the local Linux community, if there was one.

Regarding the zip file, I did it only because of some limitation in file size here, like 19 Kb or something; that really takes me back in time... So, Linux is also vulnerable to malware...

Here are download links to the same file:

<snip>

4shared says that this is the Forum code:

<snip>

I hope one of them will work.

---

### Post by oldfred on 2022-03-15
It still requires me to download a file.
Boot-Repair automatically uploads the file to a paste.ubuntu link that you post. Then we can just just click on that link to see your info.

---

### Post by QIII on 2022-03-15
> **miodrag1963 said:**
> Nice to hear you two having such a nice experience with Linux. On a rare occasions when meeting some Linux users here, I had the impression that they were confident and comfortable  with their choice. Even a shade of some underground-resistance dedication.

Despite the rumors and urban legend, there is no "underground resistence" unless you run in those hair-shirt-wearing circles.  If it didn't work, I wouldn't use it.

> I know about GUI, would be helpless without it. But I remember that after using GUI to fetch applications, and something did not work well, I discovered that the best way to get software is the hard way, since the GUI way may cause some problems.  

A bit nebulous.  We can't help with that.  The easiest way to get software is using graphical tools and standard repos.  In my opinion, the best graphical tool is Synaptic.  Hunting things up on the web and installing them using the terminal is a great way to encounter a significant emotional event.

> Then using some ppa thing as recommended all over the Web, only to learn that it does not work properly and the updated info was to use the orthodox way, since that ppa was abandoned, etc.

PPAs are "Personal Package Archives" and are the responsibility of the random person who creates them.  They don't represent Linux and it is not wise to use them indiscriminately.  It is also not always wise to follow random instructions found on the web.


> And I learned all that only too late. I would depend heavily on the local Linux community, if there was one.

Well, you've found us.

> So, Linux is also vulnerable to malware...

Who said it wasn't?  Many myths are promulgated by Linux apologists who aren't even honest with themselves.

I am not trying to be difficult, nor do I want to be one of those people who sniff at newcomers.  The problem is that we see people here all the time with the very same misconceptions and unrealistic expectations -- who say Linux is horrible because it doesn't live up to myth.  It's only horrible when approached with misconceptions and unrealistic expectations.  Please don't approach this with an attitude of Linux condemnation.  That's a great way to cause people to move along without offering help.

Please don't place your ire on this community.  We have had nothing at all to do with your frustrations to this point.  We can help from here forward.  oldfred is one of the most knowledgeable of the old timers around here.  He will certainly be happy to help you get sorted out.

Finally, please do not expect people to download random files.  99% of us simply will not.  The Linux community is generally more security conscious than that -- and the Staff frowns on users asking others to do so.

---

### Post by miodrag1963 on 2022-03-15
Nothing but wisdom from you, QIII, I have no problem with what you said. You were right, it is about my expectations, why the world is not better or smarter.

Regarding the Boot Repair, I used it two times, but the last time I did not click the upload option. I wrote down the first URL:

Boot successfully repaired.

Please write on a paper the following URL:
[https://paste.ubuntu.com/p/rKhvgJyDC7/](https://paste.ubuntu.com/p/rKhvgJyDC7/)

So, I know what to do. The above report is not up to date and you may disregard it until I run BR again, I just have nothing else to post here, until I fill my quota of minimum 10 messages for removing some restrictions. I tried the zip file and the download options since I am not sure what would happen if I run the Boot Repair again. In fact it was so challenging experience that I am still trying to find strength and determination to face all that again. I guess that copy/pasting the report here is also not welcome. So, until next time, keep well!

---

### Post by oldfred on 2022-03-15
Having as many installs as you have makes learning a bit more difficult as each has some differences.

You seem to have newer UEFI hardware, but all installs in old BIOS/MBR configuration. 
That can work, its just there are advantages to gpt partitioning and then UEFI installs.
I started converting to gpt in 2010 with XP on a MBR drive & Ubuntu on a gpt drive with my BIOS only system.

Microsoft has required vendors to install in UEFI/gpt mode since 2012.

---

### Post by tea for one on 2022-03-16
An overview of your position:-

First time using Linux
3 disks
7 operating systems
Windows in MBR of sda
Windows in MBR of sdb
Grub in MBR of sdc
All OS installations in older BIOS mode
Extended partitions on sda & sdc
Firmware EFI capable (as mentioned by [COLOR="#0000FF"]oldfred[/COLOR])

Quite an adventurous exploration for a first time user.

Nevertheless, here are my suggestions:-

Back up your Windows personal data.
Back up Linux OS personal data (if any)
Remove disks sdb and sdc
Install Windows 10 on sda in UEFI mode with GPT
Allow Windows updates to finish
Restore your date and verify that everything is OK

To explore multiple Linux systems _without_ installing, use Ventoy
[https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html)

When you have decided your Linux preference:-
Isolate/remove your Windows disk
Only have your target disk accessible
Install your choice onto your SSD in UEFI mode with GPT
The Linux OS (certainly Ubuntu) will automatically be configured with an EFI System Partition

Windows boot manager on one disk and Grub on the other disk.
Boot each OS via the dedicated key to access the device list

---

### Post by miodrag1963 on 2022-03-16
I made a fresh Boot Repair report:

[https://paste.ubuntu.com/p/bsZFm6bZFd/](https://paste.ubuntu.com/p/bsZFm6bZFd/)



> **oldfred said:**
> ... there are advantages to gpt partitioning and then UEFI installs.


When installing from live ISO's, sometimes there was a message in Gparted about these advantages, here is a screenshot:

[[IMG]https://i.ibb.co/TqGb4gj/GPT-on-BIOS.png[/IMG]]("https://ibb.co/vvWQ3jy")


But I did not know how to do it, and I already made six partitions, the only way I knew, so I didn't want to change anything, and at first it all worked well. I guess that if I would start all over, it would be something like this, with GPT 50 GiB partition:


[[IMG]https://i.ibb.co/zVwGnK0/Gparted.png[/IMG]]("https://ibb.co/gZCzjsB")

Btw. among these options:

> Install boot loader on:

Master Boot Record of SPCC Solid State Disk (/dev/sdc)
System partition (/)
Do not install a bootloader

which one should I choose? And then, should I delete this 600 MiB sdc3 partition that I wanted to use for the boot loader?

[[IMG]https://i.ibb.co/KVLh6r1/Gparted2.png[/IMG]]("https://ibb.co/NWmCxy4")



> **tea for one said:**
> Quite an adventurous exploration for a first time user.

True. I wanted to do many things in one try, I did not know which OS to choose, so I decided to evaluate them simultaneously. After I decide, I would remove redundant ones. Btw, is there a simple way to "remove" one of them? Without affecting the boot menu and would merging partition with an active OS with an empty one work?

> **tea for one said:**
> Remove disks sdb and sdc

Excellent idea that crossed my mind, but then I would lose Windows in the boot menu options. I want disk with Windows to be present and recognized by grub.

> **tea for one said:**
> Install Windows 10 on sda in UEFI mode with GPT

Cannot do that right now, it is a project too demanding at this time, although it is another good idea. I had money just for this one SSD meant for Linux only. My PC is old and in the last two months I had two hard drive failures, one is now completely dead and the other is my present Windows sda, which had a MBR problem to be repaired. All that I was ready to do now is to make at least two Windows like OS', and two standard Linuxes, just in case. As a new user, I would eventually mess something up, so I wanted to have a backup options when using one standard Linux and the one which will run my Windows programs. Not sure what would be my final decision. So far, Zorin works great, so I hope it is a keeper, Windowsfx was also great until it started to fill all the empty disk space, I reinstalled it to give it another try, but now canot boot into that new installation, and Elementary was a disappointment, I will lose it, except right now it serves some purpose. Did not have time to evaluate Kbuntu, Debian and Mint. Once the Mint booted when I picked Windowsfx and it looks very crisp, maybe a tough choice here.
 
> **tea for one said:**
> Boot each OS via the dedicated key to access the device list 

I see your points, it is so elegant. But if this means using F11 to enter the boot menu and choose a boot disk other than one set as a priority in BIOS, then it is exactly what I wanted to avoid. I want to have a boot menu with at least 10 seconds count down before auto booting the first on the menu. F11 is too fast for me, I am getting older and it shows. So many times F11 did not work well or at all.

Thanks everyone for the feedback. 

I hope that eventually we will find a solution that would save me from formatting the whole disk as a GPT. I would like to keep this Zorin, because of the effort I already made to make that one work as I want.

---

### Post by oldfred on 2022-03-16
Please do not post large screen shots or photos directly.
You can easily attach them with Forum's Go Advanced menu & the paperclip icon.
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

You always install boot loaders to a device like sda, not a partition like sda1 whether UEFI or BIOS. But with UEFI installs it actually installs files into the ESP - efi system partition. 

I have used gparted to make a new drive gpt. But you can use terminal or gdisk.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
sudo parted /dev/sda mklabel gpt
Note conversion from MBR to gpt normally totally erases drive. 
There are tools to convert, but often best to only convert data only drives as UUIDs, GUIDS all change. If boot drive at minimum total reinstall of grub & edit of fstab is required. 

Having a separate partition for grub2 is not necessary. But last install to a drive will be the default grub in control. BIOS only boots from MBR of a drive. With multiple drives, you can have different boot loaders in MBR of every drive. But then have to use UEFI/BIOS to select drive.

If no time to press UEFI key to get boot menu, you may need to turn UEFI fast boot off. That assumes no system changes & immediately reboots. Often causes issues if system has changed as then changes not recognized. Full cold boot from power down is then recommended, not warm reboot.

You can always add boot entries to grub using os-prober. But new versions of grub are turning off os-prober for a security reason. You can manually turn it back on temporarily or copy or create your own boot stanzas into 40_custom to be included in grub menu.

---

### Post by VMC on 2022-03-17
Quite the read. Enjoyed the "old timers" perspective and zen like responses. 
> True. I wanted to do many things in one try, I did not know which OS to  choose, so I decided to evaluate them simultaneously. After I decide, I  would remove redundant ones. Btw, is there a simple way to "remove" one  of them? Without affecting the boot menu and would merging partition  with an active OS with an empty one work? You could use either a Live distro or a Virtual Machine install to try out first, instead of installing into partitions and having Grub go nuts.

---

### Post by tea for one on 2022-03-17
> **VMC said:**
>  You could use either a Live distro or a Virtual Machine install to try out first, instead of installing into partitions and having Grub go nuts.

Multiple Live Distros with Ventoy as mentioned in post 12.
[https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html)

---

### Post by miodrag1963 on 2022-03-21
I am trying to figure out all that technical stuff.

You told me here that my comp is UEFI capable, but I checked as described [here]("https://itsfoss.com/check-uefi-or-bios/"):

and my system uses legacy BIOS, checked it with the both ways described.

[Here]("https://www.ubuntubuzz.com/2021/09/how-to-install-elementary-os-6-with-dualboot-uefi-and-external-disk-instructions.html") they say that: "For BIOS computer, the storage must be MBR", where storage is either hard disk or USB flash.
"For hard disk, the file system is EXT4."

I want to try Elementary. I guess the same procedure should work for the rest of them. And it did and everything worked nicely.

This Linux adventure is the first time I ever heard of UEFI and GPT, my PC is from around 2010 and the only thing I know is BIOS.

Now, oldfred said:

> **oldfred said:**
> I started converting to gpt in 2010 with XP on a MBR drive & Ubuntu on a gpt drive with my BIOS only system. 

If I am now in the similar situation as oldfred, having Windows on a MBR drive and wanting to install Linux on another drive, can that Linux-only drive be GPT? Should it be?

I also have AOMEI Partition Assistant that can convert disks to MBR/GPT, and the Help file says: "For a system or boot disk, before converting it to GPT disk, we suggest that you make sure whether your motherboard supports EFI/UEFI boot or not, if does not support, please don't convert it to GPT disk".

As far as I can tell, I am stuck with BIOS/MBR.


Solution I was looking for is something like "use this Boot Repair command line to fix everything". Boot menu does not work as it should, now it is a mess.

---

### Post by oldfred on 2022-03-21
Windows in BIOS boot mode requires MBR and in UEFI boot mode requires gpt.
And Microsoft has required vendors to install in UEFI/gpt mode since Windows 8 released in 2012. A few vendors started converting systems to UEFI with Windows 7 before Windows 8 released.
Windows XP does not know anything about gpt. It would not even see a NTFS partition on a gpt drive. But Windows 7 could see data partitions on gpt even if installed as BIOS/MBR.
Apple converted to EFI (predecessor to UEFI) when they converted to Intel based chips long before Microsoft & Linux.

BIOS does not know about gpt or MBR partitioning. It just is smart enough to jump to the MBR or first sector of a drive. A gpt drive has a protective MBR with one partition table entry saying drive is gpt, so old MBR only partition tools would not see drive as blank and automatically repartition it.

With gpt and Linux BIOS boot, you have to have a tiny 1 or 2MB unformatted partition with the bios_grub flag (if using gparted). Actual code is a very long GUID which different partition tools use different flags/codes to assign.

Boot-Repair seemed to think system was UEFI. But you can continue to use  BIOS/MBR.
But if Linux only drive some advantage to gpt.

With my BIOS only system I started converting drives to gpt with a bios_grub partition. Then in 2011 started adding both bios_grub partition and ESP - efi system partition as thought I might eventually move drive to a newer UEFI system. Then only reinstall of grub required rather than major repartitioning & reinstall of everything. Only difference with Linux is version of grub or grub-pc for BIOS and grub-efi-amd64 for UEFI. A few settings also are changed by the reinstall of grub.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by tea for one on 2022-03-21
> **miodrag1963 said:**
> You told me here that my comp is UEFI capable, but I checked as described [here]("https://itsfoss.com/check-uefi-or-bios/"):
and my system uses legacy BIOS, checked it with the both ways described.

[COLOR="#0000FF"]Windows System Summary > BIOS Mode > Legacy[/COLOR]
This information only describes the mode of OS installation.
It does not indicate if the motherboard/firmware is [COLOR="#0000FF"]UEFI capable[/COLOR].
Do you have the original motherboard manual or similar web info?
> **miodrag1963 said:**
> Solution I was looking for is something like "use this Boot Repair command line to fix everything"
A utility to fix everything - that would be wonderful but probably beyond the ingenuity of mere mortals.

---

### Post by miodrag1963 on 2022-03-21
> **tea for one said:**
> Do you have the original motherboard manual or similar web info?

I searched this manual: [https://download.msi.com/archive/mnu_exe/M7623v1.0.zip](https://download.msi.com/archive/mnu_exe/M7623v1.0.zip) for 'efi' and 'uefi' - no hits.
My motherboard is MSI 880GM-E41 series MS-7623 (v2.x) Mainboard.

---

### Post by oldfred on 2022-03-21
It looks like a Windows 7 era system which was mostly BIOS.
But vendors still call UEFI as "BIOS" even though it has been UEFI since 2012.

---

