---
title: "Ubuntu on a dual drive system"
date: 2011-12-24
forum: The Cafe
---

### Post by u-noob-tu on 2011-12-24
My dell studio laptop is getting kinda old, and im looking for ways to increase performance without buying a new computer. recently i heard about dual drive systems, and ive also heard about how insanely fast SSDs can be. now my laptop is pretty big (17"), so it has a dedicated slot for a second drive. i just have a few questions about how dual drives work.

1) what would be the recommended size SSD for Ubuntu? i imagine it wont need a big one, but id like to have a decent amount of space for programs.

2) Is installing ubuntu on an SSD identical, or at least similar, to installing on an HDD? If its not similar, how should i configure it?

3) ive heard some stuff about drive "caddies". What exactly are they? is it like a mount for the drive to fit in the laptop?

any tips and advice will be much appreciated :)

---

### Post by Paqman on 2011-12-24
> **u-noob-tu said:**
> 
1) what would be the recommended size SSD for Ubuntu? i imagine it wont need a big one, but id like to have a decent amount of space for programs.


If you've got two drives the SSD doesn't have to be big. You'd mount your /home folder, swap, and all the data on the spinning drive, and you'd leave only the / on the SSD. You could easily get away with 10GB, 20GB would be better. I have a netbook with a 30GB SSD and it runs absolutely fine.

> 2) Is installing ubuntu on an SSD identical, or at least similar, to installing on an HDD? If its not similar, how should i configure it?

You don't have to do anything special, but there are some tweaks that will improve it. Adding the option "discard" to your /etc/fstab entry for that drive will make it do some maintenance in the background. If you partition the drive you may also want to leave 1MB between partitions to ensure it's aligned correctly. Some people also mess about with scheduling and reducing writes, but IMO that's not really necessary. Having said that I do mount /tmp to a ramdisk, but that's as much to improve performance as it is to reduce writes.

> 
3) ive heard some stuff about drive "caddies". What exactly are they? is it like a mount for the drive to fit in the laptop?


A caddy is an enclosure for an internal drive so it basically becomes an external and connects over USB. Your laptop will be able to fit any 2.5" form factor drive, which includes all SSDs and any spinning drives sold as a laptop drive.

---

### Post by LowSky on 2011-12-24
drive caddies replace disk drives in laptops. 

40GB drive might be ideal. make sure you make the /temp folder mount to your RAM. Downside is you need a good deal of RAM to do that. I would recommend at least 8GB in those circumstances.

If you run anything that requires many log files like MySQL make sure you set it to delete the older logs. I ate up 15GB of space without realizing what was happening, and tracking it down was painstaking because the files were read only with root access.

---

### Post by u-noob-tu on 2011-12-24
> **LowSky said:**
> drive caddies replace disk drives in laptops. 

40GB drive might be ideal. make sure you make the /temp folder mount to your RAM. Downside is you need a good deal of RAM to do that. I would recommend at least 8GB in those circumstances.

If you run anything that requires many log files like MySQL make sure you set it to delete the older logs. I ate up 15GB of space without realizing what was happening, and tracking it down was painstaking because the files were read only with root access.
Why should you mount /temp to RAM? And i only have 4GB of RAM. Would that be a problem?

---

### Post by LowSky on 2011-12-24
/tmp (not /temp... my bad) is where the file system throws temporary files, usually the stuff for updates, upgrades, and one off system data, like the keyring, that doesn't need to be written to the drive permenatly. Putting it to RAM saves a few write cycles on a SSD. 4GB will probably be fine. Ubuntu itself barely needs 2GB, and 4GB is usually more than anyone really needs for normal use. I only say 8GB as it would mean more than plenty for nearly any situation. Plus I'm spoiled running 12GB on my desktop.

---

