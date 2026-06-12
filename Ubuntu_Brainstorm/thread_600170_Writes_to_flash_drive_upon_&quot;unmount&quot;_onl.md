---
title: "Writes to flash drive upon &quot;unmount&quot; only"
date: 2007-11-02
forum: Ubuntu Brainstorm
---

### Post by seventynine on 2007-11-02
Noticed this odd feature in Feisty/Gutsy (the only two I have used). 

When you copy a file from harddisk to a usb flash drive, it doesn't actually write to flash until you "unmount" the flash drive. You kind of expect it to be written to flash immediately, but it's not the case here. Ubuntu writes to flash only when you "unmount" which sometimes is easily forgotten if you're in a hurry. 

On three occasions so far, I completely forgot to "unmount" the flash drive, just plugged it out instead, took it somewhere, and realized that the files were never there on the flash in the first place. Kind of feel sorry for yourself when you are miles away from home by the time you realize it.

Would be great for everyone if Ubuntu wrote to flash drive immediately. ;)

---

### Post by MrFSL on 2007-11-02
It is incorrect that it will write to flash only when you unmount. It is correct that it might not write to flash immediately. This process if very common with external devices and the same behavior is seen in Windows as well.

This makes the device seem faster and the information can be written when it seems convenient to the O/S or when the device is Ejected or Unmounted.

