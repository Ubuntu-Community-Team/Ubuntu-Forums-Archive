---
title: "Corrupted .TRASH causes crashes, REFUSES to delete files!"
date: 2010-12-16
forum: Security
---

### Post by WinRiddance on 2010-12-16
I hope that I'm posting this thread in the right place. This involves a very unique problem which has caused the .Trash-1000 folder for my external USB drive to become corrupted, to the point of causing massive heat problems which then causes my system to crash, i.e. become completely inoperable, forcing me to do a hard reset.

[COLOR=DarkRed]**The scenario:**[/COLOR]  Recently I went through all of my backup data which is what I use that external USB drive for. After finding several GB of data files, some dating back 2 - 3 years from a root server that I used to have, I went ahead and tried to delete all of those files. Well, with exception to 3 folders, containing no more than perhaps 35 files _which totalled less than 8 MB in space,_ everything was deleted properly without a hitch. The files that couldn't be deleted prompted some strange "couldn't delete blahblahblah file due to input/output error" message. One message for each file that couldn't be deleted.

Now mind you, I can open these files, look at them, rename them, copy them, but I cannot delete them. Still being pretty wet as far as Linux is concerned, I tried numerous suggestions that I could find on the internet, all of which had to do with file permissions in one form or another. I've tried everything that made any sense and still can't delete those files.

All of the data is my own, all of the hardware is mine, and I'm the only one using this machine. I'm not attempting to do anything illegal.

Then I figured, smart as I am, why don't I just assign ownership of the .Trash folder to myself via the chown -R command, followed by deleting the files afterwards. Okay, the chown command gave me no error, I assumed all was well since it's my USB drive to begin with and since it automounts during every restart anyway. I just figured that this would be something to try. **BIG MISTAKE** !!!

My system runs just as perfectly as before, with but one exception. NOW, when I attempt to delete those files that I couldn't delete before, _I don't get an error message anymore_ but the CPU starts hyperventilating during the deletion process which goes on endlessly (remember, we're taking about less than 8 MB of data) ... ultimately causing the system to crash, i.e. become totally unresponsive. NOW, if I delete additional files from that USB drive and then attempt to empty the trash, the newly deleted files take substantially longer too now. Not as long as the original "bad files" but still quite long. The drive itself checks out fine and it's not a dual-boot system with Windows. Just did a virus check recently too and everything checks out in that regard as well.

**Can someone tell me how to reassign whatever original values there were** for that external drive .Trash folder? I think if I could restore those values to whatever they used to be before I used the chown -R command, perhaps then everything would be fine again as far as the crashing is concerned. HELP ....
(Please take a look at the screenshots too)

The last screenshots shows "preparing to delete" which takes a very long time. Then it takes anywhere from 15 to 45 seconds PER FILE before that miniscule file is actually supposedly deleted. Eventually, after a few files are deleted, the system crashes. I wrote "supposedly deleted" because after a reboot the files are still there ....

.

---

### Post by bodhi.zazen on 2010-12-16
> **WinRiddance said:**
> .

The .Trash in your home directory should be owned by your user.

Honestly, it could well be a bad disk =)

I would copy any data off the flash drive you wish to keep, reformat the disk, and restore the data.

If you wish, you can overwrite the disk with zeros first (using dd).

```
dd if=/dev/zero of=/dev/sdb bs=1M
```

Just make sure you specify the correct device in "dev/sdb"

---

### Post by WinRiddance on 2010-12-17
Thank you. I just had the disk thoroughly checked less than 2 weeks ago and it checks out absolutely fine. This problem is two-fold, of which I can ignore the first part with those weird files not letting themselves be deleted. But I'd think that the other problem, the one that just began when I used ... [COLOR=Navy]sudo chown -R winriddance:winriddance /media/Volume/.Trash-000[/COLOR] ... would be something that I can reverse again, no? I think that if I could just reverse whatever impact that command had on my existing USB backup drive, then everything would be okay. When I intially used that command my thinking was that if I owned the drive anyway then the command, if used for no reason, would result in accomplishing nothing at all (worst case) ... as opposed to generating a problem.

At least it would help save a ton of time over having to back up everything on that disk (about 180 GB of data), followed by copying it all back over once the disk has been cleaned.

---

### Post by CharlesA on 2010-12-17
What file system is /media/Volume ?

---