### Post by u-noob-tu on 2011-12-24
do you have any recommendations for certain specs or a particular brand? i found [COLOR=Red][this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820227510")[/COLOR] one on NewEgg that looks to be a good SSD.

also, i did read somewhere that SSD's can need firmware updates and/or require a BIOS flash. is that something to consider?

---

### Post by u-noob-tu on 2011-12-26
I just bought a Patriot Torqx 64GB SSD for $99 (plus i might get a $25 rebate on it). I probably only needed 32GB, but 64GB isnt that much more expensive and i want to be a little future proof. would someone be so kind as to give me a step by step guide on how i should go about installing ubuntu on it? never used an SSD before; heck ive never even seen one.

---

### Post by szymon_g on 2011-12-26
make sure you will connect it into SATA 6gbps /aka sata 3/ interface. connecting it into more popular, sata 3gb /aka sata 2/ will heavily limit it's performance /still will be faster than most harddrives/.
personally- i'd go for crucial's m4- [http://www.tomshardware.com/reviews/m4-ssd-capacity-comparison,2957.html](http://www.tomshardware.com/reviews/m4-ssd-capacity-comparison,2957.html) - relatively cheap and fast /esp. 256 gb version/- still leaves enough room for dual booting etc :)

---

### Post by u-noob-tu on 2011-12-26
> **szymon_g said:**
> make sure you will connect it into SATA 6gbps /aka sata 3/ interface. connecting it into more popular, sata 3gb /aka sata 2/ will heavily limit it's performance /still will be faster than most harddrives/.
personally- i'd go for crucial's m4- [http://www.tomshardware.com/reviews/m4-ssd-capacity-comparison,2957.html](http://www.tomshardware.com/reviews/m4-ssd-capacity-comparison,2957.html) - relatively cheap and fast /esp. 256 gb version/- still leaves enough room for dual booting etc :)
im pretty sure my laptop motherboard doesnt support SATA 3, unless its possible to add a SATA 3 controller to the mobo. if that is possible, that would be fantastic. 

i looked at the m4, but that was just a little more than what i wanted to spend. the specs are impressive though.

---

### Post by oldfred on 2011-12-26
I recently bought a Microcenter no brand SSD and installed two copies of Ubuntu to it. I installed 12.04 as that will be what the drive will eventually be for and 11.10 just to have a current version. I actually still boot Maverick 10.10 from my sdb 160GB rotating drive.

I learned how to directly boot an ISO from a Hard Drive and did that. I never saw an install go so quickly.:)

I may be getting a new system in 2012, so I future proofed it by using gpt, creating a 300MB efi partition as the first partition as that is what new UEFI systems need. Created a bios_grub 1MB partition as that is what my current BIOS needs and two / partitions (with /home still in / but no user data, just hidden settings). All my data and  swap is on rotating drives.

I used gparted and choose gpt under Device, Create Partition table, Advanced & choose gpt not the default msdos (MBR). Gpt is the newer partition table works great if not dual booting with Windows or if you have a new UEFI system. GPT is also recommended on the Arch site for SSDs.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

And you may want to make some settings to reduce writes:
You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD&#8217;s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition

---

### Post by u-noob-tu on 2011-12-27
> **oldfred said:**
> I recently bought a Microcenter no brand SSD and installed two copies of Ubuntu to it. I installed 12.04 as that will be what the drive will eventually be for and 11.10 just to have a current version. I actually still boot Maverick 10.10 from my sdb 160GB rotating drive.

I learned how to directly boot an ISO from a Hard Drive and did that. I never saw an install go so quickly.:)

I may be getting a new system in 2012, so I future proofed it by using gpt, creating a 300MB efi partition as the first partition as that is what new UEFI systems need. Created a bios_grub 1MB partition as that is what my current BIOS needs and two / partitions (with /home still in / but no user data, just hidden settings). All my data and  swap is on rotating drives.

I used gparted and choose gpt under Device, Create Partition table, Advanced & choose gpt not the default msdos (MBR). Gpt is the newer partition table works great if not dual booting with Windows or if you have a new UEFI system. GPT is also recommended on the Arch site for SSDs.

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

And you may want to make some settings to reduce writes:
You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
noatime,nodiratime options in fstab to make the ssd last longer when using a ext4 partition
:confused::confused::confused: sorry, that is way above my head :oops: i think i should start with some less intensive tweaks and fixes for SSDs. i think i just need to learn how to mount /home to my HDD and / to my SSD for now. lets do the uber hacker stuff after i get ubuntu up and running first :P

---

### Post by a2j on 2011-12-27
if you will get a new ssd, make sure it has good read/write specs and that your motherboard can support those speeds.

32Gb ssd should be plenty if you will use another drive for your /home. put swap and / on ssd and it will fly.

---

### Post by oldfred on 2011-12-27
Herman has lots of instructions & detail, but will walk you thru an install to an SSD.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

---

