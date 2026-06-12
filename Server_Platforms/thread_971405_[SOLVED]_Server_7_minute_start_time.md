---
title: "[SOLVED] Server 7 minute start time"
date: 2008-11-04
forum: Server Platforms
---

### Post by cmittle on 2008-11-04
Just a couple of days ago my boot time was <30 seconds on my server.  In the last couple of days it has increased by an incredible amount.  I've attached a before and after bootchart for your review.  Does anyone have a suggestion as to what I can do to repair this new issue?

[Before:]("http://i16.photobucket.com/albums/b6/promiscuousman/hardy-20081102-6.png")
[IMG]http://i16.photobucket.com/albums/b6/promiscuousman/hardy-20081102-6.png[/IMG]
[After:]("http://i16.photobucket.com/albums/b6/promiscuousman/hardy-20081104-3.png")
[IMG]http://i16.photobucket.com/albums/b6/promiscuousman/hardy-20081104-3.png[/IMG]

Thanks,
Cory

---

### Post by cariboo on 2008-11-05
Could please post your pictures as attachments, the pics are pretty useless as they are. You have to be in the Advanced Editor to be able to do this. See Screenshot.

---

### Post by cmittle on 2008-11-05
I thought they would blow up.  I think I've attached them to this post...

thanks


cory

---

### Post by cmittle on 2008-11-05
It seems that it hangs up in a proccess called vol id at least three times for very long periods.  What is this process exactly, and how can I determine the cause of this problem?

Cory

---

### Post by cmittle on 2008-11-05
After looking at the /var/log/dmesg I see several instances of comments similar to what was said [here]("http://ubuntuforums.org/showthread.php?t=969236&highlight=ata1.00"):

```
[xxx.xxxxxxx] ata1.00: status: { DRDY ERR }
[xxx.xxxxxxx] ata1.00: error: { UNC }
[xxx.xxxxxxx] ata1.00: exception emask 0x0 SAct 0x0 SErr 0x0 action 0X0
[xxx.xxxxxxx] ata1.00: BMDMA stat 0x25
[xxx.xxxxxxx] ata1.00:cmd XXXXXXXXXXXXXXXXXXXXXXXX
```

Since this is labeled ata I assume it has something to do with the above mentioned vol id process shown in the above bootchart.  

Can someone please give me some suggestions to repair this issue?

Cory

---

### Post by lykwydchykyn on 2008-11-05
Assuming you've changed nothing (no kernel updates, e.g.) since the problem started, this is likely a problem with the disk or some filesystem corruption.

DRDY ERR means "dataready error"
UNC means "uncorrectable"
cmd would be whatever command code was tried and failed (might be worth googling on that to find out what was failing, though I don't know what information you'd get).

I would recommend the following course of action:
 - Take the system down
 - boot to a liveCD
 - run an fsck on each of the partitions
 - run badblocks -v on the drive
 - Post back here if you get any interesting output from either of those.

---

### Post by cmittle on 2008-11-05
Thank you for you advice.  I am accessing my home server through ssh right now and I just realized that my 200gig backup disk did not even mount, and my boot disk is mounted as read-only.  I am going to run to the store and pickup a new IDE cable and replace that when I get home.  I will probably fsck the disks (if it doesn't do it for me), and possibly run badblocks -v as well.  

Is there a safe way to shutdown my server with the disk mounted as read only, or am I going to have to hold the power button to shut it down:|?

---

### Post by lykwydchykyn on 2008-11-05
```

shutdown -h now

```
should do the trick.  

Alternately, you can hold down alt-sysreq and type R S E I U B
That is the "safe" method to reboot if the CLI won't respond.

Though if it's mounted read-only, it shouldn't hurt anything to hard-shutdown.

---

### Post by cmittle on 2008-11-05
> **lykwydchykyn said:**
> ```

shutdown -h now

```
should do the trick.  

Alternately, you can hold down alt-sysreq and type R S E I U B
That is the "safe" method to reboot if the CLI won't respond.

Though if it's mounted read-only, it shouldn't hurt anything to hard-shutdown.

I usually do sudo shutdown -h now, but it replys that there is some in/out error because it's read only.  I'm not familiar with that other thing you said.  I just hold alt and the windows button then type rseiub?

---

### Post by lykwydchykyn on 2008-11-05
No, alt-sysreq.  sometimes it's labelled SysRq, it's usually on the same key with printscreen.  

read-only shouldn't cause I/O errors.  That's not a good sign.

---

### Post by cmittle on 2008-11-06
Last night I plugged in the new IDE cable and rebooted.  This did not solve the problem.  I tried to boot to CD and it worked, but when I chose try ubuntu without installing anything it started to load but I eventually just got output on the screen similar to that posted above DRDY ERR blah blah...I thought I would wait it out and see if I could run fsck but it never came out of it (~8 minutes).

I finally unplugged the "extra" hard disk, and booted to cd with only the disk with the OS plugged in and the boot to cd worked.  I then chose to reboot to hard disk and this worked no problem.  I can now write to the hard drive too.

Basically what I determined was that my second hard drive was causing all of these problems and would not even let my computer boot to cd if it was plugged in.  This was also causing my main hard drive to mount as read-only for some reason.

thank you for your help, my boot time is back down to 27 seconds.

---

### Post by m_duck on 2008-11-06
I'm not sure if it is related but I had a similar thing with my PC. Was the "extra" hard disk attached to a different disk controller? Only reason I ask is that my computer either won't boot / takes ages to boot if I have my secondary (built in) SATA controller activated and a disk plugged in. From looking around this is due to poor driver support of said SATA controller, just wondering if this may be true in your case too if you were wanting to get the extra disk working? (Though I wouldn't be able to help due to my lack of knowledge, but just to get you started if you were interested).

---

### Post by cmittle on 2008-11-06
No my extra disk was installed plugged into the second plug on the end of the IDE cable.  It has been like that for a long time (~3months), it just seems to have failed in the last few days.  When I was trying to boot whether to disk (other disk that operating system was installed on) or to cd this drive was making noise.  It was not severe noise but it sounded like it kept trying to start but couldn't, very periodic.  

On a side note I was recently trying to setup a backup with sbackup and it seemed to freeze up everytime time.  I had configured sbackup to write the backup files to this hard disk.  I believe this indicates that this disk has been having some troubles for at least the last week or two.  At least it was this disk that failed and not the other one:) (knock on wood)

On the plus side I know have a cool paperweight, and know what the inside of a hard disk looks like:)

---

