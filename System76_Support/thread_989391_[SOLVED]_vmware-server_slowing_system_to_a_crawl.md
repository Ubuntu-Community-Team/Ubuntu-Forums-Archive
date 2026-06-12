---
title: "[SOLVED] vmware-server slowing system to a crawl"
date: 2008-11-21
forum: System76 Support
---

### Post by MorphWVUtuba on 2008-11-21
Ok, I've been having a problem running vmware-server on my serp5.  The processor isn't pegged, but the system is unresponsive, gkrellm tells me that the hard disk is reading/writing like gangbusters, and usually the vmware-server, firefox, or just about anything else I have open greys out.

A number of comments on this thread point me towards adding nohpet or hpet=disable or acpi=off parameter in /boot/grub/menu.lst:
[http://communities.vmware.com/thread/77895?tstart=0&start=0](http://communities.vmware.com/thread/77895?tstart=0&start=0)

I want to understand this ```
acpi_osi="!Windows 2006
``` before I change anything there, as this is how it came from s76.

Any thoughts?  Suggestions?

---

### Post by thomasaaron on 2008-11-21
There's an OS setting in the BIOS. It might be set to Vista or XP. What happens if you set it to "Other"?

---

### Post by MorphWVUtuba on 2008-11-21
It is set to "Other" right now.

Might that be my problem?

---

### Post by thomasaaron on 2008-11-21
I'm not sure. Kind of doubt it. But we do no testing with vmware products. I'm doing some research now to see if anyone else is experiencing this.

---

### Post by thomasaaron on 2008-11-21
Could it be related to vmware tools? Try re-installing tools.
[http://ubuntuforums.org/showthread.php?t=879008](http://ubuntuforums.org/showthread.php?t=879008)

Also check the memory your allotting your VM. If you use too much, it'll definitely slow down the host.

This might help as well...
[http://www.phocean.net/?p=10](http://www.phocean.net/?p=10)

I'm sort of a fan of virtual box. So, I've not trouble-shot (word?) a lot of vmware issues.

---

### Post by MorphWVUtuba on 2008-11-21
Yeah, my preference is for VirtualBox also, but I can't get a work machine image to work under VirtualBox.  I sometimes use this for off-hours support, so I'm kinda stuck with this option.

I don't think it's vmware-tools, because the system will get hosed up at the Windows boot options screen if I press F8 during bootup.  I think I'll just try reinstalling vmware-server & then report back here.

---

### Post by MorphWVUtuba on 2008-11-24
PFFT!

No dice.  I'm gonna revert to Hardy & try that out.  I think I like Hardy better anyway.

Is there a reason I only get a "quiet" shut down?  And does it take longer to shut down now or does it just seem that way because I can't see anything happening?

---

### Post by thomasaaron on 2008-11-25
Quiet shutdown? As in... no progress bar?

---

### Post by MorphWVUtuba on 2008-11-25
No, as in no kernel messages.  No display, actually.  The screen powers off the instant X shuts down. :confused:

---

### Post by thomasaaron on 2008-11-25
I've not heard of this one. It could take some thought...

[**[COLOR="RoyalBlue"]This[/COLOR]**]("http://ge.ubuntuforums.com/showthread.php?t=939417") is probably a good place to start. It raises two questions for me: 

1. Did you disable the power management service in System > Preferences > Services

2. Do you have everything set to Pulse Audio on System > Preferences > Sound

---

### Post by thomasaaron on 2008-11-25
I'm starting to see this problem on some other computers. I'm wondering if it is caused by an update or something. Researching.

---

### Post by MorphWVUtuba on 2008-11-28
Installing vmware server 2.0 & upgrading my virtual machine resolved the issue.

---

