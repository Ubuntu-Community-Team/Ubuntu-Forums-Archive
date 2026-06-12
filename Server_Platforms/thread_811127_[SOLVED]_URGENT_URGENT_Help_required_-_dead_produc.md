---
title: "[SOLVED] URGENT URGENT Help required - dead production server - Sydney, Australia"
date: 2008-05-28
forum: Server Platforms
---

### Post by axialnet on 2008-05-28
Update - PROBLEM RESOLVED - but makes a good read

Error message is

Uncompressing Linux....OK, booting the Kernel.

Unable to find volume group "Vult-System-root"

ALERT! /dev/mapper/Vult--System-Root does not exist
Dropping to a shell!

PRODUCTION MAIL SERVER DOWN

Our Linux engineer on holidays
After blackout last night only 4 of 5 servers came up

The failed server is HP Proliant ML310 with single 80gb ATA drive
Partition Config unknown as it was running virtual drive.

Server runs IMAP mail (with mySQL I believe) and hosts about 10 domains

Any help would be appreciated

If you are local to Upper North shore - Sydney we could look at $$'s if skills available.

Andrew
0419 300033

---

### Post by ripin1 on 2008-05-28
in the shell, try > sudo aptitude install ubuntu-desktop
im eleven, so i doubt this will work, but hey, its worth a try.
 note:if this does work, your personal settings cant be regained. i think those are lost for good.

---

### Post by gimmerealroot on 2008-05-28
Couple questions.

1st thing.  Inhale deeply.  2nd-call tech on cell phone and leave message that 4 out of 5 servers won't boot after blackout(claim you fixed the 1st 3 when he arrives/calls).  WHoa.... just kidding.

Do you have "root" passwd?