[http://ubuntuforums.org/showthread.php?t=239631](http://ubuntuforums.org/showthread.php?t=239631)

---

### Post by kragen on 2007-11-02
how about having a "writing file to flash disk in background" progress meter up in the status area or something? Just some sort of indication that there are file operations that aren't complete yet.

---

### Post by seventynine on 2007-11-02
^Any sort of progress meter would be very useful for everyone

In its current state, you get tricked, because after the copying attempt, the files appear on the flash drive immediately. But they're not really there, yet.

---

### Post by smartboyathome on 2007-11-02
> **seventynine said:**
> ^Any sort of progress meter would be very useful for everyone

In its current state, you get tricked, because after the copying attempt, the files appear on the flash drive immediately. But they're not really there, yet.

Or maybe make the folders and files lighter (ie: more translucent) to signal that the file isn't written to the drive. When the user hovers over the icon, it could say "icon not written to drive".

---

### Post by timcredible on 2007-11-02
this is not an ubuntu thing - it's a linux/unix thing.  when you write to a flash drive, it sends the data to a cache, and then to the physical drive.  that last part of the data doesn't get written until the cache is flushed (ie. unmount the drive).  it's different from windows.

---

### Post by chrisccoulson on 2007-11-02
The behaviour can be changed by mounting the drive with the sync option. This would force all data to be written to the drive immediately. I think the user should be given the choice though, perhaps like in the attached mock-up

---

### Post by cpuobsessed on 2007-11-04
It has happened to me a couple of times that files were not written to the flash drive. The sync option should be enabled by default.

---

### Post by sicofante on 2007-11-05
> **chrisccoulson said:**
> The behaviour can be changed by mounting the drive with the sync option. This would force all data to be written to the drive immediately. I think the user should be given the choice though, perhaps like in the attached mock-up

> **cpuobsessed said:**
> It has happened to me a couple of times that files were not written to the flash drive. The sync option should be enabled by default.

I second both proposals. Pendrives should never require "unmount first". I've got into endless discussions before on this subject, so I just vote for you two guys and pray.

---

### Post by seventynine on 2007-11-09
+1

Lets hope that Ubuntu developers think of this as "Ease of Use" feature :KS

---

### Post by MrFSL on 2007-11-09
I guess no one read my link on the above post so I will outline the details here.

Flash media only has a lifetime of about 100,000 writes. (That is not a lot at all!) Please see: [http://en.wikipedia.org/wiki/Solid_state_drive](http://en.wikipedia.org/wiki/Solid_state_drive)
> Limited write cycles. Typical Flash storage will typically wear out after 100,000-300,000 write cycles, while high endurance Flash storage is often marketed with endurance of 1&#8211;5 million write cycles (many log files, file allocation tables, and other commonly used parts of the file system exceed this over the lifetime of a

To extend the life of your media, a good O/S minimizes the amount of writing to the disk. Information is cached and then all written at once when the O/S determines that you are done using the flash medium. -- This might be arbitrary (as it is in Windows) or it might be at a defined point where you tell the O/S (via unmounting) that you are through.

Do to laziness and a bewildering inability to properly eject your flash media, you would rather buy new media more often. ---- not me!

---

### Post by CrazyGuy123 on 2007-11-09
Windows does not cache removable disks by default.

Most (all?) USB flash devices now have in built wear levelling.  That means that if you write the same sector 2000 times per second, 24 hours a day, 365 days a year, it'll still last over 3 years. (presuming a 512 byte sector, 100,000 erase cycles, near ideal wear levelling, and a 1gb usb device) The reason is the built in hardware wear levelling keeps counts of how often each sector is used and will use and erase them evenly.  If a flash sector "wears out" it will move the data to a new sector and mark the sector as bad.  Error correction codes are used so data can be correctly read from a sector even if it's bad.  All that is done in the 2nd (smaller) chip in a USB sick, totally transparently to the OS.

The only reason for write caching is to speed the application up.  The same could be accomplished with a small cache that flushes itself every second.


On the same topic, why is data always lost if a usb device is mounted while the system goes into hibernation, even if the USB device is also presen after hibernation?  The cache should certainly be flushed before hibernating.

---

### Post by qamelian on 2007-11-09
> **CrazyGuy123 said:**
> Windows does not cache removable disks by default.

It does on every Windows system I have used. I have lost data on Windows XP Pro systems at work several times by forgetting to eject my thumb drive while in a hurry.

---

### Post by MrFSL on 2007-11-09
> **qamelian said:**
> It does on every Windows system I have used. I have lost data on Windows XP Pro systems at work several times by forgetting to eject my thumb drive while in a hurry.

I agree. It most certainly is cached in Windows operating systems.

---

### Post by MrFSL on 2007-11-09
on a different note - of course we can easily overcome this. 

We could script out a "copy to external media" menu which upon copy completion issued a sync command.

Might even be faster then drag and drop. Would solve the problems you are having without  unnecessarily modifying it for the rest of us!

---

### Post by CrazyGuy123 on 2007-11-09
Windows doesn't cache data according to Control Panel > Hardware > Device Manager > Disk dives > right click a usb one > properties > policies > optimize for quick removal - disables write caching.

That is the default setting.

Note that that is only the default setting as of Windows XP SP2 and later.  Earlier versions of XP and Windows 2000 and 9x versions did write caching.

Note that you can still lose data as some USB flash disks seem to have (no source for this info) a small hardware cache in - that seems to apply more to the "smart" devices like MP3 players.

Another possible reason for loosing data even if write caching is disabled is that the disk will still be marked as uncleanly unmounted, and that may cause windows to restore the bakup file allocation table, which isn't guaranteed to be up to date.

Can anyone confirm if the confusion on this issue still occurs on windows XP SP2 and later, and if it's file data that gets corrupted (ie. top half of a .bmp image turns to random noise, or black, or white), or if the file appears not to exist (the file allocation table has been restored from an old version)

---

### Post by FXEF on 2007-11-09
I would say that if you want your data written to the flash drive (Windows or Linux)  _always_ umount the drive before unplugging it. Same goes for floppy disk. I guess I've been lucky, but have on some occasions unplugged flash drives without unmounting and have not lost data. 

Question: is this a Linux kernel issue or a Ubuntu issue?

---

### Post by sicofante on 2007-11-09
> **MrFSL said:**
> Flash media only has a lifetime of about 100,000 writes. (That is not a lot at all!)
a) This is constantly changing for the better. Many current pendrives can do ten times better than that. b) If you really are that technically savvy and worried about your pendrive memory writing cycles, just turn sync writing off.


