---
title: "Fluxbuntu CE?"
date: 2007-06-29
forum: Ubuntu Christian Edition
---

### Post by marko on 2007-06-29
Has anyone had this vision?

Start class for Jr High/HS church group.  Introduce them to the fact that Bible study is cool/fun/challenging/rewarding.  Hopefully have everyone pull out their laptops (or if your church is really endowed - send each kid to their computer in the classroom), pop in a Ubuntu CE live CD, and live boot to a desktop where Bibletime/gnomesword/esword is already configured with a couple of Bibles, Strongs, Robinsons.  True in-depth Bible study in 5 minutes flat.

I have that dream.  It is only a dream.  Any chance it can become reality?

I am asking the Antix guys to see how hard it would be to take their install, add ChristianEdition stuff (like Bibletime), then re-burn it as an ISO.  Why Antix?  Because it is small, and it is live.

Could this be done with Fluxbuntu?  Sure.  But, I would prefer pre-installed Bible software..  Doesn't CE fit the bill? - I am afraid it is too fat.  This is more of a kiosk type application, and the lighter the better.

Is anyone in the CE community interested in sharing this vision?  Can anyone tell me how to make it reality?

---

### Post by mysticrider92 on 2007-06-29
Fluxbuntu could easily be reconfigured with the apps for doing this, using the same method Jereme uses for the Ubuntu CE cd's (Reconstructor, and a few other programs).  You would just add the programs you want to the cd and use the program to repack the iso.

The only problems I would see: Many people in you target age group probably don't have laptops, and those that do are more than likely not powerful enough to run as a live cd (unless the church, study group, etc provided the computer). Also, the free Bibles that can be included are not always the best for most groups, the KJV and things can be hard to understand (on the upside, everyone has the same translation availible). 

This is a good idea, it would just require a bit of work and planning. Also, as a suggestion, DSL is a very quick Debian-compatable distro that will run live on most any computer. It would just need to be made a bit more user-friendly.

---

### Post by marko on 2007-06-29
Appreciate your feedback very much.  I think your comments are very accurate, but I am willing to give it a go.  Will be tackling KJV (for linkages to references), and ESV for conservative, modern version.

I may take a peek at Fluxbuntu, but after grabbing a copy of Antix, may try that one first since it's target machine is a 500 MHZ and 128 MB.  I think most kids can round up something that simple, and just borrow it for the teaching lesson.  The beauty of this is, nothing is ever installed.  They just run and then they are done.

If it works, may post additional comments about value of this effort.

Blessings!

---

### Post by mysticrider92 on 2007-06-30
Ok, I didn't know how you were going to do the computers, but that makes sense. You might want to work on the cd a bit to remove things that could harm the computer it is used on (say, parted, fdisk, install scripts, etc.). Being based on Mepis will be good since it has the .deb package management (for making the cd). Another idea would be to get some small flash drives to use for notes and stuff like that.

---

### Post by LaserJock on 2007-06-30
You might also look at Edubuntu. If you can get ahold of 1 good computer to act as an LTSP server then the overall hardware costs (lots of old PII or PIII machines laying around to use as thin clients) and requirements go down significantly, and it doesn't need to be a LiveCD. I think if you took Edubuntu and used Xfce4 instead of Gnome and added in the Bible goodies it might work quite well.

-LaserJock

---

### Post by marko on 2007-07-02
Thanks for the comments on this.  I am hoping I manage to create the ISO successfully.  If it works out, I will post back results.

The reason I did not look into LTSP is concern for a fixed classroom situation.  In other words, I realize that if I have a computer lab situation, it is not much work to set up a LTSP server, or even pre-load the application on the PCs available.

What I am hoping to do is to save time introducing Bible study to a spontaneous group of people, with nothing but laptops as the target hardware.  Again, thinking of situations like the Jr. High Sunday School class, or possibly even the parent SS class, or guest teaching at another church with the same presentation.  The goal is to have a CD that can travel into these situations and bring everyone up on the same Bible application in little more than boot up time.

With Linux, and live ISOs, this can be a reality.  Looking forward to what happens.

---

### Post by TravMan63 on 2007-07-03
Fluxubuntu is indeed do-able - and I think much easier now than back when I did it to Breezy.

Unfortunately, we don't use Ubuntu on that machine as much now, I could try 'wining' our recording ap to it... but win98 seems to handle that ok.

The laptop was to be used for powerpoint presentations, but when the external screen (monitor output) was used - the screen went blank... 

I think that machines specs are 500 mhz, 160MB Ram. HP.

Good luck on your Fluxubuntuing... I'll be adding that to another UbuntuCE install in a week or 3...

TM

---

### Post by jonathonblake on 2007-07-13
> **marko said:**
> Thanks for the comments on this.  I am hoping I manage to create the ISO successfully.  If it works out, I will post back results.

i suspect that other people would find the ISO useful, so could you post it somewhere,please?

xan

jonathon

---

### Post by anticapitalista on 2007-07-13
marko

I would be interested to know if you managed to remaster antix to an antiXCE and if you did, how well it works on old boxes.

anticapitalista

[http://antix.mepis.org/](http://antix.mepis.org/)

---

### Post by marko on 2007-07-17
The idea is there, the time is fleeting.  Need to do this on the weekends and things have been busy with summer and kid activities.  But if I do manage to make progress, will certainly let you all know how it looks.  Esp you, Anti!  Thanks again for your hard work to make AntiX in the first place.

---

### Post by marko on 2007-07-23
Anti, in case you are still tracking this thread, would you give me a hint on how you re-master Antix?  

I have these instructions, but if you do something different, I would much rather follow your steps..  Thanks much!

----------------------------------------------
Remastering Mepis 6.5

NOTE: Use these instructions for Mepis 6.0 and newer.

$ su
# apt-get install squashfs-tools
# mkdir work
# cd work
# mkdir iso
# mount -o loop /dev/hdc iso
# mkdir squashfs
# mount -t squashfs -o loop iso/mepis/mepis squashfs
# mkdir new-iso



# rsync -a iso/ new-iso
# rm new-iso/mepis/mepis
# mkdir new-squashfs
# cp -a squashfs/* new-squashfs/
# chroot new-squashfs
# mount -t proc proc proc
# mount -t sysfs sys sys

Substitute eth0 with your LAN device.

# dhclient eth0

Edit /etc/apt/sources.list to add repo's.

# apt-get update
# apt-get remove kaquarium splashy
# apt-get install vpnc wpasupplicant vim
# umount /proc
# umount /sys
# exit
# rm new-squashfs/root/.bash_history
# mksquashfs new-squashfs new-iso/mepis/mepis



# cd new-iso
# mkisofs -l -r -R -v -V "Mepis" -no-emul-boot -boot-load-size 4 -boot-info-table -b 
 boot/grub/stage2_eltorito -c boot.catalog -hide-rr-moved -o ../mepis.iso .
# cd ..

Test the mepis.iso with qemu to see if it boots.

# apt-get install qemu
# qemu -m 256 -cdrom mepis.iso -boot d

This can take a long time to boot.

Burn the mepis.iso to CD or to a DVD if you made it too big for a CD.

---

