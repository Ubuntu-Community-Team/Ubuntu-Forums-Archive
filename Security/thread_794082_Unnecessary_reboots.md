---
title: "Unnecessary reboots?"
date: 2008-05-14
forum: Security
---

### Post by toupeiro on 2008-05-14
In this last set of security patches, I got prompted to reboot after the patches.  The patches were things such as gcc, openssl etc etc.  I didn't recognize anything in the patches that would "require" my system to be rebooted.  Can someone help me identify what was pushed out within the last few days that would require a full system reboot?  I'd be pretty discouraged to put ubuntu LTS on any high visibility systems if its going to start requiring as many reboots as windows.

---

### Post by HermanAB on 2008-05-14
You only need to reboot if you patched the kernel.

---

### Post by yaztromo on 2008-05-14
The update wasn't a kernel patch. I've been asking myself the same question since the recent security notices don't mention the need to reboot.

Buest guess: the required reboot is for paranoias sake and with these recent updates you don't *really* need to reboot. Just a guess.

@toupeiro

Nearly every patch in Windows seems to need a reboot. You'll find most patches in Ubuntu don't :)

---

### Post by HermanAB on 2008-05-14
Typically, you should just restart whatever services you updated.  I only restart my servers once a year when I update the kernel.

---

### Post by az on 2008-05-14
Updating the kernel and HAL require reboots.  There was also an xserver component that was updated and a reboot may be needed by some graphis cards to free up dynamic video card memory.

In all three cases, it's a hardware issue.  There is no way around it.

---

### Post by az on 2008-05-14
Here is a list of the postinstall scripts that call for a "reboot-required" on my system:


~$ find /var/lib/dpkg/info/ |xargs grep reboot-required
/var/lib/dpkg/info/dbus.postinst:        [ -x /usr/share/update-notifier/notify-reboot-required ] && \
/var/lib/dpkg/info/dbus.postinst:            /usr/share/update-notifier/notify-reboot-required || true
/var/lib/dpkg/info/initscripts.postinst:	if [ -x /usr/share/update-notifier/notify-reboot-required ]; then
/var/lib/dpkg/info/initscripts.postinst:		/usr/share/update-notifier/notify-reboot-required
/var/lib/dpkg/info/update-notifier-common.md5sums:e5c1a7367d8d71b165f5ecceb88d13bf  usr/share/update-notifier/notify-reboot-required
/var/lib/dpkg/info/linux-image-2.6.24-16-generic.postinst:my $notifier          = "/usr/share/update-notifier/notify-reboot-required";
/var/lib/dpkg/info/libssl0.9.8.postinst:    [ -x /usr/share/update-notifier/notify-reboot-required ] && /usr/share/update-notifier/notify-reboot-required
/var/lib/dpkg/info/update-notifier-common.list:/usr/share/update-notifier/notify-reboot-required
/var/lib/dpkg/info/ifupdown.postinst:	if [ -x /usr/share/update-notifier/notify-reboot-required ]; then
/var/lib/dpkg/info/ifupdown.postinst:	    /usr/share/update-notifier/notify-reboot-required
/var/lib/dpkg/info/libpam0g.postinst:		       && [ -x /usr/share/update-notifier/notify-reboot-required ]
/var/lib/dpkg/info/libpam0g.postinst:			/usr/share/update-notifier/notify-reboot-required
/var/lib/dpkg/info/udev.postinst:    if [ -x /usr/share/update-notifier/notify-reboot-required ]; then
/var/lib/dpkg/info/udev.postinst:	/usr/share/update-notifier/notify-reboot-required


Maybe it was /var/lib/dpkg/info/libssl0.9.8.postinst?

---

### Post by yaztromo on 2008-05-15
I'm fairly sure that's what it was on my box. Installations without a desktop don't have the reboot notification, so the USN notices always explicitly say when a reboot is necessary.. For libssl a reboot was not mentioned in the notices. Which is what got me thinking this reboot notice was erroneous and not needed.

---

### Post by toupeiro on 2008-05-15
> **yaztromo said:**
> 

@toupeiro

Nearly every patch in Windows seems to need a reboot. You'll find most patches in Ubuntu don't :)

I agree with you wholeheartedly! :)  However, I happen to have been a windows packager and know that more than 75% of the windows reboot requirements we face with patches could be circumvented by restarting a few specific services or running a few post install commands that a reboot also addresses.  The reboots are there mainly due to something called logo compliance, where Microsoft maintains a guideline of the best practice to perform when certain actions are done via the Windows Installer service.  Linux has even less of this type of requirement, therefore the only way it could get worse is if the misuse of reboots continue to grow in updates.  While you're right that its nowhere near the amount of reboots I see in windows, I don't want it to approach it either. :) My Solaris license server at work just rolled over 300 days of uptime.  It'd be nice to continue these testimonials on Ubuntu.

In any case, thank you and AZ for digging into this some more, and also for revealing the location of the postinst/postrm scripts!:KS  I'm still new to debian packages.

---

### Post by jimv on 2008-05-15
> **toupeiro said:**
> I agree with you wholeheartedly! :)  However, I happen to have been a windows packager and know that more than 75% of the windows reboot requirements we face with patches could be circumvented by restarting a few specific services or running a few post install commands that a reboot also addresses.

I would imagine that the update says reboot instead of restart X service or program because most users don't want to deal with that stuff.  If you're a server admin or advanced user though, you can deal with it though.

---

### Post by Biochem on 2008-05-15
I'm not sure but I think it has to do with the openSSL security update.

 It insures that any "bad guy" who manage to brake through using a weak key is flushed out of the system. Otherwise they could generate a valid keypair and log back in.

On this angle I don't think it was an unecessary reboot.

---

### Post by yaztromo on 2008-05-16
Thanks Biochem that sounds very plausible.

---