> **FXEF said:**
> I would say that if you want your data written to the flash drive (Windows or Linux)  _always_ umount the drive before unplugging it.
Errr.... the whole thread is about avoiding having to do this. :confused: Precisely because most people will simply unplug the pendrive and forget about ejecting it first.

This discussion can go on and on endlessly. I believe the advocates for changing the default behaviour to sync and providing an easy way for going back to "unsync" (me included) are not trying to stop EVERYONE from doing the eject thing. It's just that "the rest of us" (I would say every non-geek out there) just love unplugging these little pendrives without worrying about loosing data. Achieving this would mean a very distinctive advantage for Ubuntu. I can imagine the conversation:

Windows & Mac user: "Careful, careful!!! Do the "eject thing" before!!!" 
Ubuntu user: "Nah, this is Ubuntu, nothing is lost here by just unplugging a pendrive"

:)

---

### Post by FXEF on 2007-11-09
> **sicofante said:**
> a) 

Windows & Mac user: "Careful, careful!!! Do the "eject thing" before!!!" 
Ubuntu user: "Nah, this is Ubuntu, nothing is lost here by just unplugging a pendrive"

:)

I agree...   Question: is this a Linux kernel issue or a Ubuntu issue? I'm not a developer or programmer, so I don't have the answer.

---

### Post by sicofante on 2007-11-09
I'ts an Ubuntu issue. At least some solutions are Ubuntu's decision, like using the sync option by default.

---

### Post by bikeboy on 2007-11-11
> **CrazyGuy123 said:**
> On the same topic, why is data always lost if a usb device is mounted while the system goes into hibernation, even if the USB device is also presen after hibernation?  The cache should certainly be flushed before hibernating.

Sounds like a bug, perfect candidate for reporting, don't you think?

---

### Post by seventynine on 2007-11-12
If the sync feature is available as an 'option' it should not get in the way of anyone who wants to mount/unmount.

That option will help make ubuntu more user friendlier than what is now.

Though I still don't see the longevity arguement winning over ease of use: even just 100,000 writes = 10 writes a day * 365 days of use each year * 27 years. I can live with sync 'on' if it means that my flash drive lasts only as long as it takes a 2 yr old to grow up and have his own kids. :)

---

### Post by coolen on 2007-11-12
That's not even a two year old who's good at sports.

---

