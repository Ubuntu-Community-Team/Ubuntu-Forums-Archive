---
title: "Just reading that 16.04 will/might ship with Unity 8"
date: 2015-11-16
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2015-11-16
[Distrowatch]("http://distrowatch.com/weekly.php?issue=20151116#news") and [Softpedia]("http://news.softpedia.com/news/ubuntu-16-04-lts-with-unity-8-to-run-gtk-plus-apps-natively-495893.shtml") are both reporting that two versions of Ubuntu may be available with 16.04. 

Just wanted to say: :guitar: 

I'm pulling for Ubuntu/Canonical. Can't wait to finally try out Unity 8, not just on a laptop, but also on a mobile device.

---

### Post by Kale_Freemon on 2015-11-16
I'm not holding my breath for it. Been waiting for Unity 8 for a little while now.

---

### Post by deadflowr on 2015-11-16
You can try it out now, it's been install-able for a while on desktops.

---

### Post by neu5eeCh on 2015-11-16
> **deadflowr said:**
> You can try it out now, it's been install-able for a while on desktops.

I know, but it's still fairly dodgy, esp. with MIR. Looking forward to an official release. I'm putting my money on the possibility that they actually deliver this time.

---

### Post by grahammechanical on 2015-11-16
I would not count of it. Jane Silber at the Ubuntu Online Summit was asked something about this and her reply was; When its is ready and 16.10. I would be very surprised if Canonical messed with an LTS release.

There is something being developed called Ubuntu Personal. It is supposed to be built on snappy Ubuntu core on Mir and Unity 8 with an app store that has snap apps and something called Libertine that will let us install X apps that are not snaps, such as Libreoffice, running on XMir in a Linux container. We may get a version of that by the 16.04 release day. I see it as a parallel development.

From what I can make out this is all very "proof of concept" stuff at the moment. There is an image called personal_x86.img that is installable in KVM or on a USB stick or a hard drive using Disks utility Restore Image. But it has not been undated since 17 October and is was no further forward than the Unity 8 session we can install on Ubuntu desktop. But it was Mir & Unity 8 with transaction updates on X86 CPUs

Oh, by the way, the UOS had a demonstration of Libertine. It proved the developers are better at writing code than showing a video presentation. :)

Regards.

---

### Post by buzzingrobot on 2015-11-16
Yes, the notion of debuting Mir in an LTS is perplexing.  Perhaps, at most, as a "you break it, you buy it" option, as some ditros are doing with Wayland.

I hope, and expect, 16.04 to be a very solid release for those who don't want to immediately jump into the new stuff beginning with 16.10.

---

### Post by neu5eeCh on 2015-11-17
> **buzzingrobot said:**
> Yes, the notion of debuting Mir in an LTS is perplexing. 

As I understand it, the intent is to release two versions, one with Unity 8. It makes perfect sense to release Unity 8 as an LTS _option_. The advantage being that there *are* going to be users who jump on board. Canonical stands to gain by getting long-term feedback, bug reports, etc... LTS users who want and need a solid DE (and 7 is about as solid as a Linux DE can get) can choose it. They'll have 7 for the next several years if they stick with 16.04. In the meantime 8 is released to the wild (like 7 initially was - practically beta) and becomes the standard with 16.10. 

And the other reason Unity 8 with 16.04 makes sense is that the new package management allows Canonical to update Unity 8 as it develops -- essentially a rolling release DE on top of an LTS release. After 16.04, as far as Ubuntu goes, the only advantage to updating will be for an updated kernel/hardware stack (which can be worked around).

---

### Post by Andrew_Constantine on 2015-11-18
I really don't foresee them pushing something big into an LTS, as others also have said. I see it in a .10 release for sure. I also would hope unity 8 goes into the mainline release and we don't end up more segregated. I mean I know we have lubuntu, xubuntu kubuntu etc etc, but those are derivative projects not really spotlighted on ubuntu.com. Look at linux mint, you have all these different desktops listed on their homepage, if I'm a user I have no idea what to choose; so that being said I really hope we don't start going down the path of offering a whole crapton of desktops on the homepage, if someone is savvy enough to seek out a different desktop, all the power to him, but don't overwhelm the audience we're gathering to kill bug #1.

---

### Post by grahammechanical on 2015-11-18
I expect the default install of Ubuntu 16.04 to be much the same as at present. What is available for users to install is another matter. There are a lot of ideas and a lot of work to be done and as yet not much out there for the tester/experimenter to try. And the development period is now less than six months. And it should all be tested.

In the past, I messed with Xmir and Unity 8. I have Unity 8 session installed and it does not work with a proprietary video driver. Not that we can do much with it anyway. I have installed Ubuntu Desktop Next and that is no longer going anywhere. Recently I installed personal_x86.img which was mir + unity8 on snappy Ubuntu core and called Snappy Ubuntu Desktop Next and that seems to have come to a stand still.

I can tell you this. There is a big difference between the partition layout of traditional Ubuntu and that of Ubuntu Personal. In traditional Ubuntu we have the Ubuntu partition and a swap partition and a EFi boot partition if installing in UEFI mode.

In Ubuntu Personal there is the system boot partition, 2 system partitions and a writeable partition. No swap partition but that may change. Having two system partitions is necessary for transactional updates.

After installing Ubuntu resides in system-a partition. The next transactional update will go into system-b partition. But if the update is broken Grub will continue to boot Ubuntu from system-a. If the update succeeds then grub will boot Ubuntu from system-b. And the next update to the system will go into system-a. And so the updates to the system alternate between the system-a and the system-b partitions. It is neat. There will always be a bootable Ubuntu to load.

---

### Post by Andrew_Constantine on 2015-11-20
Won't that seriously impact available storage space though? I guess it depends on how big the system partitions are. It sounds like it's similar to kernel updates, old versions stick around in case it breaks something.

---

### Post by neu5eeCh on 2015-11-21
> **Andrew_Constantine said:**
> I really don't foresee them pushing something big into an LTS...

I don't either. That's why the current plan appears to be a choice between 7 or 8.

---