Any idea what configuration the drives are in?(ie-is the server running raid??  Go into the BIOS and look, if BIOS isn't password protected.  Change nuuuuuthing!)

What is listed when you type in
[PHP]ls -lah /dev/s*[/PHP]
and
[PHP]ls -lah /dev/hd*[/PHP]
and
[PHP]ls -lah /dev/mapper/*[/PHP]

Run [PHP]vgscan[/PHP] and post the results.

post the contents of your lvm.conf.  I'm not sure where Ubuntu Server locates this file(though, I'm 99% sure its under /etc ;), on my OS it is located on /etc/lvm/lvm.conf.

Are there any non-lvm volumes?

Post contents of /etc/fstab

Here's what one of mine looks like(fakeraid, non-lvm partitions, lvm partitions):

[PHP]/dev/md1                /boot           ext2            noauto,noatime  1 2
/dev/md6                /               reiserfs        notail,noatime  0 1
/dev/sda2               none            swap            sw,pri=3        0 0
/dev/sdb2               none            swap            sw,pri=3        0 0
/dev/sda3               none            swap            sw,pri=3        0 0
/dev/sdb3               none            swap            sw,pri=3        0 0
/dev/sda5               none            swap            sw,pri=3        0 0
/dev/sdb5               none            swap            sw,pri=3        0 0
/dev/vg/usr             /usr            reiserfs        notail,noatime  1 2
/dev/vg/portage         /usr/portage    ext2            noatime         1 2
/dev/vg/distfiles       /usr/portage/distfiles  ext2    noatime         1 2
/dev/vg/home            /home           reiserfs        notail,noatime  1 2
/dev/vg/opt             /opt            reiserfs        notail,noatime  1 2
/dev/vg/tmp             /tmp            reiserfs        notail,noatime  1 2
/dev/vg/var             /var            reiserfs        notail,noatime  1 2
/dev/vg/vartmp          /var/tmp        reiserfs        notail,noatime  1 2
/dev/vg/storage         /storage        xfs             defaults        0 0
/dev/hdb1               /.snapshot      xfs             defaults        0 0
/dev/cdrom              /mnt/cdrom      auto            noauto,ro       1 2
/dev/hdd                /mnt/dvd        iso9660         noauto,rw       0 0
[/PHP]
(Yes, I have 3 Raid1 swap partitions pri 3 on that particular machine)
Look forward to seeing more info...

---

### Post by gimmerealroot on 2008-05-28
> **ripin1 said:**
> in the shell, try 
im eleven, so i doubt this will work, but hey, its worth a try.
 note:if this does work, your personal settings cant be regained. i think those are lost for good.

ROTFLMAO!!!!!
:lolflag:[-X#-o

---

### Post by axialnet on 2008-05-28
Thank for the replies

Do you have "root" passwd?
SURE DO

Any idea what configuration the drives are in?(ie-is the server running raid??
HAS ATA RAID controller but only 1 drive

 Go into the BIOS and look, if BIOS isn't password protected. Change nuuuuuthing!)
YEP good idea

What is listed when you type in
Will get that info for you in the meantime check the dates on the attached directory dump from backup server - viewed from windows pc

NOTE
Have complete server backup from previous night but do not want to lose the new data.  Backup located on another Linux server on site.

I am really "freightened" by the LVM stuff

---

### Post by LeoSolaris on 2008-05-28
Alright before you go too far, here is a link to a snippet on the forum I found with a quick look around about /dev/mapper

[HERE]("http://ubuntuforums.org/showthread.php?t=646340")

The first logical step is to verify that the filesystem directory is intact. The easiest way I can think of to do this is to boot from a LiveCD and mount the hard drive from within the live environment. Unless you make changes to it, booting from the LiveCD will change nothing, but it will give you the ability to change things. Browse it from there just to verify that there is anything on it.

I am no where near a server expert, I just started using the Ubuntu server recently, but what it looks like is that after the power outage the raid array messed up and the system isn't seeing it properly. Check the hard drive both in the original machine with the LiveCD, and if it fails there, check it in another machine just to be sure. (If it fails there, it may by the hard drive) if it passes the second but not the first, it may be the raid card, or Linux's read of the raid card. See if you can reinstall and pass the nodmraid, I may be able to dig up a how to on it. Still looking.

If you can't get the nodmraid to work it may have fried the raid card itself.

This is speculation, but it should give you a little more to go on. Installing the desktop will give you a pretty space to look at, but it wouldn't do much to the filesystem directory. Besides, you're not booting that far are you?



Edit:  ok I'll let gimmerealroot handle it, it sounds like he knows more about this than I do. I'll shut up and watch. Maybe I can learn something.

---

### Post by axialnet on 2008-05-28
ls -lah (h is not supported)

so ls -la produces - a huge list duh

I am typing this on a windows box but I cannot use putty to the server as its down - any clues on getting the screen dumps to here

---

### Post by gimmerealroot on 2008-05-28
LVM is really very neat and less complicated than it appears.

IF the drive hasn't physically been naughty, then I suspect that what has happened is that the lvm drive mappings have been doinked.  This has happened to be on a power out as well.  1st time it happened to me I was unprepared and a little panicked, but the answer was rather simple.  

I had to 
-rebuild the volume device nodes[PHP]vgscan --mknodes[/PHP]
-activate my logical volume group(LV name should be shown by [PHP]vgscan *or* vgdisplay)[/PHP] Reactivate as follows:  [PHP]vgchange -a y[/PHP].  This also makes the LVs available for mounting.
-(You may not need this step or may need it later in the boot process)run file system check utilities on each volume just in case.
-Now all you need do is mount the reestablished LVs.

Did it for me, a couple times as a matter of fact.  I was fearful I would absolutely destroy my pretty complicated installation.  Alas, nothing to fear.  I rebuild the nodes and allowed me to see the devices under /dev/mapper/<your volume name here>

You will need all the drive mappings found in /etc/fstab when manually remounting your volumes and partitions.

Let us know how it goes.

---

### Post by axialnet on 2008-05-28
ls -la /dev/hd*  
brw-rw----  1 0  0  33, 0 /dev/hde
brw-rw----  1 0  0  3, 3 /dev/hda3
brw-rw----  1 0  0  3, 2 /dev/hda2
brw-rw----  1 0  0  3, 1 /dev/hda1
brw-rw----  1 0  0  3, 0 /dev/hda

ls -la /dev/mapper
crw-rw----  1 0  0  10, 63     control
drwxr-xr-x  7 0  0      13420  ..
drwxr-xr-x  2 0  0      60     .

vgscan
/bin/sh: vgscan: not found

---

### Post by gimmerealroot on 2008-05-28
> **LeoSolaris said:**
> Alright before you go too far, here is a link to a snippet on the forum I found with a quick look around about /dev/mapper

[HERE]("http://ubuntuforums.org/showthread.php?t=646340")

The first logical step is to verify that the filesystem directory is intact. The easiest way I can think of to do this is to boot from a LiveCD and mount the hard drive from within the live environment. Unless you make changes to it, booting from the LiveCD will change nothing, but it will give you the ability to change things. Browse it from there just to verify that there is anything on it.

I am no where near a server expert, I just started using the Ubuntu server recently, but what it looks like is that after the power outage the raid array messed up and the system isn't seeing it properly. Check the hard drive both in the original machine with the LiveCD, and if it fails there, check it in another machine just to be sure. (If it fails there, it may by the hard drive) if it passes the second but not the first, it may be the raid card, or Linux's read of the raid card. See if you can reinstall and pass the nodmraid, I may be able to dig up a how to on it. Still looking.

If you can't get the nodmraid to work it may have fried the raid card itself.

This is speculation, but it should give you a little more to go on. Installing the desktop will give you a pretty space to look at, but it wouldn't do much to the filesystem directory. Besides, you're not booting that far are you?



Edit:  ok I'll let gimmerealroot handle it, it sounds like he knows more about this than I do. I'll shut up and watch. Maybe I can learn something.

Your giving valuable advice.  It is always invaluable to have around a LiveCD with the tools you need and a "rescue" kernel ready for a lilo or grub or whatever boot.

He can verify filesystem integrity where he is at init level 1.  In fact, its a humbling and powerful run level.

No, I'm not a server expert, just a Gentoo user;)  I'm a Ubuntu Server GNUub.  Installed Ubuntu Server for the first time tonight.  On a side note, I despise the way Ubuntu prevents you from becoming real root.  Also, the completely cavalier manner in which Ubuntu(not the only distro) treats partitioning on installs, is really starting to get on my nerves.<News Flash-it aint Windows!!>  Pushing users in GUI installs to install everything on one drive that is composed of just 1 partition is a bit ludicrous to me.  Distro to user- "Everyone's going it.  Go ahead"... I digress...   /rant

Oh, and while I'm on a roll, why does a PRODUCTION SERVER have only 1 hard drive.  Why isn't there at least 2 drives is RAID 1??  Yikes.  Living on the edge, I guess.:guitar:

---

### Post by windependence on 2008-05-28
OK it sounds like the drive it can't see is a virtual drive on your SAN maybe? If that is the case, when the power went down, the connection to the SAN probably didn't come back up. It's hard without knowing your config but it sounds to me like this is what you have. Since it can;t find the virtual drive it's barking at you. Let me know if I am right on this.


-Tim

---

### Post by gimmerealroot on 2008-05-28
> **axialnet said:**
> ls -la /dev/hd*  
brw-rw----  1 0  0  33, 0 /dev/hde
brw-rw----  1 0  0  3, 3 /dev/hda3
brw-rw----  1 0  0  3, 2 /dev/hda2
brw-rw----  1 0  0  3, 1 /dev/hda1
brw-rw----  1 0  0  3, 0 /dev/hda

ls -la /dev/mapper
crw-rw----  1 0  0  10, 63     control
drwxr-xr-x  7 0  0      13420  ..
drwxr-xr-x  2 0  0      60     .

vgscan
/bin/sh: vgscan: not found

This is going to require a LiveCD or boot cd,at a minimum, with lvm. You will also have to make sure that you boot the cd with the lvm option on.  For instance, I have a Gentoo 2007.0 minimal CD with lvm and at the initial boot prompt, I enter [PHP]gentoo dolvm[/PHP]  I'm pretty tired right now, but I'm think at some point your going to have to chroot into the installation.
Hmmm...  Does the Ubuntu LiveCD have lvm?  I booted it once and forgot to look.  I know it runs Gnome and has access to terminals.

Here's a link that was very helpful when I needed it.  Ignore the references to RAID and dm-raid and skip down to the Mounting the Mundane
[http://gentoo-wiki.com/Recovering_RAID_and_LVM](http://gentoo-wiki.com/Recovering_RAID_and_LVM)
[COLOR="Red"]You need the contents of your /etc/fstab.[/COLOR]  Open your /etc/fstab with vi or nano and, if necessary hand copy all the partition mappings, device names, etc.  (I hope the root partition / isn't located on an LV,,,very bad.  Notice in the fstab example I gave you, my / resided on a physical partition, and in RAID1)

Here's another you may find has useful info.  Will be very useful for understanding the process of an lvm installation with 2 IDE drives:
[http://www.gentoo.org/doc/en/lvm2.xml](http://www.gentoo.org/doc/en/lvm2.xml)

Another good link to get ideas for Software RAID with lvm with a basic setup:
[http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID_mirror_and_LVM2_on_top_of_RAID](http://gentoo-wiki.com/HOWTO_Gentoo_Install_on_Software_RAID_mirror_and_LVM2_on_top_of_RAID)

Listen.  Feel your pain, axialnet.  Keep posting as much info as you can.  I'm sure the community here is responsive and won't leave you hangin.  Time for me to cash in the chips.

Keep bumping your thread.  Others are bound to notice.

---

### Post by gimmerealroot on 2008-05-28
> **axialnet said:**
> ls -lah (h is not supported)

so ls -la produces - a huge list duh

I am typing this on a windows box but I cannot use putty to the server as its down - any clues on getting the screen dumps to here

If you can boot a cd, I'd go with the LiveCD and start up SSHD once your ensured the IP address on the troubled server.  This way putty will work and connect.  Then its a matter of cut and paste, basically.

Contents of /var/log/dmesg, /var/log/messages, /var/log/syslog.  This will help forensically piece together the bigger picture and should have more clues as to the overall server configuration and hardware.

---

### Post by windependence on 2008-05-28
If his LVM volumes are on the virtual drive on the SAN and the SAN is not talking to the box, he doesn't need to boot from a CD or have LVM or anything. He just needs to get the connection back to the SAN so it can see the virutual drive. I THINK this is the way they are set up but he hasn't confirmed it yet. This is an enterprise setup, and many larger companies run a SAN and slice it up for all their machines.

-Tim

---

### Post by gimmerealroot on 2008-05-28
> **windependence said:**
> If his LVM volumes are on the virtual drive on the SAN and the SAN is not talking to the box, he doesn't need to boot from a CD or have LVM or anything. He just needs to get the connection back to the SAN so it can see the virutual drive. I THINK this is the way they are set up but he hasn't confirmed it yet. This is an enterprise setup, and many larger companies run a SAN and slice it up for all their machines.

-Tim

Could be, but I doubt it.  Definitely a case of "more info needed".  Axialnet?  Shed any light here?

Axialnet, just think.  The British users will be waking up in 6 hours.  Make sure to bump the thread.

---

### Post by axialnet on 2008-05-29
We have a new 64 bit HP server ready to go and just before my GURU went on holidays one of the older 64 bit servers blew up the HDD controller so the drives got tossed in the new box leaving our core mail server out in the cold.  Yep on the edge.

These things have been running along fine - till now anyway.

We have the UBUNTU original CD's here.  Would I be better getting out of init level 1 and booting off the cd's

That would probably help with getting stuff onto here as well.

I am better with a gui being a manager rather than a techo.
I have done console stuff for a long time (about 20 years) but only basic stuff - usually when something breaks.  Hey I moved all the websites to our other apache server, configured bind and got them back up (took 2 days - and I was shuffed with myself) last month and my GURU fixed the problem (stuck the drive in the new box) and had it all working in about 3 hours - I was pissed off.

So now you understand where I am at.

---

### Post by axialnet on 2008-05-29
No SAN involved here - at present.

Each box is a world unto itself.

We have GW box Primary DNS on fixed IP, GW/Proxy box running on 2 seperate links, Internal File server - (holds nightly backup of all boxes), Mail server (This broken box) and an apache server here and another in the City

---

### Post by axialnet on 2008-05-29
Bump the thread - please explain - post something in the thread??

---

### Post by windependence on 2008-05-29
Ay, looks like you may have to rebuild the LVM then. I haven't had to muck with that much.

-Tim

---

### Post by axialnet on 2008-05-29
Thanks for your thoughts anyway - I am just running thru all these genuine UBUNTU CD's I found in the GURU's office to see what's what.

This I think is NOT a time to use my trusty Knoppix CD

---

### Post by axialnet on 2008-05-29
UPDATE  ----   I have 2 CD's that seem to qualify
1 is Genuine Ubuntu v6.06.1 LTS for your PC
the other is burnt & labelled Ubuntu-Server 6.06 i386 from an ISO I think.  The folders are all dated 31/5/2006.  The genuine says it can run in read only mode BUT will it see the LVM on my dead server install????  The ISO only wants to offer various installs, Lamp install, etc.  ANYONE HELP WITH THIS????

---

### Post by gtdaqua on 2008-05-29
Reading all the posts, nobody is exactly sure if you can actuall recover your LVMs from CD. But you can definitely run partition commands from any live CD. The Ubuntu server CD, however, is not a live CD I guess. It may take you straight to install. 

But bite the bullet and attempt a recovery from a LIVE CD. If it works, it works. If not, move on. Figure out the next steps. You have had enough, mate! :)

---

### Post by gimmerealroot on 2008-05-29
> **gtdaqua said:**
> Reading all the posts, nobody is exactly sure if you can actuall recover your LVMs from CD. But you can definitely run partition commands from any live CD. The Ubuntu server CD, however, is not a live CD I guess. It may take you straight to install. 

But bite the bullet and attempt a recovery from a LIVE CD. If it works, it works. If not, move on. Figure out the next steps. You have had enough, mate! :)

I am sure he needs the liveCD.  You do need a LiveCD that has lvm modules to load.  I'm sure he can't do it from within init 1 because of the "vgscan" command not being found.  That command is part of a glob of lvm tools that will be available on the cd.  Do you have any other kernels to boot?  Are you able to select anything from the grub/lilo boot loaders or does it just automagically boot without any boot loader selection menus(I despise this trend as well)?

Further, if the Knoppix CD has lvm as a bootable option, then, by all means, use it,  boot it with lvm(check the boot options and parameters thoroughly for all LiveCD to get the boot syntax and parameters right, shouldn't be too much of a faff) and start up sshd.  You mentioned you couldn't dump the output of those needed files from putty and your WIndows box.  This will assist in getting that job done.

The output of the files I requested is vital.  There is no way around remapping those LVs and I/nor anyone else can't walk you through the remap process without at least the output of /etc/fstab.  This is important.

The log files will hold quite a bit of pertinent info.  For instance, did the server self-bork after an unattended update, etc?  Did your hda flake out?  Are you running any drive monitoring tools(like the indespensible smartmon tools)?

By "BUMP the thread", yes, I mean post to it to keep it as close to the "new threads"/"active thread" list as you can.

---

### Post by garethsimpsonuk on 2008-05-29
' install ubuntu-desktop ' that was hilarious!!!

( u may be 11 m8 and if u carry on with linux u will be an expert at a very early age but careful what advice u give. someone might actually try something like that and on a production server, i dont think the chap would be very happy)

---

### Post by gimmerealroot on 2008-05-29
axialnet,

How you making out?

---

### Post by axialnet on 2008-05-29
I have learnt heaps - especially some new procedures required in here regarding documentation of production boxes using NON-standard configurations - eg LVM.  Help has arrived so will update you all very shortly.  Keep watching this post please.

---

### Post by gimmerealroot on 2008-05-29
I'm subscribed.  Can we get a peek at your /etc/fstab/ or do I have to wait til the honeymoon?

Re: your last comment:

I've been there enough times regarding "eclectic" configurations to realize that I hadn't to rely on ole spunky to remember.  Stirring spunky produced mixed results.  So I started creating my own build documentation as I went through the process with each system.  Particularly, with Gentoo, it is so configurable and manageable that thorough self documentation is a must.  Well worth the extra time to me.  The build process(with Gentoo) is far more intense than this pop-in-the-cd-and-3-clicks-and-done stuff with a GUI.  That is what happens when one starts to "get ideas".  One tends to forget the set of twists or tricks used to accomplish the goal.

-gimmerealroot-

---

### Post by axialnet on 2008-05-29
Well its all working thanks to a very helpful assitant who runs his own web hosting company.

It appears that somehow the LVM startup volume was not active.  The actual startup should have been hda3. We worked this out by finding the relevant files on the backup image.  What we do not know is how or why the bootup defaulted back to using the LVM.  

If I consider the history of this server it was in an older machine previously that would have had several drives and LVM could have been used to span these drives into a single volume. 

But this is like last year. Why and how it suddenly decided to use that is a mystery as the server has been rebooted on the odd occassion since that time usually by extended power outages that exceed UPS run time.

The /etc/LVM folder was copied to LVM.old on 31 Jan 08 and the .cache file dated 10 Feb 08.  The fstab file (attached)was also dated 31 Jan (on the backup)

So unfortunately the outcome has not proven to be as juicy as we all thought.  The interesting side to this is having the correct tools to diagnose these things when you are not the builder of the server. Documentaion, documentation... etc

Thanks to all those who contributed. I was able to use the information gathered in response to your questions to fast track getting the server back on line.

Again a big thank you to those who bothered to care which is what makes the open source community so powerful.

Again thank you
Andrew:biggrin:

---

### Post by gtdaqua on 2008-05-30
Glad to know its finally ok now! Somehow, even the biggest of problems seem to go away over time! Because we need and will have new ones to fight with! 
Please mark this thread as SOLVED. Hopefully all your data is now safe too.

---

