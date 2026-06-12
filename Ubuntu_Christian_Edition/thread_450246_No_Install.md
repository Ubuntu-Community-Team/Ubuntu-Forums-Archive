---
title: "No Install"
date: 2007-05-21
forum: Ubuntu Christian Edition
---

### Post by rcdeacon on 2007-05-21
For some strange reason Ubuntu/Ubuntu CE/Kubuntu will not install on my Dell Dimension 4600. I get the normal opening install screen and it goes through the process of finding hardware but then I get a black screen with a statement about busybox 1.1.3 and using a bin/sh command. (not sure of the exact wording). It will come up with some things that are errors but it never goes any further. I currently have windows on hda, Mepis on hdb. Not sure of the problem.

---

### Post by heimo on 2007-05-21
Can you give us the exact error messages? If you type *exit *or hit ctrl+d, does it finish booting?

---

### Post by rcdeacon on 2007-05-21
I will have to reboot to get exact error message. I did find that it boots fine on my Acer laptop so the problem is with my Dell. I have a Nvidia graphics card (5500) which is the only thing I can think of that would be the problem. Let me reboot and then repost.

---

### Post by rcdeacon on 2007-05-21
OK.  the error.

"busyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [   56.711912] ata2.01: failed to set xfermode (err_mask=0x4)"

As it tries to find its way other addresses similar to the last one show up but the message is the same "failed to set xfermode (err_mask=0x4)

This does NOT happen when it run ce live on my acer laptop. I am seriously considering installing ce over Mepis but I need it on both and I need to get the screen resolution fixed on the acer, I need my nano 2 gen to connect and it would be nice to have logos to work (pipe dream at this point). Thanks for helping me get started.

---

### Post by heimo on 2007-05-21
Hmm.. And it does it with different versions, eg. Kubuntu too?