### Post by CrazyGuy123 on 2007-11-12
The point being made is that writing a file to the drve isn't the only thing that counts as a "write".  With write caching off, the file allocation table could be written 10's of times for just reading a file (last access time, thumbnail generation, search indexing, journalling etc.), and possibly thousands of times for creating a file (if it's written sequentially without pre-allocation, after each block is written the file allocation table is re-written to reflect the files new size).

That could mean the flash drive wears out after just a couple of uses if you're writing large files in small blocks.

The fact is that this problem is pretty much eliminated with wear levelling and block re-mapping - that ensures that a worn out block is moved elsewhere to a fresh block, and the wear levelling prevents blocks being overused in the first place.

---

### Post by chrisccoulson on 2007-11-12
I don't think turning on the sync option would be a substitute for properly unmounting the drive (you still have to eject the drive in Windows). Even if data has been fully written to the drive, there could still be applications with files open from that drive, and the system could be running an application from that drive. The sync option won't get around this, and for these reasons, you still shouldn't just pull the drive out of the conputer without properly unmounting it.

---

### Post by Kow on 2007-11-12
> **chrisccoulson said:**
> I don't think turning on the sync option would be a substitute for properly unmounting the drive (you still have to eject the drive in Windows). Even if data has been fully written to the drive, there could still be applications with files open from that drive, and the system could be running an application from that drive. The sync option won't get around this, and for these reasons, you still shouldn't just pull the drive out of the conputer without properly unmounting it.

Agreed, there is no way around this. Face it you need to unmount (or in Windows, eject) the usb drive before removing it. If data is written immediately then there is the possibility of filesystem/data corruption if an uneducated user removes the drive during the copy. If data to be written is cached and the user removes the drive without unmounting first = no harm to the filesystem on the drive. Whats more important... ALL of the data already on the flash drive or the data that is going to be written to the flash drive? The way I see Windows and Linux caching the data and then writing on unmount/eject is the safest (and best) method.

---

### Post by sicofante on 2007-11-13
I could see the techy-squad coming...

> **CrazyGuy123 said:**
> That could mean the flash drive wears out after just a couple of uses if you're writing large files in small blocks.
That's pure FUD, I'm afraid. I've been using my pendrives with sync on for long enough I can't remember. They're fine and dandy.

> **chrisccoulson said:**
> Even if data has been fully written to the drive, there could still be applications with files open from that drive, and the system could be running an application from that drive.
Non-techies are just non-techies, not stupid. When we used floppies, no one removed the floppy containing the file s/he was working on. The same applies to running apps from the pendrive. What we're talking about here and what 99% of ordinary people use their pendrives for is moving files around. Techies never have a problem with reconfiguring the system so it does exactly what they want so defaults are (or should be) designed for non-techies.

> **Kow said:**
> If data is written immediately then there is the possibility of filesystem/data corruption if an uneducated user removes the drive during the copy.
Again, this is going much too far, guys. There's no correlation between computer knowledge and intelligence (or vice versa: computer ignorance and stupidity).

The sync option is not the panacea, I know. When file-system-writes were designed, pendrives were non-existent. They are ubiquitous now. A dedicated design to deal with them is necessary. But this design is not coming tomorrow and sync-on is the closest thing to a solution right now.

---

### Post by chrisccoulson on 2007-11-13
> **sicofante said:**
> I could see the techy-squad coming...

Non-techies are just non-techies, not stupid. 

I made a valid point, but you're twisting my words. At what point in my post did I start mentioning 'techies' and 'non-techies'?

---

### Post by seventynine on 2007-11-13
> **sicofante said:**
> I could see the techy-squad coming...


That's pure FUD, I'm afraid. I've been using my pendrives with sync on for long enough I can't remember. They're fine and dandy.


Non-techies are just non-techies, not stupid. When we used floppies, no one removed the floppy containing the file s/he was working on. The same applies to running apps from the pendrive. What we're talking about here and what 99% of ordinary people use their pendrives for is moving files around. Techies never have a problem with reconfiguring the system so it does exactly what they want so defaults are (or should be) designed for non-techies.


Again, this is going much too far, guys. There's no correlation between computer knowledge and intelligence (or vice versa: computer ignorance and stupidity).

The sync option is not the panacea, I know. When file-system-writes were designed, pendrives were non-existent. They are ubiquitous now. A dedicated design to deal with them is necessary. But this design is not coming tomorrow and sync-on is the closest thing to a solution right now.

+1

Thank you!

---

### Post by chrisccoulson on 2007-11-13
> **seventynine said:**
> +1

Thank you!

You technical guys are brilliant at linux. But please don't assume that non-technical people are all stupid people who pull out their flash drives while its files are open or being read/written.

When did anyone in this thread suggest that they assume that non-technical people are all stupid people?

---

### Post by seventynine on 2007-11-13
> **chrisccoulson said:**
> I made a valid point, but you're twisting my words. At what point in my post did I start mentioning 'techies' and 'non-techies'?

You guys are obviously very good at linux. But why did you assume that we pull out flash drives while files are open or being read/written?

Sorry I seperated the last post into two, may seem like a double-post.

---

### Post by chrisccoulson on 2007-11-13
> **seventynine said:**
> You guys are obviously very good at linux. But why did you assume that we pull out flash drives while files are open or being read/written?

Sorry I seperated the last post into two, may seem like a double-post.

I didn't assume. I merely suggested that turning on the sync option by default is no substitute for properly unmounting a device, as applications may still have files open on that device. I didn't single out any type of user.

At work, I frequently attempt to eject my USB drive, before realising I've still got one document open from it (out of several open documents). Then it fails to eject, which prompts me to close down the open document before I remove my pen drive. I see many people do this on a day to day basis, so it *does* happen. It's easy to do when working with lots of documents from a mixture of the local hard drive, network drive or external drive.

Don't take offence.

---

### Post by adelgado on 2007-11-13
I think there's a rather simple solution, which will please most of us.

Enforcing one of the two solutions is not good; it will necessarily bother someone.

So, what we have to do is maintaining the two options. I think caching should be the default for two reasons:

a) It's the industry standard. Most (all?) operating systems work that way.
b) It's better for the device. There are debates over *how better* it is for the device, but everyone agrees it *is* indeed better.


