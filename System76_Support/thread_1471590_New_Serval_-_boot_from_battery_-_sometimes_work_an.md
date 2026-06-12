---
title: "New Serval - boot from battery - sometimes work and sometimes not"
date: 2010-05-03
forum: System76 Support
---

### Post by reid_rsv869 on 2010-05-03
Hello group -

Anyone ever have trouble booting from battery?  At least 50% of the time the boot process stops at a check of battery status.  If I reboot usually the machine comes up without issue. 

Not sure if it's waiting for battery status info that's not quick enough, or if something else is occurring.  

Thoughts?

Reid

---

### Post by isantop on 2010-05-04
Make sure that the battery is fully inserted in the area under the computer. Also, check both latches and make sure they are both locked.

If that doesn't work, you can drop me an email at support *at* system76 *dot* com.

---

### Post by thomasaaron on 2010-05-05
Hi, Reid.

That's definitely not a problem we're seeing across the board. Could you please post the exact message you're seeing.

Also, did you encrypt your home partition?

---

### Post by reid_rsv869 on 2010-05-05
I've took a quick photo of the screen with my Crackberry when it hangs and have attached that .jpg file.  

Yes I do have an encrypted /home space, for now.  I'm going to do a fresh install this evening. I like that security but if it's going to be a heart-ache then maybe I won't.  Suggestions?

The battery is installed as it arrived from the factory. I haven't yet re-seated it.

---

### Post by reid_rsv869 on 2010-05-05
Also, just FYI, this is now occurring with the cord connected and without (on battery).

---

### Post by thomasaaron on 2010-05-06
Yeah, I think the battery line is just a red herring.

A few lines above it, it mentions starting cryptswap.

When you create an encrypted home partition, there is a bug that may create a second swap line in your fstab file. It's easy enough to fix. To find out if that's your issue, please post the output of...

> cat /etc/fstab

---

### Post by reid_rsv869 on 2010-05-09
Glad to say that doing a fresh install of 10.4 w/out the encrypted /home space fixed this problem.  

thanks

Reid

---

### Post by wrender on 2010-05-11
I actually have been getting this problem once and a while randomly on my serp 5 with lucid.

It appears to hault at checking battery state once and a while. If I unplug the laptop from the ac power and reboot it will boot fine. I don't have an encrypted drive or home dir.

I am running lucid kubuntu.

---

### Post by isantop on 2010-05-11
Hi wrender,

Did you perform a fresh install of Lucid on your serval, or did you upgrade from 9.10. If you upgraded from 9.10, did you get to that from 9.04?

Sometimes, a bug in the upgrade process can throw weird errors at you.

---

### Post by wrender on 2010-05-11
I did a fresh install of 10.04 Kubuntu 64bit... 

It did not happen in 9.10.

---

### Post by wrender on 2010-05-12
Like I said... when it happens I unplug the ac and reboot works fine.


Not sure if it relates... but it does not recognize if the AC is plugged in. It will charge just fine and even says charging. Would be sweet to figure that one out though!O:)

---

### Post by isantop on 2010-05-12
Okay.

Go ahead and post me the output of:```
cat /etc/fstab 
```

We'll see if you have any weird problems in there.

---

### Post by wrender on 2010-05-12
Here is the output from 

> cat /etc/fstab



> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4b32723d-4446-42fb-a0b0-8d51803c73d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9abe3633-c63b-401b-9a74-f919a1f16471 none            swap    sw              0       0

---

### Post by wrender on 2010-05-14
Does that add any insight?

---

### Post by thomasaaron on 2010-05-17
Hi, Wrender.

Could you please give me a call at System76 at your convenience. Extension 603.

---

### Post by wrender on 2010-05-17
Sure thing... when is a good time during the day? (translated to canada eastern time lol)

---

### Post by thomasaaron on 2010-05-18
We're here 8:00am-4:30pm mountain time. I think that's about 10:00am-6:30pm in your neck of the woods.

---

### Post by thomasaaron on 2010-05-18
Hi, Wrender.

Sorry, I missed your call. I was on the phone with another customer. 

I just called the number you left on the message, and somebody picked up that couldn't figure out who I was asking for. 

I looked at the caller ID, and couldn't find a number starting with the area code you left.

I think we need a re-do. Sorry.

Best,
Tom

---

### Post by wrender on 2010-05-19
lol... no worries. I'll give another try tomorrow in the afternoon again. ;)

---

### Post by thomasaaron on 2010-05-19
reid_rsv869, wrender is using Kubuntu. Are you?

---

### Post by reid_rsv869 on 2010-05-31
Nope, I was using 10.4 gnome, generic

Thx

Reid

---

### Post by wrender on 2010-06-04
I have been busy with life lately... but I did try out the new 

Maverick Alpha 1 Released Kubuntu 64 bit live disc and it booted up fine and recognized the ac power being plugged in and out! :KS

So there is something definitely wrong with Lucid... 

Anyways back to dealing with life...

I hope this will lead to a solution! :)

---

