---
title: "Make my encrypted Ubuntu secure"
date: 2008-03-10
forum: Security Discussions
---

### Post by jbrown96 on 2008-03-10
I want total security of my data, so that no one could have access to it. I have Ubuntu installed from the Alternate disc and chose to encrypt the entire drive. I have a very strong password (over 30 characters of random nonsense), but I'm concerned that's not enough.
I'm sure many of you have read that there are at least five ways (that's all I can think of now) to break into the computer: brute-force/algebraic attacks, over-the-shoulder snooping (watching me type the password), hidden keylogger hardware, keylogger software on unencrypted /boot partition, and stealing the keys from RAM.
I would say the first one is basically impossible, unless some type of fictional quantum computer was used. The second is also very unlikely because I type probably 6-7 characters per second that it would be impossible to memorize or record it, without being very obvious. 
I'm not worried about those because they are out of my control. 
The hardware keylogger would be very difficult to detect, unless I took the computer apart everytime I used it, so that's basically beyond my control, too.

The last two are what trouble me. 
I think that I could create a md5sum to verify that /boot had not been tampered with, but I don't know how to do it. Could someone help me? It's also important that this md5sum could be verified before typing the password, but also keep it hidden from anyone that would be tampering with the partition. 

I have read a few stories about how encryption keys are stored in plaintext in RAM and could be retrieved (although, with some special equipment and expertise). I like using suspend on my laptop, but I wish I could erase the keys when I suspend it. Is there anyway to erase on suspend and prompt for the password on resume? I'm not totally sure how suspend works, but I thought it saves all the information to RAM and puts it in a low power state. If that is the case; the keys should be able to be overwritten, command loaded to re-mount hard drive on resume, computer goes to sleep, resumes, asks for password, mounts hard drive, and computer is ready to use.

Thoughts?

---

### Post by kidders on 2008-03-11
Hi there,

There are a few obvious things worth mentioning first, before worrying about keyloggers/etc.
[LIST]
[*]**Encrypted swap** - I'm sure you've already done this, but in the event you haven't, there's very little point in spending time thinking about more elaborate routes into your data before the basics are sorted out.
[*]**Recovering data from RAM** - I may be wrong, but afaik most methods for recovering encryption keys from RAM after a computer has been powered off involve super-cooling it. How desperate are people likely to be to gain access to your laptop?
[*]**Suspending your machine** - If your concern for your data really extends as far as your post suggests, there is no safe way to suspend your computer. Doing so makes it at least theoretically possible that your laptop may be stolen while it's still powered ... While it's on, the security measures you've mentioned offer absolutely no protection.[/LIST]
Anyhow, invasion of critical system files (including those involved in the boot procedure) is a very real concern in a variety of circumstances. You might, for instance, be interested in what Linux server admins do to protect themselves against malicious modification of initial ramdisks, or critical tools like "echo" or "[".

As you suggest, checksums are the way to go. The biggest difference between you and a server administrator in that respect is that you probably won't have easy access to a network of other trusted machines from which to verify them. You'd need to store your checksumming information on a USB key/CD/etc, I'd say. Another possibility might be to store your entire boot partition on an external device that never leaves your pocket. That way, your files and the means by which you access them are entirely separate.

---

### Post by handydan918 on 2008-03-11
IIRC, the RAm hack is easy to prevent. Just don't suspend. Shut down all the way and wait 30 minutes....

---

### Post by hyper_ch on 2008-03-12
as far as I see the cooling-ram issue is that it can happen only while the computer is still running... after a few minutes with no power the key will be gone from ram...

This would mean, in order for that attack to be successfull, that the people will know that the computer is completely encrypted... if they shut it down and reboot it later they'll be out of luck... so it's not really a big issue with this I think.

By selecting full encryption in the guided partitioner the swap is automatically encrypted ;)

regarding the boot issue, you could even setup the boot partition itself on a usb key... so no booting without it... hence no messing...

---

### Post by jbrown96 on 2008-03-12
Thanks for the responses.



