---
title: "Windows XP virtual machine not starting"
date: 2008-08-16
forum: Virtualisation
---

### Post by Jonathan Métillon on 2008-08-16
Hi,

I've not tried anymore since [that thread]("http://ubuntuforums.org/showthread.php?t=719025") but I'm tired of dual booting between Ubuntu and Windows XP.

So I try again, this time I found this tutorial: [**Boot an existing XP (Physical HD) install with VirtualBox**]("http://ubuntuforums.org/showthread.php?t=769883")

That's exactly what I want to do. I followed the steps. I had to sudo umount the /media/sda2 Windows XP partition that is automatically detected and mount by Ubuntu at boot.```
RAW host disk access VMDK file /home/john/.VirtualBox/WindowsXP.vmdk created successfully.
```So I run VirtualBox, create a new virtual Windows XP machine to use the new VMDK file.

It starts, display the word "MBR", and then black screen, nothing happens, it hangs.

Any clue?

---

### Post by Jonathan Métillon on 2008-08-16
Oops, I forgot to *enable the IO-ACPI*.

Now it works! I can run my native Windows XP from Ubuntu. THAT IS FANTASTIC!!

No more reboot to use Dreamweaver or Internet Explorer.

 :guitar:

As warned by Sand Lee's tutorial, I'm asked to activate again my Windows XP copy. I said yes to activate it now but then a message said "This Windows XP copy is already activated". And I'm forced to log out. I re-log in, and it asks me again to activate.

So this time I said no to activate now. And again I'm forced to log out. What's that? I can I get out from this MS Hell?

[[IMG]http://i35.tinypic.com/334jf5d.jpg[/IMG]]("http://i35.tinypic.com/334jf5d.jpg")

---

### Post by pytheas22 on 2008-08-16
You're running Vista in the virtual machine, right?

---

### Post by Jonathan Métillon on 2008-08-16
Hi pytheas22,

No I'm running my native physical Windows XP. No Vista on my computer.

(My Windows XP uses the official [Zune theme]("http://ubuntuforums.org/go.microsoft.com/fwlink/?LinkID=75078"))


Finally I've reboot to Windows XP, I can't get out of this activation hell, and my "Windows from VirtualBox" solution is compromised.

As suggested [here]("http://www.commentcamarche.net/forum/affich-2346063-activation-windows-deja-activee") I've corrupted the *oobetimer *key from *HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\WPAEvents* but it did nothing to allow me to really reactivate my Windows XP copy.

:(

---

### Post by pytheas22 on 2008-08-16
Alright, that explains the theme.

Can you still boot Windows normally from your hard disk (not in the virtual machine)?

---

### Post by Jonathan Métillon on 2008-08-16
Yes I can. I'm actually posting from my Windows XP, normally booted with the "Physical" hardware profile. Windows did not ask for activation that way.

This is really a problem triggered by the "Virtual" hardware profile used when booting from VirtualBox.

---

### Post by starcannon on 2008-08-16
If your ready to kiss the dualboot thing goodbye forever, I'd probably call the registration support line and re-register the copy of xp with it running in your Virtual Machine, 15minutes on the phone will possible fix you right up. Don't you just love being hassled like this by a license issue? I feel your pain, I have a few Virtual Machines I've had to deal with myself.

---

### Post by Jonathan Métillon on 2008-08-16
No, I'm not ready to quit dualbooting. I still need native physical Windows XP, like for video editing or when launching Lightroom  + Photoshop + Illustrator + InDesign see what I mean.

I'll abandon trying to use my physical Windows XP partition from Ubuntu if this causes a license issue because of the hardware profiles.

How can phone support help me when the thing says it's already activated and don't offer an option to re-activate?

And if I could re-activate, it means that when booting physicaly with the "Physical" hardware profile, Windows will ask for re-activating? Can't I activate my Windows XP copy from BOTH "Physical" and "Virtual" hardware profiles?

:confused:

---

