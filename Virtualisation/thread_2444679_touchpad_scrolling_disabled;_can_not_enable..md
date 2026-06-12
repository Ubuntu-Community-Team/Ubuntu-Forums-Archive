---
title: "touchpad scrolling disabled; can not enable."
date: 2020-06-02
forum: Virtualisation
---

### Post by ajgreeny on 2020-06-02
I play around quite a lot using VBox (6.1.8 at present) on both my desktop and laptop machines to test alternative distros to my usual LTS Xubuntu and also to test intermediate versions.

It has become impossible to use the touchpad on the laptop for either edge or two finger scrolling and it's impossible to make any changes to the settings for this.  I realise the hardware is only virtual but I am pretty sure scrolling was possible in previous versions of VBox.  I'm not sure how to see the touchpad hardware details to see if that's related to this, but I wonder if any VBox users have had similar problems with this.

I have the guest Additions, same version as the VBox, installed in guests and working fine for everything else such as folder sharing, and on my desktop with a mouse, wheel scrolling works fine.  It's just the touchpad that is disabled.

I've searched the VBox forums but found nothing of any help.

---

### Post by &amp;KyT$0P# on 2020-06-11
> **ajgreeny said:**
> I wonder if any VBox users have had similar problems with this.

I might?

Not sure if this is a related problem, but ever since upgrading my host to Xubuntu 20.04, using my touchpad to scroll in VirtualBox guests is really insensitive and somewhat glitchy.  So much so that if I don't scroll the touchpad quickly enough, the scrolling appears to do nothing.  The host key logo in the bottom right does turn off while scrolling, so something is happening, it's like the scrolling speed is just set too slow to actually scroll.

Mouse wheel scrolling works fine for me too, as does touchpad scrolling in applications on the host.

I haven't tried to solve this yet.

---

### Post by ajgreeny on 2020-06-12
Yes, it sounds the same, which in practice makes the touchpad useless for scrolling.

I don't think I had this problem on an 18.04 host but haven't booted it for so long that I have now no recollection, so I will resurrect it and see what happens.

---

### Post by &amp;KyT$0P# on 2020-06-12
I use qt5ct, I tried changing qt5ct settings on the host, but it didn't seem to have any effect on this problem.

In my Xubuntu guests, I ran [FONT=Courier New]xev[/FONT] in terminal, moved the mouse cursor into xev's window and tried to scroll with the touchpad.  xev doesn't output anything for the touchpad when touchpad scrolling wouldn't do anything in other apps in the VM.  If I scroll with mouse wheel, xev outputs one ButtonPress and one ButtonRelease for each scroll notch.

This problem also occurs with a live CD as guest.  Looks like Guest Additions or not doesn't affect this problem.

ajgreeny, if you do resurrect your 18.04 host, what does this xev test give you under 18.04 host when you scroll with touchpad and mouse wheel?

How's touchpad scrolling in VirtualBox guests for people on 20.04 host that **doesn't** use XFCE?

---

### Post by ajgreeny on 2020-06-12
I haven't done this on my laptop yet but I did run 18.04 on my desktop this afternoon and updated the kernel, linux-image-generic-5.4.0-37 plus all the extra packages that come with it, to test the huge delay I and others have seen when installing kernel updates in guests, and that problem was immediately solved, the kernel installation took about 2 minutes rather than 31 minutes in a 20.04 host.
See [https://ubuntuforums.org/showthread.php?t=2445185](https://ubuntuforums.org/showthread.php?t=2445185)

I will certainly look into the touchpad problem by booting to 18.04 later on this laptop which I am using at the moment and will report back.
I am very suspicious of the VBox package for 20.04 and think this may be the cause of both of these problems.

Watch this space!

[COLOR="#FF0000"]EDIT[/COLOR]:
I have just booted to Xubuntu 18.04 and run the same Lubuntu 20.04 guest as I was running in 20.04 and using that host OS the touchpad scrolling is behaving as it should, so it seems that it is definitely the 20.04 VBox host system that is causing this.

Like you, I will be very interested to see if other DE versions of 20.04 also suffer in the same way but I am not going to install a different version to my system to test this; we will have to wait for others to respond.

---

### Post by &amp;KyT$0P# on 2020-06-30
bump

---

### Post by &amp;KyT$0P# on 2020-07-22
bump

---

### Post by &amp;KyT$0P# on 2020-10-10
Same story with a USB touchpad plugged into a desktop computer.

---

### Post by sudodus on 2020-10-10
> **halogen2 said:**
> 
How's touchpad scrolling in VirtualBox guests for people on 20.04 host that **doesn't** use XFCE?

I have VBox in standard Ubuntu 20.04.1 LTS. There are no guest additions. VBox is booted from the current Ubuntu Groovy iso file (seen as a virtual optical device).

I recognize your descriptions: There seems to be a threshold. I have to move the two fingers quickly to scroll, but then it works fairly well. This if different from two finger scrolling the the host system.

Otherwise things seem to work, for example tap to mark, three finger tap to paste (corresponding to middle clicking of the mouse).

---

