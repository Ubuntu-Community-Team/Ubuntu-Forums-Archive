---
title: "IRC Chanops ridiculous behavior"
date: 2009-05-24
forum: Resolution Centre
---

### Post by daddysmonsters on 2009-05-24
You know I was surprised to see that the Chanops on #Ubuntu was no better than your typical 15 year old on youtube. I popped in for the first time today and got some help myself on mounting an ntfs over ssh with write permissions. Then decided to stick around while I worked and help and pay back the favor. Needless to say after walking through a compile of software, troubleshooting an overheated video card (not even Ubuntu related) and repeating sudo apt-get install xxx a hundred times. The last person (for me) had xammp running and couldn't edit a file named php.ini due to permissions. Now I will post what select all grabbed in the log here but basically I addressed the person and stated that he should first open a term and "man chmod" that he should read up on it if he was going to be running a webserver (which he obviously is) then I stated that since he didn't want to chmod 0777 everything and that as a quick fix to edit the file he should term  "sudo gedit /path/to/file.ini yadayada" Now during this the IRC channel is hectic and some chanop named mneptik or some such is just trying to pick a fight. Telling me not to mention chmod as if it's a police state and I'm speaking the name of an opposing faction to the current dictatorship. I responded calmly to him that if he read the other lines he would see that I wasn't suggesting the guy chmod 0777 all of his files, and that he will need to read it at some point and know what NOT to chmod on a web server. So of course that's not good enough the mighty chanop says never mention chmod CLEAR? lol so of course I busted his balls and called my own kick. Really more of a rant here than anything, and I'm not sure what offiicial capacity the IRC chan has to do with Ubuntu as an entity, but that's uncalled for. Ops are there to keep an eye on spam, illegal content and general tools. Not to pick fights with new users trying (and succeeding btw) to help other members. My name is zeromod btw.

 ```
02:02:35 AM) zeromod: brandon sudo apt-get install unrar    type that into a terminal
(02:02:39 AM) EGCdigital [n=EGCdigit@unaffiliated/egcdigital] entered the room.
(02:02:45 AM) zeromod: brandon then right click the rar file and extract as normal
(02:02:47 AM) saiki: I lothe firewalls, I'm on DMZ and no firewall enabled, windows on linux
(02:02:50 AM) phillipsm left the room (quit: Read error: 60 (Operation timed out)).
(02:02:51 AM) tzanger: kellyh: most people who use hardware RAID controllers are smart enough to have physical hardware backups on the shelf... I could never get the budget for a spare to be lying around
(02:02:54 AM) saiki: or*
(02:02:55 AM) blz: I just flashed back to when I was installing my RAID array... and you select the option "pysical volume for RAID"
(02:02:55 AM) mzz: blz: so you can add another raid array to the system, create a pv on it, add that pv to the group, and then grow one of the existing lvs to make use of the space (or add more)
(02:02:59 AM) joot: tzanger, blz, are you doing ubuntu support?
(02:03:00 AM) SunmanXII left the room (quit: "Leaving.").
(02:03:03 AM) Piet [i=pietor@gateway/gpg-tor/key-0xC5C71DCE] entered the room.
(02:03:03 AM) tzanger: and nobody ever noticed any kind of performance issue because it was always on a 100mbit network
(02:03:13 AM) ravelon [n=adminski@254-162-124-91.pool.ukrtel.net] entered the room.
(02:03:14 AM) tzanger: joot: if something catches my eye I can try to help
(02:03:17 AM) blz: joot:  yeah. depends on your problem
(02:03:21 AM) royalwarecast [n=warecast@117.85.110.127] entered the room.
(02:03:22 AM) Octoroks left the room (quit: Read error: 110 (Connection timed out)).
(02:03:26 AM) tzanger: blz: no not quite the same, but close
(02:03:26 AM) kellyh: tzanger: i got lucky, was given two identical servers, which both had the same identical hardware raid controllers
(02:03:28 AM) wangjing left the room (quit: Client Quit).
(02:03:32 AM) joot: tzanger, blz, 10 4
(02:03:40 AM) tzanger: RAID of course needs to know what physical disks it is creating an array out of
(02:03:41 AM) blz: tzanger:  oh god.  mind = raeped
(02:03:47 AM) ka6qzu left the room ("Ex-Chat").
(02:04:01 AM) hbbs_ [i=hobbes@gateway/gpg-tor/key-0x465B87A8] entered the room.
(02:04:02 AM) hbbs [i=hobbes@gateway/gpg-tor/key-0x465B87A8] entered the room.
(02:04:03 AM) tzanger: the LVM needs to know which "physical" devices it is using for the storage for the VGs you create
(02:04:06 AM) heshan1 [n=hesh@202.69.200.5] entered the room.
(02:04:08 AM) dSlaM: RKR: i'm not familiar with the server edition, but when i tried it i couldn't get any GUI environment (actually not any graph gard known, my guess is you have to install it or just go with the CLI, it's a server edition after all)
(02:04:17 AM) blz: So in any RAID array, you have to have a physical disk, on top of which an lvm is set up, on top of which a RAID array is set up, on top of which a PV is set up?
(02:04:30 AM) greenhousewarrio left the room (quit: Remote closed the connection).
(02:04:32 AM) mzz: blz: close, but not quite
(02:04:35 AM) tzanger: kellyh: for sure, and a lot of high-end RAID cards are fully compatible with arrays created by other hardware of the same vendor
(02:04:41 AM) blz: so "physical device" is the filesystem?
(02:04:46 AM) tzanger: kellyh: but again... I've never had that luxury :-)
(02:04:50 AM) ^Kiy^ left the room (quit: ).
(02:04:53 AM) Gnome_Danny [n=danny@adsl-223-139-158.mia.bellsouth.net] entered the room.
(02:04:55 AM) losher: blz: sounds like a lot of work just to record some TV....
(02:04:55 AM) blz: I apologize again for my utter stupidity...
(02:04:57 AM) tzanger: blz: let me try again :-)
(02:05:09 AM) tzanger: the RAID array needs physical disks to make an array out of
(02:05:14 AM) tzanger: so I give it physical disks
(02:05:15 AM) mzz: blz: physical disks -> multiple raids, each raid acts as a pv in a single lvm volume group, any number of lvs (logical volumes) uses space from that group
(02:05:18 AM) RKR: dSlaM: could you tell me how to configure the server as a DHCP server?
(02:05:20 AM) kellyh: tzanger: i had to ditch the thing in the end, too noisy for home use lol, core2duo 1.86ghz + SATA works for me now
(02:05:28 AM) Jonie left the room (quit: "No Ping reply in 90 seconds.").
(02:05:29 AM) the-light_ left the room (quit: "Ex-Chat").
(02:05:33 AM) heshan1: I'm a new to Ubuntu, I installed it on my Windows version, then I installed xampp on that, but I cnnot edit php.ini file , says no permission, how to acquire permission for me?
(02:05:36 AM) tzanger: RAID then gives me a logical disk which is redundant (because it uses the physical hardware in such a way that it enhances the reliability)
(02:05:44 AM) tzanger: i.e. by mirroring or striping + parity
(02:05:55 AM) the-light [n=se-light@91.98.154.37] entered the room.
(02:05:57 AM) Jonie [n=quassel@119.8.41.47] entered the room.
(02:05:57 AM) Octoroks [n=VIRUS@bas1-ottawa10-1279303880.dsl.bell.ca] entered the room.
(02:05:57 AM) Brime_ left the room (quit: Read error: 104 (Connection reset by peer)).
(02:06:00 AM) dsdeiz left the room (quit: "leaving").
(02:06:01 AM) tzanger: so now I have these "better" devices... the two RAID disks
(02:06:03 AM) zeromod: heshan1 open a termina   and   type  "man chmod" no quotes
(02:06:13 AM) RKR: heshan1: Did you logeed on as a SUDO user?
(02:06:14 AM) tzanger: now LVM takes devices and makes them appear as one big disk
(02:06:19 AM) blz: mzz:  oh. i think i'm getting confused because there's only 1 pv in my logical volume group...
(02:06:22 AM) dSlaM: RKR: (didn't do it for a very long time, apologies if i'm wrong)  apt-get install dhcpd
(02:06:29 AM) blz: or no.. i guess there's 2 since i'm running raid0
(02:06:33 AM) tzanger: I say "this array here, and that array there... both of these can be used to store data"
(02:06:36 AM) zeromod: heshan1 be careful how you set permissions you don't want everyone to have read write access to your files sounds like especially  a php.ini file
(02:06:43 AM) dSlaM: RKR: then edit /etc/dhcp***something
(02:06:50 AM) mzz: blz: yeah, but he has two separate raid arrays, so two pvs
(02:06:58 AM) RKR: dSlaM: No Problem
(02:06:59 AM) tzanger: so the LVM system says "awesome, so array1 is 250G and array2 is 600G, you now have 850G of storage available in the volume group"
(02:07:00 AM) butterbean [n=butterbe@cpe-98-30-15-89.woh.res.rr.com] entered the room.
(02:07:01 AM) roentgen [n=HaRT@miranda/user/roentgen] entered the room.
(02:07:02 AM) mzz: blz: err, wait, are you running raid or lvm or both?
(02:07:03 AM) the-light left the room ("Ex-Chat").
(02:07:09 AM) sleepingcreep [n=sleeping@host73-154-dynamic.3-79-r.retail.telecomitalia.it] entered the room.
(02:07:16 AM) sleepingcreep: salve a tutti
(02:07:18 AM) blz: mzz:  RAID0 ... i'm assuming on top of an LVM
(02:07:29 AM) tzanger: RAID0 is a terrible idea. most people who use it never hit the performance benefits anyway
(02:07:30 AM) mzz: blz: if you're assuming you don't have any lvm set up :)
(02:07:31 AM) zeromod: hshan1 you could also open a terminal and type  "sudo gedit  /path/to/file  and edit it that way 
(02:07:34 AM) anom01y: how would I go about upgrading my kubuntu 8.04 to xubuntu 9.04 ?
(02:07:35 AM) xemacs4321 left the room (quit: "Leaving").
(02:07:38 AM) blz: tzanger:  yes... i've noticed lol =)
(02:07:50 AM) anom01y: or do I need to reinstall entirety
(02:07:53 AM) zeromod: hshan1 that would be safer that chmod 0777 something that sounds like it's going to be on a web server
(02:08:05 AM) anom01y: !upgrade
(02:08:05 AM) ubottu: For upgrading, see the instructions at https://help.ubuntu.com/community/UpgradeNotes - see also http://www.ubuntu.com/getubuntu/upgrading
(02:08:08 AM) tzanger: blz: think of it this way: RAID gives you more reliable storage by using disks to store the data redundantly... any one disk failure won't make your data go away. right?
(02:08:09 AM) kellyh: tzanger: RAID10 or RAID50 can work well... if you've the discs
(02:08:11 AM) dSlaM: RKR: i took a course about that several months ago, if you can't manage to do it with just that tell me i'll look for the stuffs i've written
(02:08:17 AM) uukrul left the room (quit: Read error: 110 (Connection timed out)).
(02:08:19 AM) heshan1: RKR: zeromod: I cannot even copy a file to htdocs
(02:08:21 AM) blz: mzz:  but when I used the althernate cd to set it up, I selected the option of physical volume for raid... I assumed that was lvm-based
(02:08:28 AM) ghost3d left the room (quit: "Ex-Chat").
(02:08:29 AM) Filbert- left the room (quit: Read error: 54 (Connection reset by peer)).
(02:08:30 AM) mneptok: !sudo > heshan1
(02:08:30 AM) ubottu: heshan1, please see my private message
(02:08:37 AM) tzanger: kellyh: yeah RAID1/5 for me does it, and IIRC linux's implementation automatically stripes as well
(02:08:43 AM) blz: tzanger:  yeah i know about the dangers of raid0... i just tried it because I didn't *really* care about losing my shows
(02:08:45 AM) mneptok: zeromod: don;t recommend chmod when sudo will do, please
(02:08:45 AM) mzz: blz: the nice thing about lvm is that you can create any number of partitions with a human-readable name, which you can resize and move across any number of underlying "physical" volumes (can be actual drives, can be raid devices like what tzanger has)
(02:08:51 AM) Valancy [n=Valancy@bas1-toronto47-1177731286.dsl.bell.ca] entered the room.
(02:08:51 AM) f0urtyfive left the room (quit: Connection timed out).
(02:08:54 AM) mylogic_ left the room (quit: Read error: 60 (Operation timed out)).
(02:08:59 AM) RKR: heshan1: Tell me did you logged on as a SUDO user?
(02:09:07 AM) mzz: blz: I'm pretty sure "physical volume for raid" just means you're using the entire physical drive in a raid (no separate partitions on the drive)
(02:09:22 AM) blz: mzz:  ah but there are parititons on the drive
(02:09:30 AM) tzanger: blz: ok. so where RAID uses disks to make your data safer, LVM uses disks and creates a "blob" of storage that can span any number of the disks it is told it can use
(02:09:31 AM) heshan1: RKR: how can I login to SUDO?
(02:09:37 AM) Kalmi: !sudo
(02:09:37 AM) ubottu: sudo is a command to run programs with superuser privileges ("root"). Look at https://help.ubuntu.com/community/RootSudo for more information. For graphical applications see !gksu (Gnome, XFCE), or !kdesudo (KDE)
(02:09:40 AM) BePhantom [n=haiku-os@186.18.65.87] entered the room.
(02:09:41 AM) mneptok: heshan1: see the bot's .msg
(02:09:42 AM) Kalmi: !root
(02:09:42 AM) rgmz [n=raghulmz@117.201.24.41] entered the room.
(02:09:42 AM) ubottu: Do not try to guess the root password, that is impossible. Instead, realise the truth... there is no root password. Then you will see that it is 'sudo' that grants you access and not the root password. Look at https://help.ubuntu.com/community/RootSudo
(02:09:48 AM) blz: mzz:  maybe this is why my performance sucks too... but I have a raid1 /boot, a raid0 swap, and a raid0 /
(02:09:51 AM) tzanger: blz: LVM does not (normally) offer any better reliability, just the ability to use multiple disks as if they were one
(02:10:12 AM) p-suti_: if i update my ubuntu, do my staff disappear from my hd
(02:10:13 AM) zeromod: heshan1 you are straying off course bro. One issue at a time, the reason you can't move a file is probably the same reason you can't edit one. Permissions. You should learn how to chmod files and be safe especially since it sounds like you want to run a web server. Or as a quick safer approach at editing the file just open a terminal and without quotes type  "sudo gedit /path/to/your/file.ini"
(02:10:16 AM) dSlaM: sudo bash
(02:10:19 AM) blz: tzanger;  so if I wanted to, I could just make one regular filesystem (no raid) span across 2 disks...
(02:10:21 AM) p-suti_: stuff :)
(02:10:21 AM) dSlaM: AHAHAH I'm king of the box
(02:10:34 AM) tzanger: blz: EXACTLY
(02:10:35 AM) mneptok: zeromod: don't recommend chmod when sudo will do, please (x2)
(02:10:36 AM) mzz: blz: that shouldn't suck, apart from obvious problems like the drives sharing a controller, and even then I'd expect it to keep up until load's really heavy
(02:10:42 AM) mneptok: zeromod: don't make me ask a third time
(02:10:46 AM) lyrae [n=lyrae@c-68-49-141-179.hsd1.md.comcast.net] entered the room.
(02:10:47 AM) kellyh: tzanger: main advantage of LVM is not needing to delete partitions when adding more drives
(02:10:49 AM) tzanger: blz: think of your disks as car seats
(02:10:53 AM) dsdeiz [n=dsdeiz@acl1-730bts.gw.smartbro.net] entered the room.
(02:10:56 AM) blz: tzanger;  I see.  Now, if one of those disks bit the dust, would *all* my data be gone or just the data on that disk?
(02:10:59 AM) p-suti_: ?
(02:11:03 AM) RKR: heshan1: Are you the only user for that system?
(02:11:05 AM) lyrae: Hi. I have a webcam working in skype. is there a program I can use to alter the brightness/hue/etc?
(02:11:09 AM) tzanger: blz: if you have a fat guy who won't fit in one car seat, you can't have him sit comfortably in two
(02:11:10 AM) anom01y: what happens when ubuntu 8.04 support runs out ?
(02:11:17 AM) zeromod: mneptok if you read both lines you'll see i explained the dangers of chmod i also said man page the chmod command and then explained to use sudo and edit it
(02:11:20 AM) mzz: blz: and even nicer is that you can move the data to a different physical drive (or make it extend onto another physical drive) without having to umount it or edit fstab or whatever
(02:11:22 AM) anom01y: should I upgrade to 9.04 ?
(02:11:31 AM) hardbuntu [n=hardbunt@20158042189.user.veloxzone.com.br] entered the room.
(02:11:34 AM) anom01y: or stay at 8.04 if everything is working ?
(02:11:35 AM) Gnome_Danny: Hey, I got one question, How come I can't get desktop cube enabled on compiz fusion but everything else works fine
(02:11:39 AM) dSlaM: tzanger: Ryan Air apparently doesn't have any problem with that
(02:11:44 AM) the-light_ [n=se-light@91.98.154.37] entered the room.
(02:11:46 AM) tzanger: LVM gives you a car with no seats whatsoever.  and you can then custom-build as many seats in any sizes you want, as long as they'll all physically fit in the car
(02:11:46 AM) mneptok: zeromod: why *even mention* chmod? answer? don't.
(02:11:50 AM) anom01y: anyone ere run 8.04 ?
(02:11:56 AM) tzanger: dSlaM: ryan air?
(02:12:01 AM) mneptok: anom01y: i do
(02:12:08 AM) icauchy_ [n=chatzill@220.161.122.68] entered the room.
(02:12:11 AM) blz: mzz: but maybe that's why it sutters?  because of conflicts between writing to swap and / ... and that might be compounded by having to heads seek each time?  I mean i (obviously) don't know jack about these things...
(02:12:11 AM) tzanger: blz: and yes, if you have one of hte PVs die in an LVM, you're screwed.
(02:12:18 AM) Kalmi: anom01y, upgrade
(02:12:18 AM) TheNano left the room (quit: "Ex-Chat").
(02:12:20 AM) the-light_ left the room ("Ex-Chat").
(02:12:23 AM) blz: tzanger:  so it's just as bad as raid0 on that front
(02:12:24 AM) Gnome_Danny left the room (quit: "Leaving").
(02:12:25 AM) Jonie left the room (quit: "No Ping reply in 90 seconds.").
(02:12:25 AM) elscribo left the room (quit: Remote closed the connection).
(02:12:28 AM) dSlaM: tzanger: a low coast airline company, they are thinking about charging really fat people with 2 tickets instead of one ;)
(02:12:29 AM) mzz: blz: shouldn't suck significantly more than without the raid
(02:12:29 AM) christiekoehler| is now known as christiekoehler
(02:12:30 AM) zeromod: mneptok because he is running a web server henceforth permissions are a fact of life. He will need to know what should NOT be 0777 else he's not learning anything he's just typing what I tell him to in the console.
(02:12:35 AM) RKR: heshan1: Does any other have some other user account in your system?
(02:12:36 AM) anom01y: all right
(02:12:39 AM) Gnome_Danny [n=danny@adsl-223-139-158.mia.bellsouth.net] entered the room.
(02:12:39 AM) kija [n=vaio@122.172.113.34] entered the room.
(02:12:41 AM) blz: mzz:  hmm. so the original problem persists...
(02:12:42 AM) tzanger: blz: yes for the most part.  you CAN tell LVM to do RAID1-like stuff
(02:12:43 AM) mode (+o mneptok ) by ChanServ
(02:12:46 AM) anom01y left the room (quit: "Leaving").
(02:12:47 AM) mzz: blz: (and if you're hitting swap regularly on a mythtv box with several GiB of ram something really weird is going on)
(02:12:49 AM) glitch942003 [n=user@adsl-67-127-246-66.dsl.irvnca.pacbell.net] entered the room.
(02:12:50 AM) Jonie [n=quassel@119.8.41.47] entered the room.
(02:12:54 AM) uukrul [n=uukrul@76.105.204.63] entered the room.
(02:12:56 AM) ace1506 [n=ace1506@ip68-4-31-249.pv.oc.cox.net] entered the room.
(02:12:58 AM) blz: mzz:  also true
(02:12:59 AM) mneptok: zeromod: do NOT metion chmod when sudo is the preferred method. clear?!
(02:13:00 AM) tzanger: blz: for the most part though I am happy to let RAID do its thing, and just give LVM already-redundant storage
(02:13:03 AM) Kalmi: !upgrade > anom01y
(02:13:04 AM) tzanger: blz: now
(02:13:09 AM) squall_ [n=squall@p57A3CA44.dip.t-dialin.net] entered the room.
(02:13:13 AM) tzanger: blz: this is only one part of LVM's good stuff
(02:13:18 AM) Dday [n=X@c122-106-204-110.belrs3.nsw.optusnet.com.au] entered the room.
(02:13:19 AM) mode (+e futurbillgate!i=d2d46183@gateway/web/ajax/mibbit.com/x-ca0fdb775da70b96 ) by FloodBot1
(02:13:20 AM) tzanger: blz: LVM also lets you take filesystem snapshots
(02:13:23 AM) zeromod: OK roger dodger mighty waiving his sysops like arms guy
(02:13:27 AM) blz: tzanger:  is that so?
(02:13:32 AM) blz: i'm listening
(02:13:34 AM) amazin left the room (quit: Remote closed the connection).
(02:13:35 AM) tzanger: blz: LVM also lets you carve out filesystems without disturbing ohters
(02:13:35 AM) zeromod: happy you get to kick someone now
(02:13:40 AM) verne883 [n=james@121.91.68.91] entered the room.
(02:13:41 AM) zukabuka [n=avl@222.127.12.76] entered the room.
(02:13:42 AM) blz: what does that mean?
(02:13:44 AM) RKR: dSlaM: PLs see my private message!
(02:13:45 AM) tzanger: blz: and LVM also lets you resize the areas you've carved out
(02:13:47 AM) J-_ left the room (quit: ).
(02:13:51 AM) U-b-u-n-t-u: in the ifconfig which one is the mac address to use for wireless mac filtering
(02:13:52 AM) Meatball [n=rimantas@78-56-24-30.static.zebra.lt] entered the room.
(02:13:55 AM) Kalmi: tzanger, carve?
(02:13:56 AM) mneptok: zeromod: it's "chanops"
(02:14:03 AM) ancible left the room.
(02:14:05 AM) Meatball left the room (quit: Client Quit).
(02:14:07 AM) tzanger: blz: snapshots? say you want to take a backup.  you normally have to make the filesystem "quiet" for the time you take the backup or your backup can be inconsistent
(02:14:11 AM) ***zeromod attention everyone chmod is no longer a valid command as mneptok does not approve of it
(02:14:12 AM) mneptok: zeromod: but it's nice to know you're uninformed about other things, too
(02:14:12 AM) tzanger: blz: and backups can take a long time
(02:14:13 AM) blz: tzanger:  no i mean carving
(02:14:19 AM) mode (-e futurbillgate!i=d2d46183@gateway/web/ajax/mibbit.com/x-ca0fdb775da70b96 ) by FloodBot1
(02:14:23 AM) kellyh: U-b-u-n-t-u: the xx:xx:xx:xx:xx line
(02:14:24 AM) ***zeromod also we are banning lsmod as its just too hard to read
(02:14:25 AM) hardbuntu left the room (quit: Client Quit).
(02:14:35 AM) U-b-u-n-t-u: kellyh, there are 2
(02:14:35 AM) tzanger: blz:  so you what you do is you make the filesystem quiet, tell LVM to take a snapshot, then start everything back up
(02:14:38 AM) losher: anom01y: 8.04.2 LTS is supported until 2011. No need to upgrade unless there's something specific you need that you can't get in 8.04
(02:14:43 AM) overshard left the room (quit: "Leaving").
(02:14:49 AM) tzanger: and you can take your backup while the system still runs normally, sinc the snapshot is "quiet" (doesn't move)
(02:14:52 AM) heshan [n=hesh@202.69.200.5] entered the room.
(02:14:52 AM) mode (+b *!*zeromod@*east.verizon.net ) by mneptok
(02:14:52 AM) U-b-u-n-t-u: kellyh, one by the eth and one by the wlan
(02:14:57 AM) You have been kicked by mneptok: (buh bye)
```

