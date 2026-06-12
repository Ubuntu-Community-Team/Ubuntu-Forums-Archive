---
title: "Headless Server Problem"
date: 2012-06-05
forum: Server Platforms
---

### Post by pgp_protector on 2012-06-05
I've got a clean install of Ubuntu Server 12.04 built on a HP Pavilion P6-2100 Box (Full Format)
After a bit of tweeking due to the "Blank Screen" at bootup I got my Grub configured with
GRUB_CMDLINE_LINUX_DEFAULT="nosplash radeon.modeset=0 vga=773"
GRUB_CMDLINE_LINUX=""

And it loads and leaves me at the SYSTEM Login: screen as I want.

So Part 1 is working.
Web server, MySQL, Samba DNS are also all working and I can communicate, transfer data to / from the box.

Now the problem.

It goes to Sleep !! 
And when it does, given I'm using it for the networks DNS, I loose all internet connections.

If I press any key when the screen first goes black, it wakes up (Light sleep???) 
but if I leave it for about an hour or so, it will not wake up, and I can't use PuTTY to log in, all web sites that were working are down, ect.  Even pressing any keys after that point will not wake the box up.

---

### Post by pgp_protector on 2012-06-05
Ok, just added "acpi=off apm=off" to the GRUB_CMDLINE_LINUX_DEFAULT in etc/default/grub.

Ran rebuild-grub and rebooted.
I'll have to check back in an hour or so & see if it's still running :D

(Then reboot & pull the keyboard & monitor to see if it also keeps on trucking)

---

### Post by pgp_protector on 2012-06-06
Came home from work, and couldn't access the server :(
But it was behaving a bit better.
When I turned on the monitor & plugged in the keyboard, it did "wake up" and started behaving again.

Pulled the keyboard, and after about 5 mins the Log In screen went black again though.  So it's still trying to go into some form of sleep mode.

Any help out their on this?

---

### Post by kennethconn on 2012-06-06
Sort it out in BIOS not OS.

---

### Post by CharlesA on 2012-06-07
I'm not quite sure what is going on. I have my "server" running headless with just network and power plugged in and I don't have any problems with it "going to sleep."

Also, my server is just a beefy desktop box, so it might not have the same settings for power saving as the server itself. Checking the BIOS and disabling power management there might be a good way to test.

When you say "not responding" does that mean you cannot ping it or access it via ssh? Have you checked the syslog at all?

---

### Post by pgp_protector on 2012-06-08
> **CharlesA said:**
> I'm not quite sure what is going on. I have my "server" running headless with just network and power plugged in and I don't have any problems with it "going to sleep."

Also, my server is just a beefy desktop box, so it might not have the same settings for power saving as the server itself. Checking the BIOS and disabling power management there might be a good way to test.

When you say "not responding" does that mean you cannot ping it or access it via ssh? Have you checked the syslog at all?

I've turned off all BIOS settings regarding Power Savings that I can find.

After my last reboot, it is staying awake now, mostly, (Screen Turned off, keyboard Unplugged) so It appears to be working now, the only thing I'd like to disable is their still appears to be some form of screen saver / time out going on.

When I've got the monitor turned on, and press the Esc key, My Log in prompt shows up, but after a short time it goes back to a blank screen. (Is that normal,and can that be turned off? )

I'm away from the box today, and I haven't reconfigured my Modem / Router (Thanks AT&T :P ) to allow outside access yet, so I won't be able to check anything else tell tonight.

---

### Post by CharlesA on 2012-06-08
That's normal but I am not sure if you can turn it off or not.

---

### Post by IWantFroyo on 2012-06-08
Can you remove ACPI?
```
sudo apt-get remove acpi
```

---

### Post by kennethconn on 2012-06-08
I'm confused - why are you talking about monitors and keyboards when the title states it is a headless server problem.

---

### Post by IWantFroyo on 2012-06-08
> **kennethconn said:**
> i'm confused - why are you talking about monitors and keyboards when the title states it is a headless server problem.

ssh.

---

### Post by LinGNUbie on 2012-06-08
Probably the monitor doing the usual "no active signal change, so I will go into sleep mode" since there is no activity registered via a keyboard/mouse. I wouldn't think it is anything other than that and it should be safe to boot the device without a keyboard/mouse/monitor, as long as you are still able to ssh or otherwise (ftp, webmin) get into the server upon a full reboot.

---

### Post by CharlesA on 2012-06-08
> **kennethconn said:**
> I'm confused - why are you talking about monitors and keyboards when the title states it is a headless server problem.

It loses network access for some reason.

---

### Post by LinGNUbie on 2012-06-09
I have a few myself that are a little funny about having "no" K/M/M at all connected when booting, and "must" at least be hooked to a KVM to boot, then operate correctly, also with all errors and power turned "off" in the BIOS. Of course not all BIOS will strictly adhere to its programming, of course.

---

### Post by pgp_protector on 2012-06-09
> **kennethconn said:**
> I'm confused - why are you talking about monitors and keyboards when the title states it is a headless server problem.

During the initial install I've got the keyboard & monitor while I test everything out, and that way I know it's working right.  It's also how I'm verifying if it's a network issue or system when I can't connect.

When I'm happy with the box, I'll be moving it to another location in the house where it's can be less disturbed and just chug along in peace.

---

### Post by pgp_protector on 2012-06-09
> **CharlesA said:**
> That's normal but I am not sure if you can turn it off or not.

Ok, then I won't worry about that then.

It's stayed up now for at least 24 hours now, and appears to be running without issues.

---

### Post by CharlesA on 2012-06-09
> **pgp_protector said:**
> Ok, then I won't worry about that then.

It's stayed up now for at least 24 hours now, and appears to be running without issues.
Outstanding.

Don't forget to mark the thread as solved. :)

---

