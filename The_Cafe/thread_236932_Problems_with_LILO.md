---
title: "Problems with LILO"
date: 2006-08-15
forum: The Cafe
---

### Post by PaulFXH on 2006-08-15
I have a dual boot system (WinXP and Ubuntu Dapper) on my (only)
internal HD which works without difficulties.
At present, I am trying to set up a system whereby a further OS (Zenwalk
Linux) can form the third part of a triple boot scheme. However, there
are two complications:

1. Zenwalk is stored on a non-bootable USB HD
2. Zenwalk uses LILO as the bootloader while I have GRUB in the MBR
(because of Ubuntu).

Although I know that Ubuntu can boot through LILO, I prefer to remain
with Grub in the MBR for other reasons.
I have used a BootCD to enable booting of other GRUB-compliant Linux
distros from the same USB HD without problems. However, Zenwalk is proving
much more difficult because of, I suspect, the involvement of LILO.

Note that, although GRUB is in the MBR, I have installed LILO to the root partition of the USB HD partition containing Zenwalk.

Right now, although Zenwalk shows up on the Boot Options menu (because
it is included in the BootCD menu.lst), selecting it leads to a Kernel
Panic error after the kernel has been uncompressed.
The error message says (roughly, as I can't copy/paste from the boot
screen):
"Kernel panic, not syncing: VFS: can't mount file system on unknown
block (0,0)"

Can any body suggest what might be wrong?

Thanks

---

### Post by beniwtv on 2006-08-15
You have to append the correct "root" parameter on the kernel line

eg. "root=/dev/hda2"

---

### Post by PaulFXH on 2006-08-15
Thanks for your reply.
Here is the relevant part of the menu.lst file on my bootcd:

```
title          Zenwalk 2.8
root           (cd)
kernel         /boot/vmlinuz root=/dev/sda9 ro quiet splash
initrd         /boot/initrd.splash
boot
```

As you can see, the kernel line does contain the "root" part you suggested.
However, I am concerned about the initrd.splash file which appears in the next line. I used this only because no initrd.img file was available in the /boot/ directory after I had installed Zenwalk on the /dev/sda9 partition.

As I have no familiarity with LILO, I cannot say if this is or is not a feature of LILO and performs the same function that initrd.img performs with GRUB.

I would welcome any comments.
Thanks

---

### Post by beniwtv on 2006-08-15
So, let's see.

If the CD hasn't an initrd file, the kernel won't boot with initrd. So, delete the initrd line from GRUB.

If then the kernel complains about no initrd, append "noinitrd" to the kernel line.

Hope that boots the kernel.

EDIT: /dev/sda9 - Note that the kernel, in case it uses initrd from the CD would expect to be ran from the root: (cd).

---

### Post by PaulFXH on 2006-08-15
When you said "delete the initrd line from GRUB", did you mean LILO?
Here below is the important part of the /etc/lilo.conf file in the partition where Zenwalk is loaded.

image = /boot/vmlinuz
  root = /dev/sda9
  label = lilozen
  initrd = /boot/initrd.splash
  read-only

I did already "comment out" the initrd line in the menu.lst file on the bootcd, but that just led to the very same error.

Thanks

---

### Post by beniwtv on 2006-08-15
Just a tought - could it be that your Zenwalk detects the HDD as something different than /dev/sda9?. Then the "root" would be different. Just a tought.

And I've seen from your lilo.conf that there seems to be an initrd file :confused:

EDIT: try deleting "quiet" in the command line so that outputis displayed so you can see the HDD detection :)

---

### Post by PaulFXH on 2006-08-15
OK, I "commented out" the quiet splash in the kernel line and, while of course it didn't solve my problem, it did manage to throw some more light on it.