But to easy things up for those who'd like not to have to manually eject the Drives, I think we should:

a) Ask each time a device is plugged in if the user would like to have it working on sync or on cache. Or
b) Ask the first time a device is plugged in whether the user would like to have devices working on cache or sync. Or, at least
c) Easy the process of "Mounting in sync". I'm not new to Ubuntu, but I don't know how to do this, nor that it was in fact doable.

---

### Post by chrisccoulson on 2007-11-13
I've just realized that it's already possible to get external devices to mount with the sync option by modifying a gconf key. Although it's not adjustable on a per-device basis (only a per-filesystem type basis).

Using gconf-editor, navigate to /system/storage/default_options and add sync to the filesystem type that you wish to mount with this option (which would probably be vfat for most USB devices)

---

### Post by coolen on 2007-11-13
> **sicofante said:**
> I could see the techy-squad coming...


That's pure FUD, I'm afraid. I've been using my pendrives with sync on for long enough I can't remember. They're fine and dandy.


Non-techies are just non-techies, not stupid. When we used floppies, no one removed the floppy containing the file s/he was working on. The same applies to running apps from the pendrive. What we're talking about here and what 99% of ordinary people use their pendrives for is moving files around. Techies never have a problem with reconfiguring the system so it does exactly what they want so defaults are (or should be) designed for non-techies.


Again, this is going much too far, guys. There's no correlation between computer knowledge and intelligence (or vice versa: computer ignorance and stupidity).

The sync option is not the panacea, I know. When file-system-writes were designed, pendrives were non-existent. They are ubiquitous now. A dedicated design to deal with them is necessary. But this design is not coming tomorrow and sync-on is the closest thing to a solution right now.

