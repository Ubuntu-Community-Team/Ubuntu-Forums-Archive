---
title: "That's not cool"
date: 2011-02-22
forum: System76 Support
---

### Post by Speedwagon on 2011-02-22
I got my new Starling today.  Turned it on, started the setup.  Then it sat there, not doing anything... for 10-15 minutes.  Now it's broke.  Brand new netbook, and it's broke in the first 30 minutes.

---

### Post by Ebonwumon on 2011-02-22
Not that I don't empathize with you, but this seems like something you should try to resolve over email first and *then* post your experiences here afterwards.

[email]support@system76.com[/email] is their email, I believe.

---

### Post by tgalati4 on 2011-02-22
Was there evidence of damage to the package from shipping?  Try charging the battery for a few hours and then try to boot.  Sometimes new hard disks are sticky and demand more current when new.  Could be something that needs reseating like a loose RAM stick.

---

### Post by EJJ on 2011-02-22
Are you just getting a blinking cursor? Have you tried booting from a live disc?

Could be a GRUB bootloader issue. I had that happen. All it took was this resolution;

[http://knowledge76.com/index.php/Restore_Grub_Bootloader](http://knowledge76.com/index.php/Restore_Grub_Bootloader)

Sorry to hear about the situation with the Starling. Try communicating with System76 about it. Their customer service is top notch, and I speak from experience. Good luck, and keep us updated!

---

### Post by Speedwagon on 2011-02-22
> **Ebonwumon said:**
> Not that I don't empathize with you, but this seems like something you should try to resolve over email first and *then* post your experiences here afterwards.

[email]support@system76.com[/email] is their email, I believe.

I have emailed them, but since their site specifically routes you to these forums, I see no problem in posting up a problem I am having.  I actually asked them in the email if I can just bring the thing by tomorrow, since they have an office here in Denver.

Packaging was flawless, no evidence of UPS mishandling.  Battery is full as well.

Every so often, it gives me a keyboard error.  

When I try to boot to a USB drive that I just made, I get an error.  I tried remaking the USB drive a few times, even redownloaded 10.04 remix.  Error is:
```

Unknown keyword in configuration file: gfxboot
vesamenu.c32: not a COM32R image
boot:

```

When I just boot to the HDD, I get a command line error
```
Kernel panic - not syning: VFS: Unable to mount root fs on unkown-block(0,0)
```

---

### Post by EJJ on 2011-02-23
Make sure that you can boot off the live disc from another computer to verify that it is not an issue with the live disc. Is that the first thing that comes up when you launch from the drive? Or are you given the list of options. If so, you'll want to check the disc for errors, just in case.

If the live disc is bootable from another computer, then it sounds like a hardware issue. You'll have to send it back at that point.

You can also head on over to the System 76 Submit a Bug Report (if you haven't done so already.) They're pretty helpful over there. If the problem isn't remedied from there, they'll probably ask you to give em a call.

---

### Post by isantop on 2011-02-23
I think you brought your system in this morning. If so, then we got you taken care of.

If not, then by all means, I stand corrected. We can continue this here or over email.

We also have no problem with users posting problems here before email or phone. It's what it's here for. :)

---

### Post by Speedwagon on 2011-02-23
> **isantop said:**
> I think you brought your system in this morning. If so, then we got you taken care of.

If not, then by all means, I stand corrected. We can continue this here or over email.

We also have no problem with users posting problems here before email or phone. It's what it's here for. :)

Yep, that was me.  All fixed now!

I found out today that 10.10(my desktop) won't make 10.04 bootable USB drives.

---