Here are the errors that it came up with prior to announcing the Kernel Panic (I couldn't copy these so they may not be exactly verbatim):

RAMDISK: Couldn't find valid RAM disk image starting at 0.
VFS: Cannot open root device 'sda9' or unknown-block (0,0)
Please append a correct "root=" boot option

Certainly more information but not entirely sure what to make of it.

Make sense to anybody?

---

### Post by beniwtv on 2006-08-16
Seems to me that sda9 isn't detected by your Zenwalk as sda9.

Try to see what is detected.

---

### Post by PaulFXH on 2006-08-16
Hmmm....not sure.
Because the series of error messages I got yesterday commenced with "RAMDISK: Couldn't find valid RAM disk image starting at 0.", I decided to replace the initrd.splash (Initial Ram Disk) with the initrd.img I had already found in the /etc folder on the Zenwalk install CD.

Then, after making the necessary changes and burning a new boot CD, I tried again to launch Zenwalk.
This time it did find the initrd image but then gave the error:
RAMDISK: Incomplete write (28 !=32768) 4194304

This was then followed by the rest of the stuff I posted yesterday.

So, now it looks to me like the initrd that it is seeing is not what was expected. 
My belief is that the errors mentioned AFTER the first error are merely consequences of the first problem. Therefore, the rest of the error message  
"VFS: Cannot open root device 'sda9' or unknown-block (0,0)
Please append a correct "root=" boot option" is consequential rather than primary faults. This includes an apparent difficulty with /dev/sda9

Now I believe I need to get hold of, or generate, the correct initrd.img. Exactly how, I have no idea at present.

---

### Post by beniwtv on 2006-08-16
Err... I believe you can make a initrd afterwards. But if Zenwalk boots for you the image should be OK. Now, the major issue isn't the ramdisk, but the "Unable to mount root fs" error.

This is *usually* caused having the /dev/<insert device here> incorrect. 

Again, check that Zenwalk detects it's partition as /dev/sda2. It's also possible, that in absence of the Ramdisk, it is unable to mount the partition. In this case, you have to have a valid ramdisk with drivers for the usb device.

The initial ramdisk or initrd is used to mount a small file system wich can contain drivers for later being able to mount a given volume / device / partition.

Hope that this helps you a bit.

---

### Post by PaulFXH on 2006-08-16
Thanks for your reply.
You said:
> But if Zenwalk boots for you the image should be OK
But, it's not booting. It gets about 5 seconds into the boot and then stops, screaming that the RAMDISK is incompletely written.
What puzzles me is why it should start booting at all, without going through LILO. 
As it is, I seem to be booting (or trying to boot) Zenwalk with GRUB which AFAIK is a no-no.
I do agree with your comment that
> It's also possible, that in absence of the Ramdisk, it is unable to mount the partition

However, I have tried to rebuild the initrd.img file but now I keep running into a problem with permissions. The error I keep getting when trying to build the initrd is 
```
sudoers is mode 0777, should be 0440
```

I've posted on this to one of the other forums. Here's the thread if you're interested: [http://www.ubuntuforums.org/showthread.php?t=237527](http://www.ubuntuforums.org/showthread.php?t=237527)

However, this error message seems to be a serious problem and from what I've read in Google, the best way out of it is to reinstall the OS.
So, unless I hear some magic solution soon, I'm going to do this.

---

### Post by beniwtv on 2006-08-16
Well, that leaves me a bit stranded. It's not the first time I boot linux from Grub, and I even managed to boot debian etch in a sun cobalt raq4...

But that the initrd image is broken makes sense to me. Perhaps you can set the permissions for rebuilding it manually?

Going to check the other thread...

---

### Post by PaulFXH on 2006-08-17
Just to keep you up to date, I've re-installed Dapper and Zenwalk and the ```
sudoers is mode 0777, should be 0440
``` 
problem is gone.

However, the next step in the procedure which is to run ```
dpkg-reconfigure linux-image-<kernelversion>
```
in order to rebuild the initrd, still doesn't work. I get the message that the dpkg-reconfigure command doesn't exist (which is what I got all along).
So, I can't make the ramdisk file I need to enable Zenwalk to be booted from the usb hd.

I really can't figure this out (dpkg-reconfigure couldn't be broken if I've just re-installed everything) unless it has something to do with the fact that I'm not in Ubuntu anymore. but I've chroot-ed into the partition with Zenwalk. But this shouldn't be an influence as Zenwalk isn't loaded.

Hmmm............difficult but it's fun!!!:D

---