He never said they were stupid. What he said was they're uneducated. This doesn't mean they're unintelligent, or incapable. It just means they don't know enough about a particular subject (in this case, why it's best to unmount on all occasions).
It is possible for the system to be working on a device without it being apparent to the user. Just because your file manager isn't pointed there or you don't have any documents open fromt he device doesn't mean there's no activity going on there, and this can lead to data and filesystem corruption if you don't properly unmount the device.

I'd personally like to see something more obvious. I hate having to minimise/move a bunch of windows to do something simple. As much as I hate to say it, Windows' solution is pretty good. An icon in the notification area (although ours would be far simpler to use).

---

### Post by seventynine on 2007-11-14
> **chrisccoulson said:**
> I didn't assume. I merely suggested that turning on the sync option by default is no substitute for properly unmounting a device, as applications may still have files open on that device. I didn't single out any type of user.

At work, I frequently attempt to eject my USB drive, before realising I've still got one document open from it (out of several open documents). Then it fails to eject, which prompts me to close down the open document before I remove my pen drive. I see many people do this on a day to day basis, so it *does* happen. It's easy to do when working with lots of documents from a mixture of the local hard drive, network drive or external drive.

Don't take offence.

None taken. But I agree with sicofante those comments *did* appear that way.

Anyway, I guess what I'm trying to say is that sync as an option would be very good for Ubuntu. Not go get rid of cache, why can't both co-exist? Afterall Linux is about having a choice. You know many who benefit from cache but many people here and many people I know could benefit from sync.

---

### Post by BungaMan on 2007-11-15
+1 for an indicator showing data that still needs to be written from the buffer.

If the nautilus file copy dialog is gone, you'd expect it to be on the flash right?  If not then the user should know this somehow.

---

### Post by sicofante on 2007-11-15
> **BungaMan said:**
> +1 for an indicator showing data that still needs to be written from the buffer.

If the nautilus file copy dialog is gone, you'd expect it to be on the flash right?  If not then the user should know this somehow.
Agreed.

I suggested back in the Feisty idea pool that the light in the pendrive could be used for this purpose as well, but I understand not all drives have one and I'm not sure if it can be software-controlled, so some indicator in the taskbar is certainly a very good idea.

Also, I don't think anyone's asking to remove the asynchronous writings to USB devices, but make them synchronous by default. It would make things safer for "non-educated" users and a system for ordinary people should always assume the user is "non-educated". As a matter of fact, usability is precisely measured by how good a system deals with non-educated users.

---

### Post by coolen on 2007-11-15
As mentioned, having this enabled by default could have bad side effects.
Would it be possible to detect if a USB stick has wear levelling? The system could make an educated guess on whether the sync option's okay...

---

### Post by CrazyGuy123 on 2007-11-15
> **sicofante said:**
> 
That's pure FUD, I'm afraid. I've been using my pendrives with sync on for long enough I can't remember. They're fine and dandy.



I feel a bit offended by that.

Please read the whole of my comment before responding.  If you still don't believe me try running a FAT32 filesystem on a raw flash chip with no bad block logic - I bet it'll wear out within a month of normal use, or a few hours of running any kind of indexing onto the disk.   I have experience of that because the makers of "sumvision" MP3 players didn't bother implementing any kind of wear levelling or bad block detection, and I bought 10 of these devices and 6 have had the file allocation table block(s) fail so that all the files become lost chains every time the cache is cleared.

---

### Post by sicofante on 2007-11-15
> **CrazyGuy123 said:**
> If you still don't believe me try running a FAT32 filesystem on a raw flash chip with no bad block logic - I bet it'll wear out within a month of normal use, or a few hours of running any kind of indexing onto the disk. 
I'm sorry I didn't want to offend you. I'm just saying I'm running my pendrives with sync on and they're fine.

I can't imagine myself going into a store and asking for a pendrive "with bad block logic" in it. I just buy ordinary Kingston pendrives.

---

### Post by CrazyGuy123 on 2007-11-16
Ah - no problem.   Your case of using just a standard pen drive with sync and no problems nicely shows that it is a workable solution in the long term.

---

### Post by sicofante on 2007-11-16
Oh, now we're entering sarcasm mode. Well, too bad. :-(

My case shows that the argument of ordinary pendrives broken by supposed wear of their flash memory is just theory and the sync option can be used to minimize the risk of destroying your data when unplugging the drive right after you copy some casual files, as we all did in the floppy disk days.

(This is exhausting.)

---

### Post by Fanless_Puppy_Fan on 2007-11-17
This is how one guy handles it:

[http://greenfly.org/tips/usb_drive.html](http://greenfly.org/tips/usb_drive.html)

[I]Autofs saves the day

First, I installed autofs with apt-get install autofs. Then I modified /etc/auto.master and added an entry for my removable drive:

# $Id: auto.master,v 1.2 1997/10/06 21:52:03 hpa Exp $
# Sample auto.master file
# Format of this file:
# mountpoint map options
# For details of the format look at autofs(5).
/var/autofs/misc        /etc/auto.misc
/var/autofs/net         /etc/auto.net
/var/autofs/removable   /etc/auto.removable     --timeout=2

That last line tells autofs to mount any of the removable devices I will specify in /etc/auto.removable under /var/autofs/removable, and to umount them after 2 seconds of idling. I then created the /etc/auto.removable file:

usbdrive        -fstype=vfat,uid=1002,gid=1002,umask=002        :/dev/sda1

This file sets up a mount point which will end up being /var/autofs/removable/usbdrive, the mounting options to use, and which device to mount. Now, all of this happens outside of /etc/fstab, so I removed my entry for my usbdrive from /etc/fstab, and also removed the /mnt/usbdrive directory. I decided what I would do instead is have my hotplug script create a symlink to the autofs mountpoint when the drive is inserted, and remove the symlink when the drive is removed. That way, I will only deal with /mnt/usbdrive and not worry about any /var/autofs directories. The new and improved /etc/hotplug/usb/usb-storage is the following:

#!/bin/sh
case "$PRODUCT" in
   5e3/702/2) # FireXpress usb hard drive
   ln -s /var/autofs/removable/usbdrive /mnt/usbdrive
# set up what to do when you remove the drive
   echo -e '#!/bin/sh\nrm /mnt/usbdrive' > $REMOVER
   chmod a+x $REMOVER
   ;;
esac

Now, I can plug in my drive, and see that /mnt/usbdrive is created. After 2 seconds, autofs will umount the drive. You can monitor /var/log/syslog to watch this happening:

Jan 19 16:24:35 clover automount[14059]: mount(generic): calling mkdir_path /var/autofs/removable/usbdrive
Jan 19 16:24:35 clover automount[14059]: mount(generic): calling mount -t vfat -s -o uid=1002,gid=1002,umask=002 
/dev/sda1 /var/autofs/removable/usbdrive
Jan 19 16:24:36 clover automount[14059]: mount(generic): mounted /dev/sda1 type vfat 
on /var/autofs/removable/usbdrive
Jan 19 16:24:39 clover automount[14066]: running expiration on path 
/var/autofs/removable/usbdrive
Jan 19 16:24:39 clover automount[14066]: expired /var/autofs/removable/usbdrive 

As you can see, the drive unmounted seconds after the command finished, since it had been idling. It would now be safe to remove.

For the future, I am planning on setting up a similar system for my digital camera (which appears as a normal usb storage device as well) to not only automatically mount the camera, but also sync up any photos on it.

[/I]

I'm not expert enough to know if it works or not, but the arguments being leveled by the purists seem to lack the innovation required for continual improvement. I just want it to work as well as possible.

---

### Post by Evmax318 on 2007-11-18
Being a longtime windows user, I have grown accustomed to being able to just remove a USB device without using a unmount command. I think in the next release there should be an option to have a quick removal choice.

---

### Post by sicofante on 2007-11-18
This sounds interesting. There's one thing I don't get thou: if I understand conrrectly, the drive will unmount automatically after two seconds of idling. So if I need to write some more files shortly after I must unplug and plug back again, is that so? If it is, it seems a bit impractical.

But I strongly agree with you that this issue needs an imaginative attitude towards innovation.

---

### Post by MarCustomized on 2007-11-19
Actually, in Windows XP, it is recommended that you 'safely remove' USB devices using the icon in the notification area.

I do agree that there should be an instantaneous relocation of files to and from USB devices rather than the cache system.

---

### Post by 23meg on 2007-11-19
Threads merged.

---

### Post by Fanless_Puppy_Fan on 2007-11-19
> **sicofante said:**
> This sounds interesting. There's one thing I don't get thou: if I understand conrrectly, the drive will unmount automatically after two seconds of idling. So if I need to write some more files shortly after I must unplug and plug back again, is that so? If it is, it seems a bit impractical.

But I strongly agree with you that this issue needs an imaginative attitude towards innovation.

I'm pretty sure that autofs attempts to mount the filesystem referenced and then errors if it can't be mounted. Maybe someone more knowledgeable could chime in.

---

### Post by gsiliceo on 2007-11-28
Hey, how can i enable sync witn my pen drives? or any usb device, you guys talk about having it enabled but never tell how you did it, sorry im a noob.

---

### Post by smartboyathome on 2007-11-28
You have to mount it from the command line (I am guessing this is how they do it since I haven't done it). It would probably be pmount --sync /media/disk (you have to create that folder before you execute the command).

---

### Post by gsiliceo on 2007-11-28
cool thank you

---

### Post by smartboyathome on 2007-11-28
Let me know if this works for you! I haven't tried this out yet, but there shouldn't be any problems with it (if there are, it shouldn't mess up your drive since you are not running it as root).

---

### Post by gsiliceo on 2007-11-28
Im hesitating to do this, because of this article:
[Sync option destroys flash!]("http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html")

---

