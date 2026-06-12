---
title: "Running Ubuntu in a virtual machine — on Android!"
date: 2022-02-16
forum: The Cafe
---

### Post by Paddy Landau on 2022-02-16
I saw last night that Android 13 will provide a [virtualisation option]("https://www.cnx-software.com/2022/02/14/android-13-virtualization-lets-pixel-6-run-windows-11-linux-distributions/").

This will allow you to run an OS — Linux (e.g. Ubuntu), even Windows 11 — on an Android 13 tablet or phone.

I find this pretty cool.

---

### Post by DuckHook on 2022-02-16
Paddy, you're a gem. O:)

And this, just as I'm considering going the opposite direction: [https://www.pine64.org/pinephonepro/](https://www.pine64.org/pinephonepro/)

Though any sort of Linux functionality would be welcome in Android, I'm getting more and more pissed off with Android every day. The foundational structure of Android has never been trustworthy. Google pilots that ship and it goes where they want it to go. This is at odds with what I believe is good for me.

I want a Linux phone that will run Android in a VM. Now, *that* would be *hugely* appealing.

---

### Post by Paddy Landau on 2022-02-17
> **DuckHook said:**
> And this, just as I'm considering going the opposite direction: [https://www.pine64.org/pinephonepro/](https://www.pine64.org/pinephonepro/)
That's interesting. I know that there have been prior attempts to do this sort of thing, including Canonical's failed attempt with Ubuntu.
> **DuckHook said:**
> … I'm getting more and more pissed off with Android every day. The foundational structure of Android has never been trustworthy. Google pilots that ship and it goes where they want it to go.
Well, this is true of every proprietary system: Android, iOS, MacOS, Windows, and some others.

The thing is, today, you need either Android or iPhone. For example, it's how I use GPS in my car and sometimes when walking.
> **DuckHook said:**
> I want a Linux phone that will run Android in a VM.
Then, you'd still have Android!

From a functional point of view, I don't know if there'd be any difference between running a Linux and Windows VM on Android, or an Android and Windows VM on Linux.

And now, just to make things even more interesting, last night I came across brand new [Chrome OS Flex]("https://chromeenterprise.google/os/chromeosflex/") — A way to have Chrome OS running on any PC or Mac. I'm going to try putting it into a VM, to see what happens.

---

### Post by DuckHook on 2022-02-17
> **Paddy Landau said:**
> That's interesting. I know that there have been prior attempts to do this sort of thing, including Canonical's failed attempt with Ubuntu.
I suspect Shuttleworth didn't really have his heart in it. Frankly, I can understand that. It's easy for those of us in the peanut gallery to egg him on with shouts of encouragement, but it was his bucks on the line and when the crowdfunding fell short, he did what any prudent businessman would—cut his losses and run.

Times are different now. I think the Pinephone will succeed.
> Well, this is true of every proprietary system: Android, iOS, MacOS, Windows, and some others.
Exactly. And I don't trust any of them.
> The thing is, today, you need either Android or iPhone. For example, it's how I use GPS in my car and sometimes when walking.
I do the same. But it can be done with either more privacy or with less. As an example, while I leverage Google Maps, I do so without signing in. This reduces their ability to track me. In fact, I use my phone without the Google account activated. I'm hitched into my private Nextcloud instead.
> Then, you'd still have Android!
True, but the devil is in the details. Android running as a VM can be effectively contained. Android on bare metal is much harder to jail. Further, I can offload way more functions to my foundational (and trustworthy) Linux instance, thus reducing my reliance on Android to all but a few apps.

Example: in theory, I can set up a pihole on the Pinephone and force all Android apps to go through it. This would stop all apps from reporting my usage back to mothership. I suppose this can be done on Android proper, but it involves rooting the phone and installing a bunch of third party stuff that I don't really know or trust. And even then, it's not guaranteed to work.
> From a functional point of view, I don't know if there'd be any difference between running a Linux and Windows VM on Android, or an Android and Windows VM on Linux.
Oh, there's a big difference. When trying to control untrusted apps, it's always better to have them confined to a VM. And as I've said, I don't trust Android. At all. In its entirety. Not one little bit.
> And now, just to make things even more interesting, last night I came across brand new [Chrome OS Flex]("https://chromeenterprise.google/os/chromeosflex/") — A way to have Chrome OS running on any PC or Mac. I'm going to try putting it into a VM, to see what happens.
Please let us know how it goes. I have no curiosity about Chrome OS whatsoever, but I can see its use case.

---

### Post by Paddy Landau on 2022-02-17
> **DuckHook said:**
> Please let us know how it goes. I have no curiosity about Chrome OS whatsoever, but I can see its use case.
I failed to get it to install on the VM.

Google has created an odd way of going about it, and it doesn't provide an ISO. Instead, you have to use the Chrome browser on a Windows, Chromebook or Mac machine to [create a bootable USB stick]("https://support.google.com/chromeosflex/answer/11552529?ref_topic=11551271"). It's bizarre, but there's no other way to do it!

Anyway, I did that (using my VM copy of Windows). But, when I booted off it (in a new VM), it failed to start correctly, so I couldn't proceed.

I've asked for help on the official help forum, but thus far there has been no reply. I rather suspect that it simply won't be supported on a VM.

---

### Post by DuckHook on 2022-02-17
> **Paddy Landau said:**
> I failed to get it to install on the VM.

Google has created an odd way of going about it, and it doesn't provide an ISO. Instead, you have to use the Chrome browser on a Windows, Chromebook or Mac machine to [create a bootable USB stick]("https://support.google.com/chromeosflex/answer/11552529?ref_topic=11551271"). It's bizarre, but there's no other way to do it!

Anyway, I did that (using my VM copy of Windows). But, when I booted off it (in a new VM), it failed to start correctly, so I couldn't proceed.

I've asked for help on the official help forum, but thus far there has been no reply. I rather suspect that it simply won't be supported on a VM.
Disappointing, but no surprise. More Google vendor lock&#8209;in. Only Chrome browser. No ISO. No VM. That's their new shtick: supporting FOSS as a mercenary exercise while undermining its principles.

I do hope you get it working though, if only to spite Google (which is purely my personal grudge).

---

### Post by #&amp;thj^% on 2022-02-17
> **DuckHook said:**
> 
Times are different now. I think the Pinephone will succeed.



I have been watching with some interest as well.
NOTE:Non Official but they are now considering Arch based OS....(Again Non Official not meant for DuckHook but others reading )

---