This is probably what I'd try to do (second post) - even though it doesn't talk about same problem, this solution sometimes works:
[https://answers.launchpad.net/ubuntu/+question/6837](https://answers.launchpad.net/ubuntu/+question/6837)

---

### Post by rcdeacon on 2007-05-21
Thanks for the feedback. I will give that a try.

---

### Post by rcdeacon on 2007-05-21
OK. Finally got it working. The f6 thing DID NOT do the trick but it did steer me in the right direction. What I did was when the first screen popped up I hit F4 and chose a vga mode that was close to what my system can handle and it booted up fine. Thanks for the help.

---

### Post by heimo on 2007-05-21
[Googling]("http://www.google.fi/search?hl=fi&client=firefox-a&rls=org.mozilla%3Afi%3Aofficial&hs=MCl&q=+ata+failed+to+set+xfermode+%28err_mask%3D0x4%29&btnG=Hae&meta=") found:
[https://bugs.launchpad.net/ubuntu/+bug/107459](https://bugs.launchpad.net/ubuntu/+bug/107459)

No solution there, but maybe it helps to find something useful.

---

### Post by heimo on 2007-05-21
> **rcdeacon said:**
> OK. Finally got it working. The f6 thing DID NOT do the trick but it did steer me in the right direction. What I did was when the first screen popped up I hit F4 and chose a vga mode that was close to what my system can handle and it booted up fine. Thanks for the help.

Posted at same time. Excellent! Good that it works now, and thanks for posting solution.

---

### Post by rcdeacon on 2007-05-25
OK, back with the same problem. I did not install the other day when I finally got it to work. Now it does not matter what I do I simply cannot get past the splash screen and I get the following  error message:  "busyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash) Enter 'help' for a list of built-in commands.  /bin/sh: can't access tty; job control turned off (initramfs) [ 56.711912] ata2.01: failed to set xfermode (err_mask=0x4)"  Someone sent me a post on the Ubuntu forum and this problem may have something to do with the SIS chipset which my Dell system has. Cannot find a work around as of yet. Just a thought, can I install an earlier version of Ubuntu CE and upgrade to CE 3.1?

---

### Post by mhancoc7 on 2007-05-25
> **rcdeacon said:**
> Just a thought, can I install an earlier version of Ubuntu CE and upgrade to CE 3.1?

In theory, yes. You could install Ubuntu Edgy and then do dist-upgrade to Feisty. Then you could use the convert_me script to Ubuntu CE v3.1.

If you did this without making any changes to the system in between steps it should work. However, I have always had trouble with the whole dist-upgrade thing.

Jereme

---

### Post by rcdeacon on 2007-05-25
Are there any instructions for the dist-upgrade thing? Also, is this problem with installing being addressed? My computer is far from state of the art being 3 years old and it amazes me that of all of the distros out there it is Ubuntu that won't work!

---

### Post by mhancoc7 on 2007-05-25
> **rcdeacon said:**
> Are there any instructions for the dist-upgrade thing? Also, is this problem with installing being addressed? My computer is far from state of the art being 3 years old and it amazes me that of all of the distros out there it is Ubuntu that won't work!

Yes, you should be able to find instructions for dist-upgrade by searching the forums. I have read several threads on the topic in the past.

I am sure the install issue is being looked at by the Ubuntu developers, since it is an Ubuntu specific issue.

Thanks, Jereme

---

### Post by rcdeacon on 2007-06-12
I actually hate to have to revisit this issue but I would really like to install CE 3.2 but I cannot. A previous post in this same thread addresses the error I get. ( "busyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash) Enter 'help' for a list of built-in commands./bin/sh: can't access tty; job control turned off (initramfs) [   56.711912] ata2.01: failed to set xfermode (err_mask=0x4)"

I am having trouble believing that even though a significant number of people have had the same problem that there is yet to be a fix. There has got to be a way to run live and eventually install Feisty. I DO NOT have a state of the art machine! This is an old Dell (2-3 years) with a p4 processor. I did upgrade the video to a Nvidia 5500 but all other things are stock.

---

### Post by bluknight on 2007-06-12
rcdeacon,
You may like to try this at:
[http://ubuntuforums.org/showthread.php?t=421588&highlight=can%27t+access+tty](http://ubuntuforums.org/showthread.php?t=421588&highlight=can%27t+access+tty)

---

### Post by rcdeacon on 2007-06-13
Thanks for the reply. I DO NOT have a sata drive. I have two drives in my box but they are ide drives. Would this matter I wonder?

---

### Post by bluknight on 2007-06-15
> **rcdeacon said:**
> Thanks for the reply. I DO NOT have a sata drive. I have two drives in my box but they are ide drives. Would this matter I wonder?

Finally for those who installed from Fiesty LiveCd but unable to boot:
Copy the old kernel, initrd as well as the /lib/modules and lib/firmware files to your installed target, generate the new initramfs and you can now boot into your new system. Then update to the new kernel on reboot and youre all set. Heres my commands (yours may be differently mounted) as root in the LiveCd-fiesty boot:
root>mount /dev/sdc2 (target) /mnt/sdc2
root>mkdir /mnt/sdc2/lib/firmware/2.6.17-11-generic
root>cp /mnt/edgy/boot/vmlinuz /mnt/sdc2/boot/
root>cp /mnt/edgy/boot/initrd.img /mnt/sdc2/boot/
root>cp -r /mnt/edgy/lib/modules/2.6.17-11-generic /mnt/sdc2/lib/modules/
root>cp /mnt/edgy/lib/firmware/2.6.17-11-generic/* /mnt/sdc2/lib/firmware/2.6.17-11-generic/
root>mount -tproc proc /mnt/sdc2/proc
root>chroot /mnt/sdc2
su
>update-initramfs -c -k 2.6.17-11-generic
Then point your grub menu.lst file to kernel 2.6.17-11 and it will boot from it.

Ive now going to update to 2.6.20-16 and it shd work, hopefully...:) EDIT: Nope new kernel still hangs at "Loading..."

The initramfs ideas are from: [http://ubuntuforums.org/showthread.php?p=2852636&posted=1#post2852636](http://ubuntuforums.org/showthread.php?p=2852636&posted=1#post2852636)

---

