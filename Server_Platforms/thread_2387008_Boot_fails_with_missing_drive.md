---
title: "Boot fails with missing drive"
date: 2018-03-13
forum: Server Platforms
---

### Post by MickSulley on 2018-03-13
Running Ubuntu Server 17.10
I have installed an additional drive and I would like the system to boot even if this additional drive is not available.
Research tells me that adding the option 'nofail' would achieve this, but it does not.  If the disk is present it boots fine, however if it is not present it does not boot.  If I connect a terminal to it I see it goes to 'Emergency Mode'
The line I have added to fstab is -

UUID=efe620b1-8004-4fee-865b-956a12dca293       /common ext4    defaults,nofail 0       2

How can I get it to boot even if the disk is not present?
Thanks
Mick

---

### Post by howefield on 2018-03-13
Thread moved to the "*Server Platforms*" forum.

---

### Post by LHammonds on 2018-03-13
If you only have 2 physical drives and you want the system to boot even if one drive fails, that sounds like you are wanting a RAID 1 (mirroring) setup.

If the drives are different sizes, you will get a mirror that is the size of the smallest drive.

The next thing to figure out would be the implementation as hardware RAID or software RAID.  If you have a hardware RAID controller, you will get better performance using it (assuming it isn't FAKE RAID which relies on the system CPU).  However, software RAID is independent from the hardware can be moved to another machine.  Hardware RAID typically requires using the same or identical controller if moving machines or the controller fails.

LHammonds

---

### Post by MickSulley on 2018-03-14
No I do not want a RAID.  I actually have 3 disks, system on one and different storage on the other two.  

I discovered this issue when I had a problem with the system, removed 1 drive and then couldn't boot.  It seems ridiculous that a storage disk failure causes the system not to boot, and to fix it you have to edit fstab, but to do that you have to boot the system.  Yes I know there are ways to get around it, using a live DVD to boot and edit fstab for example, but it just feels that there should be an easier way.

Also what is the function of the nofail option? As far as I can see it does nothing at all.

---

### Post by darkod on 2018-03-15
From what I read nofail does not do what you expect. There was another option called nobootwait but I also read somewhere that it's discontinued since 16.04. I'm not aware if there is similar replacement...

---

### Post by MickSulley on 2018-03-15
Is this a bug then?  It seems ridiculous that on a multi drive system if any drive fails then the system will not boot even though it is a usable system apart from that one drive.

Does nofail do anything at all?  It doesn't seem to.

Anyone know if this applies to Debian as well or is it just an Ubuntu problem?  I could change to Debian server if that will fix it, but I don't want to go through the exercise if it will have the same issue.

---

### Post by darkod on 2018-03-15
Actually searching the manpage of systemd.mount it does confirm nobootwait is removed but it does say nofail should continue the boot if disk that doesn't contain /usr or /var is missing.

---

### Post by springshades on 2018-03-15
Hi Mick,

I'd like to suggest a bit of a hack workaround that has worked for me.

1. Stop the drive from mounting automatically in fstab.

You'll want to use the "noauto" option. Since this is different than what "defaults" does, you'll probably want to explicitly put in all of the fstab options instead.

2. Mount the drive manually after booting.

You can do this by adding a line in /etc/rc.local which runs after everything else. I think that just "mount /common" should work in your case. It's been a while since I've set this up, but that should pull all of your fstab options in automatically.

3. (Maybe) It's possible that you would need to enable the rc-local service by "systemctl enable rc-local", but in 16.04 that seems to be enabled by default.


Since the drive isn't mounted until the end of the boot process, the worst you should get is an error message when you boot.


About the "nofail" thing. My experience (if I'm remembering correctly) was that it wouldn't actually stop the boot process with an error. Instead, it would ask you to manually say whether you wanted to continue the boot even though the drive failed to mount. That's fine if you're sitting in front of a machine, but for a headless server it essentially means you can never boot or reboot remotely. Really stupid behavior.

---

### Post by MickSulley on 2018-03-15
Sorry - this is wrong- I was looking at the wrong drive in error - Doohhh!
Retested and your solution works!  Thankyou

Thanks for the reply, it looked like a good workaround, however.....  It now seems that noauto doesn't work either, unless I have done something stupid.  My fstab line is -
UUID=efe620b1-8004-4fee-865b-956a12dca293       /common ext4    defaults,noauto 0       2
If I unplug the disk boot fails again and goes to Emergency Mode.

Have I missed something here.

---

### Post by LHammonds on 2018-03-16
Ah, I misunderstood.  I thought you were wanting the ability to boot if the main boot drive was missing.

Why have the entries in fstab at all?

Just have the delayed mount command specifically mount the drive.

---

### Post by springshades on 2018-03-16
Hey,

There is always a chance that there is something else going on, but my guess is that the issue is that "defaults" isn't a single option. It's basically an alias for a list of options, and one of those options is "auto" (the opposite of "noauto"). Perhaps instead of using the options "defaults,noauto", you could try instead "rw,suid,dev,exec,noauto,nouser,async". All that I've done is put in all the options that defaults stands for but replaced auto with noauto. That's what I meant when I was saying you might have to explicitly put in all of the options that defaults stands for in my previous post.

I had to do something similar for a large software raid array where sometimes one or two of the disks wouldn't spin up in time to mount during boot.

It also may not hurt anything to put in the nobootwait option in addition to the rest. If it's deprecated, fstab will probably just ignore it. If it works, it doesn't confilict with any of the default options as far as I know.


@LHammonds

Perfectly fine solution. I can say that my reasoning behind doing it this way was so that if someone else needed to know what was going on (or in particular, if I needed to remember what I did a year or two later), the first place that I would check would be fstab. This way you don't need to remember a fairly non-intuitive "mount" command just in case something goes wrong later.

---

### Post by MickSulley on 2018-03-16
> Just have the delayed mount command specifically mount the drive.

That may be a better solution, but can you explain what it is please?  I have searched for it and not found it

---

### Post by springshades on 2018-03-16
Not sure if I've understood your edit correctly. If so and the solution is working, then you're currently doing this the "best way". It will be much nicer when something goes wrong or you do an upgrade in a year or two.

However, if it's not working, the solution that LHammonds is talking about is to delete the line from your fstab file and replace the very simple "mount /common" in your rc.local file with something more explicit. For example:

mount -t ext4 UUID="stuff" /common

The only reason why the simple mount command works is that it looks in your fstab file and uses the options that you put in there.

---

### Post by MickSulley on 2018-03-16
OK.
Thanks for the contributions.  To sum up I consider the problem fixed and if anyone is interested this is what I have done.

Create a /common directory to mount my additional drive -
edit /etc/fstab and add

# Additional drive for the /common directory - this will be accessible to all
UUID=efe620b1-8004-4fee-865b-956a12dca293	/common	ext4	defaults,noauto	0	2
# the noauto option means it will not mount at boot

Create /etc/rc.local (does not  exist in Ubuntu 17.10) containing -
#!/bin/sh -e
mount -t ext4 UUID=efe620b1-8004-4fee-865b-956a12dca293 /common

That will mount the drive if it is accessible.

Then run
sudo systemctl enable rc-local.service
reboot
The system will then boot, and mount /common if the disk is accessible, otherwise it will boot without it.  
Create /share within /common and do not have any files directly in /common.  That way if it does not mount you won't be creating stuff in /common on the system disk

---

