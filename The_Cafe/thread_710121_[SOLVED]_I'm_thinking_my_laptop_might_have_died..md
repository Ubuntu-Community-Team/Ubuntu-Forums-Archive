---
title: "[SOLVED] I'm thinking my laptop might have died."
date: 2008-02-28
forum: The Cafe
---

### Post by WorldTripping on 2008-02-28
I wonder if anyone here has an opinion about this.

The other day, when I booted into Xubuntu 7.10, I got the message "Starting Up..", then it just hung.

Rebooting would not get past this point, and a recovery mode boot stalls at line "Some PCI error".

I'd been faffing around that day, and thought I might have fecked something up.

So I booted into a LiveCD of DSL, and recovered some data to a memory stick.

Still not booting, so I wiped the HDD (DBAN) and re-installed Xubuntu 7.10.

Now I'm back to "Starting Up.." and hanging.

I also tried a different HDD with a copy of Fluxbuntu 7.10 on it, and it hangs at the same point.

Am I looking at a motherboard failure here ?

I think I might be looking for a new laptop.

Any Ubuntu friendly laptop guides out there (never could get Compiz working on this old machine) ?

Any thoughts appreciated.

---

### Post by clb137 on 2008-02-28
HI,

Your laptop must be ok if you can live boot,  when you live bbot can you see all your hard drive (IE Using Gparted?).
I have seen before some people have had problems with the allocation of PCI resource 8 and 9.
I tryed ubuntu but had to change to LinuxMint try it its Ubuntu based.

Let me know how you get on  good luck

CLint

---

### Post by popch on 2008-02-28
> **WorldTripping said:**
> I'd been faffing around that day, and thought I might have fecked something up.

Er - what? If you have done something which might have affected your laptop, you'd better say so in words we can understand.

I don't quite see how the motherboard can be seriously damaged when you can boot off a CD, start the GRUB, re-install Linux on your HDD and recover data off the HD (not in that order).

How long did you wait when the laptop hung? Was there any disk activity while it did so? Are you quite sure the display actually shows what's going on, or is there any possibility that it's just an invisible X session?

---

### Post by WorldTripping on 2008-02-28
hmmm,

Why would I suddenly get a PCI conflict ?

One day Xubuntu works fine, the next it stalls on boot.

One wipe and reinstall later, and it stalls again.

Would a fresh install not resolve any PCI issue ?

If not how could I resolve it myself ?

I have a copy of LinuxMint somewhere, I'll try and install it tonight.

(Actually, I've never been able to get any LiveCD after 6.06 to run, I've always had to just install later versions from the Alternate CD.)

---

### Post by az on 2008-02-28
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by WorldTripping on 2008-02-28
> **popch said:**
> Er - what? If you have done something which might have affected your laptop, you'd better say so in words we can understand.

I don't quite see how the motherboard can be seriously damaged when you can boot off a CD, start the GRUB, re-install Linux on your HDD and recover data off the HD (not in that order).

How long did you wait when the laptop hung? Was there any disk activity while it did so? Are you quite sure the display actually shows what's going on, or is there any possibility that it's just an invisible X session?

Sorry, I meant tinkering / tweaking Xubuntu, not digging around inside the box with a screwdriver :)

I don't understand this either.

I can boot from the DBAN CD, and wipe the HDD.

I can boot a LiveCD of DSL, and access the partitioned HDD.
(As mentioned before I can't boot other Live CD's, and have not been able to do for a while.)

I can install Xubuntu.

When I reboot it hangs, saying "Starting Up".

It stays like that. No Disk activity. No lights. It will stay like that til I hard reboot.

I can put in a different HDD, one that I know has a working copy of Fluxbuntu on it.

Same thing.."Starting Up", then hanging.

I'm at a loss to explain this.

---

### Post by WorldTripping on 2008-02-28
> **az said:**
> [https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Cheers for that.

I can certainly run memtest overnight.

But how can I install smartmontools package when I can't boot into the OS ?

---

### Post by az on 2008-02-28
Use a live cd.

---

### Post by WorldTripping on 2008-02-28
> **az said:**
> Use a live cd.

ah, OK.

As I said in an earlier post, the only LiveCD I can run is Ubuntu 6.06.

I can do this tonight, as the disk is currently being wiped again, before I instal LinuxMint as **clb137** said to try.

I'll have a look at the SMART tools, but I seriously doubt whether this is a HDD issue as:

1) It's a relatively new drive.
2) I get the same 'hang' when using a different drive.

The thing is truly do not understand is how Xubuntu will not boot, after a fresh install onto a newly wiped HDD, on a system that it used to run perfectly on.

Thanks for everyone's time / posts.

---

### Post by solitaire on 2008-02-28
Can you get into the Laptop BIOS?

Try resetting the BIOS to the Default settings (or SAFE) settings and trying to install it.

