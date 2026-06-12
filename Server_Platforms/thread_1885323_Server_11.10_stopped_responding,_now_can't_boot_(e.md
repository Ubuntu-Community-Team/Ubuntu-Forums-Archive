---
title: "Server 11.10 stopped responding, now can't boot (even recovery)"
date: 2011-11-23
forum: Server Platforms
---

### Post by bvz on 2011-11-23
Last night I kicked off a file transfer to my 11.10 server.  This morning I find that the server has fallen off the network.  I cannot get to it via ping.  I cannot even sit down at the physical console (the screen won't come on).  The fans are still running though.

So I hard-boot it.

Now it boots up to the point where it lists the daemons it is starting, and hangs on denyhosts.

Eventually I hard-boot it again.

I try to boot into recovery mode and it shows me an ascii gui that should let me continue boot, run fsck on the disks, etc...

Alas, nothing I do on the keyboard does anything.  It is as though the machine were hung up again.  If I unplug and then re-plug in the keyboard I get messages that the USB device is being mounted/added what-have-you.  But the keyboard still does not work.

It does work in GRUB when I am selecting my boot options though.

Any ideas what is going on?  Is this an issue with denyhosts?  I did temporarily turn off ufw... could denyhosts be hanging because of that?  How do I go about fixing this if I can't even get to a console?

Totally stuck.  Any clues or leads appreciated.


Edit:
I have tried booting from the CD (usb thumb drive actually) but get kind of stuck at that step.  Rescue mode from the CD appears to just be a full on installation and I am not ready to wipe out the drive just yet.  Dropping into a shell from there does not appear to let me browse my actual drive (it says to try /target but there is no /target that I can tell)

Obviously I am a little out of my element here.  Yikes.


**UPDATE 11-26-2011:**
The culprit was S.M.A.R.T. though I still cannot tell why.  Jump to posts **#6** and **#7** for more details

---

### Post by bvz on 2011-11-23
Small update...

I was able to get my keyboard to react in recovery mode, so I chose fsck.  It has been about two hours so far and all I have is the following:

```
fsck from util-linux 2.19.1
[   14.596040] Adding 2077692k swap on /dev/sda5.  Priority:-1 extents:1 across:2077692k SS
/dev/sda1: 55447/1826816 files (0.2% non-contiguous), 403279/7296512 blocks
[   17.464789] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
```

Should I be seeing more than that?

Also, I managed to disable denyhosts and it just locked up on a different daemon... which leads me to believe it is actually starting up all the daemons and just locking up on whatever comes next.

Any logs I should be looking at?

Thanks

---

### Post by bvz on 2011-11-24
Another clue in the ongoing (and lonely) saga of my server...

I downloaded and installed Ubuntu 11.10 desktop to a usb drive and booted off of that.  From there I ran fsck on what I think is my boot drive (sda1).

It returns instantly with the following:

```
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: clean, 55447/1826816 files, 403279/7296512 blocks
```

So, for some reason, fsck now appears to think everything is all fine on this partition.


fsck on the second partition (sda2) gives me the following info:

```
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
```


and fsck on the last partition (sda5) gives me the following info:

```
fsck from util-linux 2.19.1
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5
```


Are these actual errors in the disk or is this a result of the fact that I have booted from a different drive and am running fsck on partitions that I shouldn't be running it on?

---

### Post by bvz on 2011-11-24
Ok, between checking on the Turkey, I have been trying a few new things and here are the results.  I am still having difficulty making sense of them so any insights are appreciated.

I unplugged my RAID array (just unplugged the SATA cables from the drives, but left the Roswell 4-part card installed).

With this configuration, the server boots!  (of course, it complains that /dev/md0 is missing, but if I hit 's' to skip mounting it, the server boots just fine).

So, I rebooted into the recovery mode and tried fsck again.  Once again, it locks up exactly as described above.

So I rebooted into the desktop version from my USB disk and opened a terminal and tried sudo fsck /dev/sda1

All I get this time are the following:
```

ubunut@ubuntu: sudo fsck -v /dev/sda1
fsck form util-linux 2.19.1
ubunut@ubuntu: sudo fsck -v /dev/sda2
fsck form util-linux 2.19.1
ubunut@ubuntu: sudo fsck -v /dev/sda5
fsck form util-linux 2.19.1
```

Does this mean fsck is showing no errors?

I'm not sure how to put together all these clues, and I would still be appreciative of any suggestions as to what to try next.

I'll just keep posting until it is solved.

---

### Post by bvz on 2011-11-25
Since it boots whenever the individual drives in the array are unplugged, I figured I might be able to get it to start if I removed the array from fstab and the mdadm.conf file.

No dice.  Still locks up if the drives are physically plugged in.

So the next thing I tried was to not use mdadm.  I issued the command mdadm -S /dev/md0 (which may or may not be necessary) and renamed /etc/mdadm/mdadm.conf to /etc/mdadm/mdadm.conf.disabled

Still no joy.

Next I tried unplugging just the first drive in the array.  The system boots!

Same thing if I unplug just the second drive in the array.  And the third.  And the fourth.  If ANY of the drives in my array has its SATA connection pulled before booting, the system boots up correctly (this is with mdadm turned off, and the fstab having no reference to the array).

If I plug all four in, however, it just locks up again.  Weird.

Time for turkey leftovers.  Next I'll look at disabling the S.M.A.R.T. monitoring.

---

### Post by bvz on 2011-11-25
Well, that "fixed" it.  Sort of.

smartmontools was the culprit.

I disabled it by editing /etc/default/smartmontools and commenting out the line that says:

start_smartd=yes

and restarted.  The server boots up just fine.  But it does not stay up "fine".  After about 10 minutes or so it stops responding to pings, the console blanks out and nothing I can do revives it (no hitting keys, no plugging/unplugging of the keyboard, nothing).

sigh.

Update:  A couple of times it sort of dies even though the console is still showing the login screen.  No keyboard presses register, and I cannot ping the machine anymore (and it disappears from my Mac's list of servers)

---

### Post by bvz on 2011-11-26
I feel like I'm having a conversation with myself :)

This is such a specific and weird problem that it would be hard for anyone else to diagnose though...

As it happens, the locking up was occurring at exact time intervals.  At 9:45.  At 10:00.  Etc.  I only just noticed that because I would sit in front of the computer watching it to see when it locks up (you can tell because the cursor would suddenly freeze).

As it happens, these are exactly at the same time that a script (running hddtemp) was checking the hard drive temperatures on my Array.  hddtemp uses S.M.A.R.T. to get the data.

The weird part is that this script has been active for a while (at least a couple of days - the same as smartmontools) but now suddenly locks up the machine.  I can call this script manually and it will lock the server up.  Running the hddtemp command directly on the command line works though.

None of this makes any sense to me, but I am going to go ahead and mark this thread solved (for what it is worth... can't imagine it helps anyone else as it appears to be such a specific issue to my setup).

That said, I am going to continue to post here IF I figure out what went wrong with S.M.A.R.T. monitoring.

---

### Post by trundlenut on 2011-11-27
Have you tried booting the machine with only one drive at a time connected to the raid card?  It could be that you have some sort of hardware problem with one drive that is casuing the issue.

Also can you get at the SMART data from either the machine bios or raid card bios?  That may help to narrow down the problem.

---

### Post by bvz on 2011-11-29
Thanks for the suggestions (sorry for the delayed response... week started with a bang).

I have not tried it with only one drive connected but I will give it a shot.  I *did* try it with only three drives plugged in and it boots (any three drives and it boots.  All four and it doesn't).

I have uninstalled smartmontools and not had a moment to test hddtemp or re-installing them since.  I will give it a shot tomorrow though and post back here.

---

### Post by bvz on 2011-11-29
Just a quick update...

I ran my script which checks the drive temps (using hddtemp) and it is not locking up my system since I uninstalled smartmontools.

I have not yet re-installed smartmontools and tested that.  More to come.

---

### Post by bvz on 2011-12-01
Ok,

After having re-installed smartmontools everything seems to be working.  I have been unable to re-produce the circumstances that led to the machine locking up.

Running some long tests on the drives today but it is looking like I may not ever figure out exactly what happened.

---

### Post by bvz on 2011-12-04
Well, luck of lucks...  it is doing it again :(

Machine was running fine for a few days, but I have not been using it via the Mac finder.  I have only been working on it via ssh.  But everything works, and it boots up just fine.

Then I used the finder to delete about 250 Gigs of data that was on the array.  It chugged along for about 45 minutes and just when it appeared to be nearly done, gave me an error (Like an idiot I didn;t copy down the error, but I believe it was a -50)

At the same time, I noticed the server was locked up again.

Now I have the exact same symptoms as before.

I can boot if I have any number of drives attached to the array (other than if they are all attached.  I.e. I can have one drive - any drive - attached or I can have any three attached, etc...)

My roswell 4-port fake raid card (which I am just using as 4 ports, not as a raid controller) does not allow me to get much info.  Booting with just a single drive (I have tried all four) does not cause any issues (other than the RAID not mounting of course)

If I turn off smartd, the system boots just fine.  But then my script which runs hddtemp will kick in via cron and the computer will lock up within a few moments.

I hope people don't mind, but I am going to start a new thread with this since it has drifted so far from the original post that I think most folks won't bother (and should not have to) read this far.

The thread is here:
[http://ubuntuforums.org/showthread.php?p=11512635#post11512635](http://ubuntuforums.org/showthread.php?p=11512635#post11512635)

---

### Post by Jive Turkey on 2011-12-05
I'm guessing you have a hardware problem that manifests when your HDDs need more power or get busy.  PSUs can fade before they fail completely.  I'd be willing to bet that your problem will go away if you put in a bigger better PSU.

problem may be your raid card too.

---

### Post by bvz on 2011-12-05
Thanks for the suggestions.

I'll check the raid card and power supply (though the power supply is brand spankin new and should be far more than adequate).

At this point I am starting to suspect the raid card because it only locks up when I access the smart data, and it locks up regardless of which drive I access (though not every time)...

I have turned off smartmontools and am currently half way through copying 550 Gigs of data via netatalk.  It is excruciatingly slow, and the raid seems to be resyncing for some reason, but at least it is not locking up...

---

