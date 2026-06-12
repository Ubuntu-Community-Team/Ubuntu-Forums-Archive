---
title: "Friend's computer won't boot! Help!"
date: 2008-02-20
forum: The Cafe
---

### Post by akiratheoni on 2008-02-20
I'm trying to fix up my friend's computer (it's a Dell Dimension E310 with Windows XP). 

I barely did anything on it and I couldn't open Windows Explorer at all so I inserted an Ubuntu Gutsy Gibbon LiveCD and turned the computer off.

Now, it won't boot up completely anymore. I don't think it's the LiveCD's fault. I remove the LiveCD and the same thing happens.

Basically, when I hit the power button, it goes to the Dell screen where I should be able to access my BIOS and then afterwards, it goes to a black screen and just stays there.

There's another problem... there are no PS/2 ports and I only have keyboards that have PS/2 connections. I have a mouse that's USB but basically, I can't access the BIOS...

Please, help! Can anyone help me? I don't want to tell my friend I broke her computer :(

EDIT: If it's more appropriate could someone move this to the Windows forum please?

---

### Post by Mazza558 on 2008-02-20
Sounds like a hardware failure if it's not getting past POST. It's probably trying to shut down autmatically. Is it a completely black screen?

---

### Post by akiratheoni on 2008-02-20
> **Mazza558 said:**
> Sounds like a hardware failure if it's not getting past POST. It's probably trying to shut down autmatically. Is it a completely black screen?

Yeah, the screen is black (it's not giving that 'No Signal Input' message, though). It was just working like a couple minutes ago, though >.<

---

### Post by hessiess on 2008-02-20
could be a bad gfx card, ram, mobo or psu. try with only one stik of ram

---

### Post by akiratheoni on 2008-02-20
Actually it finally coughed up a pretty obvious error:

"Keyboard failure"

It doesn't stay at that particular error screen and seems to attempt to continue the booting sequence but can I assume at this point the reason it's not booting up because of the missing keyboard?

---

### Post by Mze on 2008-02-20
you need a USB keyboard.. or USB adapter for a PS2 keyboard. 

most probably the BIOS is set to halt when there are any errors, for e.g. missing keyboard, mouse etc.

If after plugging in your USB keyboard, you still can't boot, you may have to reset CMOS - consult motherboard manual or run a search on Google for the Dell brand you're working on.

---

### Post by akiratheoni on 2008-02-20
I'm going to pick up a USB keyboard tomorrow.

But the weird thing is that the computer first booted up once without the keyboard without ANY problems... Okay, there were problems; Windows Explorer wouldn't open and such, but it was able to load Windows. Ah well I'll see tomorrow, then.

---

### Post by akiratheoni on 2008-02-21
Okay so I've been able to boot into a LiveCD of Ubuntu but booting into Windows still does not work. It's quite frustrating me :(

Attempting to mount the Windows disk gets me this:
```
root@ubuntu:/home/ubuntu# mount /dev/sda2 /media/Windows
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/Windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/Windows ntfs-3g defaults,force 0 0
```

I don't want to use the force option unless absolutely necessary... help...

---

### Post by Mze on 2008-02-21
[Possible cause]("http://en.opensuse.org/SDB:Windows_partition_not_mounting")

---

### Post by akiratheoni on 2008-02-21
> **Mze said:**
> [Possible cause]("http://en.opensuse.org/SDB:Windows_partition_not_mounting")

Thanks for the link. However, I'm aware that it's because Windows is probably in hibernation or something

I cannnot boot into Windows; despite the fact I have a keyboard attached now, it still won't boot into it. I just get a blank screen after the Dell loading screen.

On an interesting note, I could mount the disk on PCLinuxOS 2007 and Linux Mint 3.1, but not on Ubuntu 7.10 or Linux Mint 4.0... I think it's because of the ntfs-3g? Damn. This is really weird.

I don't think reinstallation is an option here... I would have to talk to the owner of the computer.

---

### Post by Bigbluecat on 2008-02-22
Insert the Windows install disk and use the repair facility to get windows back working. This will wipe grub from the MBR. So afterwards you need to load the Ubuntu LiveCD again and restore grub.

---