I've seen it happen with older laptops that if Onboard devices like infra-red ports and Serial ports are set tothe same COM port which usualy don't hinder install but when the OS starts it gets stuck trying to put 2 devices onto the same COM port for some reason.

Resetting to Default or Safe should take this out of the equasion... :D

---

### Post by WorldTripping on 2008-02-28
> **solitaire said:**
> Can you get into the Laptop BIOS?

Try resetting the BIOS to the Default settings (or SAFE) settings and trying to install it.

I've seen it happen with older laptops that if Onboard devices like infra-red ports and Serial ports are set tothe same COM port which usualy don't hinder install but when the OS starts it gets stuck trying to put 2 devices onto the same COM port for some reason.

Resetting to Default or Safe should take this out of the equasion... :D

That sounds interesting, and certainly plausable. I'll have a look tonight, (at work at the moment).

But what could have upset the BIOS ? It's something that I never mess around in.

Thanks in advance.

---

### Post by mips on 2008-02-28
What Brand & Model laptop do you have? A web link would be nice.

There might be know issues with certain models that you are not aware of. Also might just require a certain paramater at boot time in order for it not to hang.

I really don't think your hardware is faulty at all.

---

### Post by Bartender on 2008-02-28
You mentioned something about a new HDD.
A while back I was inside a dual-boot desktop PC and failed to get the IDE cable completely plugged in.  Some of the pins must have been touching but not making full contact.  Windows would come up but Ubuntu hung at a point that sounds very similar to yours if I remember correctly. 
Is yours SATA?  Since there are fewer contacts in SATA plug I'm guessing a connection error on SATA would result in total failure, not partial.  But it might be worth checking out.

---

### Post by WorldTripping on 2008-02-29
OK,

So just an update on how this is going.

In response to earlier posts:

The laptop is a Toshiba 'Satellite' 1415-S105 1.6GHz 256MB RAM laptop.

It currently has a 40Gb HDD in it, repacing the original 20Gb one. AFAIK there is no loose connection, and I can access the HDD when using DSL etc.

I have been using Ubuntu for a while on this machine now, having been through distros; Ubuntu 6.06, Ubuntu 7.04, X/Ubuntu 7.10, LinuxMint 4.0-Fluxbox, Fluxbuntu 7.10 and DSL 3.4.1

All have worked perfectly, up until the other day, when Xubuntu suddenly hung at boot.

So, last night I did some checking, and here are the results.

I reset the BIOS, and as I thought the only difference between my setting and the default ones were the boot order.

I ran a memtest overnight, and there were no errors.

Ubuntu 6.06 LiveCD, boots fine, but took 20 mins to load.
Ubuntu 7.04 LiveCD, boots fine, but took 25 mins to load.

LinuxMint4.0-Fluxbox, LiveCD boots (eventually).

LinuxMint4.0-Fluxbox, installs, but took over two hours.

LinuxMint4.0-Fluxbox hangs on normal boot, with a black screen and a flashing cursor.
In recovery mode, it hangs at error message 9.812987-Setting up standard PCI resources. Earlier on in the log there was the message 9.811538 Motherboard not detected.

Xubuntu 7.10, installs.

Same results as with LinuxMint, hang at normal boot, saying "starting up", and a similar set of mesages in recovery mode.

Fluxbox 7.10 hangs on installation.

However DSL will both run from LiveCD and boot properly.

As I said earlier, all of these distros used to work perfectly.

This is really starting to annoy me now.

Anyone any idea what on earth could be wrong ?

---

### Post by WorldTripping on 2008-02-29
Just tries to install Ubuntu 7.10 and I'm getting similar messages to above.

Back to DSL; looks like I'll be with this distro for a bit.

Anyone any clue as to what the problem might be ?

---

### Post by stoodleysnow on 2008-02-29
Either a problem with your RAM or your motherboard.

Try running a memory test and try swapping the RAM for a known working stick. Sometimes RAM develops strange little problems that can cause errors like these.

Otherwise it's the motherboard. Check the capacitors on the motherboard, if there are any electrolytic (aluminium cylinder) capacitors, are they bulging or leaking?
If not that, something else motherboard related.

Ah, just had an idea. Could it be to do with power management/acpi/apic problems? If that's likely try the --noacpi or --noapic options on GRUB at boot.

---

### Post by WorldTripping on 2008-02-29
Cheers for that.

I'll try and look inside the laptop this weekend.

I'm pretty sure its not memory, as an overnight memtest went fine, but the symptoms do seem to explain why everything is so slow.

Any other ways of checking memory ?

I'm sure that it's not a motherboard problem as I can run LiveCD, and install DamnSmallLinux.

I'm at a loss to explain why I can't run/install a distro today that I could a year ago.

---

### Post by WorldTripping on 2008-03-04
Well,

I don't know what's happened, but over the weekend out of curiosity I loaded Windows back onto the machine; and it worked just fine.

After that I did a quick install of Ubuntu 7.04, and everything seems to be working fine.

No idea why, just glad it is !

---