I found a site [http://groups.google.com/group/linux.debian.security/browse_thread/thread/32a97040215cc98e]("http://groups.google.com/group/linux.debian.security/browse_thread/thread/32a97040215cc98e") that has a script to run a md5sum on /boot. 

I still have some questions about the keys in RAM. Is there no way to wipe the keys when entering suspend? How does suspend work; is data stored to RAM or the hard drive? That would seem to be the main limiter for erasing the keys. 

Part of the paranoia about suspend is that someone could guess my user password to log into my computer. Is there any way to force a shutdown after a certain number of password attempts (someone gets 3 chances to login, then it shuts down)?

I really wish I could boot my computer instantly... time to drool about LinuxBIOS and OpenBIOS
Thanks

---

### Post by Dr Small on 2008-03-12
> regarding the boot issue, you could even setup the boot partition itself on a usb key... so no booting without it... hence no messing...

That sounds interesting. I wonder how that could be done.
*Dr Small goes off to search.

---

### Post by kevdog on 2008-03-13
Dr. Small

I'd be real interested to see what you could dig up about the specifics of putting the /boot partition on a USB stick!

---

### Post by hyper_ch on 2008-03-13
> **Dr Small said:**
> That sounds interesting. I wonder how that could be done.
*Dr Small goes off to search.

Not sure if that should work but

(0) make your usb pendrive bootable (e.g. installing DSL or something on it)

(1) copy your /boot folder to th usb pendrive

(2) install grub on it and alter the according menu.lst

(3) set your computer's bios to boot from the pendrive as first device

I have not tested this at all... but something like that should make it working.

---

### Post by Dr Small on 2008-03-13
That should work, but I have no spare pendrive to test it out with, nor a spare system. But, let's think on the pratical side of this (forgetting that this is a cool idea, nonetheless).

If the system could not boot without the pendrive, then couldn't someone just bootup with a livecd and rebuild your /boot from the ground up so the system would boot?

Ok... you say, lockout the BIOS. Good idea, but this dude works for the NSA :p
He opens the case.... opps. The case is locked. He breaks the lock, pulls the CMOS battery, waits five minutes, sticks it back in. Boots the system, edits the BIOS and boots from CD. Back to stage 1.

The point is, no matter how much physical security you put on it, there is always someone who can break it. But nonetheless, it sounds like a cool idea.

What I am wondering, is how much bare minimal can you get on the Flash drive, just so it will run GRUB and have nothing else. That would be super tiny, (as it wouldn't have most of the filesystem, if any) and would take up little to no space.

Dr Small

---

### Post by hyper_ch on 2008-03-13
> **Dr Small said:**
> If the system could not boot without the pendrive, then couldn't someone just bootup with a livecd and rebuild your /boot from the ground up so the system would boot?l

Well, if you have the whole harddisk as one encrypted partition they can't just add anything new...  if they manage to sneak into it, setting up another /boot partition and set the system to boot from that, well then it's still up to you to check that it is being booted from the pendrive...

As they won't know what your menu list is, you could - just to make sure - alter your name entries into your menu list and to not autostart any of the entries... they would need to get your pendrive to know what to write to... if the system will be auto-booted you know it's not booting from the pendrive and if they use the usual names (linux kernel xxxxx) then you'll also know it's not booting from the pendrive...

You'd need bootloader and a kernel on the pendrive... DSL can do that with 70mb to install a fully functional 2.4 GUI system.... nowadays with pendrives up to 16gb I think you can spare 100mb (for multiple kernels) on it.

---

### Post by MrIch on 2008-03-17
this is an example script which checks changes of the boot partition...
```

        echo "Checking boot partition for changes..." 
         echo ------------------------------------------------------------ 
 
         if [ -r /dev/disk/by-uuid/$BOOTUID ] ; then 
                 echo "Partition ID   $BOOTUID" 
         else 
                 echo "Partition ID should be $BOOTUID" 
                 echo "Partition was not found!" 
                 echo ------------------------------------------------------------ 
                 echo ALERT SYSTEM WAS MODIFIED!!! 
                 sleep 10 
                 echo 
                 echo Press any key to continue... 
                 read A 
                 exit 1 
         fi 
 
         THISHASH=`/usr/bin/sha1sum /dev/disk/by-uuid/$BOOTUID | /usr/bin/awk '{ print \$1 }'` 
 
     if [ $THISHASH != $BOOTHASH ] ; then 
                 echo "SHA1 Hash should be $BOOTHASH" 
                 echo "SHA1 Hash is        $THISHASH" 
                 echo ------------------------------------------------------------ 
                 echo ALERT SYSTEM WAS MODIFIED!!! 
                 sleep 10 
                 echo 
                 echo Press any key to continue... 
                 read A 
                 exit 1 
         else 
                 echo "SHA1 Hash      $THISHASH" 
                 echo ------------------------------------------------------------ 
                 echo everything is ok! 
         fi 
 
         echo ------------------------------------------------------------ 

```
but keep in mind, grub seems to change something at the boot partition at every boot, thus this script does not work very well...

The RAM attack could be prevented by running a program which fills the RAM with random data at shutdown, perhaps with an additional reboot...

---