### Post by WinRiddance on 2010-12-17
**NTFS** ... because that way I can share personal files with Windows users like my Mom. ;)

---

### Post by CharlesA on 2010-12-17
> **WinRiddance said:**
> **NTFS** ... because that way I can share personal files with Windows users like my Mom. ;)
Ok. chown and chmod don't work on NTFS.

Try this:

```
gksu nautilus
```

Browse to the .Trash folder on the NTFS drive and delete it.

---

### Post by WinRiddance on 2010-12-17
Hi again. If you look at the third screenshot of my original post you'll see that that's another thing that I already tried ... opening Nautilus as root and then deleting that whole darn .Trash-0000 folder. Just tried it again with the same result.

This is really nuts. As I mentioned before, **I can use, copy, and rename those files** ... privileges already belong to me, but I can't for whatever weird reason delete them. All of the files in question came off my Linux (Debian) root server from a couple of years ago. All of them belonged to a specific internet domain that I had some custom modifications performed on ... something to the effect of allowing a person to register into a free account with a bunch of different graphical user options (personal homepage, calendar, notebook, photo album, greeting cards, games, etc.) ... which was a process that actually worked similar to a c-panel. My custom panel had two functions, one for the admin to assign individual users, and the second function for those users to enjoy their account with all of the graphical toys that was made available to them. I say that it worked similar to c-panel since it was my own custom design, but more specifically for people who knew nothing about computers or websites ... everything worked strictly via point and click.

All of the files that can't be deleted _came from those custom functions_ that I had installed on that particular domain. They got onto my hard disk via FTP since everything that we had running on the server was also backed up onto my personal hard disk. The prudent thing to do, just in case that server ever develops serious issues for whatever reason ....

I had several domains with various different functions and all of them were backed up on my personal system. _But it's only those particular custom files from that one specific domain_ that I can't seem to get rid of when I try to delete them.

---

### Post by CharlesA on 2010-12-17
That's crazy.

Does it let you delete the files if you plug it into a Windows box?

---

### Post by WinRiddance on 2010-12-17
Yeah, I know, this is definitely one of the weirdest things that I've ever dealt with.
I do have an old WinXP Pro box flying around ... but it won't let me access the drive at all.
There's only one user set up on the Windows box - ME - but I get "error accessing the drive permission denied" messages when I want to open it up. Don't know why, but I don't have time to goof around with that Windows machine right now.

There's some kind of setting, and I don't even think that it has anything to do with ownership anymore, which prevents me from deleting only those particular files. I'm beginning to think that when I had that custom work done on the server, perhaps the programmer who hard coded those extra administrative features with options for me inadvertently added something to the hard code that is causing this. A virus would come to mind but that's not it, since nothing else is impacted by those files. The server was a Linux Debian server though, and Ubuntu is also based on Linux Debian. Somehow my system is "recognizing" those few particular files as something that inherently belongs to the inner workings of Linux, hence won't permit me to delete those files, even when I'm using root access. Yup, it's crazy alright ....

**Here's something even crazier** ... didn't notice that until now when I physically went to inspect the contents of the .Trash-0000 folder again. Somewhere along the line, yesterday as I was going through several different times of trying to delete those files (I'm assuming this) while waiting on this endless process to complete before the system would crash ... **those files were duplicated!** No kidding, now those files still exist, but with additional duplicates of the same original folders/contents within the original .Trash-0000 folder. It looks, at least to me, almost like that trash bin is trying to read two different sets of deleted files which would obviously be impossible. But that too, might somehow explain this really weird phenomena that's been going on with those files ... ???

---

### Post by CharlesA on 2010-12-17
I'd probably just copy the data I want to keep off the drive and format it.

Something is definitely messed up.

Just the the heck of it, what does this return?

```
ls -lad /media/Volume/.Trash*
```

EDIT: I noticed that you were getting an input/output error in the OP. That's probably the problem - the OS can't read from that area of the drive.

---

### Post by WinRiddance on 2010-12-17
This is what I got back:

```
drwx------ 1 winriddance winriddance 0 2010-12-17 14:03 /media/Volume/.Trash-1000
```Just did that. The time is off by 30 minutes though for whatever reason ...
I believe you're right. One of these days I'll have to do the ugly bit of saving, moving, and later recovering all of that data again, in between which I'll be reformatting that drive. Thanks for all of your time. I'm not going to mark this as solved since no actual resolution has been found to the initial problem (aside from formatting the disk).

---

### Post by CharlesA on 2010-12-17
With those permissions, you should be able to delete the folder.

You could also run badblocks on the drive, to see if it finds any areas that it can't read.

---

### Post by WinRiddance on 2010-12-17
Alright, I never heard of "badblocks" before but after doing some extensive checking realize at least a few points about it.

1. Must be run from the terminal (no problem)
2. Should be used on an unmounted disk (no problem)
3. Can't find anything about NTFS file systems ... Problem ???
4. Can't find anything about ext4 file systems ... Problem ???
5. Wondering if the following would be the correct command for me ... ???

```
# fsck -vc /dev/sdb1
```6. Or should I use something else since fsck is strictly for linux file systems, while that disk is NTFS ... ???

**Something like this perhaps?**  badblocks -nvs /dev/hda
(however, running sudo fdisk -l doesn't give ma an "HDA" to use)
Oh, the love and joy of getting used to Linux ... ;)  ;)  ;)