---

### Post by daddysmonsters on 2009-05-24
Baiting people seems to be A-ok and I will also take this time to apologize to elky for my poor sentence structure and lack of practical grammar in my posting. As was pointed out immediately as I attempted to stake a complaint on ubuntu-ops. Of course then you read into my statement that ops was not allowed to  "counter my bad advice" which btw was the same advice as the op. And well, I didn't get much further than that because "elky" had to calm "hobsee" down before things got out of hand. Pfft, a joke and such is my first experience in the community. I'm not some ranting 9 year old, I won't go screaming that I'll never use ubuntu or linux again because really who would care? Besides that I love ubuntu and linux as a whole. But I will without a doubt state that After being put into a postion where I lost my own temper in front of my peers and then having everything from my grammar to my impractical advice bashed. I won't be attending any bloody council meetings anytime soon. Ubuntu IRC support? YMMV.

---

### Post by KiwiNZ on 2009-05-24
We have no responsibility for the IRC channels

Please refer his to  #ubuntu-ops to address this

---

### Post by daddysmonsters on 2009-05-24
Well then It makes me smile a little to know there is still hope for the forums. Sadly as presented in my second post (felt no need to edit such a large post with codeblock in it) It resulted in insults to my sentence structure. I apologize for putting it here, but was frustrated and by the time I found that I had to go to the ops chan I had already ranted.

---