---

### Post by CharlesA on 2010-12-17
I've used badblocks on an NTFS drive no problem.

All physical drives are listed as sda, sdb, sdc with newer versions of Linux.

---

### Post by WinRiddance on 2010-12-17
Okay, well, umh, badblocks didn't work for me. I unmounted the disk first.
When I tried this:  winriddance@winriddance-laptop:~$ sudo e2fsck -c -c -k -C 0 /dev/sdb1

I received this as a response:

> 
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>The above command was explained in another forum, step by step, like this:

> The filesystem should not be mounted while this takes place, so if it  is needed for your normal running system you will need to run e2fsck while booted from a "live CD" or similar.  The -c option is what causes the surface scan to be added to what the checker does, then second -c makes it do a non-destructive write+read test, -k tells it to keep any existing list of badblocks instead of retesting them and -C 0 just makes e2fsck output more progress information as it does its work. See man e2fsck for more detail.
This was in answer to another Ubuntu user with an NTFS partition question.
In another forum someone mentioned that NTFS partitions require different parameters since fsck is (supposedly) strictly for Linux ext2, ext3 and ext4 partitions. I'm also wondering if it makes a difference that this is not a regular hard disk, but instead an external USB drive ???

On yet another source that I found via google one more individual mentioned that e2fsck can't be used on an NTFS partition.

Aside from that there appear to be tons of answers from dates between 2001 and 2006, all of which put me off a little since hard disk technology has gone through quite some changes in the past 5 years, in particular as far as USB volumes are concerned. I did not try the **e2fsck -b 8193** option since I'm not certain how that might (or might not) impact any existing data on that USB disk?

---

### Post by CharlesA on 2010-12-17
fsck doesn't work on NTFS partitions. You'd probably have better luck running chkdisk on it from a Windows box.

The syntax I use with badblocks is this:

```
sudo badblocks -nv /dev/sdX
```

---

### Post by WinRiddance on 2010-12-17
Great, that did the trick. Thanks.
It's testing now. I'll report the results here later ... possibly much later ... ;)

Alright, it's finished now, got done in the middle of the night and took at least 10 hours for that 250 GB drive. Here's the output from the terminal, including the original command that I used (thanks again for that).

> winriddance@winriddance-laptop:~$ sudo badblocks -nv /dev/sdb1
Checking for bad blocks in non-destructive read-write mode
From block 0 to 244196000
Testing with random pattern: Pass completed, 0 bad blocks found.
winriddance@winriddance-laptop:~$ 

So we know the drive is absolutely fine, but the garbage bin/permissions oddity still remains.

---

### Post by ellaivarios on 2011-07-16
Hi, I have a similar problem, after trying to copy a huge file on a 10GB usb stick, the trash folder contains files with really weird jarbled up filenames. Every time I detelete these, they reappear. and reappear and reappear! The folder .Trash-1000 contains infinite copies of itself, again and again and again!

I tried:
[HTML]rm -rf * [/HTML]

but to no avail.
I formatted the drive, but it is still acting wonky, same behavior!!

I checked it for errors and IT APPEARS PERFECT!

so weird!

seems we are in the bucket together on this one, even if you experienced this so long ago!

---

### Post by CharlesA on 2011-07-16
Replace the drive if a format didn't get rid of the problem.

---

### Post by cariboo on 2011-07-16
I agree with CharlesA, I've seen the same thing on a usb thumb drive, a format usually cures the problem.

---

